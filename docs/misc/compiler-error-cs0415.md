---
title: "Compilerfehler CS0415 | Microsoft Docs"
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
  - "CS0415"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0415"
ms.assetid: 1ed45b02-4568-4af4-b2a6-c8b01230d19a
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0415
Das IndexerName\-Attribut ist nur für einen Indexer gültig, bei dem es sich nicht um eine explizite Schnittstellenmemberdeklaration handelt.  
  
 Dieser Fehler tritt auf, wenn Sie ein IndexerName\-Attribut für einen Indexer verwenden, der eine explizite Implementierung einer Schnittstelle darstellt. Dieser Fehler kann vermieden werden, indem der Schnittstellenname aus der Deklaration des Indexers entfernt wird, falls das möglich ist. Weitere Informationen finden Sie bei der [IndexerNameAttribute\-Klasse](frlrfSystemRuntimeCompilerServicesIndexerNameAttributeClassTopic).  
  
 Im folgenden Beispiel wird CS0415 generiert:  
  
```  
// CS0415.cs using System; using System.Runtime.CompilerServices; public interface IA { int this[int index] { get; set; } } public class A : IA { [IndexerName("Item")]  // CS0415 int IA.this[int index] // Try this line instead: // public int this[int index] { get { return 0; } set { } } static void Main() { } }  
```