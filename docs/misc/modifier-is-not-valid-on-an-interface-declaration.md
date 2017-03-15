---
title: "&#39;&lt;modifizierer&gt;&#39; ist in Schnittstellendeklarationen ung&#252;ltig. | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30397"
  - "vbc30397"
helpviewer_keywords: 
  - "BC30397"
ms.assetid: 9143dc87-c396-4ff9-9987-0b460ee32b38
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;modifizierer&gt;&#39; ist in Schnittstellendeklarationen ung&#252;ltig.
Sie haben einen Modifizierer verwendet, der in `Interface`\-Deklarationen nicht gültig ist. Die einzigen gültigen Modifizierer für `Sub`\-, `Function`\- und `Property`\-Anweisungen, die in einer `Interface`\-Deklaration deklariert sind, sind die Schlüsselwörter `Overloads` und `Default`. Andere Modifizierer, wie etwa `Public`, `Private`, `Friend`, `Protected`, `Shared`, `Static`, `Overrides`, `MustOverride` und `Overridable`, sind ungültig.  
  
 **Fehler\-ID:** BC30397  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie den Modifizierer.  
  
## Siehe auch  
 [NICHT IM BUILD: Schnittstellendefinition](http://msdn.microsoft.com/de-de/7840a52c-9c38-42c4-adbc-e2c02e9dc204)