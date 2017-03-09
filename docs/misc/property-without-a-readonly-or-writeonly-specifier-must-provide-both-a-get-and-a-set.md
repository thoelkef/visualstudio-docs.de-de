---
title: "Eine Eigenschaft ohne einen ReadOnly- oder WriteOnly-Bezeichner muss ein &#39;Get&#39; und ein &#39;Set&#39; haben. | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30124"
  - "vbc30124"
helpviewer_keywords: 
  - "BC30124"
ms.assetid: b24fc997-9a6b-44d1-b712-dab498a6fc72
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Eine Eigenschaft ohne einen ReadOnly- oder WriteOnly-Bezeichner muss ein &#39;Get&#39; und ein &#39;Set&#39; haben.
Wenn eine Eigenschaft nicht als `ReadOnly` oder `WriteOnly` deklariert ist, muss sie Prozeduren zum Lesen und Schreiben des Werts bereitstellen.  
  
 **Fehler\-ID:** BC30124  
  
### So beheben Sie diesen Fehler  
  
1.  Stellen Sie sicher, dass Sie sowohl eine `Get`\- als auch eine `Set`\-Prozedur zwischen der `Property`\-Anweisung und der `End Property`\-Anweisung einbeziehen.  
  
2.  Stellen Sie sicher, dass andere Prozeduren innerhalb der `Property`\-Deklaration korrekt abgeschlossen sind.  
  
## Siehe auch  
 [Property Statement](/dotnet/visual-basic/language-reference/statements/property-statement)   
 [Get Statement](/dotnet/visual-basic/language-reference/statements/get-statement)   
 [Set Statement](/dotnet/visual-basic/language-reference/statements/set-statement)