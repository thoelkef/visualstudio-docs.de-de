---
title: 'CA2214: Überschreibbare Methoden in Konstruktoren nicht aufrufen'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotCallOverridableMethodsInConstructors
- CA2214
helpviewer_keywords:
- CA2214
- DoNotCallOverridableMethodsInConstructors
ms.assetid: 335b57ca-a6e8-41b4-a20e-57ee172c97c3
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 589aefaab69a6ea7f211ff7a3de19515ed7e9163
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="ca2214-do-not-call-overridable-methods-in-constructors"></a>CA2214: Überschreibbare Methoden in Konstruktoren nicht aufrufen
|||
|-|-|
|TypeName|DoNotCallOverridableMethodsInConstructors|
|CheckId|CA2214|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Der Konstruktor eines nicht versiegelten Typs Ruft eine virtuelle Methode in der Klasse definiert.

## <a name="rule-description"></a>Regelbeschreibung
 Wenn eine virtuelle Methode aufgerufen wird, ist der tatsächliche Typ, der die Methode ausgeführt wird, nicht bis zur Laufzeit ausgewählt. Wenn ein Konstruktor eine virtuelle Methode aufruft, ist es möglich, dass der Konstruktor für die Instanz, die die Methode aufruft, nicht ausgeführt wurde.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, rufen Sie nicht virtuelle Methoden des Typs mithilfe der Konstruktoren des Typs.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel. Der Konstruktor sollte neu gestaltet werden, um den Aufruf der virtuellen Methode zu vermeiden.

## <a name="example"></a>Beispiel
 Das folgende Beispiel veranschaulicht den Effekt der Verstoß gegen diese Regel. Die Anwendung zu testen, erstellt eine Instanz des `DerivedType`, dies bedeutet, dass ihre Basisklasse (`BadlyConstructedType`) Konstruktor ausgeführt. `BadlyConstructedType`der Konstruktor ruft falsch virtuelle Methode `DoSomething`. Wie die Ausgabe zeigt, `DerivedType.DoSomething()` ausgeführt wird, und gilt für sollten Sie vor dem `DerivedType`Konstruktor führt.

 [!code-csharp[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/CSharp/ca2214-do-not-call-overridable-methods-in-constructors_1.cs)]
 [!code-vb[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/VisualBasic/ca2214-do-not-call-overridable-methods-in-constructors_1.vb)]

 Folgende Ergebnisse werden zurückgegeben:

 **Aufrufen des Basiskonstruktors. ** 
 **Abgeleitete DoSomething heißt - initialisiert? Nicht**
**aufrufen abgeleiteten Ctor.**