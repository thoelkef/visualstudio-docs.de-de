---
title: "Instanzmember und &#39;Me&#39; d&#252;rfen in Strukturen nicht in Lambdaausdr&#252;cken verwendet werden. | Microsoft Docs"
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
  - "vbc36638"
  - "bc36638"
helpviewer_keywords: 
  - "BC36638"
ms.assetid: 5c24a7c7-50f6-4ffb-9ed2-07e2abc4eaf3
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instanzmember und &#39;Me&#39; d&#252;rfen in Strukturen nicht in Lambdaausdr&#252;cken verwendet werden.
Sie haben in einer Struktur einen Lambdaausdruck definiert, der auf ein Instanzmember der Struktur verweist oder `Me` verwendet. Im folgenden Codebeispiel sind diese zwei Verweise dargestellt.  
  
```vb#  
Structure Structure1 Public InstanceMember As Integer Public Function ExampleFun() As Integer '' The error is caused by use of InstanceMember. 'Dim fun1 = Function() InstanceMember '' The error is caused by use of Me. 'Dim fun2 = Function() Me.InstanceMember 'Return fun1() End Function End Structure  
```  
  
 **Fehler\-ID:** BC36638  
  
### So beheben Sie diesen Fehler  
  
-   Weisen Sie das Instanzmember einer lokalen Variablen zu, und verwenden Sie die lokale Variable in Ihrer Anweisung.  
  
    ```vb#  
    Public Function ExampleFunFix() As Integer Dim temp = InstanceMember Dim fun1 = Function() temp Return fun1() End Function  
    ```  
  
## Siehe auch  
 [Lambda Expressions](/dotnet/visual-basic/programming-guide/language-features/procedures/lambda-expressions)   
 [Me](http://msdn.microsoft.com/de-de/a65973c7-cf06-4547-9b25-9fba885525c2)   
 [Structure Statement](/dotnet/visual-basic/language-reference/statements/structure-statement)