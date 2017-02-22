---
title: "CA1804: Nicht verwendete lokale Variablen entfernen | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1804"
  - "RemoveUnusedLocals"
helpviewer_keywords: 
  - "RemoveUnusedLocals"
  - "CA1804"
ms.assetid: cc332e67-6543-4813-bd8a-6f6fc75bf22a
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1804: Nicht verwendete lokale Variablen entfernen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|RemoveUnusedLocals|  
|CheckId|CA1804|  
|Kategorie \(Category\)|Microsoft.Performance|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 In einer Methode wird eine lokale Variable deklariert, aber höchstens als Empfänger einer Zuweisungsanweisung verwendet.  Damit eine Analyse gemäß dieser Regel möglich ist, muss die getestete Assembly mit Debuginformationen erstellt werden, und die zugehörige Programmdatenbankdatei \(PDB\) muss verfügbar sein.  
  
## Regelbeschreibung  
 Nicht verwendete lokale Variablen und unnötige Zuweisungen vergrößern die Assembly unnötig und beeinträchtigen die Leistung.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, entfernen oder verwenden Sie die lokale Variable.  Beachten Sie, dass der C\#\-Compiler \(gehört zum Lieferumfang von [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]\) nicht verwendete lokale Variablen entfernt, wenn die `optimize`\-Option aktiviert ist.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie eine Warnung dieser Regel, wenn die Variable vom Compiler ausgegeben wurde.  Eine Warnung dieser Regel kann ebenso gefahrlos unterdrückt werden, bzw. die Regel kann deaktiviert werden, wenn das Leistungsverhalten und die Codepflege nicht im Vordergrund stehen.  
  
## Beispiel  
 Im folgenden Beispiel werden mehrere nicht verwendete lokale Variablen veranschaulicht.  
  
 [!code-vb[FxCop.Performance.UnusedLocals#1](../code-quality/codesnippet/VisualBasic/ca1804-remove-unused-locals_1.vb)]
 [!code-cs[FxCop.Performance.UnusedLocals#1](../code-quality/codesnippet/CSharp/ca1804-remove-unused-locals_1.cs)]  
  
## Verwandte Regeln  
 [CA1809: Übermäßige lokale Variablen vermeiden](../code-quality/ca1809-avoid-excessive-locals.md)  
  
 [CA1811: Nicht aufgerufenen privaten Code vermeiden](../code-quality/ca1811-avoid-uncalled-private-code.md)  
  
 [CA1812: Nicht instanziierte interne Klassen vermeiden](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)  
  
 [CA1801: Nicht verwendete Parameter überprüfen](../code-quality/ca1801-review-unused-parameters.md)