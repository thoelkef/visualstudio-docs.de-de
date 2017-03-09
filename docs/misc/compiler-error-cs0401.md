---
title: "Compilerfehler CS0401 | Microsoft Docs"
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
  - "CS0401"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0401"
ms.assetid: 94eac5a8-7344-44d2-9d0c-a9954993603d
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0401
Die new\(\)\-Einschränkung muss zuletzt angegeben werden.  
  
 Listen Sie bei der Verwendung mehrerer Einschränkungen alle anderen Einschränkungen vor der Einschränkung 'new\(\)' auf.  
  
## Beispiel  
 Im folgenden Beispiel wird CS0401 generiert:  
  
```  
// CS0401.cs // compile with: /target:library using System; class C<T> where T : new(), IDisposable {}  // CS0401 class D<T> where T : IDisposable { static void F<U>() where U : new(), IDisposable{}   // CS0401 }  
```