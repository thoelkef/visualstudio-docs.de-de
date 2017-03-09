---
title: "Strukturen k&#246;nnen keine nicht freigegebene &#39;Sub New&#39; ohne Parameter deklarieren. | Microsoft Docs"
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
  - "vbc30629"
  - "bc30629"
helpviewer_keywords: 
  - "BC30629"
ms.assetid: f4298ef7-85b1-4543-b764-4c3abda84baa
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Strukturen k&#246;nnen keine nicht freigegebene &#39;Sub New&#39; ohne Parameter deklarieren.
In Strukturen deklarierte `Sub New`\-Konstruktoren müssen entweder Argumente annehmen oder mit dem `Shared`\-Modifizierer deklariert werden.  
  
 **Fehler\-ID:** BC30629  
  
### So beheben Sie diesen Fehler  
  
-   Ändern Sie den `Sub New`\-Konstruktor, sodass dieser Argumente akzeptiert.  
  
-   Wenden Sie den `Shared`\-Modifizierer an, um den Konstruktor freizugeben.  
  
## Siehe auch  
 [Structure Statement](/dotnet/visual-basic/language-reference/statements/structure-statement)   
 [Structures](/dotnet/visual-basic/programming-guide/language-features/data-types/structures)