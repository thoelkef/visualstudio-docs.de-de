---
title: "CA1012: Abstrakte Typen d&#252;rfen keine Konstruktoren aufweisen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AbstractTypesShouldNotHaveConstructors"
  - "CA1012"
helpviewer_keywords: 
  - "CA1012"
ms.assetid: 09f458ac-dd88-4cd7-a47f-4106c1e80ece
caps.latest.revision: 25
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 25
---
# CA1012: Abstrakte Typen d&#252;rfen keine Konstruktoren aufweisen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AbstractTypesShouldNotHaveConstructors|  
|CheckId|CA1012|  
|Kategorie \(Category\)|Microsoft.Design|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Ein öffentlicher Typ ist abstrakt und verfügt über einen öffentlichen Konstruktor.  
  
## Regelbeschreibung  
 Konstruktoren von abstrakten Datentypen können nur von abgeleiteten Typen aufgerufen werden.  Da öffentliche Konstruktoren Instanzen eines Typs erstellen und Sie keine Instanzen eines abstrakten Datentyps erstellen können, ist ein abstrakter Datentyp mit einem öffentlichen Konstruktor fehlerhaft konzipiert.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, machen Sie entweder den Konstruktor zu einem geschützten Konstruktor, oder deklarieren Sie den Typ nicht als abstrakten Datentyp.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  Der abstrakte Typ verfügt über einen öffentlichen Konstruktor.  
  
## Beispiel  
 Das folgende Beispiel enthält einen abstrakten Typ, der gegen diese Regel verstößt.  
  
 [!code-vb[FxCop.Design.AbstractTypeBad#1](../code-quality/codesnippet/VisualBasic/ca1012-abstract-types-should-not-have-constructors_1.vb)]
 [!code-cs[FxCop.Design.AbstractTypeBad#1](../code-quality/codesnippet/CSharp/ca1012-abstract-types-should-not-have-constructors_1.cs)]  
  
## Beispiel  
 Im folgenden Beispiel wird der vorherige Verstoß korrigiert, indem der Konstruktorzugriff von `public` in `protected` geändert wird.  
  
 [!code-cs[FxCop.Design.AbstractTypeGood#1](../code-quality/codesnippet/CSharp/ca1012-abstract-types-should-not-have-constructors_2.cs)]
 [!code-vb[FxCop.Design.AbstractTypeGood#1](../code-quality/codesnippet/VisualBasic/ca1012-abstract-types-should-not-have-constructors_2.vb)]