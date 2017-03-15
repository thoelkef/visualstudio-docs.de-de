---
title: "Compilerfehler CS1646 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1646"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1646"
ms.assetid: 5e4b0f1e-8de3-42b0-bde6-9f882677a409
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1646
Schlüsselwort, Bezeichner oder Zeichenfolge erwartet nach dem ausführlichen Spezifizierer: @  
  
 Informationen zur Verwendung des ausführlichen Spezifizierers '@' finden Sie unter den Zeichenfolgenliteralen. Der ausführliche Spezifizierer ist nur vor einer Zeichenfolge, einem Schlüsselwort oder einem Bezeichner zulässig. Entfernen Sie alle unangemessenen @\-Symbole, oder fügen Sie die vorgesehene Zeichenfolge, das Schlüsselwort oder den Bezeichner hinzu.  
  
 Im folgenden Beispiel wird CS1646 generiert:  
  
```  
// CS1646 class C { int i = @5;  // CS1646 // Try this line instead: // int i = 5; }  
```