---
title: "Relationaler Operator erwartet | Microsoft Docs"
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
  - "bc30239"
  - "vbc30239"
helpviewer_keywords: 
  - "BC30239"
ms.assetid: c5701568-77a1-441b-a0f7-f7b36cbd17e3
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Relationaler Operator erwartet
Eine `Case`\-Anweisung enthält eine `Is`\-Klausel, aber keinen Vergleichsoperator wie `=` oder `>`. Wenn eine `Case`\-Anweisung keinen Operator enthält, wird `=` angenommen, und `Is` wird nicht verwendet.  
  
 **Fehler\-ID:** BC30239  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie das `Is`\-Schlüsselwort, oder fügen Sie einen Vergleichsoperator dahinter ein.  
  
## Siehe auch  
 [Select...Case Statement](/dotnet/visual-basic/language-reference/statements/select-case-statement)   
 [Comparison Operators in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators)   
 [Comparison Operators](/dotnet/visual-basic/language-reference/operators/comparison-operators)