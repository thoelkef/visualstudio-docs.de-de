---
title: "Compilerfehler CS0835 | Microsoft Docs"
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
  - "CS0835"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0835"
ms.assetid: 593c26f6-6d82-49a6-8ace-4d29dd9f5fbe
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0835
Lambda kann nur dann in einen Ausdrucksbaum konvertiert werden, wenn das Typargument 'typ' ein Delegattyp ist.  
  
 Wenn ein Lambdaausdruck in einen Ausdrucksbaum konvertiert wird, muss der Ausdrucksbaum einen Delegattyp für sein Argument aufweisen. Darüber hinaus muss der Lambdaausdruck in den Delegattyp konvertierbar sein.  
  
### So beheben Sie diesen Fehler  
  
1.  Ändern Sie den Typparameter von `int` in einen Delegattyp, z. B. `Func<int,int>`.  
  
## Beispiel  
 Im folgenden Beispiel wird CS0835 generiert:  
  
```  
// cs0835.cs using System; using System.Linq; using System.Linq.Expressions; public class C { public static int Main() { Expression<int> e = x => x + 1; // CS0835 // Try the following line instead. // Expression<Func<int,int>> e2 = x => x + 1; return 1; } }  
```