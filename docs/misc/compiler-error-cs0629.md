---
title: "Compilerfehler CS0629 | Microsoft Docs"
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
  - "CS0629"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0629"
ms.assetid: 20f22ef0-3c6f-4108-ab09-3f0752375a10
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0629
Der bedingte Member 'member' kann den Schnittstellenmember 'Basisklassenmember' im Typ 'Typname' nicht implementieren.  
  
 Das Attribut [Conditional](http://msdn.microsoft.com/de-de/e1c4913b-74d0-421a-8a6d-c14b3f0e68fb) kann nicht für die Implementierung einer Schnittstelle verwendet werden.  
  
 Im folgenden Beispiel wird CS0629 generiert:  
  
```  
// CS0629.cs interface MyInterface { void MyMethod(); } public class MyClass : MyInterface { [System.Diagnostics.Conditional("debug")] public void MyMethod()    // CS0629, remove the Conditional attribute { } public static void Main() { } }  
```