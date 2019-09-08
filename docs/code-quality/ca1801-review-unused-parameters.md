---
title: 'CA1801: Nicht verwendete Parameter überprüfen.'
ms.date: 06/24/2019
ms.topic: reference
f1_keywords:
- AvoidUnusedParameters
- CA1801
- ReviewUnusedParameters
helpviewer_keywords:
- CA1801
- ReviewUnusedParameters
ms.assetid: 5d73545c-e153-4b7c-a7b2-be6bf5aca5be
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a73ce207d8efb0c6309ba52648c7231f89bc7984
ms.sourcegitcommit: 0f44ec8ba0263056ad04d2d0dc904ad4206ce8fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2019
ms.locfileid: "70766044"
---
# <a name="ca1801-review-unused-parameters"></a>CA1801: Nicht verwendete Parameter überprüfen.

|||
|-|-|
|TypeName|ReviewUnusedParameters|
|CheckId|CA1801|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechend: Wenn der Member außerhalb der Assembly nicht sichtbar ist, unabhängig von der Änderung, die Sie vornehmen.<br /><br /> Nicht unterbrechend: Wenn Sie den Member so ändern, dass er den Parameter in seinem Text verwendet.<br /><br /> Unterbrechen: Wenn Sie den Parameter entfernen und dieser außerhalb der Assembly sichtbar ist.|

## <a name="cause"></a>Ursache

Eine Methoden Signatur enthält einen Parameter, der im Methoden Text nicht verwendet wird.

Diese Regel untersucht nicht die folgenden Arten von Methoden:

- Methoden, auf die ein Delegat verweist.

- Methoden, die als Ereignishandler verwendet werden.

- Methoden, die mit `abstract` dem`MustOverride` -Modifizierer (in Visual Basic) deklariert wurden.

- Methoden, die mit `virtual` dem`Overridable` -Modifizierer (in Visual Basic) deklariert wurden.

- Methoden, die mit `override` dem`Overrides` -Modifizierer (in Visual Basic) deklariert wurden.

- Methoden, die mit `extern` dem`Declare` -Modifizierer (Anweisung in Visual Basic) deklariert wurden.

Bei Verwendung von [FxCop-Analyzern](install-fxcop-analyzers.md)werden Parameter, die mit dem [Verwerfungs](/dotnet/csharp/discards) Symbol benannt sind, nicht durch diese Regel gekennzeichnet, `_` `_1`z. b `_2`., und. Dadurch wird das Warnungs Rauschen bei Parametern reduziert, die für die Signatur Anforderungen benötigt werden, z. b. eine Methode, die als Delegat verwendet wird, ein Parameter mit speziellen Attributen oder ein Parameter, dessen Wert zur Laufzeit implizit von einem Framework aufgerufen wird, auf den aber nicht verwiesen wird. Ordnung.

## <a name="rule-description"></a>Regelbeschreibung

Überprüfen Sie Parameter in nicht virtuellen Methoden, die nicht im Methoden Text verwendet werden, um sicherzustellen, dass keine Unrichtigkeit vorhanden ist, um den Zugriff darauf zu vermeiden. Nicht verwendete Parameter verursachen Wartungs-und Leistungskosten.

Manchmal kann ein Verstoß gegen diese Regel auf einen Implementierungs Fehler in der-Methode hinweisen. Beispielsweise sollte der-Parameter im Methoden Text verwendet werden. Unterdrückt Warnungen dieser Regel, wenn der Parameter aufgrund der Abwärtskompatibilität vorhanden sein muss.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie den nicht verwendeten Parameter (ein Breaking Change), oder verwenden Sie den-Parameter im Methoden Text (ein nicht-Breaking Change).

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken:

- Im zuvor gelieferten Code, für den die Korrektur ein Breaking Change wäre.

- Für den `this` -Parameter in einer benutzerdefinierten Erweiterungs <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=nameWithType>Methode für. Die Funktionen in der <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> -Klasse sind statisch, sodass es nicht erforderlich ist, auf `this` den-Parameter im Methoden Text zuzugreifen.

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt zwei Methoden. Eine Methode verstößt gegen die Regel, und die andere Methode erfüllt die Regel.

[!code-csharp[FxCop.Usage.ReviewUnusedParameters#1](../code-quality/codesnippet/CSharp/ca1801-review-unused-parameters_1.cs)]

## <a name="related-rules"></a>Verwandte Regeln

[CA1811: Nicht aufgerufenen privaten Code vermeiden](../code-quality/ca1811-avoid-uncalled-private-code.md)

[CA1812: Nicht instanziierte interne Klassen vermeiden](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

[CA1804: Nicht verwendete lokale Variablen entfernen](../code-quality/ca1804-remove-unused-locals.md)
