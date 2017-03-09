---
title: "Ein impliziter Verweis auf ein Objekt, das bearbeitet wird, ist nicht g&#252;tig, wenn ein anderer Konstruktor aufgerufen wird. | Microsoft Docs"
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
  - "vbc31096"
  - "bc31096"
helpviewer_keywords: 
  - "BC31096"
ms.assetid: 558a2beb-aa5d-41a8-8655-ad3d16ac8acd
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Ein impliziter Verweis auf ein Objekt, das bearbeitet wird, ist nicht g&#252;tig, wenn ein anderer Konstruktor aufgerufen wird.
Es wurde auf einen Objektmember verwiesen, bevor die Objekterstellung vom Konstruktor des Objekts abgeschlossen wurde.  
  
 **Fehler\-ID:** BC31096  
  
### So beheben Sie diesen Fehler  
  
-   Beim Aufrufen eines Konstruktors von einem anderen Konstruktor sollten `MyBase`, `MyClass` oder `Me` nicht verwendet werden.  
  
## Siehe auch  
 [Object Lifetime: How Objects Are Created and Destroyed](../Topic/Object%20Lifetime:%20How%20Objects%20Are%20Created%20and%20Destroyed%20\(Visual%20Basic\).md)   
 [NICHT IM BUILD: Verwenden von Konstruktoren und Destruktoren](http://msdn.microsoft.com/de-de/548eebe1-86c4-4377-b2f5-447cb8be3d90)