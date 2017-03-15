---
title: "Compilerfehler CS0758 | Microsoft Docs"
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
  - "CS0758"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0758"
ms.assetid: 06ddd548-1311-40db-9078-8a18107b8346
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0758
Beide partiellen Methodendeklarationen müssen einen params\-Parameter verwenden, oder keine von beiden darf einen params\-Parameter verwenden.  
  
 Wenn in einem Teil einer partiellen Methode ein `params`\-Parameter angegeben ist, muss dieser Parameter auch im anderen Teil enthalten sein.  
  
### So beheben Sie diesen Fehler  
  
1.  Fügen Sie einem Teil der Methode den `params`\-Modifizierer hinzu, oder entfernen Sie in aus dem anderen Teil.  
  
## Beispiel  
 Durch den folgenden Code wird der Fehler CS0758 ausgelöst:  
  
```  
using System; public partial class C { partial void Part(int i, params char[] array); partial void Part(int i, char[] array) // CS0758 { } public static int Main() { return 1; } }  
```  
  
## Siehe auch  
 [Partielle Klassen und Methoden](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)   
 [params](/dotnet/csharp/language-reference/keywords/params)