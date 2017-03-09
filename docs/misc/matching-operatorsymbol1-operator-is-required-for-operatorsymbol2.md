---
title: "F&#252;r &quot;&lt;Operatorsymbol2&gt;&quot; ist ein zugeh&#246;riger &quot;&lt;Operatorsymbol2&gt;&quot;-Operator erforderlich. | Microsoft Docs"
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
  - "bc33033"
  - "vbc33033"
helpviewer_keywords: 
  - "BC33033"
ms.assetid: d2805e4f-08a8-4760-9539-565f51b88d13
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# F&#252;r &quot;&lt;Operatorsymbol2&gt;&quot; ist ein zugeh&#246;riger &quot;&lt;Operatorsymbol2&gt;&quot;-Operator erforderlich.
Ein Operator ist definiert, und der erforderliche zugehörige Operator ist nicht definiert.  
  
 Die folgenden Operatoren müssen als zueinander passende Paare definiert werden:  
  
-   `=` und `<>`  
  
-   `>` und `<`  
  
-   `>=` und `<=`  
  
-   `IsTrue` und `IsFalse`  
  
 Wenn Sie einen dieser Operatoren in einer Klasse oder Struktur definieren, müssen Sie auch den zugehörigen Operator in der gleichen Klasse oder Struktur definieren.  
  
 Auch wenn Sie den zugehörigen Operator nicht explizit verwenden, muss ihn vielleicht [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] verwenden. Wenn Sie beispielsweise eine Klasse oder Struktur definieren, die Sie als Zählervariable in [For...Next\-Anweisung](/dotnet/visual-basic/language-reference/statements/for-next-statement) verwenden, benötigt [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] sowohl den `>=`\- als auch den `<=`\-Operator \(und den `+`\-Operator\).  
  
 **Fehler\-ID:** BC33033  
  
### So beheben Sie diesen Fehler  
  
-   Definieren Sie den zugehörigen Operator in der gleichen Klasse oder Struktur. Definieren Sie ihn unbedingt in sinnvoller Art und Weise, da [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ihn möglicherweise in einer nicht vorhersehbaren Situation verwendet.  
  
## Siehe auch  
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)   
 [Operators and Expressions](/dotnet/visual-basic/programming-guide/language-features/operators-and-expressions/index)