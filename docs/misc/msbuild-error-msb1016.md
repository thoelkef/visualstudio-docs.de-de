---
title: "MSBuild Error MSB1016 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.MissingVerbosityError"
helpviewer_keywords: 
  - "MSB1016"
ms.assetid: 967a9757-0513-48ae-bf1d-b1b019993c70
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB1016
**Geben Sie den Ausführlichkeitsgrad an.**  
  
 Ein Ausführlichkeitsgrad muss für den Schalter **\/verbosity** angegeben werden.  
  
### So beheben Sie diesen Fehler  
  
1.  Geben Sie den Ausführlichkeitsgrad im Format `/verbosity:<level>` an.  Die verfügbaren Ausführlichkeitsgrade sind: q\[uiet\], m\[inimal\], n\[ormal\], d\[etailed\] und diag\[nostic\], z. B. `/verbosity:quiet`,  `/verbosity:q` oder  `/v:q`.  
  
## Siehe auch  
 [Command\-Line Reference](../msbuild/msbuild-command-line-reference.md)