---
title: "F&#252;r den &quot;&lt;Typparametername1&gt;&quot;-Typparameter von &quot;&lt;Signatur der generischen Prozedur&gt;&quot; war kein R&#252;ckschluss auf ein Typargument m&#246;glich | Microsoft Docs"
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
  - "vbc32116"
  - "bc32116"
helpviewer_keywords: 
  - "BC32116"
ms.assetid: 6bfb02ec-814a-4b1f-a585-6d902a861d00
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# F&#252;r den &quot;&lt;Typparametername1&gt;&quot;-Typparameter von &quot;&lt;Signatur der generischen Prozedur&gt;&quot; war kein R&#252;ckschluss auf ein Typargument m&#246;glich
Für den "\<Typparametername1\>"\-Typparameter von "\<Signatur der generischen Prozedur\>" war kein Rückschluss auf ein Typargument möglich. Das Typargument, das per Rückschluss von dem an den "\<Parametername1\>"\-Parameter übergebenen Argument abgeleitet wurde, verursacht einen Konflikt mit dem Typargument, das per Rückschluss von dem an den "\<Parametername2\>"\-Parameter übergebenen Argument abgeleitet wurde.  
  
 Eine generische Prozedur wird ohne Typargumente aufgerufen, und durch den Versuch, den Typ abzuleiten, wurde eine Datentypkonflikt zwischen den Typparametern verursacht.  
  
 Wenn Sie eine generische Prozedur aufrufen, geben Sie in der Regel für jeden Typparameter, der durch die generische Prozedur definiert wird, ein Typargument an. Wenn Sie keine Typargumente angeben, versucht der Compiler, die an die Typparameter zu übergebenden Typen abzuleiten. Wenn durch den Kontext des Aufrufs Datentypinformationen für einen Typparameter bereitgestellt werden, die einen Konflikt verursachen, schlägt der Typrückschluss fehl.  
  
 Dieser Fehler kann durch folgenden Code generiert werden.  
  
```  
Public Sub takeTwoValues(Of t)(ByVal x As t, ByVal y As t) End Sub Call takeTwoValues(4, 2.5)  
```  
  
 Weil der Compiler aufgrund des ersten Arguments `Integer` für den Typparameter `t` ableitet, aber aufgrund des zweiten Arguments für denselben Typparameter `Double` ableitet, entsteht ein Konflikt in Bezug auf den an `t` zu übergebenden Datentyp.  
  
 **Fehler\-ID:** BC32116  
  
### So beheben Sie diesen Fehler  
  
-   Geben Sie Typargumente für den generischen Typ an, damit der Compiler sie nicht ableiten muss.  
  
    ```  
    Call takeTwoValues(Of Double)(4, 2.5)  
    ```  
  
     Beachten Sie, dass in diesem Fall, in dem zwei normale Argumente unterschiedliche Datentypen aufweisen, der aufrufende Code ein Typargument übergeben muss, das den Anforderungen dieser beiden Datentypen entspricht. In diesem Fall wird `Integer` zu `Double` erweitert.  
  
     \- oder \-  
  
-   Definieren Sie die generische Prozedur neu, indem Sie für die normalen Parameter unterschiedliche Typparameter angeben, sodass beim Ableiten der Typen kein Konflikt entsteht.  
  
    ```  
    Public Sub takeTwoValues(Of t1, t2)(ByVal x As t1, ByVal y As t2)  
    ```  
  
## Siehe auch  
 [Generische Typen in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)