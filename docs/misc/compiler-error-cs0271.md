---
title: "Compilerfehler CS0271 | Microsoft Docs"
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
  - "CS0271"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0271"
ms.assetid: eadc9fb5-7770-4ec4-94f6-3c7cf37eec06
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0271
Die Eigenschaft oder der Indexer 'Eigenschaft\/Indexer' kann in diesem Kontext nicht verwendet werden, da der get\-Accessor nicht verfügbar ist.  
  
 Dieser Fehler tritt auf, wenn Sie versuchen, auf einen nicht verfügbaren `get`\-Accessor zuzugreifen. Um diesen Fehler zu beheben, erweitern Sie die Zugriffsmöglichkeit auf den Accessor, oder ändern Sie die Aufrufposition. Weitere Informationen finden Sie unter [Accessorzugriff](/dotnet/csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility) und [Eigenschaften](/dotnet/csharp/programming-guide/classes-and-structs/properties).  
  
 Im folgenden Beispiel wird der Fehler CS0271 generiert:  
  
```  
// CS0271.cs public class MyClass { public int Property { private get { return 0; } set { } } public int Property2 { get { return 0; } set { } } } public class Test { public static void Main(string[] args) { MyClass c = new MyClass(); int a = c.Property;   // CS0271 int b = c.Property2;   // OK } }  
```