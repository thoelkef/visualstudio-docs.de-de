---
title: "Ein Aufruf an einen Konstruktor ist nur als erste Anweisung in einem Instanzenkonstruktor g&#252;ltig | Microsoft Docs"
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
  - "vbc30282"
  - "bc30282"
helpviewer_keywords: 
  - "BC30282"
ms.assetid: c51b172f-fbd7-4ef5-8276-01a4bf6ed35b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Ein Aufruf an einen Konstruktor ist nur als erste Anweisung in einem Instanzenkonstruktor g&#252;ltig
Ein Aufruf von `New()` erfolgt nach der ersten Anweisung eines Konstruktors. Wenn ein Konstruktor einen anderen Konstruktor explizit aufruft, muss dieser Aufruf in der ersten Anweisung nach der `Sub New()`\-Anweisung erfolgen.  
  
 **Fehler\-ID:** BC30282  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie den Aufruf von `New()`, oder verschieben Sie ihn an den Anfang des Konstruktors.  
  
## Siehe auch  
 [NICHT IM BUILD: Verwenden von Konstruktoren und Destruktoren](http://msdn.microsoft.com/de-de/548eebe1-86c4-4377-b2f5-447cb8be3d90)