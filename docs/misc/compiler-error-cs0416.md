---
title: "Compilerfehler CS0416 | Microsoft Docs"
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
  - "CS0416"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0416"
ms.assetid: 61bfe40d-5e87-47e5-933f-3491e28ace42
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0416
'Typparameter': Ein Attributargument kann keine Typparameter verwenden.  
  
 Ein Typparameter wurde als Attributargument verwendet. Dies ist nicht zulässig. Verwenden Sie einen nicht generischen Typ.  
  
 Im folgenden Beispiel wird CS0416 generiert:  
  
```  
// CS0416.cs public class MyAttribute : System.Attribute { public MyAttribute(System.Type t) { } } class G<T> { [MyAttribute(typeof(G<T>))]  // CS0416 public void F() { } }  
```