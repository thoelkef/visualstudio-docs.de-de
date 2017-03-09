---
title: "Compilerwarnung (Stufe 1) CS3018 | Microsoft Docs"
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
  - "CS3018"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3018"
ms.assetid: 35d2f4bd-10c3-4e9f-8e02-389ab84db2cd
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 1) CS3018
"Typ" ist ein Member des nicht CLS\-kompatiblen Typs "Typ" und kann daher nicht als CLS\-kompatibel markiert werden  
  
 Diese Warnung wird ausgegeben, wenn eine geschachtelte Klasse mit dem auf `true` festgelegten CLSCompliant\-Attribut als Member einer Klasse deklariert wird, die mit dem CLSCompliant\-Attribut deklariert ist, das auf `false` festgelegt ist. Dies ist unzulässig, weil eine geschachtelte Klasse nicht CLS\-kompatibel sein kann, wenn diese ein Member einer äußeren Klasse ist, die nicht CLS\-kompatibel ist. Entfernen Sie das CLSCompliant\-Attribut aus der geschachtelten Klasse, oder legen Sie es von `true` auf `false` fest, um diese Warnmeldung zu vermeiden. Weitere Informationen zur CLS\-Kompatibilität finden Sie unter [Schreiben von CLS\-kompatiblem Code](http://msdn.microsoft.com/de-de/4c705105-69a2-4e5e-b24e-0633bc32c7f3) und [Sprachenunabhängigkeit und sprachunabhängige Komponenten](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md).  
  
## Beispiel  
 Im folgenden Beispiel wird CS3018 generiert.  
  
```  
// CS3018.cs // compile with: /target:library using System; [assembly: CLSCompliant(true)] [CLSCompliant(false)] public class Outer { [CLSCompliant(true)]   // CS3018 public class Nested {} // OK public class Nested2 {} [CLSCompliant(false)] public class Nested3 {} }  
```