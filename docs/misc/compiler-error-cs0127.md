---
title: "Compilerfehler CS0127 | Microsoft Docs"
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
  - "CS0127"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0127"
ms.assetid: b20333bf-badf-4f96-a3ee-bd35f4f7e807
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0127
Da 'Funktion' 'void' zurückgibt, darf auf ein Rückgabeschlüsselwort kein Objektausdruck folgen.  
  
 Eine Methode mit dem Rückgabetyp [void](/dotnet/csharp/language-reference/keywords/void) kann keinen Wert zurückgeben. Weitere Informationen finden Sie unter [Methoden](/dotnet/csharp/programming-guide/classes-and-structs/methods).  
  
 Im folgenden Beispiel wird CS0127 generiert:  
  
```  
// CS0127.cs namespace MyNamespace { public class MyClass { public int hiddenMember2 { get { return 0; } set   // CS0127, set has an implicit void return type { return 0;   // remove return statement to resolve this CS0127 } } public static void Main() { } } }  
```