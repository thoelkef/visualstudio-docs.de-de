---
title: "Informationen f&#252;r den Typ von &#39;&lt;Typname&gt;&#39; wurden nicht in die Laufzeit geladen. | Microsoft Docs"
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
  - "vbc30750"
  - "bc30750"
helpviewer_keywords: 
  - "BC30750"
ms.assetid: b0f074f9-571d-48f8-b334-4fd34b61cd89
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Informationen f&#252;r den Typ von &#39;&lt;Typname&gt;&#39; wurden nicht in die Laufzeit geladen.
Es wurde auf einen Typ verwiesen, der von der Common Language Runtime nicht geladen wurde.  
  
 **Fehler\-ID:** BC30750  
  
### So beheben Sie diesen Fehler  
  
1.  Strukturieren Sie den Code um, sodass der Typ innerhalb des aktuellen Bereichs definiert ist.  
  
2.  Vergewissern Sie sich, dass der Member definiert ist und Sie den Membernamen richtig geschrieben haben.  
  
3.  Versuchen Sie, auf einen der im Modul deklarierten Member zuzugreifen. In einigen Fällen können in der Debugumgebung Member nicht gefunden werden, weil die Module, in denen sie deklariert sind, nicht geladen wurden.  
  
## Siehe auch  
 [Debuggen in Visual Studio](../debugger/debugging-in-visual-studio.md)