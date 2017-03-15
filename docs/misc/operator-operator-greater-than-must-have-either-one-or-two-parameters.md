---
title: "Der &quot;&lt;Operator&gt;&quot;-Operator muss entweder einen oder zwei Parameter aufweisen | Microsoft Docs"
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
  - "bc33016"
  - "vbc33016"
helpviewer_keywords: 
  - "BC33016"
ms.assetid: 70f43905-037e-4040-83c0-f39334b3e07a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Der &quot;&lt;Operator&gt;&quot;-Operator muss entweder einen oder zwei Parameter aufweisen
Ein Operator, der unär oder binär sein kann, ist mit keinem Parameter oder mit mehr als zwei Parametern definiert.  
  
 Ein unärer\/binärer Operator muss entweder einen oder zwei Parameter aufweisen.  
  
 **Fehler\-ID:** BC33016  
  
### So beheben Sie diesen Fehler  
  
-   Ändern Sie die Definition so, dass sie entweder einen oder zwei Parameter angibt.  
  
-   Wenn Sie keine oder mehr als zwei Parameter benötigen, müssen Sie die [Function Statement](/dotnet/visual-basic/language-reference/statements/function-statement) zum Definieren einer `Function`\-Prozedur anstelle eines Operators verwenden.  
  
## Siehe auch  
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)