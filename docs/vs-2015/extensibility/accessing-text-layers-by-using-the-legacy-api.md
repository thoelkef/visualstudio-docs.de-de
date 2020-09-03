---
title: Zugreifen auf Text Ebenen mithilfe der Legacy-API | Microsoft-Dokumentation
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
ms.openlocfilehash: 975e8624a6ffbfe0c5ae7544f2b978487465e34e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148026"
---
# <a name="accessing-text-layers-by-using-the-legacy-api"></a>Zugreifen auf Textebenen mithilfe der Legacy-API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Eine Text Ebene kapselt in der Regel einen Aspekt des Textlayouts. Beispielsweise blendet eine "Function-at-a-Time"-Ebene Text vor und nach einer Funktion aus, die die Einfügemarke (Text Einfügemarke) enthält.  
  
 Eine Text Ebene befindet sich zwischen einem Puffer und einer Ansicht und ändert die Art und Weise, wie die Ansicht den Inhalt des Puffers sieht.  
  
## <a name="text-layer-information"></a>Textebeneninformationen  
 In der folgenden Liste wird beschrieben, wie Textebenen in funktionieren [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] :  
  
- Der Text in einer Text Ebene kann mit Syntax Farben und Markierungen versehen werden.  
  
- Sie können derzeit keine eigenen Ebenen implementieren.  
  
- Eine Ebene <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer> macht verfügbar, die von abgeleitet ist <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> . Der Text Puffer selbst wird auch als Schicht implementiert, sodass eine Ansicht polymorph mit zugrunde liegenden Ebenen umgehen kann.  
  
- Zwischen der Ansicht und dem Puffer kann eine beliebige Anzahl von Ebenen liegen. Jede Ebene ist nur mit der darunter liegenden Ebene zu tun, und die Ansicht befasst sich größtenteils mit der obersten Ebene. (Die Ansicht enthält einige Informationen über den Puffer.)  
  
- Eine Ebene kann sich nur auf darunter liegenden Ebenen auswirken. Sie kann sich nicht auf die übergeordneten Ebenen außerhalb der Ursprungs Standard Ereignisse auswirken.  
  
- Im Editor werden ausgeblendeter Text, synthetischer Text und Zeilenumbruch als Ebenen implementiert. Sie können ausgeblendeten und synthetischen Text implementieren, ohne direkt mit den Ebenen zu interagieren. Weitere Informationen finden Sie Untergliederung [in einem Legacy Sprachdienst](../extensibility/internals/outlining-in-a-legacy-language-service.md) und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSyntheticTextSession> .  
  
- Jede Textschicht verfügt über ein eigenes lokales Koordinatensystem, das über die-Schnittstelle verfügbar gemacht wird <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer> . Die Zeilenumbruch Ebene kann z. b. zwei Zeilen enthalten, während der zugrunde liegende Text Puffer möglicherweise nur eine Zeile enthält.  
  
- Die Ansicht kommuniziert mit Ebenen über die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView> Schnittstelle. Verwenden Sie diese Schnittstelle, um Ansichts Koordinaten mit Puffer Koordinaten abzustimmen.  
  
- Jede Ebene, z. b. die synthetische Text Schicht, von der Text stammt, muss eine lokale Implementierung von bereitstellen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A> .  
  
- Außerdem <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer> muss eine Textebene <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> die Ereignisse in der-Schnittstelle implementieren und auslösen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents> .  
  
## <a name="see-also"></a>Weitere Informationen  
 [Syntax Farbgebung in benutzerdefinierten Editoren](../extensibility/syntax-coloring-in-custom-editors.md)   
 [Verwenden von Text Markern mit der Legacy-API](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Anpassen von Editorfarben und -menüs mit der Legacy-API](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)
