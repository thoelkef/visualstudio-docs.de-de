---
title: "Gewusst wie: Verwenden des Animationsbereichs der Statusleiste | Microsoft Docs"
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
  - "Statusleiste, Programmierung"
  - "Statusleiste, Animationsbereich"
  - "Animationsbereich, Statusleiste"
ms.assetid: ec6fb915-7bc8-4a90-8156-70c1a243caff
caps.latest.revision: 14
caps.handback.revision: 14
manager: "douge"
---
# Gewusst wie: Verwenden des Animationsbereichs der Statusleiste
Der Animation [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Bereich der Statusleiste wird eine Schleife Animation an, die entweder einen längeren Vorgangs oder einen Vorgang der unbestimmten Länge angibt \(z. B. mehrere Projekte in einer Projektmappe erstellen\).  
  
### Um den Bereich der Visual Studio\-Statusleiste Animationen verwenden  
  
1.  Rufen Sie eine Instanz der <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar>\-Schnittstelle, die von den <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> Dienst bereitgestellt wird.  
  
2.  Starten Sie die Animation, indem Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.Animation%2A>\-Methode der Statusleiste aufrufen.  Übergeben Sie 1 als Wert des ersten Parameters und ein Verweis auf einen animierten Symbol als der Wert des zweiten Parameters.  
  
3.  Beenden Sie die Animation, indem Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.Animation%2A>\-Methode der Statusleiste aufrufen.  Übergeben Sie 0 als Wert des ersten Parameters und ein Verweis auf den animierten Symbol als der Wert des zweiten Parameters.  
  
## Beispiel  
 In diesem Beispiel wird veranschaulicht, wie eine integrierte Animation im Bereich Animation ausgeführt wird.  
  
 [!code-cs[VSSDKAnimationStatusBar#1](../misc/codesnippet/CSharp/how-to-use-the-animation-region-of-the-status-bar_1.cs)]
 [!code-vb[VSSDKAnimationStatusBar#1](../misc/codesnippet/VisualBasic/how-to-use-the-animation-region-of-the-status-bar_1.vb)]  
  
## Siehe auch  
 [Erweitern Sie die Statusleiste](../extensibility/extending-the-status-bar.md)   
 [Gewusst wie: Lesen aus und Schreiben in die Feedbackbereich der Statusleiste](../misc/how-to-read-from-and-write-to-the-feedback-region-of-the-status-bar.md)   
 [Gewusst wie: Programmieren des Statusanzeigenbereichs der Statusleiste](../misc/how-to-program-the-progress-bar-region-of-the-status-bar.md)   
 [Gewusst wie: Programmieren des Designerbereichs der Statusleiste](../misc/how-to-program-the-designer-region-of-the-status-bar.md)