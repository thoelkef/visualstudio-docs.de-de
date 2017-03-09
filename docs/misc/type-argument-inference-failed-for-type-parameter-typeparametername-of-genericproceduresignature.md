---
title: "F&#252;r den Typparameter &lt;Typparametername&gt; von &lt;Signatur der generischen Prozedur&gt; war kein R&#252;ckschluss auf ein Typargument m&#246;glich. | Microsoft Docs"
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
  - "vbc32051"
  - "bc32051"
helpviewer_keywords: 
  - "BC32051"
ms.assetid: a9c2a0ce-e225-4549-bfd8-d42df5d16bfd
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# F&#252;r den Typparameter &lt;Typparametername&gt; von &lt;Signatur der generischen Prozedur&gt; war kein R&#252;ckschluss auf ein Typargument m&#246;glich.
Für den Typparameter \<Typparametername\> von \<Signatur der generischen Prozedur\> war kein Rückschluss auf ein Typargument möglich. Das Typargument konnte nicht aus dem Argument abgeleitet werden, das an den Parameter \<Parametername\> übergeben wurde.  
  
 Eine generische Prozedur wird ohne Angabe von Typargumenten aufgerufen, und der Compiler kann den an einen der Parameter zu übergebenden Typ nicht ableiten.  
  
 Wenn Sie eine generische Prozedur aufrufen, geben Sie in der Regel für jeden Typparameter, der durch die generische Prozedur definiert wird, ein Typargument an. Wenn Sie keine Typargumente angeben, versucht der Compiler, die an die Typparameter zu übergebenden Typen abzuleiten. Wenn durch den Kontext des Aufrufs Datentypinformationen für einen Typparameter bereitgestellt werden, die einen Konflikt verursachen, schlägt der Typrückschluss fehl.  
  
 Dieser Fehler kann durch folgenden Code generiert werden.  
  
```  
Public Sub doSomething(Of t)(ByVal arg1 As t(), ByVal arg2 As t) End Sub Call doSomething(6, 42)  
```  
  
 Im vorhergehenden Beispiel leitet der Compiler den Typ `Integer` für `t` basierend auf dem an `arg2` übergebenen Wert 42 ab. Dieser Rückschluss würde jedoch voraussetzen, dass `arg1` vom Typ `Integer()` ist, also ein Array von `Integer`. Der an `arg1` übergebene Wert 6 stimmt aber nicht mit diesem Typ überein.  
  
 **Fehler\-ID:** BC32051  
  
### So beheben Sie diesen Fehler  
  
-   Geben Sie Typargumente für die generische Prozedur an, damit der Compiler sie nicht ableiten muss.  
  
-   Geben Sie normale Argumente mit Typen an, die mit denjenigen der Typargumente übereinstimmen.  
  
## Siehe auch  
 [Generische Typen in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)