---
title: "Der &#39;&lt;Typparametername&gt;&#39;-Typparameter f&#252;r &#39;&lt;Generischer_Prozedurname&gt;&#39; kann nicht abgeleitet werden. | Microsoft Docs"
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
  - "vbc32050"
  - "bc32050"
helpviewer_keywords: 
  - "BC32050"
ms.assetid: e4a69ffb-0764-4e5a-8de1-40f881a3f4fb
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Der &#39;&lt;Typparametername&gt;&#39;-Typparameter f&#252;r &#39;&lt;Generischer_Prozedurname&gt;&#39; kann nicht abgeleitet werden.
Eine generische Prozedur wird ohne Angabe einer Liste der Typargumente aufgerufen, und der Typrückschluss schlägt für eines der Typargumente fehl.  
  
 Wenn Sie eine generische Prozedur aufrufen, geben Sie normalerweise für jeden Typparameter, der von der Prozedur definiert wird, ein Typargument ein. Alternativ können Sie vollständig auf die Liste der Typargumente verzichten. Dann versucht der Compiler, aus dem Kontext des Aufrufs Rückschlüsse auf den Typ der einzelnen Typargumente zu ziehen. Weitere Informationen finden Sie unter „Typrückschluss“ in [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures).  
  
 Eine mögliche Fehlerursache beim Typrückschluss ist ein Rangfolgekonflikt zwischen einem Typparameter und dem aufrufenden Typ. Dies wird im folgenden Code veranschaulicht.  
  
```  
Public Sub displayLargest(Of t As IComparable)(ByVal arg() As t) ' Insert code to find and display the largest element of arg(). End Sub Public Sub callGenericSub() Dim testValue As Integer findLargest(testValue) Dim testMatrix(,) As Integer findLargest(testMatrix) End Sub  
```  
  
 Im vorherigen Code erzeugen die beiden Aufrufe von `findLargest` diesen Fehler, da der Typparameter `t` ein eindimensionales Array erfordert, während die vom Compiler aus den Aufrufen abgeleiteten Typargumente ein Skalar \(`testValue`\) und ein zweidimensionales Array \(`testMatrix`\) sind.  
  
 **Fehler\-ID:** BC32050  
  
### So beheben Sie diesen Fehler  
  
-   Stellen Sie sicher, dass die Typen der normalen Argumente dazu führen, dass der Typrückschluss konsistent mit den für die generische Prozedur deklarierten Typparametern ist.  
  
     \- oder \-  
  
-   Rufen Sie die generische Prozedur mit einer vollständigen Liste der Typargumente auf, sodass ein Typrückschluss nicht erforderlich ist.  
  
## Siehe auch  
 [Generische Typen in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)   
 [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)