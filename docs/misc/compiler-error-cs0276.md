---
title: "Compilerfehler CS0276 | Microsoft Docs"
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
  - "CS0276"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0276"
ms.assetid: 0c49017f-c7a9-42a5-9d0a-6f1d82142bd7
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0276
"Eigenschaft\/Indexer": Zugriffsmodifizierer für Accessoren können nur verwendet werden, wenn die Eigenschaft oder der Indexer sowohl einen get\- als auch einen set\-Accessor hat.  
  
 Dieser Fehler tritt auf, wenn Sie eine Eigenschaft oder einen Indexer mit nur einem Accessor deklarieren und einen Zugriffsmodifizierer für den Accessor verwenden. Entfernen Sie den Zugriffsmodifizierer, oder fügen Sie einen weiteren Accessor hinzu, um diesen Fehler zu beheben.  
  
## Beispiel  
 Im folgenden Beispiel wird der Fehler CS0276 generiert:  
  
```  
// CS0276.cs public class MyClass { public int Property { protected set { }   // CS0276 } public int Property2 { internal get { }   // CS0276 } }  
```