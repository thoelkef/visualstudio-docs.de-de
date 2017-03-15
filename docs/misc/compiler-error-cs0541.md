---
title: "Compilerfehler CS0541 | Microsoft Docs"
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
  - "CS0541"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0541"
ms.assetid: ed812c07-24f7-43c6-9a44-553f27f6249d
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0541
'Deklaration': Eine explizite Schnittstellendeklaration kann nur in einer Klasse oder einer Struktur deklariert werden.  
  
 Eine explizite [Schnittstellendeklaration](/dotnet/csharp/language-reference/keywords/interface) wurde außerhalb einer [Klasse](/dotnet/csharp/language-reference/keywords/class) oder [Struktur](/dotnet/csharp/language-reference/keywords/struct) gefunden.  
  
 Im folgenden Beispiel wird CS0541 generiert:  
  
```  
// CS0541.cs namespace x { interface IFace { void F(); } interface IFace2 : IFace { void IFace.F();   // CS0541 } }  
```