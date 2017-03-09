---
title: "Compilerfehler CS1954 | Microsoft Docs"
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
  - "CS1954"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1954"
ms.assetid: bdec399e-c43d-46d3-a01b-ef3572786fe5
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1954
Die beste überladene Methodenübereinstimmung 'Methode' für das Auflistungsinitialisiererelement kann nicht verwendet werden. Add\-Methoden des Auflistungsinitialisierers dürfen über keine ref\- oder out\-Parameter verfügen.  
  
 Damit eine Auflistungsklasse mit einem Auflistungsinitialisierer initialisiert wird, muss die Klasse über eine `public` `Add`\-Methode verfügen, die keinen `ref`\- oder `out`\-Parameter darstellt.  
  
### So beheben Sie diesen Fehler  
  
-   Wenn Sie den Quellcode der Auflistungsklasse ändern können, stellen Sie eine `Add`\-Methode bereit, die keine `ref`\- oder `out`\-Parameter übernimmt.  
  
-   Wenn Sie die Auflistungsklasse ändern können, initialisieren Sie sie mit den von ihr bereitgestellten Konstruktoren. Sie können dafür keinen Auflistungsinitialisierer verwenden.  
  
## Beispiel  
 Im folgenden Beispiel wird Fehler CS1954 generiert, da die einzig verfügbare Überladung der `Add`\-Liste in `MyList` über einen `ref`\-Parameter verfügt.  
  
```  
// cs1954.cs using System.Collections.Generic; class MyList<T> : IEnumerable<T> { List<T> _list; public void Add(ref T item) { _list.Add(item); } public System.Collections.Generic.IEnumerator<T> GetEnumerator() { int index = 0; T current = _list[index]; while (current != null) { yield return _list[index++]; } } System.Collections.IEnumerator System.Collections.IEnumerable.GetEnumerator() { return GetEnumerator(); } } public class MyClass { public string tree { get; set; } } class Program { static void Main(string[] args) { MyList<MyClass> myList = new MyList<MyClass> { new MyClass { tree = "maple" } }; // CS1954 } }  
  
```  
  
## Siehe auch  
 [Objekt\- und Auflistungsinitialisierer](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers)