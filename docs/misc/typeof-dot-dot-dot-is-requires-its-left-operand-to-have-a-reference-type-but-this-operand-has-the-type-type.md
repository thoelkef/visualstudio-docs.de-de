---
title: "„TypeOf ... Is“ erfordert, dass der linke Operand einen Verweistyp hat. Dieser Operand hat jedoch den Typ &lt;Typ&gt;. | Microsoft Docs"
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
  - "bc30021"
  - "vbc30021"
helpviewer_keywords: 
  - "BC30021"
ms.assetid: a6e76fc8-9c7f-4e55-8b68-e6e7b03a6737
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# „TypeOf ... Is“ erfordert, dass der linke Operand einen Verweistyp hat. Dieser Operand hat jedoch den Typ &lt;Typ&gt;.
Der `TypeOf...Is`\-Ausdruck überprüft die Laufzeittyp\-Kompatibilität einer Objektvariable. Diese Kompatibilität ist für Werttypen nicht definiert.  
  
 **Fehler\-ID:** BC30021  
  
### So beheben Sie diesen Fehler  
  
-   Wenn `Option Strict` \= `Off`, verwenden Sie die `TypeName`\- oder `VarType`\-Funktion, um die Datentypinformationen der Variablen abzurufen.  
  
-   Wenn `Option Strict` \= `On`, bestimmt die Variablendeklaration den Datentyp der Variablen.  
  
## Siehe auch  
 [Comparison Operators in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators)   
 [NICHT IM BUILD: TypeName\-Funktion \(Visual Basic\)](http://msdn.microsoft.com/de-de/6197bc6c-e8a6-4711-883c-0c95e94e272c)   
 [NICHT IM BUILD: VarType\-Funktion \(Visual Basic\)](http://msdn.microsoft.com/de-de/e820b6fc-faa6-4de4-836a-0466032dc190)   
 [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement)