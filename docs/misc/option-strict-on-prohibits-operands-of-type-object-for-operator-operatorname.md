---
title: "„Option Strict On“ l&#228;sst keine Operanden des Typs &#39;Object&#39; f&#252;r den &#39;&lt;Operatorname&gt;&#39;-Operator zu. | Microsoft Docs"
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
  - "bc30038"
  - "vbc30038"
helpviewer_keywords: 
  - "BC30038"
ms.assetid: eb047d36-1fb4-460d-ae98-c76f31a89bed
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# „Option Strict On“ l&#228;sst keine Operanden des Typs &#39;Object&#39; f&#252;r den &#39;&lt;Operatorname&gt;&#39;-Operator zu.
Die einzigen für Objektvariablen definierten Operatoren sind `Is` und `TypeOf...Is`. Wenn `Option Strict` dem Wert `On` entspricht, müssen alle Operanden Datentypen sein, die für den angegebenen Operator definiert wurden.  
  
 **Fehler\-ID:** BC30038  
  
### So beheben Sie diesen Fehler  
  
-   Verwenden Sie die entsprechenden Typkonvertierungsfunktionen wie `CInt` oder `CStr`, um die Operanden in Datentypen zu konvertieren, die für den Operator definiert wurden.  
  
## Siehe auch  
 [Is Operator](/dotnet/visual-basic/language-reference/operators/is-operator)   
 [Comparison Operators in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators)   
 [Type Conversion Functions](/dotnet/visual-basic/language-reference/functions/type-conversion-functions)