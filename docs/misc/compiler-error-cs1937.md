---
title: "Compilerfehler CS1937 | Microsoft Docs"
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
  - "CS1937"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1937"
ms.assetid: f13e8dc9-8c20-477e-8b74-7192848e08a2
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1937
Der Name 'Name' auf der linken Seite von 'Equals' liegt nicht im Bereich. Erwägen Sie den Austausch der Ausdrücke auf beiden Seiten von „Equals“.  
  
 Das `equals`\-Schlüsselwort ist ein spezieller Operator, der in einer `join`\-Klausel verwendet wird, um die Gleichheit zwischen zwei Ausdrücken zu ermitteln. Die Bereichsvariable für die linke Quellsequenz liegt auf der linken Seite von „Equals“ im Bereich, und die Bereichsvariable für die rechte Quelle liegt nur auf der linken Seite von „Equals“ im Bereich. Sie können dies überprüfen, indem Sie im folgenden Codebeispiel mit IntelliSense experimentieren.  
  
### So beheben Sie diesen Fehler  
  
1.  Tauschen Sie die Position der beiden Bereichsvariablen, wie in der kommentierten Zeile im folgenden Beispiel veranschaulicht:  
  
## Beispiel  
 Im folgenden Beispiel wird CS1937 generiert:  
  
```  
// cs1937.cs using System.Linq; class Test { static void Main() { int[] sourceA = { 1, 2, 3, 4, 5 }; int[] sourceB = { 3, 4, 5, 6, 7 }; var query = from a in sourceA join b in sourceB on b equals a // CS1937 // Try the following line instead. //join b in sourceB on a equals b select new { a, b }; } }  
```  
  
 Im Allgemeinen wird die linke Seite als „äußere“ Seite und die Rechte als „innere“ Seite bezeichnet.  
  
## Siehe auch  
 [join\-Klausel](/dotnet/csharp/language-reference/keywords/join-clause)