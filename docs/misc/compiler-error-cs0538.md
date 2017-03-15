---
title: "Compilerfehler CS0538 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0538"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0538"
ms.assetid: 46ac205e-16b0-4637-bd0f-9a755ac19f18
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0538
"Name" in der expliziten Schnittstellendeklaration ist keine Schnittstelle.  
  
 Es wurde versucht, explizit eine [Schnittstelle](/dotnet/csharp/language-reference/keywords/interface) zu deklarieren, die nicht angegeben ist.  
  
 Im folgenden Beispiel wird CS0538 generiert:  
  
```  
// CS0538.cs interface MyIFace { void F(); } public class MyClass { public void G() { } } class C: MyIFace { void MyIFace.F() { } void MyClass.G()   // CS0538, MyClass not an interface { } }  
```