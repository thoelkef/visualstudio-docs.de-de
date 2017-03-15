---
title: "Die Protokolldatei kann nicht geschrieben werden, weil das Schreiben in diese Datei dazu f&#252;hren w&#252;rde, dass der freie Speicherplatz auf dem Datentr&#228;ger unter den ReservedSpace-Wert absinkt. | Microsoft Docs"
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
  - "vbrApplicationLog_ReservedSpaceEncroached"
ms.assetid: 95832e70-4ecc-47aa-90c1-f35c4d468151
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die Protokolldatei kann nicht geschrieben werden, weil das Schreiben in diese Datei dazu f&#252;hren w&#252;rde, dass der freie Speicherplatz auf dem Datentr&#228;ger unter den ReservedSpace-Wert absinkt.
Die <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>\-Klasse konnte aus diesem Grund nicht in die Protokolldatei schreiben:  
  
-   Die Menge des freien Speicherplatzes \(in Byte\) ist kleiner als der Wert der <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A>\-Eigenschaft  
  
     – und –  
  
-   Der Wert der <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>\-Eigenschaft ist <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption>.  
  
### So beheben Sie diesen Fehler  
  
1.  Archivieren Sie die vorhandenen Protokolle, und entfernen Sie diese vom Computer, damit das <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>\-Objekt neue Protokolle erstellen kann.  
  
2.  Ändern Sie den Wert der <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A>\-Eigenschaft in einen kleinere Zahl, um weniger Speicherplatz auf dem Datenträger zu reservieren.  
  
3.  Legen Sie die <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>\-Eigenschaft auf <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption> fest, um Nachrichten ohne Warnung zu verwerfen, wenn nicht genügend freier Speicherplatz verfügbar ist.  
  
## Siehe auch  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A>   
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>   
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>   
 [My.Application.Log\-Objekt](/dotnet/visual-basic/language-reference/objects/my-application-log-object)   
 [My.Log Object](/dotnet/visual-basic/language-reference/objects/my-log-object)