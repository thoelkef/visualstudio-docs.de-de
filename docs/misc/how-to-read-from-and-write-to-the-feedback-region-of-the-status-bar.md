---
title: "Gewusst wie: Lesen aus und Schreiben in die Feedbackbereich der Statusleiste | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Feedbackbereich, Statusleiste"
  - "Statusleiste, Feedbackbereich"
  - "Statusleiste, Übersicht"
ms.assetid: e639561c-e1e7-4660-b2a2-8bca80f34a29
caps.latest.revision: 12
caps.handback.revision: 12
manager: "douge"
---
# Gewusst wie: Lesen aus und Schreiben in die Feedbackbereich der Statusleiste
Der Bereich der Statusleiste anzeigen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Feed\-back simsen.  Sie können Text, wird durch statischen Text festlegen und abrufen und heben Sie den angezeigten Text hervor.  
  
### Um den Bereich der Visual Studio\-Statusleiste Feed\-back verwenden  
  
1.  Rufen Sie eine Instanz der <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar>\-Schnittstelle, die von den <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> Dienst bereitgestellt wird.  
  
2.  Bestimmen, ob die Statusleiste fixiert ist, indem Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.IsFrozen%2A>\-Methode der <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar>\-Instanz aufrufen.  
  
3.  Legen Sie den Text des Bereichs Feed\-back fest, indem Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.SetText%2A>\-Methode aufgerufen haben und in eine Textzeichenfolge haben.  
  
4.  Lesen Sie den Text des Bereichs Feed\-back, indem Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.GetText%2A>\-Methode aufgerufen haben.  
  
## Beispiel  
 In diesem Beispiel wird veranschaulicht, wie Text im Bereich Feed\-back Text geschrieben und gelesen wird.  
  
 [!code-cs[VSSDKFeedbackStatusBar#1](../misc/codesnippet/CSharp/how-to-read-from-and-write-to-the-feedback-region-of-the-status-bar_1.cs)]
 [!code-vb[VSSDKFeedbackStatusBar#1](../misc/codesnippet/VisualBasic/how-to-read-from-and-write-to-the-feedback-region-of-the-status-bar_1.vb)]  
  
 Im obigen Beispiel wird der Code die folgenden Aufgaben aus:  
  
-   Ruft eine Instanz der <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar>\-Schnittstelle aus dem <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> Dienst.  
  
-   Überprüft, ob die Statusleiste fixiert werden, indem Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.IsFrozen%2A>\-Methode aufruft.  
  
-   Unterdrückt weitere Aktualisierungen der Statusleiste durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.FreezeOutput%2A>\-Methode.  
  
-   Liest den Text von der Statusleiste durch das Aufrufen der Methode <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.GetText%2A> und in einem Meldungsfeld angezeigt.  
  
-   Ermöglicht die Aktualisierungen der Statusleiste durch Aufrufen von <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.FreezeOutput%2A> und Übergeben von Parametern in 0.  
  
-   Löscht den Inhalt der Statusleiste durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.Clear%2A>\-Methode.  
  
## Siehe auch  
 [Erweitern Sie die Statusleiste](../extensibility/extending-the-status-bar.md)   
 [Gewusst wie: Programmieren des Statusanzeigenbereichs der Statusleiste](../misc/how-to-program-the-progress-bar-region-of-the-status-bar.md)   
 [Gewusst wie: Verwenden des Animationsbereichs der Statusleiste](../misc/how-to-use-the-animation-region-of-the-status-bar.md)   
 [Gewusst wie: Programmieren des Designerbereichs der Statusleiste](../misc/how-to-program-the-designer-region-of-the-status-bar.md)