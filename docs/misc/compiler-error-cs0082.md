---
title: "Compilerfehler CS0082 | Microsoft Docs"
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
  - "CS0082"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0082"
ms.assetid: 7612976f-de2c-4f6b-87c9-43175821650c
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0082
Der Typ "Typ" reserviert bereits einen Member namens "Name" mit den gleichen Parametertypen.  
  
 Eigenschaften zum Zeitpunkt der Kompilierung werden in Methoden mit `get_` und\/oder `set_` vor dem Bezeichner übersetzt. Wenn Sie eine eigene Methode definieren, die mit dem Methodennamen in Konflikt steht, wird ein Fehler generiert.  
  
## Beispiel  
 Im folgenden Beispiel wird der Fehler CS0082 generiert:  
  
```  
//cs0082.cs class MyClass { //property public int MyProp { get //CS0082 { return 1; } } //conflicting Get public int get_MyProp() { return 2; } public static int Main() { return 1; } }  
```  
  
## Siehe auch  
 [Eigenschaften](/dotnet/csharp/programming-guide/classes-and-structs/properties)