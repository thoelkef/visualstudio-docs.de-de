---
title: "&#39;Exit Function&#39; ist in Sub oder Property ung&#252;ltig | Microsoft Docs"
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
  - "vbc30067"
  - "bc30067"
helpviewer_keywords: 
  - "BC30067"
ms.assetid: 207fef65-4383-4120-9e5a-e0e14d168a72
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Exit Function&#39; ist in Sub oder Property ung&#252;ltig
`Exit Function` tritt in einer `Sub`\-Prozedur oder einer `Property`\-Prozedur auf. Eine `Exit`\-Anweisung muss dem Block entsprechen, in dem sie verwendet wird.  
  
 **Fehler\-ID:** BC30067  
  
### So beheben Sie diesen Fehler  
  
-   Ersetzen Sie `Exit Function` durch die `Exit Sub`\- bzw. `Exit Property`\-Anweisung.  
  
## Siehe auch  
 [Sub Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/sub-procedures)   
 [Function\-Prozeduren](/dotnet/visual-basic/programming-guide/language-features/procedures/function-procedures)   
 [Eigenschaftenprozeduren](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)