---
title: "Es kann kein Datentyp f&#252;r &#39;&lt;Variablename&gt;&#39; abgeleitet werden, da die Arraydimensionen nicht &#252;bereinstimmen. | Microsoft Docs"
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
  - "bc36909"
  - "vbc36909"
helpviewer_keywords: 
  - "BC36909"
ms.assetid: e41fec81-efec-4395-a0a5-d81906a2d4f1
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Es kann kein Datentyp f&#252;r &#39;&lt;Variablename&gt;&#39; abgeleitet werden, da die Arraydimensionen nicht &#252;bereinstimmen.
Wenn die Dimensionen, die zum Initialisieren eines Arrays verwendet werden, nicht mit den Dimensionen in der Deklaration übereinstimmen, kann der Compiler keinen Datentyp für das Array ableiten. Beispielsweise verursacht der folgende Code diesen Fehler.  
  
```vb#  
' Valid. exampleArray1 is a one-dimensional array of integers. Dim exampleArray1() = New Integer() {1, 2, 3} ' Not valid. 'Dim exampleArray2(,) = New Integer() {1, 2, 3} 'Dim exampleArray3(,) = New Integer() {}  
```  
  
 **Fehler\-ID:** BC36909  
  
## Siehe auch  
 [Local Type Inference](/dotnet/visual-basic/programming-guide/language-features/variables/local-type-inference)   
 [NOTINBUILD Gewusst wie: Initialisieren eines mehrdimensionalen Arrays](http://msdn.microsoft.com/de-de/502dcf8b-d86c-46f1-ad7d-3ce809645774)