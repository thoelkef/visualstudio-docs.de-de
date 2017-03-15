---
title: "&quot;Sub New&quot; kann nicht als &quot;Overrides&quot; deklariert werden. | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30283"
  - "bc30283"
helpviewer_keywords: 
  - "BC30283"
ms.assetid: 0e71cdcb-b62e-4a36-8829-83de5c453c74
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;Sub New&quot; kann nicht als &quot;Overrides&quot; deklariert werden.
Ein Konstruktor gibt an, dass er einen geerbten Konstruktor überschreibt. Konstruktoren können nicht überschrieben werden.  
  
 **Fehler\-ID:** BC30283  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie das `Overrides`\-Schlüsselwort aus der `Sub`\-Deklaration.  
  
## Siehe auch  
 [NICHT IM BUILD: Überschreiben von Eigenschaften und Methoden](http://msdn.microsoft.com/de-de/2167e8f5-1225-4b13-9ebd-02591ba90213)   
 [NICHT IM BUILD: Verwenden von Konstruktoren und Destruktoren](http://msdn.microsoft.com/de-de/548eebe1-86c4-4377-b2f5-447cb8be3d90)