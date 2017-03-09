---
title: "Ungeplante Fiber | Microsoft Docs"
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
  - "bc30948"
  - "vbc30948"
helpviewer_keywords: 
  - "BC30948"
ms.assetid: 982bf6d2-ce62-4451-8a23-82dacf8ee100
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Ungeplante Fiber
Der Debugger kann einen Ausdruck nicht auswerten, da dieser sich in einer logischen Fiber befindet, die nicht für einen physischen Thread geplant wurde. Dies kann vorkommen, wenn der Prozess unter SQL Server mit Fibers ausgeführt wird.  
  
 Eine Fiber besteht aus einem Stapel und einem Registerkontext und kann in jedem Thread ausgeführt werden. Eine Fiber kann aus einem Thread ausgelagert und später in einem anderen Thread neu gestartet werden.  
  
 **Fehler\-ID:** BC30948  
  
### So beheben Sie diesen Fehler  
  
-   Stellen Sie sicher, dass die Fiber für einen physischen Thread geplant ist.  
  
## Siehe auch  
 [Debugging SQL](http://msdn.microsoft.com/de-de/f27c17e6-1d90-49f2-9fc0-d02e6a27f109)   
 [Debuggen in Visual Studio](../debugger/debugging-in-visual-studio.md)