---
title: "Compilerfehler CS0037 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0037"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0037"
ms.assetid: 1d34a71e-10a0-4fa8-9b94-343e69428c61
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0037
NULL kann nicht in 'typ' konvertiert werden, da dieser Werttyp nicht auf NULL festgelegt werden kann.  
  
 Der Compiler kann einem Werttyp nicht NULL zuweisen; NULL kann nur [Verweistypen](/dotnet/csharp/language-reference/keywords/reference-types) oder Typen zugewiesen werden, die NULL\-Werte zulassen.[Struktur](/dotnet/csharp/language-reference/keywords/struct) ist ein Werttyp. Weitere Informationen finden Sie unter [Typen, die NULL\-Werte zulassen](/dotnet/csharp/programming-guide/nullable-types/index).  
  
 Im folgenden Beispiel wird CS0037 generiert:  
  
```  
// CS0037.cs public struct s { } class a { public static void Main() { int i = null;   // CS0037 s ss = null;    // CS0037 } }  
```