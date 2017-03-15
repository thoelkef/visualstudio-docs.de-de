---
title: "Compilerfehler CS0460 | Microsoft Docs"
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
  - "CS0460"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0460"
ms.assetid: 98d39ded-d3f9-4520-b912-892e574c056b
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0460
Einschränkungen für Überschreibungs\- und explizite Schnittstellenimplementierungsmethoden werden von der Basismethode geerbt und können daher nicht direkt angegeben werden.  
  
 Wenn eine generische Methode, die Teil einer abgeleiteten Klasse ist, eine Methode in der Basisklasse überschreibt, können Sie keine Einschränkungen für die überschriebene Methode angeben. Die überschriebene Methode in der abgeleiteten Klasse erbt die Einschränkungen von der Methode in der Basisklasse.  
  
## Beispiel  
 Im folgenden Beispiel wird CS0460 generiert.  
  
```  
// CS0460.cs // compile with: /target:library class BaseClass { BaseClass() { } } interface I { void F1<T>() where T : BaseClass; void F2<T>() where T : struct; void F3<T>() where T : BaseClass; } class ExpImpl : I { void I.F1<T>() where T : BaseClass {}   // CS0460 void I.F2<T>() where T : class {}  // CS0460 }  
```