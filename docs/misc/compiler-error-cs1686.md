---
title: "Compilerfehler CS1686 | Microsoft Docs"
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
  - "CS1686"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1686"
ms.assetid: 46a9e82b-57f4-416d-8e49-242bfff5433a
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1686
Die Adressen von "Variable" \(lokal\) oder der entsprechenden Member können nicht übernommen und in einer anonymen Methode oder einem lambda\-Ausdruck verwendet werden.  
  
 Dieser Fehler wird generiert, wenn Sie eine Variable verwenden und versuchen, deren Adresse zu übernehmen und eine dieser Aktionen in einer anonymen Methode erfolgt.  
  
## Beispiel  
 Im folgenden Beispiel wird CS1686 generiert:  
  
```  
// CS1686.cs // compile with: /unsafe /target:library class MyClass { public unsafe delegate int * MyDelegate(); public unsafe int * Test() { int j = 0; MyDelegate d = delegate { return &j; };   // CS1686 return &j;   // OK } }  
```