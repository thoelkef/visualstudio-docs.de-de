---
title: "Zugreifen auf Textebenen über die Legacy-API | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text layers
ms.assetid: 2258fcdd-38d1-479d-b8f8-1d4e6525f72c
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 8a5f7a80e8d594f3c9e62ecd2047cc1116948d2c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="accessing-text-layers-by-using-the-legacy-api"></a>Zugreifen auf Textebenen über die Legacy-API
Eine Ebene kapselt normalerweise einige Aspekte der TextLayout. Eine Ebene "-Funktion-am-a-Time" Blendet z. B. Text, vor und nach einer Funktion, die das Caretzeichen (Texteinfügemarke) enthält.  
  
 Eine Ebene zwischen einen Puffer und einer Ansicht befindet, und ändert die Möglichkeit, die die Sicht der Pufferinhalt angezeigt.  
  
## <a name="text-layer-information"></a>Textinformationen-Ebene  
 Die folgende Liste beschreibt die Funktionsweise von Ebenen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]:  
  
-   Der Text in einem Textebene kann mit Syntaxfarben und Marker gestaltet werden.  
  
-   Sie dürfen keine eigene Ebenen derzeit implementieren.  
  
-   Stellt eine Ebene <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>, abgeleitet aus <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>. Die Textpuffer selbst wird auch als eine Schicht implementiert, dadurch kann eine Ansicht, um die darunter liegenden Ebenen polymorph zu verarbeiten.  
  
-   Zwischen der Ansicht und der Puffer kann eine beliebige Anzahl von Ebenen liegen. Jede Ebene betrifft nur die Ebene darunter, und die Ansicht befasst sich größtenteils mit der obersten Ebene. Einige Informationen über den Puffer (es ist erforderlich.)  
  
-   Eine Ebene kann nur Ebenen auswirken, die darunter liegenden sind. Sie haben keine Auswirkungen der darüber liegenden Ebenen hinter Standardereignissen Ursprung auf.  
  
-   Im Editor werden ausgeblendetem Text, synthetischen Text und Zeilenumbruch als Ebenen implementiert. Sie können ausgeblendete und synthetische Text implementieren, ohne direkte Interaktion mit den Ebenen. Weitere Informationen finden Sie unter [Gliederung im ein Legacy-Sprachdienst](../extensibility/internals/outlining-in-a-legacy-language-service.md) und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSyntheticTextSession>.  
  
-   Jede Ebene weist ein eigenen lokale Koordinatensystem, die durch verfügbar gemacht wird die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer> Schnittstelle. Die Zeilenumbruch Ebene kann z. B. zwei Zeilen enthalten, während die zugrunde liegenden Textpuffer möglicherweise nur eine Zeile enthalten.  
  
-   Die Ansicht kommuniziert mit den Ebenen über der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView> Schnittstelle. Verwenden Sie diese Schnittstelle, um Koordinaten mit Puffer Koordinaten abstimmen.  
  
-   Eine Ebene, z. B. die synthetische Textebene, die Text stammt eine lokale Implementierung bereitstellen muss <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A>.  
  
-   Neben <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>, eine Ebene muss implementieren <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> und das Auslösen der Ereignisse in der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents> Schnittstelle.  
  
## <a name="see-also"></a>Siehe auch  
 [Syntaxfarben in benutzerdefinierten Editoren](../extensibility/syntax-coloring-in-custom-editors.md)   
 [Verwenden von Text Marker mit der Legacy-API](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Anpassen von Editor-Steuerelemente und Menüs, über die Legacy-API](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)