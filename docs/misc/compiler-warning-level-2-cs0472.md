---
title: "Compilerwarnung (Stufe 2) CS0472 | Microsoft Docs"
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
  - "cs0472"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0472"
ms.assetid: dc80e0a3-dbd3-4a81-b8bb-a59b510cd3e1
caps.latest.revision: 4
caps.handback.revision: 4
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 2) CS0472
Das Ergebnis des Ausdrucks ist immer 'wert1', da ein Wert vom Typ 'wert2' nie gleich 'null' oder vom Typ 'wert3' sein kann  
  
 Der Compiler sollte eine Warnung ausgeben, wenn ein Operator mit einem Konstanten null\-Wert verwendet wird.  
  
## Beispiel  
 Im folgenden Beispiel wird CS0472 generiert:  
  
```  
public class Test { public static int Main() { int i = 5; int counter = 0; // Comparison: if (i == null)  // CS0472 // To resolve, use a valid value for i. counter++; return counter; } }  
```