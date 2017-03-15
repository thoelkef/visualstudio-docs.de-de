---
title: "Der Typ &quot;&lt;Typname&gt;&quot; wird nicht unterst&#252;tzt, weil er direkt oder indirekt von sich selbst erbt. | Microsoft Docs"
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
  - "bc30916"
  - "vbc30916"
helpviewer_keywords: 
  - "BC30916"
ms.assetid: cea33daf-1971-4b70-a01d-7d8b5c9e4269
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Der Typ &quot;&lt;Typname&gt;&quot; wird nicht unterst&#252;tzt, weil er direkt oder indirekt von sich selbst erbt.
Eine Klasse oder Schnittstelle erbt von sich selbst oder von einer anderen Klasse oder Schnittstelle, die letztendlich von ihr erbt.  
  
 Visual Basic unterstützt keine zirkuläre Vererbung.  
  
 **Fehler\-ID:** BC30916  
  
### So beheben Sie diesen Fehler  
  
-   Ändern Sie die Vererbungsstruktur so, dass sie auf einer Basisklasse oder Schnittstelle basiert, die nicht von einer anderen Klasse oder Schnittstelle erbt.  
  
## Siehe auch  
 [Inheritance Basics](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)