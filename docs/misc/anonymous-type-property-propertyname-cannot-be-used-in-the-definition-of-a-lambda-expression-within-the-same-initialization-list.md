---
title: "Die anonyme Typeigenschaft &quot;&lt;Eigenschaftenname&gt;&quot; kann nicht in der Definition eines Lambda-Ausdrucks innerhalb derselben Initialisierungsliste verwendet werden | Microsoft Docs"
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
  - "vbc36549"
  - "bc36549"
helpviewer_keywords: 
  - "BC36549"
ms.assetid: 6d04692a-957a-41ce-a19c-fcb06a186d1a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die anonyme Typeigenschaft &quot;&lt;Eigenschaftenname&gt;&quot; kann nicht in der Definition eines Lambda-Ausdrucks innerhalb derselben Initialisierungsliste verwendet werden
In der Initialisierungsliste eines anonymen Typs definierte Eigenschaften können nicht Teil der Definition eines Lambda\-Ausdrucks in derselben Liste sein. Beispielsweise darf im folgenden Code die `Num`\-Eigenschaft nicht in der Definition von `LambdaFun` enthalten sein.  
  
```vb#  
' Not valid.  
'Dim anon = New With {.Num = 4, .LambdaFun = Function() .Num > 0}  
```  
  
 **Fehler\-ID:** BC36549  
  
### So beheben Sie diesen Fehler  
  
1.  Teilen Sie den anonymen Typ in zwei Teile:  
  
    ```vb#  
    Dim anon1 = New With {.Num = 4}  
    Dim anon2 = New With {.LambdaFun = Function() anon1.Num > 0}  
    ' - or -  
    Dim anon3 = New With {.lambdaFun = Function(n As Integer) n > 0}  
    Console.WriteLine((anon2.LambdaFun)())  
    Console.WriteLine(anon3.lambdaFun(anon1.Num))  
    anon1.Num = -5  
    Console.WriteLine((anon2.LambdaFun)())  
    Console.WriteLine(anon3.lambdaFun(anon1.Num))  
    ```  
  
     Wenn Sie `anon1.Num` als `Key`\-Eigenschaft deklarieren, kann der zugehörige Wert nicht geändert werden.  
  
2.  Als Alternative können Sie eine reguläre Function\-Anweisung verwenden, um auf die anonyme Typeigenschaft zuzugreifen:  
  
    ```vb#  
    Function testNum(ByVal n As Integer) As Boolean  
        Return n > 0  
    End Function  
    Console.WriteLine(testNum(anon1.Num))  
    ```  
  
3.  Auf ähnliche Weise können Sie eine außerhalb des anonymen Typs definierte Lambda\-Funktion verwenden:  
  
    ```vb#  
    Dim lambdaFun1 = Function() anon1.Num > 0  
    Dim lambdaFun2 = Function(n As Integer) n > 0  
    ```  
  
## Siehe auch  
 [Lambda Expressions](/dotnet/visual-basic/programming-guide/language-features/procedures/lambda-expressions)   
 [Anonymous Types](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types)