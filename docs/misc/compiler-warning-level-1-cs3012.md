---
title: "Compilerwarnung (Stufe 1) CS3012 | Microsoft Docs"
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
  - "CS3012"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3012"
ms.assetid: 1f7555b4-61e4-4821-85c9-586301df4c5c
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 1) CS3012
Das CLSCompliant\-Attribut kann nicht für ein Modul angegeben werden, das sich vom CLSCompliant\-Attribut der Assembly unterscheidet.  
  
 Damit ein Modul mithilfe von `[module:System.CLCSompliant(true)]` CLS\-kompatibel \(Common Language Specification\) sein kann, muss es mit der Compileroption [\/target:module](../Topic/-target:module%20\(C%23%20Compiler%20Options\).md) erstellt werden. Weitere Informationen zur CLS finden Sie unter [Sprachenunabhängigkeit und sprachunabhängige Komponenten](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md).  
  
## Beispiel  
 Im folgenden Beispiel wird CS3012 generiert, wenn ohne `/target:module` erstellt wird:  
  
```  
// CS3012.cs // compile with: /W:1 [module:System.CLSCompliant(true)]   // CS3012 public class C { public static void Main() { } }  
```