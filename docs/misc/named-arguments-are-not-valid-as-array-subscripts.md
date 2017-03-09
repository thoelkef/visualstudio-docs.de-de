---
title: "Benannte Argumente sind als Arrayfeldindex ung&#252;ltig. | Microsoft Docs"
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
  - "vbc30075"
  - "bc30075"
helpviewer_keywords: 
  - "BC30075"
ms.assetid: a25025c9-0763-4c19-9e9b-cffb9aacaa8a
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Benannte Argumente sind als Arrayfeldindex ung&#252;ltig.
Ein Arrayindex wird mit der Syntax definiert, die für das namentliche Übergeben eines Prozedurarguments \(z. B. `Array(Index := 10)`\) verwendet wird. Diese Syntax ist für Arrayfeldindizes ungültig.  
  
 **Fehler\-ID:** BC30075  
  
### So beheben Sie diesen Fehler  
  
-   Verwenden Sie eine normale Variable oder einen Konstantenausdruck als Arrayindex, z. B. `Array(10)`.  
  
## Siehe auch  
 [NOTINBUILD: Übersicht über Arrays in Visual Basic](http://msdn.microsoft.com/de-de/ca50e2f2-b4d2-4c57-9169-9abbcc3392d8)   
 [Passing Arguments by Position and by Name](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name)