---
title: "Compilerfehler CS0763 | Microsoft Docs"
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
  - "CS0763"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0763"
ms.assetid: 940870ba-1250-4365-acaa-7f968ee96c5b
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0763
Beide partiellen Methodendeklarationen müssen statisch sein, oder keine von beiden darf statisch sein.  
  
 Bei einer partiellen Methodendeklaration kann nicht ein Teil statisch und der andere Teil nicht statisch sein.  
  
### So beheben Sie diesen Fehler  
  
1.  Legen Sie beide Teile entweder als statisch oder als nicht statisch fest.  
  
## Beispiel  
 Mit dem folgenden Code wird CS0763 generiert:  
  
```  
// cs0763.cs using System; public partial class C { static partial void Part(); partial void Part() // CS0763 { } public static int Main() { return 1; } }  
```  
  
## Siehe auch  
 [Partielle Klassen und Methoden](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)   
 [Statische](/dotnet/csharp/language-reference/keywords/static)