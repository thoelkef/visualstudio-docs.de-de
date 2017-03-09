---
title: "Compilerfehler CS0756 | Microsoft Docs"
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
  - "CS0756"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0756"
ms.assetid: 847b20b0-bbf0-43a2-8728-4b54cb3d9cd6
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0756
Eine partielle Methode darf nicht über mehrere definierende Deklarationen verfügen.  
  
 Die definierende Deklaration einer partiellen Methode ist der Teil, der die Signatur der Methode, aber nicht die Implementierung \(Methodenkörper\) angibt. Eine partielle Methode darf nur genau eine definierende Deklaration für jede eindeutige Signatur haben. Jede überladene Version einer partiellen Methode muss ihre eigene definierende Deklaration haben.  
  
### So beheben Sie diesen Fehler  
  
1.  Entfernen Sie für die partielle Methode alle definierenden Deklaration bis auf eine.  
  
## Beispiel  
  
```  
// cs0756.cs using System; public partial class C { partial void Part(); partial void Part(); // CS0756 public static int Main() { return 1; } }  
```  
  
## Siehe auch  
 [Partielle Klassen und Methoden](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)