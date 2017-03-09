---
title: "Compilerfehler CS1108 | Microsoft Docs"
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
  - "CS1108"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1108"
ms.assetid: 26e82d6a-6ebf-4beb-912e-1bcb86b668aa
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1108
Ein Parameter kann nicht alle angegebenen Modifizierer aufweisen. Für den Parameter wurden zu viele Modifizierer angegeben.  
  
 Bestimmte Kombinationen von Parametermodifizierern, z. B. `ref` und `out`, sind nicht zulässig, da sie für den Compiler sich gegenseitig ausschließende Bedeutungen haben.  
  
## Beispiel  
 Im folgenden Beispiel wird der Fehler CS1108 generiert:  
  
```  
// cs1108.cs // Compile with: /target:library public class Test { // Regular Instance Method. public void TestMethod(ref out int i) {} // CS1108 }  
```