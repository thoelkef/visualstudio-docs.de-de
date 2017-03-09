---
title: "&#39;Default&#39; kann nicht mit &#39;&lt;Spezifizierer&gt;&#39; kombiniert werden. | Microsoft Docs"
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
  - "vbc30490"
  - "bc30490"
helpviewer_keywords: 
  - "BC30490"
ms.assetid: fb29622c-a176-4185-94ae-2c1ca85adddb
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Default&#39; kann nicht mit &#39;&lt;Spezifizierer&gt;&#39; kombiniert werden.
Sie haben versucht, das `Default`\-Schlüsselwort mit einem Spezifizierer wie `Shared` oder `Private` zu kombinieren. Das ist in diesem Kontext nicht gültig.  
  
 **Fehler\-ID:** BC30490  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie `Default`.  
  
     \- oder \-  
  
-   Entfernen Sie den Spezifizierer, der den Konflikt verursacht.  
  
## Siehe auch  
 [Default](/dotnet/visual-basic/language-reference/modifiers/default)