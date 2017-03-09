---
title: "&quot;End AddHandler&quot; muss die erste Anweisung in einer Zeile sein | Microsoft Docs"
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
  - "bc31118"
  - "vbc31118"
helpviewer_keywords: 
  - "BC31118"
ms.assetid: 70371cd4-207f-4e0f-b18d-1be510781b66
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;End AddHandler&quot; muss die erste Anweisung in einer Zeile sein
Eine `End AddHandler`\-Anweisung folgt auf einen als Anweisungstrennzeichen verwendeten Doppelpunkt \(:\). In der entsprechenden Quellzeile darf nur `End AddHandler` als Anweisung vorkommen.  
  
 **Fehler\-ID:** BC31118  
  
### So beheben Sie diesen Fehler  
  
-   Setzen Sie jede Anweisung in eine eigene Zeile.  
  
## Siehe auch  
 [Gewusst wie: Umbrechen und Zusammenfassen von Anweisungen in Code](../Topic/How%20to:%20Break%20and%20Combine%20Statements%20in%20Code%20\(Visual%20Basic\).md)   
 [AddHandler Statement](/dotnet/visual-basic/language-reference/statements/addhandler-statement)   
 [Event Statement](/dotnet/visual-basic/language-reference/statements/event-statement)