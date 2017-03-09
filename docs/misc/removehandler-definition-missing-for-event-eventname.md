---
title: "Die RemoveHandler-Definition fehlt f&#252;r das &quot;&lt;Ereignisname&gt;&quot;-Ereignis. | Microsoft Docs"
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
  - "bc31131"
  - "vbc31131"
helpviewer_keywords: 
  - "BC31131"
ms.assetid: 0ef68daf-b66e-4ecf-bf2c-dcacabd8aa3d
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die RemoveHandler-Definition fehlt f&#252;r das &quot;&lt;Ereignisname&gt;&quot;-Ereignis.
Wenn ein Ereignis als `Custom` deklariert wird, müssen sie ein Verfahren zum Entfernen eines Ereignishandlers bereitstellen.  
  
 **Fehler\-ID:** BC31131  
  
### So beheben Sie diesen Fehler  
  
1.  Fügen Sie eine `RemoveHandler`\-Deklaration zwischen der `Custom Event`\-Anweisung und der `End Event`\-Anweisung ein.  
  
2.  Stellen Sie sicher, dass andere Prozeduren innerhalb der Ereignisdeklaration korrekt abgeschlossen sind.  
  
## Siehe auch  
 [RemoveHandler Statement](/dotnet/visual-basic/language-reference/statements/removehandler-statement)   
 [Event Statement](/dotnet/visual-basic/language-reference/statements/event-statement)