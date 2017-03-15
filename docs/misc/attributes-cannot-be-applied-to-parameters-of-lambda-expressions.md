---
title: "Attribute k&#246;nnen nicht auf Parameter von Lambdaausdr&#252;cken angewendet werden. | Microsoft Docs"
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
  - "vbc36634"
  - "bc36634"
helpviewer_keywords: 
  - "BC36634"
ms.assetid: ed751d8d-11b7-4210-97e0-0319edff8c34
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Attribute k&#246;nnen nicht auf Parameter von Lambdaausdr&#252;cken angewendet werden.
Sie haben ein Attribut auf einen Parameter in der Definition eines Lambdaausdrucks angewendet, das nicht unterstützt wird. Der folgende Code verursacht diesen Fehler.  
  
```vb#  
Sub LambaAttribute()  
    ' Not valid.  
    Dim add1 = _  
    Function(<System.Runtime.InteropServices.InAttribute()> m As Integer) _  
                   m + 1  
End Sub  
```  
  
 **Fehler\-ID:** BC36634  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie das Attribut, oder überarbeiten Sie ggf. den Code durch Ändern des Lambdaausdrucks in eine reguläre Funktion.  
  
## Siehe auch  
 <xref:System.Runtime.InteropServices.InAttribute>   
 [Lambda Expressions](/dotnet/visual-basic/programming-guide/language-features/procedures/lambda-expressions)   
 [NICHT IM BUILD: Attribute in Visual Basic](http://msdn.microsoft.com/de-de/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)