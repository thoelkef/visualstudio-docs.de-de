---
title: 'CA2104: Schreibgeschützte änderbare Referenztypen nicht deklarieren.'
ms.date: 11/01/2018
ms.topic: reference
f1_keywords:
- DoNotDeclareReadOnlyMutableReferenceTypes
- CA2104
helpviewer_keywords:
- CA2104
- DoNotDeclareReadOnlyMutableReferenceTypes
ms.assetid: 81b83ee5-4db5-4be0-9f8d-90b53894ec3b
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: a033ed83d6d349ac3876a6f11a24570f3ff8f60c
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55945013"
---
# <a name="ca2104-do-not-declare-read-only-mutable-reference-types"></a>CA2104: Schreibgeschützte änderbare Referenztypen nicht deklarieren.

|||
|-|-|
|TypeName|DoNotDeclareReadOnlyMutableReferenceTypes|
|CheckId|CA2104|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Nicht unterbrechend|

> [!NOTE]
> Regel CA2104 ist veraltet und wird in einer zukünftigen Version von Visual Studio entfernt.

## <a name="cause"></a>Ursache

Ein extern sichtbarer Typ enthält ein extern sichtbares schreibgeschütztes Feld, bei dem es sich um einen änderbaren Referenztyp handelt.

## <a name="rule-description"></a>Regelbeschreibung

Ein änderbarer Typ ist ein Typ, dessen Instanzdaten geändert werden können. Die <xref:System.Text.StringBuilder?displayProperty=fullName> Klasse ist ein Beispiel für einen änderbaren Referenztyp. Es enthält Elemente, die den Wert einer Instanz der Klasse ändern können. Ein Beispiel für einen unveränderlichen Referenztyp ist der <xref:System.String?displayProperty=fullName> Klasse. Nach der sie instanziiert wurde, kann ihr Wert niemals ändern.

Die schreibgeschützten Modifizierer ([Readonly](/dotnet/csharp/language-reference/keywords/readonly) in C#, [ReadOnly](/dotnet/visual-basic/language-reference/modifiers/readonly) in Visual Basic und [const](/cpp/cpp/const-cpp) in C++) auf einem Verweistyp Feld (oder Zeiger in C++) verhindert, dass das Feld aus durch eine andere Instanz des Verweistyps ersetzt. Allerdings verhindert der Modifizierer der Instanzdaten des Felds nicht, die durch den Verweistyp geändert wird.

Diese Regel möglicherweise versehentlich angezeigt einem Verstoß für einen Typ, ist, tatsächlich unveränderlich. In diesem Fall ist es sicher ist, die die Warnung zu unterdrücken.

Schreibgeschützte Arrayfelder sind von dieser Regel ausgenommen verursachen jedoch stattdessen einen Verstoß gegen die [CA2105: Arrayfelder sollten nicht schreibgeschützt sein](../code-quality/ca2105-array-fields-should-not-be-read-only.md) Regel.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie den schreibgeschützten Modifizierer oder, wenn eine wichtige Änderung akzeptabel ist, ersetzen Sie das Feld mit einem unveränderlichen Typ.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Es ist sicher eine Warnung dieser Regel zu unterdrücken, wenn der Feldtyp unveränderlich ist.

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt eine Felddeklaration, die einen Verstoß gegen diese Regel führt dazu, dass:

[!code-cpp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CPP/ca2104-do-not-declare-read-only-mutable-reference-types_1.cpp)]
[!code-csharp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CSharp/ca2104-do-not-declare-read-only-mutable-reference-types_1.cs)]
[!code-vb[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/VisualBasic/ca2104-do-not-declare-read-only-mutable-reference-types_1.vb)]