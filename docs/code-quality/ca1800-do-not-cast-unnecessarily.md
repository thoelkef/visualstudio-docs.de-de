---
title: "CA1800: Keine unn&#246;tigen Umwandlungen | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1800"
  - "DoNotCastUnnecessarily"
helpviewer_keywords: 
  - "DoNotCastUnnecessarily"
  - "CA1800"
ms.assetid: b79a010a-6627-421e-8955-6007e32fa808
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1800: Keine unn&#246;tigen Umwandlungen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotCastUnnecessarily|  
|CheckId|CA1800|  
|Kategorie \(Category\)|Microsoft.Performance|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Eine Methode führt doppelte Umwandlungen für eines ihrer Argumente oder eine ihrer lokalen Variablen aus.  Damit eine umfassende Analyse gemäß dieser Regel möglich ist, muss die getestete Assembly mit Debuginformationen erstellt werden, und die zugehörige Programmdatenbankdatei \(PDB\) muss verfügbar sein.  
  
## Regelbeschreibung  
 Doppelte Umwandlungen beeinträchtigen die Leistung, insbesondere wenn die Umwandlungen in kompakten Iterationsanweisungen ausgeführt werden.  Wenn explizite doppelte Umwandlungsoperationen durchgeführt werden müssen, sollte das Ergebnis der Umwandlung in einer lokalen Variablen gespeichert und die lokale Variable statt der doppelten Umwandlungsoperationen verwendet werden.  
  
 Wenn mit dem Operator `is` von C\# getestet wird, ob die Umwandlung erfolgreich durchgeführt werden kann, bevor die eigentliche Umwandlung erfolgt, sollten Sie erwägen, stattdessen das Ergebnis des Operators `as` zu testen.  Dieses Vorgehen bietet die gleiche Funktionalität ohne die implizite vom Operator `is` ausgeführte Umwandlungsoperation.  
  
## Behandeln von Verstößen  
 Sie beheben Verstöße gegen diese Regel, indem Sie die Methodenimplementierung so ändern, dass die Anzahl von Umwandlungsoperationen möglichst gering ist.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Eine Warnung dieser Regel kann gefahrlos unterdrückt werden bzw. die Regel kann völlig ignoriert werden, wenn die Leistung nicht von Belang ist.  
  
## Beispiel  
 Im folgenden Beispiel wird eine Methode veranschaulicht, die den Operator `is` von C\# verwendet und gegen die Regel verstößt.  Eine zweite Methode verstößt nicht gegen die Regel, da der Operator `is` durch einen Test des Ergebnisses des Operators `as` ersetzt wird. Dadurch wird die Anzahl der Umwandlungsoperationen pro Iteration von zwei auf eins verringert.  
  
 [!code-cs[FxCop.Performance.UnnecessaryCastsAsIs#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_1.cs)]  
  
## Beispiel  
 Im folgenden Beispiel werden zwei Methoden veranschaulicht: die Methode `start_Click`, die mehrere doppelte explizite Umwandlungen enthält und damit gegen die Regel verstößt, sowie die Methode `reset_Click`, die die Regel einhält, indem das Umwandlungsergebnis in einer lokalen Variablen gespeichert wird.  
  
 [!code-vb[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/VisualBasic/ca1800-do-not-cast-unnecessarily_2.vb)]
 [!code-cs[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_2.cs)]  
  
## Siehe auch  
 [as](/dotnet/csharp/language-reference/keywords/as)   
 [is](/dotnet/csharp/language-reference/keywords/is)