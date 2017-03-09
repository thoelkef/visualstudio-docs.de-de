---
title: "Compilerfehler CS1615 | Microsoft Docs"
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
  - "CS1615"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1615"
ms.assetid: 518bb07f-0e3a-4761-9931-66845eb5df1a
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1615
Das Argument "Zahl" darf nicht mit dem 'Schlüsselwort'\-Schlüsselwort übergeben werden.  
  
 Eines der Schlüsselwörter `ref` oder **out** wurde verwendet, aber die Funktion hat keinen `ref`\- oder **out** \-Parameter für dieses Argument. Um diesen Fehler zu beheben, entfernen Sie das fehlerhafte Schlüsselwort, und verwenden Sie das entsprechende Schlüsselwort, das mit der Funktionsdeklaration übereinstimmt.  
  
 Im folgenden Beispiel wird CS1615 generiert:  
  
```  
// CS1615.cs class C { public void f(int i) {} public static void Main() { int i = 1; f(ref i);  // CS1615 } }  
```