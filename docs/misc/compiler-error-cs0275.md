---
title: "Compilerfehler CS0275 | Microsoft Docs"
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
  - "CS0275"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0275"
ms.assetid: 4d59f11c-b0ea-4c91-b2cb-cbe3be9a9ba2
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0275
„accessor“: Zugriffsmodifizierer können nicht für Accessoren in einer Schnittstelle verwendet werden.  
  
 Dieser Fehler tritt auf, wenn Sie einen Zugriffsmodifizierer für einen Accessor einer Eigenschaft oder eines Indexers in einer Schnittstelle verwenden. Zum Beheben dieses Fehlers entfernen Sie den Zugriffsmodifizierer.  
  
## Beispiel  
 Im folgenden Beispiel wird der Fehler CS0275 generiert:  
  
```  
// CS0275.cs public interface MyInterface { int Property { get; internal set;   // CS0275 } }  
```