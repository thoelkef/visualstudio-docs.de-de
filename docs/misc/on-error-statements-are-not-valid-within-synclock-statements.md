---
title: "&#39;On Error&#39;-Anweisungen sind innerhalb von &#39;SyncLock&#39;-Anweisungen nicht g&#252;ltig. | Microsoft Docs"
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
  - "bc30752"
  - "vbc30752"
helpviewer_keywords: 
  - "BC30752"
ms.assetid: 5c726627-b0fc-4edf-bd29-a83a0009f44d
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;On Error&#39;-Anweisungen sind innerhalb von &#39;SyncLock&#39;-Anweisungen nicht g&#252;ltig.
`On Error`\-Anweisungen können nicht innerhalb von `SyncLock`\-Blöcken verwendet werden, da die die Threadsynchronisierung stören würde.  
  
 **Fehler\-ID:** BC30752  
  
### So beheben Sie diesen Fehler  
  
1.  Platzieren Sie `On Error`\-Anweisungen außerhalb von `SyncLock`\-Blöcken.  
  
## Siehe auch  
 [On Error Statement](/dotnet/visual-basic/language-reference/statements/on-error-statement)