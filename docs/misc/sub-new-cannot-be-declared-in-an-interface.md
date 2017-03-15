---
title: "&quot;Sub New&quot; kann nicht in einer Schnittstelle deklariert werden | Microsoft Docs"
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
  - "bc30363"
  - "vbc30363"
helpviewer_keywords: 
  - "BC30363"
ms.assetid: 371d9aa8-a935-48ce-ada2-0a69ba20e070
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;Sub New&quot; kann nicht in einer Schnittstelle deklariert werden
Sie haben versucht, `Sub New` in einer Schnittstelle zu deklarieren. Da es sich um einen Konstruktor handelt, kann `Sub New` nur einmal bei der Erstellung einer Klasse ausgeführt werden. "Sub New" kann nicht explizit an einer beliebigen Stelle aufgerufen werden, außer in der ersten Codezeile eines anderen Konstruktors derselben Klasse oder einer abgeleiteten Klasse.  
  
 **Fehler\-ID:** BC30363  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie `Sub New`, oder verschieben Sie das Element im Code an eine geeignete Position.  
  
## Siehe auch  
 [NICHT IM BUILD: Verwenden von Konstruktoren und Destruktoren](http://msdn.microsoft.com/de-de/548eebe1-86c4-4377-b2f5-447cb8be3d90)