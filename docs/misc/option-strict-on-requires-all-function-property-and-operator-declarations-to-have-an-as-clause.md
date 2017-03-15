---
title: "„Option Strict On“ erfordert, dass alle Funktions-, Eigenschafts- und Operatordeklarationen eine As-Klausel enthalten. | Microsoft Docs"
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
  - "vbc30210"
  - "bc30210"
helpviewer_keywords: 
  - "BC30210"
ms.assetid: 4d217e56-0eac-4834-bcad-234a69809390
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# „Option Strict On“ erfordert, dass alle Funktions-, Eigenschafts- und Operatordeklarationen eine As-Klausel enthalten.
Eine Deklaration enthält eine deklarierte Eigenschaft oder Funktionsrückgabe ohne eine `As`\-Klausel. Wenn `Option Strict` \= `On` ist, muss jede Variable, jede Eigenschaft, jedes Prozedurargument und jede Funktionsrückgabe mit einer `As`\-Klausel zur Angabe des Daten\-Typs deklariert werden, z. B. `Dim MyNum As Short`.  
  
 **Fehler\-ID:** BC30210  
  
### So beheben Sie diesen Fehler  
  
1.  Überprüfen, ob das `As`\-Schlüsselwort falsch geschrieben wurde.  
  
2.  Geben Sie eine `As`\-Klausel für die deklarierte Eigenschaft oder Funktionsrückgabe an, oder setzen Sie `Option Strict Off`.  
  
## Siehe auch  
 [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Eigenschaftenprozeduren](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [Function\-Prozeduren](/dotnet/visual-basic/programming-guide/language-features/procedures/function-procedures)