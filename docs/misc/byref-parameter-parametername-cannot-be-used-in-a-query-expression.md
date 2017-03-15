---
title: "Der ByRef-Parameter &quot;&lt;Parametername&gt;&quot; kann in einem Abfrageausdruck nicht verwendet werden. | Microsoft Docs"
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
  - "vbc36533"
  - "bc36533"
helpviewer_keywords: 
  - "BC36533"
ms.assetid: 8067ac87-dd6b-4869-87d0-8a4ce272de41
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Der ByRef-Parameter &quot;&lt;Parametername&gt;&quot; kann in einem Abfrageausdruck nicht verwendet werden.
Ein Parameter in einer LINQ\-Abfrage ist ein Zeigertyp. In Abfrageausdrücken verwendete Parameter können nicht per Verweis übergeben werden.  
  
 **Fehler\-ID:** BC36533  
  
### So beheben Sie diesen Fehler  
  
1.  Deklarieren Sie eine neue Variable, und weisen Sie den Wert der neuen Variablen einer Kopie des Werts zu, der per Verweis übergeben wird. Verwenden Sie die kopierte Variable in der LINQ\-Abfrage. Im Folgenden finden Sie ein Beispiel dazu:  
  
    ```vb#  
    Sub RunQuery(ByVal collection As List(Of Integer), _  
                 ByRef filterValue As Integer)  
        Dim fv = filterValue  
        Dim queryResult = From num In collection _  
                          Where num < fv  
    End Sub  
    ```  
  
### So beheben Sie diesen Fehler  
  
1.  Ersetzen Sie bei dem in der Abfrage verwendeten Parameter das `ByRef`\-Schlüsselwort durch das `ByVal`\-Schlüsselwort.  
  
## Siehe auch  
 [Differences Between Passing an Argument By Value and By Reference](/dotnet/visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference)   
 [Introduction to LINQ in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [LINQ](/dotnet/visual-basic/programming-guide/language-features/linq/index)