---
title: 'CA2214: Überschreibbare Methoden in Konstruktoren nicht aufrufen.'
ms.date: 11/04/2016
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
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: ef2a5631247f882a70ae94877da02f576ff04a5d
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55946027"
---
# <a name="ca2214-do-not-call-overridable-methods-in-constructors"></a>CA2214: Überschreibbare Methoden in Konstruktoren nicht aufrufen.

|||
|-|-|
|TypeName|DoNotCallOverridableMethodsInConstructors|
|CheckId|CA2214|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache

Der Konstruktor mit einem nicht versiegelten Typ ruft es sich um eine virtuelle Methode, die in der Klasse definiert.

## <a name="rule-description"></a>Regelbeschreibung

Wenn eine virtuelle Methode aufgerufen wird, ist der tatsächliche Typ, der die Methode ausgeführt wird, nicht bis zur Laufzeit ausgewählt. Wenn ein Konstruktor eine virtuelle Methode aufruft, ist es möglich, dass der Konstruktor für die Instanz, die die Methode aufruft, nicht ausgeführt wurde.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, rufen Sie nicht virtuellen Methoden eines Typs mithilfe der Konstruktoren des Typs.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Unterdrücken Sie keine Warnung dieser Regel. Der Konstruktor muss überarbeitet werden, um den Aufruf der virtuellen Methode zu entfernen.

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt die Auswirkungen der Verstoß gegen diese Regel. Die testanwendung erstellt eine Instanz des `DerivedType`, wodurch ihre Basisklasse (`BadlyConstructedType`) Konstruktor ausgeführt. `BadlyConstructedType`der Konstruktor ruft nicht ordnungsgemäß die virtuelle Methode `DoSomething`. Die Ausgabe zeigt, `DerivedType.DoSomething()` ausgeführt wird, und gilt für sollten Sie vor dem `DerivedType`der Konstruktor ausgeführt wird.

[!code-csharp[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/CSharp/ca2214-do-not-call-overridable-methods-in-constructors_1.cs)]
[!code-vb[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/VisualBasic/ca2214-do-not-call-overridable-methods-in-constructors_1.vb)]

Dieses Beispiel erzeugt die folgende Ausgabe:

```txt
Calling base ctor.
Derived DoSomething is called - initialized ? No
Calling derived ctor.
```