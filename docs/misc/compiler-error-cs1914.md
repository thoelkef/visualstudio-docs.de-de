---
title: "Compilerfehler CS1914 | Microsoft Docs"
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
  - "CS1914"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1914"
ms.assetid: e61361b6-4660-41fd-a574-cc48e1b3873c
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1914
Das statische Feld 'Name' kann nicht in einem Objektinitialisierer zugewiesen werden.  
  
 Objektinitialisierer initialisieren definitionsgemäß Objekte oder Instanzen von Klassen. Sie können nicht zum Initialisieren eines `static`\-Felds eines Typs verwendet werden. Unabhängig davon, wie viele Instanzen einer Klasse erstellt werden, gibt es nur eine Kopie eines `static`\-Felds.  
  
### So beheben Sie diesen Fehler  
  
1.  Ändern Sie das Feld in ein Instanzenfeld des entsprechenden Typs, oder entfernen Sie den Versuch, es über den Objektinitialisierer zu initialisieren.  
  
## Beispiel  
 Der folgende Code generiert CS1914, da der Initialisierer versucht, das `TestClass.Number`\-Feld zu initialisieren, das `static` ist:  
  
```  
// cs1914.cs using System.Linq; public class TestClass { public string Message { get; set; } public static int Number { get; set; } } class Test { static void Main() { TestClass b = new TestClass() { Message = "Hello", Number = "555-1212" }; // CS1914 } }  
```