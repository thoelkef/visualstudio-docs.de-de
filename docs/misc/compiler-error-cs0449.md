---
title: "Compilerfehler CS0449 | Microsoft Docs"
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
  - "CS0449"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0449"
ms.assetid: 32c07a2c-4c48-4d07-b643-72422a6b9fac
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0449
Die class\- oder struct\-Einschränkung muss vor allen anderen Einschränkungen stehen.  
  
 Die Typparametereinschränkungen eines generischen Typs oder einer generischen Methode müssen in einer bestimmten Reihenfolge auftreten: zuerst `class` oder `struct` \(falls vorhanden\), dann beliebige Schnittstelleneinschränkungen und zuletzt beliebige Konstruktoreinschränkungen. Dieser Fehler wird dadurch verursacht, dass die `class`\- oder `struct`\-Einschränkung nicht an erster Stelle steht. Um diesen Fehler zu beheben, ändern Sie die Reihenfolge der Einschränkungsklauseln.  
  
## Beispiel  
 Im folgenden Beispiel wird CS0449 generiert.  
  
```  
// CS0449.cs // compile with: /target:library interface I {} public class C4 { public void F1<T>() where T : class, struct, I {}   // CS0449 public void F2<T>() where T : I, struct {}   // CS0449 public void F3<T>() where T : I, class {}   // CS0449 // OK public void F4<T>() where T : class {} public void F5<T>() where T : struct {} public void F6<T>() where T : I {} }  
```