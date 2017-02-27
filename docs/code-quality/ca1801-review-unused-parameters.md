---
title: "CA1801: Nicht verwendete Parameter &#252;berpr&#252;fen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AvoidUnusedParameters"
  - "CA1801"
  - "ReviewUnusedParameters"
helpviewer_keywords: 
  - "CA1801"
  - "ReviewUnusedParameters"
ms.assetid: 5d73545c-e153-4b7c-a7b2-be6bf5aca5be
caps.latest.revision: 30
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 30
---
# CA1801: Nicht verwendete Parameter &#252;berpr&#252;fen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ReviewUnusedParameters|  
|CheckId|CA1801|  
|Kategorie \(Category\)|Microsoft.Usage|  
|Unterbrechende Änderung|Nicht unterbrechend – Wenn der Member unabhängig von der vorgenommenen Änderung außerhalb der Assembly nicht sichtbar ist.<br /><br /> Nicht unterbrechend – Wenn Sie den Member ändern, um den Parameter im Text zu verwenden.<br /><br /> Unterbrechend – Wenn Sie den Parameter entfernen und er außerhalb der Assembly sichtbar ist.|  
  
## Ursache  
 Eine Methodensignatur enthält einen Parameter, der nicht im Methodentext verwendet wird.  Die folgenden Methoden werden mit dieser Regel nicht geprüft:  
  
-   Methoden, auf die von einem Delegaten verwiesen wird.  
  
-   Methoden, die als Ereignishandler verwendet werden.  
  
-   Methoden, die mit dem `abstract`\-Modifizierer \(`MustOverride` in Visual Basic\) deklariert werden.  
  
-   Methoden, die mit dem `virtual`\-Modifizierer \(`Overridable` in Visual Basic\) deklariert werden.  
  
-   Methoden, die mit dem `override`\-Modifizierer \(`Overrides` in Visual Basic\) deklariert werden.  
  
-   Methoden, die mit dem `extern`\-Modifizierer \(`Declare`\-Anweisung in Visual Basic\) deklariert werden.  
  
## Regelbeschreibung  
 Überprüfen Sie in nicht virtuellen Methoden die Parameter, die nicht im Methodentext verwendet werden, um sicherzustellen, dass im Umfeld des gescheiterten Zugriffs keine Richtigkeit vorhanden ist.  Nicht verwendete Parameter führen zu höheren Wartungskosten und einer geringeren Leistung.  
  
 Manchmal kann ein Verstoß dieser Regel auf einen Implementierungsfehler in der Methode hinweisen.  Der Parameter sollte beispielsweise im Methodentext verwendet werden.  Unterdrücken Sie Warnungen dieser Regel, wenn der Parameter zwecks Abwärtskompatibilität vorhanden sein muss.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie den nicht verwendeten Parameter \(eine unterbrechende Änderung\), oder verwenden Sie den Parameter im Methodentext \(eine nicht unterbrechende Änderung\).  
  
## Wann sollten Warnungen unterdrückt werden?  
 Eine Warnung dieser Regel kann bei zuvor veröffentlichtem Code, für den die Korrektur eine unterbrechende Änderung wäre, gefahrlos unterdrückt werden.  
  
## Beispiel  
 Im folgenden Beispiel werden zwei Methoden veranschaulicht.  Eine Methode verstößt gegen die Regel, und die andere Methode erfüllt die Regel.  
  
 [!code-cs[FxCop.Usage.ReviewUnusedParameters#1](../code-quality/codesnippet/CSharp/ca1801-review-unused-parameters_1.cs)]  
  
## Verwandte Regeln  
 [CA1811: Nicht aufgerufenen privaten Code vermeiden](../code-quality/ca1811-avoid-uncalled-private-code.md)  
  
 [CA1812: Nicht instanziierte interne Klassen vermeiden](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)  
  
 [CA1804: Nicht verwendete lokale Variablen entfernen](../code-quality/ca1804-remove-unused-locals.md)