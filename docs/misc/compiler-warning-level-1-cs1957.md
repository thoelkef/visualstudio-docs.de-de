---
title: "Compilerwarnung (Stufe 1) CS1957 | Microsoft Docs"
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
  - "CS1957"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1957"
ms.assetid: a4823211-52ce-4ffa-b19b-ee874069409f
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 1) CS1957
Member „name“ setzt „method“ außer Kraft. Es gibt mehrere Kandidaten, die zur Laufzeit außer Kraft gesetzt werden können. Welche Methode aufgerufen wird, ist implementierungsabhängig festzulegen, .  
  
 Methodenparameter, die sich nur darin unterscheiden, ob sie `ref` oder `out` sind, können zur Laufzeit nicht unterschieden werden.  
  
### So vermeiden Sie diese Warnung  
  
1.  Geben Sie einer der Methoden einen anderen Namen oder eine andere Anzahl von Parametern.  
  
## Beispiel  
 Durch den folgenden Code wird der Fehler CS1957 ausgelöst:  
  
```  
// cs1957.cs class Base<T, S> { public virtual string Test(out T x) // CS1957 { x = default(T); return "Base.Test"; } public virtual void Test(ref S x) { } } class Derived : Base<int, int> { public override string Test(out int x) { x = 0; return "Derived.Test"; } static int Main() { int x; if (new Derived().Test(out x) == "Derived.Test") return 0; return 1; } }  
```