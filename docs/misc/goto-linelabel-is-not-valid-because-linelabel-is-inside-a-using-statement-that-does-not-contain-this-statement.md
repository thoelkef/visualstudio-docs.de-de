---
title: "&#39;GoTo &lt;Zeilenbezeichnung&gt;&#39; ist nicht g&#252;ltig, da sich &#39;&lt;Zeilenbezeichnung&gt;&#39; in einer Using-Anweisung befindet, die diese Anweisung nicht enth&#228;lt. | Microsoft Docs"
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
  - "bc36009"
  - "vbc36009"
helpviewer_keywords: 
  - "BC36009"
ms.assetid: ebec3cac-d378-4e9b-a792-12e9ece5599e
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;GoTo &lt;Zeilenbezeichnung&gt;&#39; ist nicht g&#252;ltig, da sich &#39;&lt;Zeilenbezeichnung&gt;&#39; in einer Using-Anweisung befindet, die diese Anweisung nicht enth&#228;lt.
Ein `GoTo`\-Anweisung außerhalb einer `Using`\-Konstruktion versucht, zu einer Zeilenbezeichnung in der Konstruktion zu verzweigen.  
  
 Es ist nicht zulässig, von außerhalb einer `Using`...`End Using`\-Konstruktion in diese Konstruktion zu verzweigen.  
  
 **Fehler\-ID:** BC36009  
  
### So beheben Sie diesen Fehler  
  
-   Ändern Sie die Zeilenbezeichnung in der `GoTo`\-Anweisung in eine Bezeichnung, die sich nicht innerhalb einer `For`...`Next`\-, `For Each`...`Next`\-, `SyncLock`...`End SyncLock`\-, `Try`...`Catch`...`Finally`\-, `With`...`End With`\- oder `Using`...`End Using`\-Konstruktion befindet.  
  
     \- oder \-  
  
-   Entfernen Sie die `GoTo`\-Anweisung vollständig. Die einzige Möglichkeit, um in eine `Using`...`End Using`\-Konstruktion zu gelangen, besteht darin, die Kontrolle an die `Using`\-Anweisung selbst zu übergeben.  
  
## Siehe auch  
 [GoTo Statement](/dotnet/visual-basic/language-reference/statements/goto-statement)   
 [Using Statement](/dotnet/visual-basic/language-reference/statements/using-statement)