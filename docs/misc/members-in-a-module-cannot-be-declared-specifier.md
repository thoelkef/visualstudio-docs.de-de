---
title: "Member in einem Modul k&#246;nnen nicht als &#39;&lt;Spezifizierer&gt;&#39; deklariert werden. | Microsoft Docs"
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
  - "vbc30436"
  - "bc30436"
helpviewer_keywords: 
  - "BC30436"
ms.assetid: c0560864-64f6-4c76-803f-d9c51df89d62
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Member in einem Modul k&#246;nnen nicht als &#39;&lt;Spezifizierer&gt;&#39; deklariert werden.
Sie haben einen Spezifizierer verwendet, der für einen Member innerhalb einer `Module`\-Anweisung ungültig ist. Module können nie instanziiert werden, unterstützen keine Vererbung und können keine Schnittstellen implementieren.  
  
 **Fehler\-ID:** BC30436  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie den Spezifizierer.  
  
## Siehe auch  
 [Module Statement](/dotnet/visual-basic/language-reference/statements/module-statement)