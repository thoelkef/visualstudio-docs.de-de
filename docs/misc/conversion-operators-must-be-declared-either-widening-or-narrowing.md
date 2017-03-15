---
title: "Konvertierungsoperatoren m&#252;ssen entweder als &#39;Widening&#39; oder als &#39;Narrowing&#39; deklariert werden. | Microsoft Docs"
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
  - "vbc33017"
  - "bc33017"
helpviewer_keywords: 
  - "BC33017"
ms.assetid: 5972d955-ce1d-4348-a021-167eecb3a507
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Konvertierungsoperatoren m&#252;ssen entweder als &#39;Widening&#39; oder als &#39;Narrowing&#39; deklariert werden.
Von einer [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)\-Anweisung wird weder [Widening](/dotnet/visual-basic/language-reference/modifiers/widening) noch [Narrowing](/dotnet/visual-basic/language-reference/modifiers/narrowing) angegeben.  
  
 Wenn Sie einen Konvertierungsoperator definieren, müssen Sie ihn entweder als `Widening` oder als `Narrowing` deklarieren. Diese Merkmale schließen sich gegenseitig aus, Sie können also nicht beide angeben.  
  
 **Fehler\-ID:** BC33017  
  
### So beheben Sie diesen Fehler  
  
-   Entscheiden Sie, ob der Konvertierungsoperator `Widening` oder `Narrowing` sein soll, und nehmen Sie das entsprechende Schlüsselwort in die `Operator`\-Anweisung auf. Sie müssen eins von beiden angeben.  
  
## Siehe auch  
 [Widening and Narrowing Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)   
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)