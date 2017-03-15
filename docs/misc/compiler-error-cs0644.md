---
title: "Compilerfehler CS0644 | Microsoft Docs"
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
  - "CS0644"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0644"
ms.assetid: 835f3ee2-f897-4ba2-ad13-af629a9ab7fe
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0644
Die "Klasse1"\-Klasse kann nicht von der speziellen "Klasse2"\-Klasse abgeleitet werden.  
  
 Klassen können nicht explizit von den folgenden Basisklassen erben:  
  
-   **System.Enum**  
  
-   **System.ValueType**  
  
-   **System.Delegate**  
  
-   **System.Array**  
  
 Diese Klassen werden vom Compiler als implizite Basisklassen verwendet. Beispielsweise ist **System.ValueType** die implizite Basisklasse von Strukturen.  
  
 Im folgenden Beispiel wird CS0644 generiert:  
  
```  
// CS0644.cs class MyClass : System.ValueType   // CS0644 { }  
```