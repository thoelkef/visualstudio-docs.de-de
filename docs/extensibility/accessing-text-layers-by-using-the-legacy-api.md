---
title: Zugreifen auf Textebenen mithilfe der Legacy-API | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text layers
ms.assetid: 2258fcdd-38d1-479d-b8f8-1d4e6525f72c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a0ba962ba4c18773b5c85480bce62ab728cab307
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62892232"
---
# <a name="access-text-layers-by-using-the-legacy-api"></a>Text Datenzugriffsebenen mithilfe der legacy-API
Eine Textebene kapselt normalerweise einen Aspekt des Textlayouts. Beispielsweise blendet eine Ebene "-Funktion-at-a-Time" Text vor und nach einer Funktion, die die Einfügemarke (Einfügemarke) enthält.

 Eine Textebene befindet sich zwischen einem Puffer und einer Ansicht, und ändert die Möglichkeit, die die Sicht die Inhalte des Puffers angezeigt wird.

## <a name="text-layer-information"></a>Textinformationen-Ebene
 Die folgende Liste beschreibt die Funktionsweise der Textebenen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]:

- Der Text in einem Textebene kann mit farbige syntaxmarkierung und Markierung versehen werden.

- Sie können derzeit nicht Ihre eigenen Schichten implementieren.

- Stellt eine Ebene <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>, ergibt sich aus <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>. Textpuffer selbst wird ebenfalls als eine Ebene implementiert, dem eine Ansicht für die zugrunde liegenden Schichten polymorph behandeln zu können.

- Eine beliebige Anzahl von Ebenen kann zwischen der Ansicht und der Puffer liegen. Jede Schicht behandelt nur die darunter liegende Ebene aus, und die Ansicht befasst sich hauptsächlich mit der obersten Ebene. (Die Ansicht einige Informationen über den Puffer verfügen.)

- Eine Schicht kann nur Schichten auswirken, die darunter liegenden sind. Dies kann nicht auf die darüber liegenden Ebenen über stammen von Standardereignissen auswirken.

- Im Editor werden ausgeblendetem Text, synthetischen Text und Zeilenumbruch als Ebenen implementiert werden. Sie können die synthetischen ein- und ausgeblendeten Text implementieren, ohne direkte Interaktion mit den Ebenen. Weitere Informationen finden Sie unter [Gliederung in einem legacysprachdiensten](../extensibility/internals/outlining-in-a-legacy-language-service.md) und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSyntheticTextSession>.

- Jede Textebene verfügt über einen eigenen lokalen Koordinatensystem, die durch verfügbar gemacht wird die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer> Schnittstelle. Die Wrap-Zeile-Ebene, kann z. B. zwei Zeilen enthalten, während der zugrunde liegenden Textpuffer nur eine Zeile enthalten kann.

- Die Sicht eine Verbindung mit Ebenen über der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView> Schnittstelle. Verwenden Sie diese Schnittstelle, um die Koordinaten der Strukturansicht mit pufferkoordinaten abstimmen.

- Eine Ebene, z. B. die synthetischen Textebene, die Text erstellt eine lokale Implementierung bereitstellen muss <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A>.

- Darüber hinaus <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>, muss eine Textebene implementieren <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> und Auslösen der Ereignisse in der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents> Schnittstelle.

## <a name="see-also"></a>Siehe auch
- [Syntaxfarben in benutzerdefinierten Editoren](../extensibility/syntax-coloring-in-custom-editors.md)
- [Verwenden von Textmarkierungen mit der legacy-API](../extensibility/using-text-markers-with-the-legacy-api.md)
- [Passen Sie Editor-Steuerelemente und Menüs an, indem Sie mithilfe der legacy-API](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)