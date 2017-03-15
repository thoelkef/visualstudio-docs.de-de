---
title: "Compilerfehler CS0261 | Microsoft Docs"
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
  - "CS0261"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0261"
ms.assetid: c2af7b31-4a48-457a-8d9b-0956dd0d46f9
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0261
Partielle Deklarationen von 'Typ' müssen entweder nur Klassen, nur Strukturen oder nur Schnittstellen sein.  
  
 Dieser Fehler tritt auf, wenn ein partieller Typ an verschiedenen Stellen als anderer Typ eines Konstrukts deklariert ist. Weitere Informationen finden Sie unter [Partielle Klassen und Methoden](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods).  
  
 Im folgenden Beispiel wird CS0261 generiert:  
  
```  
// CS0261.cs partial class A  // CS0261 – A declared as a class here, but as a struct below { } partial struct A { }  
```