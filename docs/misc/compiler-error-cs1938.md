---
title: "Compilerfehler CS1938 | Microsoft Docs"
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
  - "CS1938"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1938"
ms.assetid: fc8de996-f7a1-46e8-b07b-aea520b391b9
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1938
Der Name 'Name' auf der rechten Seite von „Equals“ liegt nicht im Bereich. Erwägen Sie den Austausch der Ausdrücke auf beiden Seiten von „Equals“.  
  
 Das `equals`\-Schlüsselwort ist ein spezieller Operator, der in einer `join`\-Klausel verwendet wird, um die Gleichheit zwischen zwei Ausdrücken zu ermitteln. Die Bereichsvariable für die linke Quellsequenz liegt auf der linken Seite von „equals“ im Bereich, und die Bereichsvariable für die rechte Quelle liegt nur auf der linken Seite von „equals“ im Bereich. Sie können dies überprüfen, indem Sie im folgenden Codebeispiel mit IntelliSense experimentieren.  
  
### So beheben Sie diesen Fehler  
  
1.  Tauschen Sie die Position der beiden Bereichsvariablen, wie in der kommentierten Zeile im folgenden Beispiel veranschaulicht:  
  
## Beispiel  
 Durch den folgenden Code wird der Fehler CS1938 ausgelöst:  
  
```  
// cs1938.cs using System.Linq; class Test { static void Main() { int[] sourceA = { 1, 2, 3, 4, 5 }; int[] sourceB = { 3, 4, 5, 6, 7 }; var query = from a in sourceA join b in sourceB on b equals a // CS1938 // Try the following line instead. // join b in sourceB on a equals b select new { a, b }; } }  
```  
  
## Siehe auch  
 [join\-Klausel](/dotnet/csharp/language-reference/keywords/join-clause)