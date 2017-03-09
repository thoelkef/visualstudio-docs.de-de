---
title: "Compilerfehler CS0713 | Microsoft Docs"
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
  - "CS0713"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0713"
ms.assetid: 27a46765-d982-43ba-909f-9278e26b80d2
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0713
Die statische Klasse 'statischer Typ' kann nicht vom Typ 'Typ' abgeleitet werden. Statische Klassen müssen von 'Object' abgeleitet werden.  
  
 Wenn dies zulässig wäre, würde die statische Klasse Methoden und nicht statische Member von der Basisklasse erben, daher wäre sie nicht statisch. Daher ist dies nicht zulässig.  
  
 Im folgenden Beispiel wird CS0713 generiert:  
  
```  
// CS0713.cs public class Base { } public static class Derived : Base  // CS0713 { } public class CMain { public static void Main() { } }  
```