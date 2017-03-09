---
title: "Compilerfehler CS1013 | Microsoft Docs"
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
  - "CS1013"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1013"
ms.assetid: e5b1d24d-e558-4f7c-b2b1-3a644710005d
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1013
Ungültige Zahl  
  
 Der Compiler hat eine falsch formatierte Zahl erkannt. Weitere Informationen zu ganzzahligen Typen finden Sie unter [Tabelle ganzzahliger Typen](/dotnet/csharp/language-reference/keywords/integral-types-table).  
  
## Beispiel  
 Im folgenden Beispiel wird CS1013 generiert:  
  
```  
// CS1013.cs class Sample { static void Main() { int i = 0x;   // CS1013 } }  
```