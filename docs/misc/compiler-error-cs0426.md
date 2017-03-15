---
title: "Compilerfehler CS0426 | Microsoft Docs"
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
  - "CS0426"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0426"
ms.assetid: 62df0deb-3624-436e-9691-ebe3ee1fc31f
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0426
Der Typname 'Bezeichner' ist im Typ 'Typ' nicht vorhanden.  
  
 Dieser Fehler tritt auf, wenn Sie auf einen Typ verweisen, der in einem anderen Typ geschachtelt ist, aber ein derartig geschachtelter Typ nicht vorhanden ist. Dies kann vorkommen, wenn Sie den Namen des geschachtelten Typs falsch eingegeben haben. Überprüfen Sie die Schreibweise der verwendeten Namen, und überprüfen Sie, ob der einschließende Typ über den erwarteten Member verfügt.  
  
 Im folgenden Beispiel wird CS0426 generiert, da die Klasse C nicht über den geschachtelten Typ A verfügt:  
  
```  
// CS0426.cs class C { // No nested types are declared. } class D { public static void Main() { C c = new C(); // Attempt to reference a nested type A: C.A a; // CS0426 because no such type C.A } }  
```  
  
## Siehe auch  
 [Klassen und Strukturen](/dotnet/csharp/programming-guide/classes-and-structs/index)