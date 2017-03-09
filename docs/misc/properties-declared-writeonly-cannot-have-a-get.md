---
title: "Eigenschaften, die als &#39;WriteOnly&#39; deklariert ist, d&#252;rfen kein &#39;Get&#39; aufweisen. | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30023"
  - "vbc30023"
helpviewer_keywords: 
  - "BC30023"
ms.assetid: ac290f7d-cbc3-4979-a5d9-1ae1bb26e79d
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Eigenschaften, die als &#39;WriteOnly&#39; deklariert ist, d&#252;rfen kein &#39;Get&#39; aufweisen.
Die `Get`\-Prozedur liest den Wert einer Eigenschaft.`WriteOnly`\-Eigenschaften können nicht gelesen werden.  
  
 **Fehler\-ID:** BC30023  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie das Schlüsselwort "`WriteOnly`" aus der `Property`\-Anweisung, oder entfernen Sie die `Get`\-Prozedur aus dem Eigenschaftentext.  
  
## Siehe auch  
 [Property Statement](/dotnet/visual-basic/language-reference/statements/property-statement)   
 [Get Statement](/dotnet/visual-basic/language-reference/statements/get-statement)   
 [WriteOnly](/dotnet/visual-basic/language-reference/modifiers/writeonly)