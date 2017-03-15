---
title: "WriteOnly-Eigenschaft muss ein &#39;Set&#39; bereitstellen. | Microsoft Docs"
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
  - "bc30125"
  - "vbc30125"
helpviewer_keywords: 
  - "BC30125"
ms.assetid: c2b18086-9cd9-4094-b9a9-491c8d617096
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# WriteOnly-Eigenschaft muss ein &#39;Set&#39; bereitstellen.
Wenn eine Eigenschaft als `WriteOnly` deklariert wird, muss sie eine Prozedur zum Schreiben des Werts bereitstellen.  
  
 **Fehler\-ID:** BC30125  
  
### So beheben Sie diesen Fehler  
  
1.  Zwischen der `Property`\-Anweisung und der `End Property`\-Anweisung muss eine `Set`\-Prozedur eingefügt sein.  
  
2.  Stellen Sie sicher, dass andere Prozeduren innerhalb der `Property`\-Deklaration korrekt abgeschlossen sind.  
  
## Siehe auch  
 [Property Statement](/dotnet/visual-basic/language-reference/statements/property-statement)   
 [Set Statement](/dotnet/visual-basic/language-reference/statements/set-statement)