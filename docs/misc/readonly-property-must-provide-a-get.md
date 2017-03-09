---
title: "ReadOnly-Eigenschaft muss ein „Get“ bereitstellen. | Microsoft Docs"
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
  - "bc30126"
  - "vbc30126"
helpviewer_keywords: 
  - "BC30126"
ms.assetid: a522c39e-1f11-45c8-a00b-3546c842909a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ReadOnly-Eigenschaft muss ein „Get“ bereitstellen.
Wenn eine Eigenschaft als `ReadOnly` deklariert wird, muss sie eine Prozedur zum Lesen des Werts bereitstellen.  
  
 **Fehler\-ID:** BC30126  
  
### So beheben Sie diesen Fehler  
  
1.  Zwischen der `Property`\-Anweisung und der `End Property`\-Anweisung muss eine `Get`\-Prozedur eingefügt sein.  
  
2.  Stellen Sie sicher, dass andere Prozeduren innerhalb der `Property`\-Deklaration korrekt abgeschlossen sind.  
  
## Siehe auch  
 [Property Statement](/dotnet/visual-basic/language-reference/statements/property-statement)   
 [Get Statement](/dotnet/visual-basic/language-reference/statements/get-statement)