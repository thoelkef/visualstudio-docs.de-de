---
title: "GoSub-Anweisungen werden nicht mehr unterst&#252;tzt. | Microsoft Docs"
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
  - "vbc30814"
  - "bc30814"
helpviewer_keywords: 
  - "BC30814"
ms.assetid: fef2d78f-39ba-4aad-93b3-c7a08df9f805
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# GoSub-Anweisungen werden nicht mehr unterst&#252;tzt.
`GoSub` kann nicht zum Aufrufen einer Prozedur verwendet werden.  
  
 **Fehler\-ID:** BC30814  
  
### So beheben Sie diesen Fehler  
  
-   Rufen Sie Prozeduren direkt ohne `GoSub`auf. Beispiel:  
  
    ```  
    CalculateInterest(Amount, Rate, Time)  
    ```  
  
## Siehe auch  
 [Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/index)