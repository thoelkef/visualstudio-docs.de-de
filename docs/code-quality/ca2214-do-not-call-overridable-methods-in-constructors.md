---
title: "CA2214: &#220;berschreibbare Methoden in Konstruktoren nicht aufrufen | Microsoft Docs"
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
  - "DoNotCallOverridableMethodsInConstructors"
  - "CA2214"
helpviewer_keywords: 
  - "CA2214"
  - "DoNotCallOverridableMethodsInConstructors"
ms.assetid: 335b57ca-a6e8-41b4-a20e-57ee172c97c3
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2214: &#220;berschreibbare Methoden in Konstruktoren nicht aufrufen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotCallOverridableMethodsInConstructors|  
|CheckId|CA2214|  
|Kategorie \(Category\)|Microsoft.Usage|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Der Konstruktor eines unversiegelten Typs ruft eine virtuelle Methode auf, die in seiner Klasse definiert ist.  
  
## Regelbeschreibung  
 Beim Aufruf einer virtuellen Methode wird der eigentliche Typ, der die Methode ausführt, erst zur Laufzeit ausgewählt.  Wenn ein Konstruktor eine virtuelle Methode aufruft, wurde möglicherweise der Konstruktor für die Instanz, von der die Methode aufgerufen wird, nicht ausgeführt.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, rufen Sie die virtuellen Methoden eines Typs nicht in den Konstruktoren des Typs auf.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  Der Konstruktor sollte neu konzipiert werden, sodass der Aufruf der virtuellen Methode entfällt.  
  
## Beispiel  
 Im folgenden Beispiel wird die Wirkung eines Verstoßes gegen diese Regel veranschaulicht.  Die Testanwendung erstellt eine Instanz von `DerivedType`, die die Ausführung ihres Basisklassenkonstruktors \(`BadlyConstructedType`\) bewirkt.  Der Konstruktor von `BadlyConstructedType` ruft fehlerhafterweise die virtuelle `DoSomething`\-Methode auf.  Die Ausgabe zeigt, dass `DerivedType.DoSomething()` vor der Ausführung des Konstruktors von `DerivedType` ausgeführt wird.  
  
 [!code-cs[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/CSharp/ca2214-do-not-call-overridable-methods-in-constructors_1.cs)]
 [!code-vb[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/VisualBasic/ca2214-do-not-call-overridable-methods-in-constructors_1.vb)]  
  
 Folgende Ergebnisse werden zurückgegeben:  
  
  **Aufrufen des Basiskonstruktors.**  
**Abgeleitetes DoSomething wird aufgerufen \- initialisiert?  nein**  
**Aufrufen des abgeleiteten Konstruktors.**