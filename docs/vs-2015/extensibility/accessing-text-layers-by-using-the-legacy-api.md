---
title: Zugreifen auf Textebenen mithilfe der Legacy-API | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text layers
ms.assetid: 2258fcdd-38d1-479d-b8f8-1d4e6525f72c
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6ae3c134fb97b7ec899dc63c2f0d23420390302d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58947013"
---
# <a name="accessing-text-layers-by-using-the-legacy-api"></a>Zugreifen auf Textebenen mithilfe der Legacy-API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Eine Textebene kapselt normalerweise einen Aspekt des Textlayouts. Beispielsweise blendet eine Ebene "-Funktion-at-a-Time" Text vor und nach einer Funktion, die die Einfügemarke (Einfügemarke) enthält.  
  
 Eine Textebene befindet sich zwischen einem Puffer und einer Ansicht, und ändert die Möglichkeit, die die Sicht die Inhalte des Puffers angezeigt wird.  
  
## <a name="text-layer-information"></a>Textinformationen-Ebene  
 Die folgende Liste beschreibt die Funktionsweise der Textebenen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]:  
  
-   Der Text in einem Textebene kann mit farbige syntaxmarkierung und Markierung versehen werden.  
  
-   Sie können derzeit nicht Ihre eigenen Schichten implementieren.  
  
-   Stellt eine Ebene <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>, ergibt sich aus <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>. Textpuffer selbst wird ebenfalls als eine Ebene implementiert, dem eine Ansicht für die zugrunde liegenden Schichten polymorph behandeln zu können.  
  
-   Eine beliebige Anzahl von Ebenen kann zwischen der Ansicht und der Puffer liegen. Jede Schicht behandelt nur die darunter liegende Ebene aus, und die Ansicht befasst sich hauptsächlich mit der obersten Ebene. (Die Ansicht einige Informationen über den Puffer verfügen.)  
  
-   Eine Schicht kann nur Schichten auswirken, die darunter liegenden sind. Dies kann nicht auf die darüber liegenden Ebenen über stammen von Standardereignissen auswirken.  
  
-   Im Editor werden ausgeblendetem Text, synthetischen Text und Zeilenumbruch als Ebenen implementiert werden. Sie können die synthetischen ein- und ausgeblendeten Text implementieren, ohne direkte Interaktion mit den Ebenen. Weitere Informationen finden Sie unter [Gliederung in einem Legacysprachdienst](../extensibility/internals/outlining-in-a-legacy-language-service.md) und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSyntheticTextSession>.  
  
-   Jede Textebene verfügt über einen eigenen lokalen Koordinatensystem, die durch verfügbar gemacht wird die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer> Schnittstelle. Die Wrap-Zeile-Ebene, kann z. B. zwei Zeilen enthalten, während der zugrunde liegenden Textpuffer nur eine Zeile enthalten kann.  
  
-   Die Sicht eine Verbindung mit Ebenen über der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView> Schnittstelle. Verwenden Sie diese Schnittstelle, um die Koordinaten der Strukturansicht mit pufferkoordinaten abstimmen.  
  
-   Eine Ebene, z. B. die synthetischen Textebene, die Text erstellt eine lokale Implementierung bereitstellen muss <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A>.  
  
-   Darüber hinaus <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>, muss eine Textebene implementieren <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> und Auslösen der Ereignisse in der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents> Schnittstelle.  
  
## <a name="see-also"></a>Siehe auch  
 [Syntaxfarben in benutzerdefinierten Editoren](../extensibility/syntax-coloring-in-custom-editors.md)   
 [Verwenden von Textmarkierungen mit der Legacy-API](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Anpassen von Editorfarben und -menüs mit der Legacy-API](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)
