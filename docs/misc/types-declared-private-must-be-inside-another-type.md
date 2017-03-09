---
title: "Typen, die als &quot;Private&quot; deklariert sind, m&#252;ssen sich innerhalb eines anderen Typs befinden. | Microsoft Docs"
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
  - "vbc31089"
  - "bc31089"
helpviewer_keywords: 
  - "BC31089"
ms.assetid: 44ea5fe4-4af6-4cea-a4a5-2cf966df2937
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Typen, die als &quot;Private&quot; deklariert sind, m&#252;ssen sich innerhalb eines anderen Typs befinden.
Der `Private`\-Modifizierer wurde für einen Typ verwendet, der sich nicht in einem anderen Typ befindet.  
  
 **Fehler\-ID:** BC31089  
  
### So beheben Sie diesen Fehler  
  
1.  Verwenden Sie einen weniger restriktiven Zugriffsmodifizierer, z. B. `Friend`.  
  
2.  Deklarieren Sie den Typ innerhalb eines anderen Typs.  
  
## Siehe auch  
 [Private](/dotnet/visual-basic/language-reference/modifiers/private)