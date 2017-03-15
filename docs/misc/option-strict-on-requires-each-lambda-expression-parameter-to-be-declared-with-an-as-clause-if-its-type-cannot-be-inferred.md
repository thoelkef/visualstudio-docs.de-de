---
title: "„Option Strict On“ erfordert, dass alle Parameter von Lambdaausdr&#252;cken mit einer As-Klausel deklariert werden, wenn der Typ nicht abgeleitet werden kann. | Microsoft Docs"
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
  - "bc36642"
  - "vbc36642"
helpviewer_keywords: 
  - "BC36642"
ms.assetid: 2aaa62b8-49c9-4ae8-b0f5-08e3f0b5ad10
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# „Option Strict On“ erfordert, dass alle Parameter von Lambdaausdr&#252;cken mit einer As-Klausel deklariert werden, wenn der Typ nicht abgeleitet werden kann.
Sie haben einen Parameter in einem Lambdaausdruck deklariert, ohne eine `As`\-Klausel mit „`Option Strict` On“ zu verwenden.  
  
```  
' Not valid when Option Strict is on. ' Dim increment1 = Function (n) n + 1  
```  
  
 Die vorhergehende Deklaration ist gültig, wenn der Typ von `n` abgeleitet werden kann. Wenn Sie z. B. den vorherigen Lambdaausdruck einem Funktionsdelegaten, `Del`, zuweisen:  
  
```  
Delegate Function Del(ByVal p As Integer) As Integer  
```  
  
 Jetzt kann der Typ von `n` vom Parameter `p` abgeleitet werden:  
  
```  
Dim increment2 as Del = Function(n) n + 1  
```  
  
 **Fehler\-ID:** BC36642  
  
### So beheben Sie diesen Fehler  
  
-   Fügen Sie eine `As`\-Klausel zur Parameterdeklaration hinzu:  
  
    ```  
    Dim increment3 = Function (n As Integer) n + 1  
    ```  
  
## Siehe auch  
 [Lambda Expressions](/dotnet/visual-basic/programming-guide/language-features/procedures/lambda-expressions)