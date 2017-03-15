---
title: "Ein Verweis auf ein Objekt, das bearbeitet wird, ist nicht g&#252;ltig, wenn ein anderer Konstruktor aufgerufen wird. | Microsoft Docs"
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
  - "bc31095"
  - "vbc31095"
helpviewer_keywords: 
  - "BC31095"
ms.assetid: 68be49f1-e662-45c7-9998-e0006324535d
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Ein Verweis auf ein Objekt, das bearbeitet wird, ist nicht g&#252;ltig, wenn ein anderer Konstruktor aufgerufen wird.
Es wurde auf einen Objektmember verwiesen, bevor die Objekterstellung vom Konstruktor des Objekts abgeschlossen wurde.  
  
 **Fehler\-ID:** BC31095  
  
### So beheben Sie diesen Fehler  
  
-   Beim Aufrufen eines Konstruktors von einem anderen Konstruktor sollte `MyBase`, `MyClass` oder `Me` nicht verwendet werden.  
  
## Siehe auch  
 [Object Lifetime: How Objects Are Created and Destroyed](../Topic/Object%20Lifetime:%20How%20Objects%20Are%20Created%20and%20Destroyed%20\(Visual%20Basic\).md)   
 [NICHT IM BUILD: Verwenden von Konstruktoren und Destruktoren](http://msdn.microsoft.com/de-de/548eebe1-86c4-4377-b2f5-447cb8be3d90)