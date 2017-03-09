---
title: "Compilerfehler CS1622 | Microsoft Docs"
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
  - "CS1622"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1622"
ms.assetid: 6b53a777-4cd8-423a-84ff-22ff588044d3
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1622
Von Iteratoren kann kein Wert zurückgegeben werden. Verwenden Sie die "yield return"\-Anweisung, um einen Wert zurückzugeben, oder die "yield break"\-Anweisung, um die Iteration zu beenden.  
  
 Ein Iterator ist eine spezielle Funktion, die einen Wert eher über eine yield\-Anweisung als über eine return\-Anweisung zurückgibt. Weitere Informationen finden Sie unter **Iteratoren**.  
  
 Im folgenden Beispiel wird CS1622 generiert:  
  
```  
// CS1622.cs // compile with: /target:library using System.Collections; class C : IEnumerable { public IEnumerator GetEnumerator() { return (IEnumerator) this;  // CS1622 yield return this;   // OK } }  
```