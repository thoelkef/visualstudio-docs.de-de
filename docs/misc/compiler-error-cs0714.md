---
title: "Compilerfehler CS0714 | Microsoft Docs"
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
  - "CS0714"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0714"
ms.assetid: fbb5dc55-645c-4980-bf4b-3c2f84a3c6cd
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0714
'Statischer Typ': Statische Klassen können keine Schnittstellen implementieren.  
  
 Schnittstellen können nicht statische Methoden für Objekte definieren und daher nicht von statischen Klassen implementiert werden. Stellen Sie sicher, dass die Klasse nicht versucht, Schnittstellen zu implementieren, um diesen Fehler zu beheben.  
  
## Beispiel  
 Im folgenden Beispiel wird CS0714 generiert:  
  
```  
// CS0714.cs interface I { } public static class C : I  // CS0714 { public static void Main() { } }  
```