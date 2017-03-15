---
title: "Compilerfehler CS0154 | Microsoft Docs"
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
  - "CS0154"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0154"
ms.assetid: 815150da-09b4-4593-825f-1dd435c92da8
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0154
Die Eigenschaft oder der Indexer "Eigenschaft" kann in diesem Kontext nicht verwendet werden, weil der Get\-Accessor fehlt.  
  
 Der Versuch, eine [Eigenschaft](/dotnet/csharp/programming-guide/classes-and-structs/using-properties) zu verwenden, ist fehlgeschlagen, da in der Eigenschaft keine Get\-Accessormethode definiert wurde. Weitere Informationen finden Sie unter [Felder](/dotnet/csharp/programming-guide/classes-and-structs/fields).  
  
## Beispiel  
 Im folgenden Beispiel wird CS0154 generiert:  
  
```  
// CS0154.cs public class MyClass2 { public int i { set { } // uncomment the get method to resolve this error /* get { return 0; } */ } } public class MyClass { public static void Main() { MyClass2 myClass2 = new MyClass2(); int j = myClass2.i;   // CS0154, no get method } }  
```