---
title: "Compilerfehler CS0119 | Microsoft Docs"
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
  - "CS0119"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0119"
ms.assetid: 048924f1-378f-4021-bd20-299d3218f810
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0119
"Name\_Konstrukt1" ist "Konstrukt1" und im angegebenen Kontext nicht gültig.  
  
 Der Compiler hat ein unerwartetes Konstrukt festgestellt, wie z. B.:  
  
-   Ein Klassenkonstruktor ist kein gültiger Testausdruck in einer Bedingungsanweisung.  
  
-   Anstelle eines Instanznamens wurde ein Klassenname zum Verweisen auf ein Arrayelement verwendet.  
  
-   Ein Methodenbezeichner wird verwendet, als würde es sich um eine Struktur oder Klasse handeln.  
  
## Beispiel  
 Im folgenden Beispiel wird CS0119 generiert.  
  
```  
// CS0119.cs using System; public class MyClass { public static void Test() {} public static void Main() { Console.WriteLine(Test.x);   // CS0119 } }  
```