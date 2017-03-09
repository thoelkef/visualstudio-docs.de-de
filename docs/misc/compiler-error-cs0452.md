---
title: "Compilerfehler CS0452 | Microsoft Docs"
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
  - "CS0452"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0452"
ms.assetid: 50a87734-fe07-4bce-891d-a76e131db6cc
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0452
Der Typ "Typname" muss ein Referenztyp sein, damit er als Parametername\-Parameter im generischen Typ oder in der generischen Methode "Bezeichner des generischen Elements" verwendet werden kann.  
  
 Dieser Fehler tritt auf, wenn Sie einen Werttyp, etwa `struct` oder `int`, als Parameter für einen generischen Typ oder eine generische Methode übergeben, der oder die eine Verweistypeinschränkung hat.  
  
## Beispiel  
 Im folgenden Code wird der Fehler CS0452 generiert.  
  
```  
// CS0452.cs using System; public class BaseClass<S> where S : class { } public class Derived1 : BaseClass<int> { } // CS0452 public class Derived2<S> : BaseClass<S> where S : struct { } // CS0452  
```  
  
## Siehe auch  
 [Einschränkungen für Typparameter](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters)