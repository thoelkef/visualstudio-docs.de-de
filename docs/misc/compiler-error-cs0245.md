---
title: "Compilerfehler CS0245 | Microsoft Docs"
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
  - "CS0245"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0245"
ms.assetid: 3f2beb2f-a510-4568-9d11-bb1f65066acd
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0245
Destruktoren und object.Finalize können nicht direkt aufgerufen werden. Rufen Sie IDisposable.Dispose auf, sofern verfügbar.  
  
 Weitere Informationen finden Sie unter [Programmieren für die Garbage Collection](../Topic/Garbage%20Collection.md) und [Destruktoren](/dotnet/csharp/programming-guide/classes-and-structs/destructors).  
  
 Im folgenden Beispiel wird CS0245 generiert:  
  
```  
// CS0245.cs using System; using System.Collections; class MyClass // : IDisposable { /* public void Dispose() { // cleanup code goes here } */ void m() { this.Finalize();   // CS0245 // this.Dispose(); } public static void Main() { } }  
```