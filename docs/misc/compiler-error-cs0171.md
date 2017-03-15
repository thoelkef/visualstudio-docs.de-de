---
title: "Compilerfehler CS0171 | Microsoft Docs"
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
  - "CS0171"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0171"
ms.assetid: 8c1d76c9-1048-4579-9031-23e3566e6288
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0171
Das dahinter liegende Feld für die automatisch implementierte Eigenschaft "Name" muss vollständig zugewiesen werden, bevor die Steuerung wieder an den Aufrufer übergeben wird. Sie könnten den Standardkonstruktor u. U. aus einem Konstruktorinitialisierer aufrufen.  
  
 Ein Konstruktor in einer [Struktur](/dotnet/csharp/language-reference/keywords/struct) muss alle Felder in der Struktur initialisieren. Weitere Informationen finden Sie unter [Konstruktoren](/dotnet/csharp/programming-guide/classes-and-structs/constructors).  
  
 Im folgenden Beispiel wird CS0171 generiert:  
  
```  
// CS0171.cs struct MyStruct { MyStruct(int initField)   // CS0171 { // i = initField;      // uncomment this line to resolve this error } public int i; } class MyClass { public static void Main() { MyStruct aStruct = new MyStruct(); } }  
```