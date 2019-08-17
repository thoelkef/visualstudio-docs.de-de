---
title: 'CA2214: Überschreibbare Methoden in Konstruktoren nicht aufrufen.'
ms.date: 05/29/2016
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
ms.openlocfilehash: a59346cb70269d4d2b405279fc9ea5573a879b1e
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2019
ms.locfileid: "69546999"
---
# <a name="ca2214-do-not-call-overridable-methods-in-constructors"></a>CA2214: Überschreibbare Methoden in Konstruktoren nicht aufrufen.

|||
|-|-|
|TypeName|DoNotCallOverridableMethodsInConstructors|
|CheckId|CA2214|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache

Der Konstruktor eines nicht versiegelten Typs Ruft eine virtuelle Methode auf, die in der-Klasse definiert ist.

## <a name="rule-description"></a>Regelbeschreibung

Wenn eine virtuelle Methode aufgerufen wird, wird der tatsächliche Typ, der die Methode ausführt, erst zur Laufzeit ausgewählt. Wenn ein Konstruktor eine virtuelle Methode aufruft, ist es möglich, dass der Konstruktor für die-Instanz, die die-Methode aufruft, nicht ausgeführt wurde.

> [!NOTE]
> Die Legacy-Analyse Implementierung dieser Regel hat eine andere Diagnose Meldung: " **\[Konstruktorname] enthält eine Aufrufkette, die einen von der-Klasse definierten virtuellen Methoden aufführt. Überprüfen Sie die folgende aufrufsstapel auf unbeabsichtigte Folgen**". Die [FxCop-Analysen](install-fxcop-analyzers.md) -Implementierung dieser Regel weist die Diagnose Meldung "keine**über schreibbaren Methoden in Konstruktoren abrufen" auf**.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, müssen Sie die virtuellen Methoden eines Typs nicht innerhalb der Konstruktoren des Typs abrufen.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Unterdrücken Sie keine Warnung dieser Regel. Der Konstruktor sollte neu gestaltet werden, um den aufzurufenden Befehl der virtuellen Methode auszuschließen.

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt die Auswirkung des Verstoßes gegen diese Regel. Die Testanwendung erstellt eine Instanz von `DerivedType`, die bewirkt, dass der Basisklassenkonstruktor (`BadlyConstructedType`) ausgeführt wird. `BadlyConstructedType`der Konstruktor ruft fälschlicherweise die virtuelle Methode `DoSomething`auf. Wie die Ausgabe zeigt, `DerivedType.DoSomething()` wird ausgeführt `DerivedType`, bevor der Konstruktor ausgeführt wird.

[!code-csharp[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/CSharp/ca2214-do-not-call-overridable-methods-in-constructors_1.cs)]
[!code-vb[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/VisualBasic/ca2214-do-not-call-overridable-methods-in-constructors_1.vb)]

Dieses Beispiel erzeugt die folgende Ausgabe:

```txt
Calling base ctor.
Derived DoSomething is called - initialized ? No
Calling derived ctor.
```