---
title: "Compilerwarnung (Stufe 3) CS1718 | Microsoft Docs"
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
  - "CS1718"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1718"
ms.assetid: 7c1c11fd-4f91-482d-b8f7-efe2a361634e
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 3) CS1718
Der Vergleich erfolgte mit der gleichen Variablen. Wollten Sie etwas anderes vergleichen?  
  
 Wenn Sie etwas anderes vergleichen wollten, sollten Sie die Anweisung einfach korrigieren.  
  
 Eine andere Möglichkeit ist, dass Sie "True" oder "False" testen und dazu Anweisungen wie `if (a == a) (true)` oder `if (a < a) (false)` verwendet haben. Nehmen Sie stattdessen einfach `if (true)` oder `if (false)`. Hierfür gibt es zwei Gründe:  
  
-   Es ist einfacher: Einfach zu sagen, was Sie meinen, bringt immer größere Klarheit.  
  
-   Verwirrung wird vermieden: Ein neues Feature von C\# 2.0 sind Werttypen, die auf NULL festgelegt werden können, analog zum Wert `null` in T\-SQL, die von SQL Server verwendete Programmiersprache. Mit T\-SQL vertraute Entwickler machen sich möglicherweise Gedanken über die Auswirkungen auf NULL festlegbarer Typen auf Ausdrücke wie `if (a == a)`, da in T\-SQL die ternäre Logik Verwendung findet. Bei Verwendung von `true` oder `false` vermeiden Sie mögliche Verwirrungen.  
  
## Beispiel  
 Mit dem folgenden Code wird die Warnung CS1718 generiert.  
  
```  
// CS1718.cs using System; public class Tester { public static void Main() { int i = 0; if (i == i) { // CS1718.cs //if (true) { i++; } } }  
```