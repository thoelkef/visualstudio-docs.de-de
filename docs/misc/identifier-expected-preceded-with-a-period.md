---
title: "Bezeichner mit vorangestelltem Punkt erwartet. | Microsoft Docs"
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
  - "bc36576"
  - "vbc36576"
helpviewer_keywords: 
  - "BC36576"
ms.assetid: 02217cc4-8972-4a6d-97a6-4ecbb7399af2
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Bezeichner mit vorangestelltem Punkt erwartet.
Ein Wert, von dem kein Eigenschaftenname abgeleitet werden kann, wurde in die Initialisiererliste der Deklaration eines anonymen Typs eingefügt, ohne das er einem Eigenschaftennamen zugewiesen wurde.  
  
```  
' Not valid. ' Dim anon1 = New With {.grade = 100, 95}  
```  
  
 **Fehler\-ID:** BC36576  
  
### So beheben Sie diesen Fehler  
  
-   Geben Sie für jeden Wert in der Initialisiererliste einen Eigenschaftennamen an, wie im folgenden Code gezeigt:  
  
    ```  
    Dim anon2 = New With {.grade1 = 100, .grade2 = 95}  
    ```  
  
## Siehe auch  
 [Object Initializers: Named and Anonymous Types](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [Gewusst wie: Deklarieren einer Instanz eines anonymen Typs \(Visual Basic\)](http://msdn.microsoft.com/de-de/119f616c-9bcd-4731-ac00-4285be5959f7)   
 [Gewusst wie: Ableiten von Eigenschaftennamen und Typen in Deklarationen von anonymen Typen](../Topic/How%20to:%20Infer%20Property%20Names%20and%20Types%20in%20Anonymous%20Type%20Declarations%20\(Visual%20Basic\).md)