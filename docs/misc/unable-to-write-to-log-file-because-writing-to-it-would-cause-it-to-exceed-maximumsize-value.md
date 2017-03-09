---
title: "In der Protokolldatei kann nicht geschrieben werden, weil dies dazu f&#252;hren w&#252;rde, dass sie den MaximumSize-Wert &#252;berschreitet. | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrApplicationLog_FileExceedsMaximumSize"
ms.assetid: 61747a9c-e460-424b-a365-73cdba9dd428
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# In der Protokolldatei kann nicht geschrieben werden, weil dies dazu f&#252;hren w&#252;rde, dass sie den MaximumSize-Wert &#252;berschreitet.
Die <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>\-Klasse konnte aus folgendem Grund nicht in die Protokolldatei schreiben:  
  
-   Die Größe der Protokolldatei \(in Bytes\) ist größer als der Wert der <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A>\-Eigenschaft.  
  
     \- und \-  
  
-   Der Wert der <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>\-Eigenschaft ist <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption>.  
  
### So beheben Sie diesen Fehler  
  
1.  Archivieren Sie die vorhandenen Protokolle, und entfernen Sie diese vom Computer, damit das <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>\-Objekt neue Protokolle erstellen kann.  
  
2.  Ändern Sie den Wert der <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A>\-Eigenschaft, um größere Protokolle zuzulassen.  
  
3.  Legen Sie die <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>\-Eigenschaft auf <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption> fest, um Nachrichten ohne Warnung zu verwerfen, wenn das Protokoll zu groß ist.  
  
## Siehe auch  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A>   
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>   
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>   
 [My.Application.Log\-Objekt](/dotnet/visual-basic/language-reference/objects/my-application-log-object)   
 [My.Log Object](/dotnet/visual-basic/language-reference/objects/my-log-object)