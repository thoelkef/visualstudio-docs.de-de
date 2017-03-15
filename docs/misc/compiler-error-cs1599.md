---
title: "Compilerfehler CS1599 | Microsoft Docs"
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
  - "CS1599"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1599"
ms.assetid: 4cdb282d-0f5d-459b-afc1-8980fbb22067
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1599
Die Methode oder der Delegat kann nicht den Typ „type“ zurückgeben.  
  
 Einige Typen in der .NET Framework\-Klassenbibliothek, z. B. <xref:System.TypedReference>, <xref:System.RuntimeArgumentHandle> und <xref:System.ArgIterator> können nicht als Rückgabetypen verwendet werden, weil mit ihnen potenziell unsichere Operationen ausgeführt werden können.  
  
 Im folgenden Beispiel wird CS1599 generiert.  
  
```  
// CS1599.cs using System; class MyClass { public static void Main() { } public TypedReference Test1()   // CS1599 { return null; } public ArgIterator Test2()   // CS1599 { return null; } }  
```