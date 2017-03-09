---
title: "Arraymodifizierer d&#252;rfen nicht im Parameternamen von Lambda-Ausdr&#252;cken angegeben werden, sondern nur f&#252;r ihren Typ | Microsoft Docs"
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
  - "vbc36643"
  - "bc36643"
helpviewer_keywords: 
  - "BC36643"
ms.assetid: 34b6141b-6eab-4641-a3f4-53ef28c1792b
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Arraymodifizierer d&#252;rfen nicht im Parameternamen von Lambda-Ausdr&#252;cken angegeben werden, sondern nur f&#252;r ihren Typ
Arrayargumente können an Lambda\-Ausdrücke gesendet werden, aber die Parameterdeklaration muss den Elementtyp enthalten.  
  
```vb#  
' Not valid.  
' Dim arrayExample1 = Function(arrayPara()) 2  
  
' Valid.  
Dim arrayExample2 = Function(arrayPara() As Integer) arrayPara.Length > 0  
Dim arrayexample3 = Function(arrayPara As Integer()) arrayPara.Length > 0  
```  
  
 **Fehler\-ID:** BC36643  
  
### So beheben Sie diesen Fehler  
  
-   Geben Sie den Typ der Elemente im Arrayparameter an.  
  
## Siehe auch  
 [Lambda Expressions](/dotnet/visual-basic/programming-guide/language-features/procedures/lambda-expressions)