---
title: "Compilerfehler CS1953 | Microsoft Docs"
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
  - "CS1953"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1953"
ms.assetid: b8af5eed-0f3b-4258-b4e2-f5d184288239
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1953
Das Lambda einer Ausdrucksbaumstruktur darf keine Methodengruppe enthalten.  
  
 Ein Methodenaufruf erfordert den `()`\-Operator. Der Methodenname ohne diesen Operator bezieht sich auf die Methodengruppe, die den Satz aller überladenen Methoden mit diesem Namen darstellt.  
  
### So beheben Sie diesen Fehler  
  
1.  Wenn Sie die Methode aufrufen möchten, fügen den `()`\-Operator hinzu.  
  
## Beispiel  
 Im folgenden Beispiel wird der Fehler CS1953 generiert:  
  
```  
// cs1953.cs using System; using System.Linq.Expressions; class CS1953 { public static void Main() { double num = 10; Expression<Func<bool>> testExpr = () => num.GetType is int; // CS1953 } }  
```