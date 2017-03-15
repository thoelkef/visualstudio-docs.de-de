---
title: "Compilerfehler CS0831 | Microsoft Docs"
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
  - "CS0831"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0831"
ms.assetid: f626a77d-3844-4438-954b-b8201e72b1b5
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0831
Eine Ausdrucksbaumstruktur darf keinen Basiszugriff enthalten.  
  
 Basiszugriff bedeutet, dass ein Funktionsaufruf, bei dem es sich normalerweise um einen virtuellen Funktionsaufruf handeln würde, als nicht virtueller Funktionsaufruf für die Basisklassenmethode ausgeführt wird. Dies ist in der Ausdrucksbaumstruktur selbst nicht zulässig, aber Sie können eine Hilfsmethode in Ihrer Klasse aufrufen, die die Basisklassenmethode aufruft.  
  
### So beheben Sie diesen Fehler  
  
1.  Wenn Sie auf diese Weise auf eine Basisklassenmethode zugreifen müssen, erstellen Sie eine Hilfsmethode, die die Basisklasse aufruft und die Hilfsmethode über die Ausdrucksbaumstruktur aufrufen lässt. Dieses Verfahren wird im folgenden Code dargestellt.  
  
## Beispiel  
 Im folgenden Beispiel wird CS0831 generiert:  
  
```  
// cs0831.cs using System; using System.Linq; using System.Linq.Expressions; public class A { public virtual int BaseMethod() { return 1; } } public class C : A { public override int BaseMethod() { return 2; } public int Test(C c) { Expression<Func<int>> e = () => base.BaseMethod(); // CS0831 // Try the following line instead, // along with the BaseAccessHelper method. // Expression<Func<int>> e2 = () => BaseAccessHelper(); return 1; } // Uncomment to call from e2 expression above. // int BaseAccessHelper() // { //     return base.BaseMethod(); // } }   
```