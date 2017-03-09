---
title: "Compilerwarnung (Stufe 1) CS3005 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS3005"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3005"
ms.assetid: 64b687e3-2dbd-45dd-b6da-81f77eb7d6bd
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 1) CS3005
Der Bezeichner "Bezeichner", der sich nur hinsichtlich der Groß\- und Kleinschreibung unterscheidet, ist nicht CLS\-kompatibel.  
  
 Ein [public](/dotnet/csharp/language-reference/keywords/public)\-, [protected](/dotnet/csharp/language-reference/keywords/protected)\- oder `protected` `internal`\-Bezeichner, der sich nur in der Groß\-\/Kleinschreibung eines oder mehrerer Buchstaben von einem anderen `public`\-, `protected`\- oder `protected` `internal`\-Bezeichner unterscheidet, ist nicht mit der Common Language Specification \(CLS\) kompatibel. Weitere Informationen zur CLS\-Kompatibilität finden Sie unter [Schreiben von CLS\-kompatiblem Code](http://msdn.microsoft.com/de-de/4c705105-69a2-4e5e-b24e-0633bc32c7f3) und [Sprachenunabhängigkeit und sprachunabhängige Komponenten](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md).  
  
## Beispiel  
 Im folgenden Beispiel wird CS3003 generiert:  
  
```  
// CS3005.cs using System; [assembly:CLSCompliant(true)] public class a { public static int a1 = 0; public static int A1 = 1;   // CS3005 public static void Main() { Console.WriteLine(a1); Console.WriteLine(A1); } }  
```