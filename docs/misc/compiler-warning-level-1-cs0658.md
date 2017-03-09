---
title: "Compilerwarnung (Stufe 1) CS0658 | Microsoft Docs"
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
  - "CS0658"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0658"
ms.assetid: 0309074c-741a-492c-9370-73b4bbfd3c1a
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 1) CS0658
"Attributmodifizierer" ist kein bekannter Attributpfad. Alle Attribute in diesem Block werden ignoriert.  
  
 Es wurde ein ungültiger Attributmodifizierer angegeben. Weitere Informationen finden Sie unter [Attributziele](http://msdn.microsoft.com/de-de/59a261f0-1cfb-4aa5-b610-6b735389882c).  
  
 Im folgenden Beispiel wird CS0658 generiert:  
  
```  
// CS0658.cs using System; public class TestAttribute : Attribute{} [badAttributeLocation: Test]   // CS0658, badAttributeLocation is invalid class ClassTest { public static void Main() { } }  
```