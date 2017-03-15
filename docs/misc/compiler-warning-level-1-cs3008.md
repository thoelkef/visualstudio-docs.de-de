---
title: "Compilerwarnung (Stufe 1) CS3008 | Microsoft Docs"
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
  - "CS3008"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3008"
ms.assetid: 593f6114-bc7b-4789-958f-97bbf99c1c9f
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 1) CS3008
Der Bezeichner 'identifier', der sich nur hinsichtlich der Groß\- und Kleinschreibung unterscheidet, ist nicht CLS\-kompatibel.  
  
 Ein [öffentlicher](/dotnet/csharp/language-reference/keywords/public), [geschützter](/dotnet/csharp/language-reference/keywords/protected) oder `protected` `internal` Bezeichner stört die Kompatibilität mit der Common Language Specification \(CLS\), wenn er mit einem Unterstrichzeichen \(\_\) beginnt. Weitere Informationen zur CLS\-Kompatibilität finden Sie unter [Erstellen von CLS\-kompatiblem Code](http://msdn.microsoft.com/de-de/4c705105-69a2-4e5e-b24e-0633bc32c7f3) und [Sprachenunabhängigkeit und sprachunabhängige Komponenten](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md).  
  
## Beispiel  
 Im folgenden Beispiel wird CS3008 generiert:  
  
```  
// CS3008.cs using System; [assembly:CLSCompliant(true)] public class a { public static int _a = 0;  // CS3008 // OK, private // private static int _a1 = 0; public static void Main() { } }  
```