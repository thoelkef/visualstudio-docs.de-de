---
title: "Methode kann nicht gleichzeitig eine „On Error GoTo“-Anweisung und einen Lambda- oder Abfrageausdruck enthalten. | Microsoft Docs"
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
  - "bc36595"
  - "vbc36595"
helpviewer_keywords: 
  - "BC36595"
ms.assetid: 4e7cc11e-f53d-4481-afb4-653a81d54483
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Methode kann nicht gleichzeitig eine „On Error GoTo“-Anweisung und einen Lambda- oder Abfrageausdruck enthalten.
Eine Methode enthält sowohl eine `On Error Goto`\-Anweisung als auch einen Lambda\-Ausdruck oder eine LINQ\-Abfrage. Sie können in einer Methode nicht gleichzeitig eine `On Error Goto`\-Anweisung und einen Lambda\-Ausdruck oder einer LINQ\-Abfrage verwenden.  
  
 **Fehler\-ID:** BC36595  
  
### So beheben Sie diesen Fehler  
  
1.  Ersetzen Sie den Ausnahmebehandlungscode, der die `On Error Goto`\-Anweisung mit einer `Try...Catch`\-Anweisung verwendet.  
  
## Siehe auch  
 [Einführung in die Ausnahmebehandlung \(Visual Basic\)](http://msdn.microsoft.com/de-de/9792f16a-0cd2-40bd-ace2-f7a4344c0e52)   
 [Try...Catch...Finally Statement](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [Introduction to LINQ in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [Lambda Expressions](/dotnet/visual-basic/programming-guide/language-features/procedures/lambda-expressions)   
 [On Error Statement](/dotnet/visual-basic/language-reference/statements/on-error-statement)