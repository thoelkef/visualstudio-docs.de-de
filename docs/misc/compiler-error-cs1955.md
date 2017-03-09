---
title: "Compilerfehler CS1955 | Microsoft Docs"
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
  - "CS1955"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1955"
ms.assetid: 38a8542d-da53-4739-b807-46c8c077363c
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1955
Der nicht aufrufbare Member "Name" kann nicht wie eine Methode verwendet werden.  
  
 Nur Methoden und Delegaten können aufgerufen werden. Dieser Fehler wird generiert, wenn Sie versuchen, leere Klammern zu verwenden, um etwas anderes als eine Methode oder einen Delegaten aufzurufen.  
  
### So beheben Sie diesen Fehler  
  
1.  Entfernen Sie die Klammern aus dem Ausdruck.  
  
## Beispiel  
 Durch den folgenden Code wird der Fehler CS1955 ausgelöst, weil der Code versucht, ein Feld und eine Eigenschaft mit dem Methodenaufrufoperator [\(\)](/dotnet/csharp/language-reference/operators/invocation-operator) aufzurufen. Felder oder Eigenschaften können nicht aufgerufen werden, aber Sie können mit dem Memberzugriffsoperator \( [.](/dotnet/csharp/language-reference/operators/member-access-operator) \) auf den zugehörigen gespeicherten Wert zugreifen.  
  
```  
// cs1955.cs class A { public int x = 0; public int X { get { return x; } set { x = value; } } } class Test { static int Main() { A a = new A(); a.x(); // CS1955 a.X(); // CS1955 // Try this line instead: // int num = a.x; } }  
```