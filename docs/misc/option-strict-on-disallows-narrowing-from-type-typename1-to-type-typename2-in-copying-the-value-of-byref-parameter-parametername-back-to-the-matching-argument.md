---
title: "„Option Strict On“ l&#228;sst das Einschr&#228;nken von Typ &#39;&lt;Typname1&gt;&#39; auf Typ &#39;&lt;Typname2&gt;&#39; beim Zur&#252;ckkopieren des ByRef-Parameterwerts &#39;&lt;Parametername&gt;&#39; in das entsprechende Argument nicht zu. | Microsoft Docs"
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
  - "bc32029"
  - "vbc32029"
helpviewer_keywords: 
  - "BC32029"
ms.assetid: fc9ae5d2-b506-47cf-a50c-116fda5ed206
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# „Option Strict On“ l&#228;sst das Einschr&#228;nken von Typ &#39;&lt;Typname1&gt;&#39; auf Typ &#39;&lt;Typname2&gt;&#39; beim Zur&#252;ckkopieren des ByRef-Parameterwerts &#39;&lt;Parametername&gt;&#39; in das entsprechende Argument nicht zu.
Ein Prozeduraufruf stellt ein `ByRef`\-Argument mit einem Datentyp bereit, der in den deklarierten Typ des Arguments erweitert wird, und `Option Strict` ist `On`. Die erweiternde Konvertierung ist zulässig, wenn das Argument an die Prozedur übergeben wird, aber wenn die Prozedur den Inhalt des Variablenarguments im aufrufenden Code ändert, ist die umgekehrte Konvertierung einschränkend. Einschränkende Konvertierungen sind mit `Option Strict On` nicht zulässig.  
  
 **Fehler\-ID:** BC32029  
  
### So beheben Sie diesen Fehler  
  
-   Geben Sie jedes `ByRef`\-Argument im Prozeduraufruf mit demselben Datentyp wie für den deklarierten Typ an, oder wählen Sie „`Option Strict Off`“.  
  
## Siehe auch  
 [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Passing Arguments by Value and by Reference](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference)   
 [Widening and Narrowing Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)   
 [Implicit and Explicit Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions)