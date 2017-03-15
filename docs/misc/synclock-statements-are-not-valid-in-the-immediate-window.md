---
title: "SyncLock-Anweisungen sind im Direktfenster nicht g&#252;ltig | Microsoft Docs"
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
  - "vbc30135"
  - "bc30135"
helpviewer_keywords: 
  - "BC30135"
ms.assetid: 099771a1-5bf4-4c16-8fc3-262926c771df
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# SyncLock-Anweisungen sind im Direktfenster nicht g&#252;ltig
Die `SyncLock`\-Anweisung synchronisiert Threads und ist in einem Debugkontext nicht zulässig.  
  
 **Fehler\-ID:** BC30135  
  
### So beheben Sie diesen Fehler  
  
-   Verwenden Sie im **Direktfenster** keine `SyncLock`\-Anweisung.  
  
## Siehe auch  
 [Direktfenster](../ide/reference/immediate-window.md)   
 [SyncLock Statement](/dotnet/visual-basic/language-reference/statements/synclock-statement)