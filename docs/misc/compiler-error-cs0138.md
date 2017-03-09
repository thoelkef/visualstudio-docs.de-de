---
title: "Compilerfehler CS0138 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0138"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0138"
ms.assetid: 970545f8-5ee5-428e-921a-3aa29f68d16d
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0138
Eine using\-Namespacedirektive kann nur auf Namespaces angewendet werden. "Typ" ist ein Typ und kein Namespace.  
  
 Eine [using](/dotnet/csharp/language-reference/keywords/using)\-Direktive kann nur den Namen eines Namespaces als Parameter annehmen. Weitere Informationen finden Sie unter [Namespaces](/dotnet/csharp/programming-guide/namespaces/index).  
  
 Im folgenden Beispiel wird CS0138 generiert:  
  
```  
// CS0138.cs using System.Object;   // CS0138  
```