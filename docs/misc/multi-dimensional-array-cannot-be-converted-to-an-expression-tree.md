---
title: "Ein mehrdimensionales Array kann nicht in eine Ausdrucksbaumstruktur konvertiert werden. | Microsoft Docs"
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
  - "bc36603"
  - "vbc36603"
helpviewer_keywords: 
  - "BC36603"
ms.assetid: 65eefab7-c7ad-4dcd-bebf-2d16fba9f28f
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Ein mehrdimensionales Array kann nicht in eine Ausdrucksbaumstruktur konvertiert werden.
Die meisten Ausdrücke können in Ausdrucksbaumstrukturen konvertiert werden, mehrdimensionale Arrays jedoch nicht. Beispielsweise verursacht der folgende Code diesen Fehler:  
  
```vb#  
Module Module1 Sub Main() '' A multi-dimensional array cannot be converted. 'Dim expTree As Expressions.Expression(Of Func(Of Object)) = _ '    Function() New Integer(1, 1) {{1, 2}, {2, 3}} ' A one-dimensional array can be converted. Dim expTree2 As Expressions.Expression(Of Func(Of Object)) = _ Function() New Integer() {1, 2, 3} End Sub End Module  
```  
  
 **Fehler\-ID:** BC36603  
  
## Siehe auch  
 [NICHT IM BUILD: Ausdrucksbaumstrukturen in LINQ](http://msdn.microsoft.com/de-de/1a2e8e74-4bbc-45ab-9a46-2b6cfce3bcb2)   
 [Gewusst wie: Verwenden von Ausdrucksbaumstrukturen zum Erstellen dynamischer Abfragen](../Topic/How%20to:%20Use%20Expression%20Trees%20to%20Build%20Dynamic%20Queries%20\(C%23%20and%20Visual%20Basic\).md)   
 [NOTINBUILD: Mehrdimensionale Arrays in Visual Basic](http://msdn.microsoft.com/de-de/d92cad25-07e2-4d79-8ea4-ab269700f5de)