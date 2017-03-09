---
title: "Compilerfehler CS0177 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0177"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0177"
ms.assetid: 852a8c2a-2411-4800-af7c-4c572d9900d3
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0177
Der out\-Parameter "Parameter" muss eine Zuweisung erhalten, bevor die Steuerung die aktuelle Methode verlässt.  
  
 Einem Parameter, der mit dem [out](/dotnet/csharp/language-reference/keywords/out)\-Schlüsselwort gekennzeichnet ist, wurde im Methodenkörper kein Wert zugewiesen. Weitere Informationen finden Sie unter [Übergeben von Parametern](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters)  
  
 Im folgenden Beispiel wird CS0177 generiert:  
  
```  
// CS0177.cs public class MyClass { public static void Foo(out int i)   // CS0177 { // uncomment the following line to resolve this error //   i = 0; } public static void Main() { int x = -1; Foo(out x); } }  
```