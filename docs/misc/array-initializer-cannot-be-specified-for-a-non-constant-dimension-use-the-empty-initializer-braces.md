---
title: "Der Arrayinitialisierer kann nicht f&#252;r eine nicht konstante Dimension angegeben werden. Verwenden Sie den leeren Initialisierer &#39;{}&#39;. | Microsoft Docs"
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
  - "vbc30949"
  - "bc30949"
helpviewer_keywords: 
  - "BC30949"
ms.assetid: b3d27d9c-7a1f-4bac-ad71-388b24b807b3
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Der Arrayinitialisierer kann nicht f&#252;r eine nicht konstante Dimension angegeben werden. Verwenden Sie den leeren Initialisierer &#39;{}&#39;.
Ein Array initialisiert eine Dimension, die zum Zeitpunkt der Kompilierung nicht bekannt ist.  
  
 Der folgende Code generiert diese Warnung.  
  
```  
Dim j As Integer Dim intArray As Integer = New Integer(1, j) {{0, 100}, {1,101}}  
```  
  
 Mit folgendem Code wird der Fehler vermieden.  
  
```  
Dim intArray As Integer = New Integer(1, j) {} For i As Integer = 0 To j intArray(0, i) = i intArray(1, i) = 100 + i Next i  
```  
  
 **Fehler\-ID:** BC30949  
  
### So beheben Sie diesen Fehler  
  
-   Geben Sie nach Möglichkeit eine konstante Dimension in der Arraydeklaration an.  
  
-   Wenn Sie keine konstante Dimension angeben können, müssen Sie das Array mit einer Schleife initialisieren, wenn die nicht konstante Dimension bekannt ist.  
  
## Siehe auch  
 [For Each...Next\-Anweisung](/dotnet/visual-basic/language-reference/statements/for-each-next-statement)   
 [NOTINBUILD: Übersicht über Arrays in Visual Basic](http://msdn.microsoft.com/de-de/ca50e2f2-b4d2-4c57-9169-9abbcc3392d8)   
 [How to: Initialize an Array Variable in Visual Basic](../Topic/How%20to:%20Initialize%20an%20Array%20Variable%20in%20Visual%20Basic.md)   
 [NOTINBUILD Gewusst wie: Initialisieren eines mehrdimensionalen Arrays](http://msdn.microsoft.com/de-de/502dcf8b-d86c-46f1-ad7d-3ce809645774)