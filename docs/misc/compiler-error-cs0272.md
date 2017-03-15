---
title: "Compilerfehler CS0272 | Microsoft Docs"
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
  - "CS0272"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0272"
ms.assetid: 16a9aab6-922a-45a3-a0ef-f32e99f3950f
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0272
Die Eigenschaft oder der Indexer "Eigenschaft\/Indexer" kann in diesem Kontext nicht verwendet werden, da der set\-Accessor nicht verfügbar ist.  
  
 Dieser Fehler tritt auf, wenn der Programmcode nicht in der Lage ist, auf den `set` zuzugreifen. Um diesen Fehler zu beheben, erweitern Sie die Zugriffsmöglichkeit auf den Accessor, oder ändern Sie die Aufrufposition. Weitere Informationen finden Sie unter [Einschränken des Accessorzugriffs](/dotnet/csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility).  
  
## Beispiel  
 Im folgenden Beispiel wird der Fehler CS0272 generiert:  
  
```  
// CS0272.cs public class MyClass { public int Property { get { return 0; } private set { } } } public class Test { static void Main() { MyClass c = new MyClass(); c.Property = 10;      // CS0272 // To resolve, remove the previous line // or use an appropriate modifier on the set accessor. } }  
```