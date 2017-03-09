---
title: "Der Operator &lt;Operator&gt; muss zwei Parameter haben. | Microsoft Docs"
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
  - "bc33015"
  - "vbc33015"
helpviewer_keywords: 
  - "BC33015"
ms.assetid: 506ea996-8abe-4dbe-aff4-d3910bf4399e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Der Operator &lt;Operator&gt; muss zwei Parameter haben.
Ein binärer Operator wird mit weniger oder mehr als zwei Parametern definiert.  
  
 Ein binärer Operator muss über genau zwei Parameter verfügen.  
  
 **Fehler\-ID:** BC33015  
  
### So beheben Sie diesen Fehler  
  
-   Ändern Sie die Definition so, dass sie genau zwei Parameter angibt.  
  
-   Wenn Sie nur einen Parameter benötigen, müssen Sie einen unären Operator definieren.  
  
-   Wenn Sie keine oder mehr als zwei Parameter benötigen, müssen Sie die [Function Statement](/dotnet/visual-basic/language-reference/statements/function-statement) zum Definieren einer `Function`\-Prozedur anstelle eines Operators verwenden.  
  
## Siehe auch  
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)