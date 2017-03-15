---
title: "Arraydeklarationen k&#246;nnen keine unteren Grenzen bestimmen. | Microsoft Docs"
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
  - "vbc30805"
  - "bc30805"
helpviewer_keywords: 
  - "BC30805"
ms.assetid: f2055387-f4dc-4366-89fb-d752929a0258
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Arraydeklarationen k&#246;nnen keine unteren Grenzen bestimmen.
Arrays haben immer die Untergrenze 0 \(null\). Sie können 0 \(null\) als untere Grenze angeben, um den Code besser lesbar zu gestalten. Sie können für die untere Grenze jedoch keinen anderen Wert angeben.  
  
 **Fehler\-ID:** BC30805  
  
### So beheben Sie diesen Fehler  
  
-   Dimensionieren Sie Arrays entsprechend, dass sie eine Nummer kleiner als die Gesamtzahl der Elemente sind. Beispielsweise weist `Dim y(6)` dieselbe Größe \(7 Elemente\) wie `Dim x(3 To 9)` auf. Sie können auch `Dim y(0 To 6)` angeben.  
  
-   Verwenden Sie Offsets, um untere Grenzen ungleich 0 \(null\) zu simulieren. Im folgende Beispiel wird ein Array mit der Dimension 3 bis 9 simuliert.  
  
    ```  
    Const offset As Integer = 3 Dim arrayIndex As Integer ' arrayIndex can vary between 3 and 9. Dim y(0 To 6) ' The preceding statement allocates the same number of elements ' as Dim y(3 To 9). y(arrayIndex - offset) = value ' The preceding statement converts arrayIndex to the ' corresponding index of y.  
    ```  
  
## Siehe auch  
 [Arrays](/dotnet/visual-basic/programming-guide/language-features/arrays/index)   
 [Array Dimensions in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/arrays/array-dimensions)   
 [NOTINBUILD Gewusst wie: Angeben einer unteren Grenze von 0 \(null\) für ein Array](http://msdn.microsoft.com/de-de/20ffd49a-64f7-4634-8ed0-46ba1049d935)