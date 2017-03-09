---
title: "Compilerfehler CS1688 | Microsoft Docs"
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
  - "CS1688"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1688"
ms.assetid: e15672a1-2570-4e65-99fc-7acc190ae643
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1688
Ein anonymer Methodenblock ohne Parameterliste kann nicht in den Delegattyp 'delegat' konvertiert werden, da er mindestens einen out\-Parameter aufweist.  
  
 Der Compiler lässt in den meisten Fällen das Auslassen von Parametern in anonymen Methodenblöcken zu. Dieser Fehler tritt auf, wenn der anonyme Methodenblock keine Parameterliste enthält, der Delegat aber einen `out`\-Parameter aufweist. Der Compiler lässt diese Situation nicht zu, da er die Anwesenheit des `out`\-Parameters ignorieren müsste, was vermutlich nicht das richtige Verhalten darstellt.  
  
## Beispiel  
 Der folgende Code generiert den Fehler CS1688.  
  
```  
// CS1688.cs using System; delegate void OutParam(out int i); class ErrorCS1676 { static void Main() { OutParam o; o = delegate  // CS1688 // Try this instead: // o = delegate(out int i) { Console.WriteLine(""); }; } }  
```