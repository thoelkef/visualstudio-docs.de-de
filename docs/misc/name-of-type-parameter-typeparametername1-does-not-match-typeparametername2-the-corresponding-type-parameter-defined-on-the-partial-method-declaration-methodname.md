---
title: "Der Name von Typparameter &#39;&lt;Typparametername1&gt;&#39; stimmt nicht mit &#39;&lt;Typparametername2&gt;&#39; &#252;berein, dem entsprechenden Typparameter, der in der Deklaration der partiellen &#39;&lt;Methodenname&gt;&#39;-Methode definiert wurde. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31443"
  - "bc31443"
helpviewer_keywords: 
  - "BC31443"
ms.assetid: 27c81cc1-325e-4e86-9d00-34f81e928076
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Der Name von Typparameter &#39;&lt;Typparametername1&gt;&#39; stimmt nicht mit &#39;&lt;Typparametername2&gt;&#39; &#252;berein, dem entsprechenden Typparameter, der in der Deklaration der partiellen &#39;&lt;Methodenname&gt;&#39;-Methode definiert wurde.
In einer partiellen Methode, die mindestens einen Typparameter enthält, müssen die Namen der Typparameter in der Deklaration der Methode und in der Implementierung der Methode übereinstimmen.  
  
 Die folgende Deklaration und Implementierung verursachen z. B. diesen Fehler.  
  
```vb#  
' Definition of the partial method signature with type parameter T. Partial Private Sub OnNameChanged(Of T)() End Sub  
```  
  
```vb#  
'' Implementation of the partial method with type parameter N. 'Private Sub OnNameChanged(Of N)() '    Console.WriteLine("Name was changed to " & Me.Name) 'End Sub  
```  
  
 **Fehler\-ID:** BC31443  
  
### So beheben Sie diesen Fehler  
  
-   Untersuchen Sie die Typparameter, um zu ermitteln, an welcher Stelle sie nicht übereinstimmen. Ändern Sie die Namen bei Bedarf, damit sie identisch sind.  
  
## Siehe auch  
 [Partial Methods](/dotnet/visual-basic/programming-guide/language-features/procedures/partial-methods)   
 [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)