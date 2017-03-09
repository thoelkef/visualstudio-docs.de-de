---
title: "Compilerfehler CS1722 | Microsoft Docs"
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
  - "CS1722"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1722"
ms.assetid: cf698a80-e4c9-46e2-96a0-8b8b5a08fc37
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1722
Die "Klasse"\-Basisklasse muss vor einer Schnittstelle aufgeführt werden.  
  
 Wenn Sie eine Klasse, von der geerbt werden soll, und die zu implementierenden Schnittstellen angeben, müssen Sie zuerst den Klassennamen angeben.  
  
## Beispiel  
 Im folgenden Beispiel wird CS1722 generiert:  
  
```  
// CS1722.cs // compile with: /target:library public class A {} interface I {} public class MyClass : I, A {}   // CS1722 public class MyClass2 : A, I {}   // OK  
```