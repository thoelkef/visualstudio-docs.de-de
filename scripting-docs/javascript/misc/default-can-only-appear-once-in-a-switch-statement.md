---
title: "&quot;default&quot; darf in einer switch-Anweisung nur einmal angegeben werden | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.WebClient.Help.SCRIPT1027"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: a94100f4-6ee5-4759-b635-9d309e47111e
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# &quot;default&quot; darf in einer switch-Anweisung nur einmal angegeben werden
Sie haben versucht, die **default**\-Anweisung mehrmals innerhalb einer switch\-Anweisung zu verwenden.  Der Standardfall ist immer die letzte case\-Anweisung in einer switch\-Anweisung \(es ist der Fortfahrenfall\).  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie zusätzliche **default** \-case\-Anweisungen aus der `switch`\-Anweisung \(verwenden Sie höchstens eine als "default" deklarierte case\-Anweisung in der switch\-Anweisung\).  
  
## Siehe auch  
 [switch\-Anweisung](../../javascript/reference/switch-statement-javascript.md)   
 [Steuerung des Programmablaufs](../../javascript/controlling-program-flow-javascript.md)   
 [Reservierte Wörter in JavaScript](../../javascript/reference/javascript-reserved-words.md)