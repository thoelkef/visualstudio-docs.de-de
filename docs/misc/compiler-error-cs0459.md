---
title: "Compilerfehler CS0459 | Microsoft Docs"
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
  - "CS0459"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0459"
ms.assetid: 01b058dd-8d65-4e9d-9de1-d47f9488d22a
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0459
Die Adresse einer schreibgeschützten lokalen Variablen kann nicht abgerufen werden.  
  
 Es gibt drei allgemeine Szenarien in der Programmiersprache C\#, durch die schreibgeschützte lokale Variablen generiert werden: `foreach`, `using` und `fixed`. In jedem dieser Fälle ist es unzulässig, in die schreibgeschützte lokale Variable zu schreiben oder deren Adresse zu übernehmen. Dieser Fehler wird generiert, wenn der Compiler erkennt, dass Sie versuchen, die Adresse einer schreibgeschützten lokalen Variablen zu übernehmen.  
  
## Beispiel  
 Im folgenden Beispiel wird beim Versuch, die Adresse einer schreibgeschützten lokalen Variablen in einer `foreach`\-Schleife und in einem `fixed`\-Anweisungsblock zu übernehmen, CS0459 generiert.  
  
```  
// CS0459.cs // compile with: /unsafe class A { public unsafe void M1() { int[] ints = new int[] { 1, 2, 3 }; foreach (int i in ints) { int *j = &i;  // CS0459 } fixed (int *i = &_i) { int **j = &i;  // CS0459 } } private int _i = 0; }  
```