---
title: "„}“ erwartet. | Microsoft Docs"
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
  - "vbc30370"
  - "bc30370"
helpviewer_keywords: 
  - "BC30370"
ms.assetid: a4ce9be9-fc5d-46ec-a217-c3428bd0b97e
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# „}“ erwartet.
Ein Arrayinitialisierer oder eine Einschränkungsliste wurde nicht auf korrekte Weise beendet.  
  
 Die Elementwerte zum Initialisieren eines Arrays müssen in geschweiften Klammern angegeben werden \(`{}`\).  
  
```  
Dim demoArray() As Integer = New Integer() {1, 2, 3}   
```  
  
 Gleichermaßen müssen die Einschränkungen in einer Einschränkungsliste für einen generischen Typparameter in geschweiften Klammern angegeben werden.  
  
```  
Public Class dictionaryMaker(Of t As {IComparable, IDisposable, New})   
```  
  
 **Fehler\-ID:** BC30370  
  
### So beheben Sie diesen Fehler  
  
-   Verwenden Sie „}“ zum Beenden des Arrayinitialisierers oder der Einschränkungsliste.  
  
## Siehe auch  
 [Arrays](/dotnet/visual-basic/programming-guide/language-features/arrays/index)   
 [How to: Initialize an Array Variable in Visual Basic](../Topic/How%20to:%20Initialize%20an%20Array%20Variable%20in%20Visual%20Basic.md)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)   
 [Generische Typen in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)