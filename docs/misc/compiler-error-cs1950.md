---
title: "Compilerfehler CS1950 | Microsoft Docs"
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
  - "CS1950"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1950"
ms.assetid: e37fb5b1-09e0-47a6-9db5-a48f90ea7bbb
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1950
Die optimale überladene Add\-Methode 'Name' für den Auflistungsinitialisierer weist einige ungültige Argumente auf.  
  
 Zur Unterstützung von Auflistungsinitialisierern muss eine Klasse „IEnumerable“ implementieren und eine öffentliche `Add`\-Methode besitzen. Um den Typ mithilfe eines Auflistungsinitialisierers zu initialisieren, muss der Eingabeparameter der `Add`\-Methode mit dem Typ des Objekts kompatibel sein, das Sie hinzufügen möchten.  
  
### So beheben Sie diesen Fehler  
  
-   Verwenden Sie einen kompatiblen Typ im Auflistungsinitialisierer.  
  
-   Ändern Sie die Eingabeparameter und\/oder den Zugriff auf die `Add`\-Methode im Auflistungstyp.  
  
-   Fügen Sie eine neue `Add`\-Methode mit einem Eingabeparameter hinzu, der mit dem übereinstimmt, was Sie übergeben.  
  
-   Machen Sie Ihre Auflistungsklasse generisch, sodass sie eine `Add`\-Methode enthalten kann, die jeden von Ihnen übergebenen Typ akzeptiert.  
  
## Beispiel  
 Im folgenden Beispiel wird CS1950 generiert:  
  
```  
// cs1950.cs using System.Collections; class TestClass : CollectionBase { public void Add(int c) { } } class Test { static void Main() { TestClass t = new TestClass { "hi" }; // CS1950 } }  
```  
  
## Siehe auch  
 [Objekt\- und Auflistungsinitialisierer](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers)