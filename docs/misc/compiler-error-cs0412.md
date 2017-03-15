---
title: "Compilerfehler CS0412 | Microsoft Docs"
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
  - "CS0412"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0412"
ms.assetid: eeb2afbc-9416-4bcf-b116-d6adc5cfd4ca
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0412
'Generisch': Ein Parameter oder eine lokale Variable kann nicht den gleichen Namen aufweisen wie der Typparameter einer Methode.  
  
 Es besteht ein Namenskonflikt zwischen dem Typparameter einer generischen Methode und einer lokalen Variablen in der Methode oder einem der Parameter der Methode. Benennen Sie alle in Konflikt stehenden Parameter oder lokalen Variablen um, um diesen Fehler zu vermeiden.  
  
## Beispiel  
 Im folgenden Beispiel wird CS0412 generiert:  
  
```  
// CS0412.cs using System; class C { // Parameter name is the same as method type parameter name public void G<T>(int T)  // CS0412 { } public void F<T>() { // Method local variable name is the same as method type // parameter name double T = 0.0;  // CS0412 Console.WriteLine(T); } public static void Main() { } }  
```