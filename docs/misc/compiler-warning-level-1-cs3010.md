---
title: "Compilerwarnung (Stufe 1) CS3010 | Microsoft Docs"
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
  - "CS3010"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3010"
ms.assetid: d57bd750-df15-4e6a-9579-66de8b276b7e
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 1) CS3010
„member“: CLS\-kompatible Schnittstellen dürfen nur CLS\-kompatible Member aufweisen.  
  
 In einer Assembly, die mit `[assembly:CLCSompliant(true)]` markiert ist, enthält eine Schnittstelle einen mit `[CLCSompliant(false)]` markierten Member. Entfernen Sie eines der CLS\-Kompatibilitätsattribute \(Common Language Specification\). Weitere Informationen zur CLS\-Kompatibilität finden Sie unter [\<PAVE OVER\> Schreiben von CLS\-kompatiblem Code](http://msdn.microsoft.com/de-de/4c705105-69a2-4e5e-b24e-0633bc32c7f3) und [Sprachenunabhängigkeit und sprachunabhängige Komponenten](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md).  
  
## Beispiel  
 Im folgenden Beispiel wird der Fehler CS3010 generiert:  
  
```  
// CS3010.cs using System; [assembly:CLSCompliant(true)] public interface I { [CLSCompliant(false)] int M();   // CS3010 } public class C : I { public int M() { return 1; } public static void Main() { } }  
```