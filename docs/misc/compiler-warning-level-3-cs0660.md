---
title: "Compilerwarnung (Stufe 3) CS0660 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0660"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0660"
ms.assetid: 2f77b45b-c5c6-46af-abe9-002e67887896
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 3) CS0660
'Klasse' definiert den Operator \=\= oder \!\=, aber überschreibt Object.Equals\(object o\) nicht.  
  
 Der Compiler hat den benutzerdefinierten Gleichheits\- oder Ungleichheitsoperator, aber keine Überschreibung für die **Equals**\-Funktion erkannt. Ein benutzerdefinierte Gleichheits\- oder Ungleichheitsoperator impliziert, dass Sie auch die **Equals**\-Funktion überschreiben möchten. Weitere Informationen finden Sie unter [NIB – Richtlinien zum Überschreiben von Equals\(\) und des \=\=\-Operators \(C\#\-Programmierhandbuch\)](http://msdn.microsoft.com/de-de/7e4c24c5-7693-4c45-88fb-ba5204fbcb20).  
  
 Im folgenden Beispiel wird CS0660 generiert:  
  
```  
// CS0660.cs // compile with: /W:3 /warnaserror class Test   // CS0660 { public static bool operator == (object o, Test t) { return true; } // uncomment the Equals function to resolve // public override bool Equals(object o) // { //    return true; // } public override int GetHashCode() { return 0; } public static void Main() { } }  
```