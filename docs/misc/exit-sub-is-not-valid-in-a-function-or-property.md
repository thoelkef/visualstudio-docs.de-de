---
title: "„Exit Sub“ ist ung&#252;ltig in „Function“ oder „Property“. | Microsoft Docs"
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
  - "bc30065"
  - "vbc30065"
helpviewer_keywords: 
  - "BC30065"
ms.assetid: d6426861-ba64-4dca-9100-262c6c058bd9
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# „Exit Sub“ ist ung&#252;ltig in „Function“ oder „Property“.
`Exit Sub` wird in einer `Function`\- oder `Property`\-Prozedur verwendet. Eine `Exit`\-Anweisung muss dem Block entsprechen, in dem sie verwendet wird.  
  
 **Fehler\-ID:** BC30065  
  
### So beheben Sie diesen Fehler  
  
-   Ersetzen Sie `Exit Sub` mit der `Exit Function`\- bzw. `Exit Property`\-Anweisung.  
  
## Siehe auch  
 [Sub Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/sub-procedures)   
 [Function\-Prozeduren](/dotnet/visual-basic/programming-guide/language-features/procedures/function-procedures)   
 [Eigenschaftenprozeduren](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)