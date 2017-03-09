---
title: "If-Operanden d&#252;rfen keine benannten Argumente sein | Microsoft Docs"
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
  - "bc33105"
  - "vbc33105"
helpviewer_keywords: 
  - "BC33105"
ms.assetid: 596baeb6-a44f-4d92-beb7-06624b60c00d
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# If-Operanden d&#252;rfen keine benannten Argumente sein
Die Verwendung von benannten Argumenten in den Operanden des `If`\-Operators ist ungültig. Dieser Fehler wird beispielsweise durch den folgenden Code verursacht:  
  
```  
Dim i As Integer Dim result As String ' Not valid. ' result = (If(i > 0, TruePart:="positive", FalsePart:="not positive")  
```  
  
 Dies stellt einen Unterschied zur `IIf`\-Funktion dar, die benannte Argumente zulässt, wie im folgenden Code zu sehen:  
  
```  
' Valid. IIf(i > 0, TruePart:="positive", FalsePart:="not positive")  
```  
  
 **Fehler\-ID:** BC33105  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie die Namenszuweisungen aus den Operanden, wie im folgenden Code dargestellt.  
  
    ```  
    result = If(i > 0, "positive", "not positive")  
    ```  
  
## Siehe auch  
 [If Operator](/dotnet/visual-basic/language-reference/operators/if-operator)   
 [Passing Arguments by Position and by Name](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name)