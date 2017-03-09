---
title: "Compilerwarnung (Stufe 1) CS3002 | Microsoft Docs"
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
  - "CS3002"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3002"
ms.assetid: 34f19735-76d2-4d78-bd52-45989a86fca4
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 1) CS3002
Der Rückgabetyp von "Methode" ist nicht CLS\-kompatibel.  
  
 [Öffentliche](/dotnet/csharp/language-reference/keywords/public), [geschützte](/dotnet/csharp/language-reference/keywords/protected) oder `protected` `internal`\-Methoden müssen einen Wert zurückgeben, dessen Typ mit der Common Language Specification \(CLS\) kompatibel ist. Weitere Informationen zur CLS\-Kompatibilität finden Sie unter [Schreiben von CLS\-kompatiblem Code](http://msdn.microsoft.com/de-de/4c705105-69a2-4e5e-b24e-0633bc32c7f3) und [Sprachenunabhängigkeit und sprachunabhängige Komponenten](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md).  
  
## Beispiel  
 Im folgenden Beispiel wird CS3002 generiert:  
  
```  
// CS3002.cs [assembly:System.CLSCompliant(true)] public class a { public ushort bad()   // CS3002, public method { ushort a; a = ushort.MaxValue; return a; } private ushort OK()   // OK, private method { ushort a; a = ushort.MaxValue; return a; } public static void Main() { } }  
```