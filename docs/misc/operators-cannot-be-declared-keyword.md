---
title: "Operatoren k&#246;nnen nicht als &#39;&lt;Schl&#252;sselwort&gt;&#39; deklariert werden. | Microsoft Docs"
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
  - "vbc33013"
  - "bc33013"
helpviewer_keywords: 
  - "BC33013"
ms.assetid: bfd805f4-e30e-4553-9cb7-2690595f0480
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Operatoren k&#246;nnen nicht als &#39;&lt;Schl&#252;sselwort&gt;&#39; deklariert werden.
Ein Operator ist mit einem Schlüsselwort deklariert, das für Operatordefinitionen nicht gültig ist.  
  
 Jeder Operator muss sowohl als [Public](/dotnet/visual-basic/language-reference/modifiers/public) als auch als [Shared](/dotnet/visual-basic/language-reference/modifiers/shared) deklariert werden. Darüber hinaus muss ein Konvertierungsoperator entweder mit [Widening](/dotnet/visual-basic/language-reference/modifiers/widening) oder [Narrowing](/dotnet/visual-basic/language-reference/modifiers/narrowing) deklariert werden, aber nicht mit beiden. Eine Operatordefinition kann optional die Schlüsselwörter [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads) oder [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows) enthalten. Keine anderen Schlüsselwörter sind in einem [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement) zulässig.  
  
 **Fehler\-ID:** BC33013  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie das ungültige Schlüsselwort aus der Operatordefinition.  
  
## Siehe auch  
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)