---
title: "Der Wert einer lokalen Variablen kann f&#252;r eine Methode, die sich nicht oben auf dem Stapel befindet, nicht festgelegt werden. | Microsoft Docs"
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
  - "bc30711"
  - "vbc30711"
helpviewer_keywords: 
  - "BC30711"
ms.assetid: b2aa290f-3311-448a-af46-ff2a2add5788
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Der Wert einer lokalen Variablen kann f&#252;r eine Methode, die sich nicht oben auf dem Stapel befindet, nicht festgelegt werden.
Sie können Variablen nur ändern, wenn sie am Anfang der Aufrufliste stehen. Wenn `procedure1` z. B. `procedure2` aufruft und Sie sich in `procedure1` befinden, können Sie keine Variablen in `procedure2` ändern.  
  
 **Fehler\-ID:** BC30711  
  
### So beheben Sie diesen Fehler  
  
-   Ändern Sie die Variablen, die sich am Anfang der Aufrufliste befinden.  
  
## Siehe auch  
 [Debuggen in Visual Studio](../debugger/debugging-in-visual-studio.md)