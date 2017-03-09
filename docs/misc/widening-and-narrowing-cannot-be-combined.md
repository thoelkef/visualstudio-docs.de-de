---
title: "&#39;Widening&#39; und &#39;Narrowing&#39; k&#246;nnen nicht kombiniert werden. | Microsoft Docs"
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
  - "bc33001"
  - "vbc33001"
helpviewer_keywords: 
  - "BC33001"
ms.assetid: 1c576344-083c-45ad-bc71-0489bd3976be
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Widening&#39; und &#39;Narrowing&#39; k&#246;nnen nicht kombiniert werden.
Ein [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement) gibt sowohl [Widening](/dotnet/visual-basic/language-reference/modifiers/widening) als auch [Narrowing](/dotnet/visual-basic/language-reference/modifiers/narrowing) an.  
  
 Wenn Sie einen Konvertierungsoperator definieren, müssen Sie ihn entweder als `Widening` oder als `Narrowing` deklarieren. Diese Merkmale schließen sich gegenseitig aus, Sie können also nicht beide angeben.  
  
 **Fehler\-ID:** BC33001  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie das entweder das `Widening`\- oder das `Narrowing`\-Schlüsselwort aus der `Operator`\-Anweisung. Sie müssen eins von beiden angeben.  
  
## Siehe auch  
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)