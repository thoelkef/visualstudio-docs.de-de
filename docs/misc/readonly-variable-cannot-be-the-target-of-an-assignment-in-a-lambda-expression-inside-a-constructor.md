---
title: "Die ReadOnly-Variable kann nicht das Ziel einer Zuweisung in einem Lambdaausdruck innerhalb eines Konstruktors sein. | Microsoft Docs"
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
  - "bc36602"
  - "vbc36602"
helpviewer_keywords: 
  - "BC36602"
ms.assetid: f96f8c79-86df-4727-bc6d-f0844da21395
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die ReadOnly-Variable kann nicht das Ziel einer Zuweisung in einem Lambdaausdruck innerhalb eines Konstruktors sein.
Sie haben aus einem Lambdaausdruck heraus auf eine `ReadOnly`\-Variable verwiesen, was nicht zulässig ist. Im folgende Code wird dieser Fehler durch Senden der `ReadOnly` Variablen `m` als Argument für einen `ByRef`\-Parameter verursacht.  
  
```vb#  
Class Class1 ReadOnly m As Integer Sub New() ' The use of m triggers the error. Dim f = Function() Test(m) End Sub Function Test(ByRef n As Integer) As String End Function End Class  
```  
  
 **Fehler\-ID:** BC36602  
  
### So beheben Sie diesen Fehler  
  
-   Ändern Sie nach Möglichkeit Parameter `n` in Funktion `Test` in einen `ByVal`\-Parameter, wie im folgenden Code gezeigt.  
  
    ```vb#  
    Class Class1Fix1 ReadOnly m As Integer Sub New() Dim f = Function() Test(m) End Sub Function Test(ByVal n As Integer) As String End Function End Class  
    ```  
  
### So beheben Sie diesen Fehler  
  
-   Weisen Sie die `ReadOnly` Variable `m` einer lokalen Variablen im Konstruktor zu, und verwenden Sie die lokale Variable anstelle von `m`, wie im folgenden Code dargestellt.  
  
    ```vb#  
    Class Class1Fix2 ReadOnly m As Integer Sub New() Dim temp = m Dim f = Function() Test(temp) End Sub Function Test(ByRef n As Integer) As String End Function End Class  
    ```  
  
## Siehe auch  
 [Lambda Expressions](/dotnet/visual-basic/programming-guide/language-features/procedures/lambda-expressions)   
 [ReadOnly](/dotnet/visual-basic/language-reference/modifiers/readonly)   
 [NICHT IM BUILD: Verwenden von Konstruktoren und Destruktoren](http://msdn.microsoft.com/de-de/548eebe1-86c4-4377-b2f5-447cb8be3d90)