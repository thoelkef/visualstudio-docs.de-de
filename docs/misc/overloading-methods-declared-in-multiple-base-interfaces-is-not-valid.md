---
title: "Das &#220;berladen von Methoden, die in mehreren Basisschnittstellen deklariert sind, ist nicht zul&#228;ssig. | Microsoft Docs"
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
  - "bc31410"
  - "vbc31410"
helpviewer_keywords: 
  - "BC31410"
ms.assetid: 7d1831c2-837c-4b02-8492-d0fc038fe184
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Das &#220;berladen von Methoden, die in mehreren Basisschnittstellen deklariert sind, ist nicht zul&#228;ssig.
Mehrere geerbte Schnittstellen überladen implizit dieselbe Methode.  
  
 **Fehler\-ID:** BC31410  
  
### So beheben Sie diesen Fehler  
  
-   Verwenden sie den `Shadows`\-Modifizierer anstelle des `Overloads`\-Modifizierers.  
  
## Siehe auch  
 [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads)   
 [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows)