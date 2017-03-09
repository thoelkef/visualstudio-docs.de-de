---
title: "Compilerfehler CS0752 | Microsoft Docs"
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
  - "CS0752"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0752"
ms.assetid: f9a373d6-31ed-42db-8206-80cbe9b8c546
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0752
Eine partielle Methode darf keine out\-Parameter enthalten.  
  
 Eine partielle Methode darf keinen [out](/dotnet/csharp/language-reference/keywords/out)\-Parameter enthalten. Out\-Parameter sind nicht zulässig, da es beim Entfernen der partiellen Methode durch den Compiler keine Garantie gibt, dass der out\-Parameter jemals zugewiesen wird.  
  
### So beheben Sie diesen Fehler  
  
1.  Entfernen Sie den out\-Modifizierer aus dem Parameter, und verwenden Sie stattdessen der Rückgabewert der Methode. Andernfalls entfernen Sie den partiellen Modifizierer aus der Methodendeklaration.  
  
## Beispiel  
 Durch den folgenden Code wird der Fehler CS0752 ausgelöst:  
  
```  
// cs0752.cs public partial class C { partial void Part(out int num); // CS0752 // try the following line instead // partial void Part(int num); public static int Main() { return 1; } }  
```  
  
## Siehe auch  
 [Partielle Klassen und Methoden](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)