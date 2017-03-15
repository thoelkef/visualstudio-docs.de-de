---
title: "Zugreifen auf Textebenen mithilfe der Legacy-API | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Editoren [Visual Studio SDK] legacy - Textebenen"
ms.assetid: 2258fcdd-38d1-479d-b8f8-1d4e6525f72c
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Zugreifen auf Textebenen mithilfe der Legacy-API
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Eine Text der Ebene kapselt normalerweise alle Aspekte der Textlayouts.  Zum Beispiel simsen Felle einer „FUNCTION\-an\-ein TIMEs“ Ebene vor und nach einer Funktion, die die Einfügemarke enthält \(Texteinfügemarke\).  
  
 Eine Text der Ebene befindet sich zwischen einem Puffer und einer Ansicht und ändert die Art und Weise die Ansicht der Inhalt des Puffers anzuzeigen.  
  
## Text\-Ebenen\-Informationen  
 In der folgenden Liste wird beschrieben, wie Text in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Ebenen arbeiten:  
  
-   Der Text in a Text der Ebene kann mit Markern und Syntaxfarbe verziert werden.  
  
-   Sie können nicht nur implementieren, Ebenen verfügen.  
  
-   Eine Ebene verfügbar macht <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>, die von <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>abgeleitet ist.  Der Textpuffer selbst wird auch als Stufe implementiert, die eine Ansicht ermöglicht, polymorphically zugrunde liegenden Ebenen zu arbeiten.  
  
-   Beliebige Anzahl von Ebenen befindet sich zwischen der Ansicht und dem Puffer.  Jede Ebene behandelt nur die Ebene unterhalb sie, und die Ansicht verarbeitet größtenteils die oberste Ebene.  \(Die Ansicht enthält einige Informationen über den Puffer.\)  
  
-   Eine Ebene kann nur Ebenen auswirken, die unter sie sind.  Es kann die Ebenen darüber über das Auslösen von Ereignissen Standard nicht hinaus auswirken.  
  
-   Im Editor wird ausgeblendeter Text, synthetischer Text und Zeilenvorschub als Ebenen implementiert.  Sie können auch ausgeblendeter Text synthetischen implementieren, ohne direkt mit den Ebenen zu interagieren.  Weitere Informationen finden Sie unter [Gliederung im ein Legacy\-Sprachdienst](../extensibility/internals/outlining-in-a-legacy-language-service.md) und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSyntheticTextSession>.  
  
-   Jede Text Anwendungsebene hat ein eigenes lokales Koordinatensystem, das von der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>\-Schnittstelle verfügbar gemacht wird.  Die Zeile Umbruch Ebene könnte beispielsweise zwei Zeilen, während der zugrunde liegenden Textpuffer möglicherweise nur eine Zeile enthält.  
  
-   Die Ansicht wird mit Ebenen von der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>\-Schnittstelle.  Verwenden Sie diese Schnittstelle, um Puffer mit Koordinaten Ansicht Koordinaten zuzuordnen.  
  
-   Jede Ebene wie die synthetische Text der Ebene, die Text auslöst, muss eine lokale Implementierung des <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A>bereitstellen.  
  
-   Neben <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>muss eine Text der Ebene <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> implementieren und die Ereignisse in der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>\-Schnittstelle auslösen.  
  
## Siehe auch  
 [Syntaxfarben in benutzerdefinierten Editoren](../extensibility/syntax-coloring-in-custom-editors.md)   
 [Verwenden von Text Marker mit der Legacy\-API](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Anpassen von Editor\-Steuerelemente und Menüs mit der Legacy\-API](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)