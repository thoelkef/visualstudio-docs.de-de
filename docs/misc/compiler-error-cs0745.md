---
title: "Compilerfehler CS0745 | Microsoft Docs"
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
  - "CS0745"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0745"
ms.assetid: 6ae77eb2-a940-43aa-a198-3042d144613a
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0745
Kontextabhängiges Schlüsselwort "by" erwartet.  
  
 Das Muster für die `group`\-Klausel ist `group...by`, optional gefolgt von `into`, wie im folgenden Beispiel gezeigt:  
  
```  
string[] names = { "Bob", "Bill", "Jonetta", "Mary" }; var query = from name in names group name by name[0];  
```  
  
 oder  
  
```  
var query2 = from name in names group name by name[0] into g //...additional query clauses  
```  
  
### So beheben Sie diesen Fehler  
  
1.  Fügen Sie der `group`\-Klausel das `by`\-Schlüsselwort hinzu.  
  
## Beispiel  
 Der folgende Code generiert CS0745:  
  
```  
// cs0745.cs using System; using System.Linq; public class C { public static int Main() { string[] names = { "Bob", "Bill", "Jonetta", "Mary" }; var query = from name in names group name name[0]; // CS0745 return 1; } }  
```  
  
## Siehe auch  
 [LINQ\-Abfrageausdrücke](/dotnet/csharp/programming-guide/linq-query-expressions/index)   
 [group\-Klausel](/dotnet/csharp/language-reference/keywords/group-clause)