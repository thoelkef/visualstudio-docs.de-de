---
title: "Compilerfehler CS0743 | Microsoft Docs"
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
  - "CS0743"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0743"
ms.assetid: 0dc8040a-a12f-4da6-9ed0-c0284905ee83
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0743
Kontextbezogenes Schlüsselwort "on" erwartet.  
  
 Das Muster für eine `join`\-Klausel ist `join`...`in`...`on`...`equals`, wie im folgenden Beispiel gezeigt:  
  
```  
var query = from x in array1 join y in array2 on x equals y select x;  
```  
  
### So beheben Sie diesen Fehler  
  
1.  Fügen Sie der `join`\-Klausel das `on`Schlüsselwort hinzu.  
  
## Beispiel  
 Mit dem folgenden Code wird CS0743 generiert:  
  
```  
// cs0743.cs using System; using System.Linq; public class C { public static int Main() { int[] array1 = { 1, 2, 3 ,4, 5, 6,}; int[] array2 = { 5, 6, 7, 8, 9 }; var c = from x in array1 join y in array2 x equals y // CS0743 select x; return 1; } }  
```  
  
## Siehe auch  
 [LINQ\-Abfrageausdrücke](/dotnet/csharp/programming-guide/linq-query-expressions/index)   
 [join\-Klausel](/dotnet/csharp/language-reference/keywords/join-clause)