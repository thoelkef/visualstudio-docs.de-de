---
title: "F&#252;r Arrays, die mit expliziten Grenzen deklariert sind, ist keine explizite Initialisierung zul&#228;ssig. | Microsoft Docs"
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
  - "bc30672"
  - "vbc30672"
helpviewer_keywords: 
  - "BC30672"
ms.assetid: 4b525e8d-bde5-4408-8c10-7605ca039f0e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# F&#252;r Arrays, die mit expliziten Grenzen deklariert sind, ist keine explizite Initialisierung zul&#228;ssig.
Arrays können nicht initialisiert werden, wenn sie mit einer bestimmten Größe deklariert wurden.  
  
 **Fehler\-ID:** BC30672  
  
### So beheben Sie diesen Fehler  
  
-   Deklarieren Sie das Array, und initialisieren Sie es separat.  
  
-   Deklarieren und initialisieren Sie es als dynamisches Array, und verwenden Sie ggf. `ReDim`. Beispiel:  
  
    ```  
    Dim A() As Integer = {0, 1, 2, 3} ReDim Preserve A(3)  
    ```  
  
## Siehe auch  
 [Arrays](/dotnet/visual-basic/programming-guide/language-features/arrays/index)