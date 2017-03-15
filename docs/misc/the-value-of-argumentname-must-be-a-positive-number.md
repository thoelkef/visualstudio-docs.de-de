---
title: "Der Wert von &lt;argumentname&gt; muss eine positive Zahl sein | Microsoft Docs"
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
  - "vbrApplicationLog_NegativeNumber"
ms.assetid: 597c412c-499e-49d2-b656-af2d90c292a5
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Der Wert von &lt;argumentname&gt; muss eine positive Zahl sein
Der Wert der Eigenschaft <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A> muss größer als null sein.  
  
 Die <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A>\-Eigenschaft gibt die Menge des verfügbaren Speicherplatzes auf dem Datenträger in Byte an, was erforderlich ist, damit Nachrichten in die Protokolldatei geschrieben werden können  
  
### So beheben Sie diesen Fehler  
  
-   Legen Sie die <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A>\-Eigenschaft auf eine positive Zahl fest.  
  
## Siehe auch  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A>   
 [My.Application.Log\-Objekt](/dotnet/visual-basic/language-reference/objects/my-application-log-object)   
 [My.Log Object](/dotnet/visual-basic/language-reference/objects/my-log-object)