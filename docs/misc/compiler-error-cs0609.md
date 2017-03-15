---
title: "Compilerfehler CS0609 | Microsoft Docs"
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
  - "CS0609"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0609"
ms.assetid: f3ff07a6-1190-4a1c-86a5-f607e1a32b78
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0609
Das IndexerName\-Attribut kann nicht für einen mit 'override' markierten Indexer festgelegt werden.  
  
 Das Name\-Attribut \(**IndexerNameAttribute**\) kann nicht auf eine indizierte Eigenschaft angewendet werden, die eine Überschreibung darstellt. Weitere Informationen finden Sie unter [Indexer](/dotnet/csharp/programming-guide/indexers/index).  
  
 Im folgenden Beispiel wird CS0609 generiert:  
  
```  
// CS0609.cs using System; using System.Runtime.CompilerServices; public class idx { public virtual int this[int iPropIndex] { get { return 0; } set { } } } public class MonthDays : idx { [IndexerName("MonthInfoIndexer")]   // CS0609, delete to resolve this CS0609 public override int this[int iPropIndex] { get { return 0; } set { } } } public class test { public static void Main( string[] args ) { } }  
```