---
title: "Compilerfehler CS0668 | Microsoft Docs"
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
  - "CS0668"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0668"
ms.assetid: 7bdaa795-ce13-4284-b753-a617c1735cfa
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0668
Zwei Indexer haben unterschiedliche Namen. Das IndexerName\-Attribut muss für jeden Indexer in einem Typ mit dem gleichen Namen verwendet werden.  
  
 Die an das **IndexerName**\-Attribut übergebenen Werte müssen für alle Indexer in einem Typ identisch sein. Weitere Informationen zum **IndexerName**\-Attribut finden Sie unter [IndexerNameAttribute\-Klasse](frlrfSystemRuntimeCompilerServicesIndexerNameAttributeClassTopic).  
  
 Im folgenden Beispiel wird CS0668 generiert:  
  
```  
// CS0668.cs using System; using System.Runtime.CompilerServices; class IndexerClass { [IndexerName("IName1")] public int this [int index]   // indexer declaration { get { return index; } set { } } [IndexerName("IName2")] public int this [string s]    // CS0668, change IName2 to IName1 { get { return int.Parse(s); } set { } } void Main() { } }  
```