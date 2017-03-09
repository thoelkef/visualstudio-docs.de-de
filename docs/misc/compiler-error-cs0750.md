---
title: "Compilerfehler CS0750 | Microsoft Docs"
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
  - "CS0750"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0750"
ms.assetid: 84fb6841-7f47-405a-ae05-95567692f73d
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0750
Eine partielle Methode darf keine Zugriffsmodifizierer oder die Modifizierer "virtual", "abstract", "override", "new", "sealed" oder "extern" enthalten.  
  
 Aufgrund ihres besonderen Verhaltens unterliegen partielle Methoden Beschränkungen hinsichtlich der Modifizierer, die sie akzeptieren können .  
  
### So beheben Sie diesen Fehler  
  
1.  Entfernen Sie den unzulässigen Modifizierer aus der Methodendeklaration.  
  
## Beispiel  
 Im folgenden Beispiel wird der Fehler CS0750 generiert:  
  
```  
// cs0750.cs using System; public class Base { protected virtual void PartG() { } protected void PartH() { } protected virtual void PartI() { } } public partial class C:Base { // All these partial method declarations // will generate CS0750. public partial void PartA(); private partial void PartB(); protected partial void PartC(); internal partial void PartD(); virtual partial void PartE(); abstract partial void PartF(); override partial void PartG(); new partial void PartH(); sealed override partial void PartI(); extern partial void PartJ(); public static int Main() { return 1; } }  
```  
  
## Siehe auch  
 [Partielle Klassen und Methoden](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)