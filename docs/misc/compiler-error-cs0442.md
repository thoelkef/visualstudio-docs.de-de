---
title: "Compilerfehler CS0442 | Microsoft Docs"
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
  - "CS0442"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0442"
ms.assetid: a411660d-0db6-4b63-b19e-f4538fc201e5
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0442
„Property“: Abstrakte Eigenschaften können keine private\-Accessoren haben.  
  
 Dieser Fehler tritt auf, wenn Sie den Zugriffsmodifizierer „private“ verwenden, um einen abstrakten Accessor zu ändern. Zum Beheben dieses Fehlers verwenden Sie einen anderen Zugriffsmodifizierer, oder verwenden Sie eine nicht abstrakte Eigenschaft.  
  
## Beispiel  
 Im folgenden Beispiel wird CS0442 generiert:  
  
```  
// CS0442.cs public abstract class MyClass { public abstract int AbstractProperty { get; private set;   // CS0442 // Try this instead: // set; } }  
```