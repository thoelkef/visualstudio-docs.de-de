---
title: "Compilerfehler CS0439 | Microsoft Docs"
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
  - "CS0430"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0439"
ms.assetid: 5cbac869-1b1b-45f9-98c8-38c17348035f
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0439
Eine externe Aliasdeklaration muss allen anderen im Namespace definierten Elementen vorangehen.  
  
 Dieser Fehler tritt auf, wenn eine `extern`\-Deklaration innerhalb des gleichen Namespaces nach anderen Einträgen auftritt, wie etwa einer `using`\-Deklaration. Die `extern`\-Deklarationen müssen allen anderen Namespaceelementen vorangehen.  
  
## Beispiel  
 Im folgenden Beispiel wird der Fehler CS0439 generiert:  
  
```  
// CS0439.cs using System; extern alias MyType;   // CS0439 // To resolve the error, make the extern alias the first line in the file. public class Test { public static void Main() { } }  
```