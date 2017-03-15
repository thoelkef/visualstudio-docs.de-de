---
title: "ReDim-Anweisungen erfordern eine in Klammern gesetzte Liste der neuen Grenzen jeder Arraydimension. | Microsoft Docs"
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
  - "bc30670"
  - "vbc30670"
helpviewer_keywords: 
  - "BC30670"
ms.assetid: b2c5fea3-e7db-4797-b917-d61a65befbd4
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ReDim-Anweisungen erfordern eine in Klammern gesetzte Liste der neuen Grenzen jeder Arraydimension.
Geben Sie die neue Größe eines Arrays im Rahmen einer `ReDim`\-Anweisung an.  
  
 **Fehler\-ID:** BC30670  
  
### So beheben Sie diesen Fehler  
  
-   Geben Sie die Größe der einzelnen Ränge des Arrays an. Beispiel:  
  
    ```  
    ReDim arr(5, 6)  
    ```  
  
## Siehe auch  
 [ReDim Statement](/dotnet/visual-basic/language-reference/statements/redim-statement)