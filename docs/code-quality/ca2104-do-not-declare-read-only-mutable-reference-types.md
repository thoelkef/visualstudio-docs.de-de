---
title: 'CA2104: Schreibgeschützte änderbare Referenztypen nicht deklarieren'
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
ms.openlocfilehash: 8f4f165b4b00f46b478907c9affca672b4c7f113
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232955"
---
# <a name="ca2104-do-not-declare-read-only-mutable-reference-types"></a>CA2104: Schreibgeschützte änderbare Referenztypen nicht deklarieren.

|||
|-|-|
|TypeName|DoNotDeclareReadOnlyMutableReferenceTypes|
|CheckId|CA2104|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Nicht unterbrechend|

> [!NOTE]
> Die Regel CA2104 ist veraltet und wird in einer zukünftigen Version von Visual Studio entfernt. Sie wird aufgrund der komplizierten Analyse, die erforderlich ist, um die tatsächliche Unveränderlichkeit eines Typs zu ermitteln, nicht als [Analyzer](roslyn-analyzers-overview.md) implementiert.

## <a name="cause"></a>Ursache

Ein extern sichtbarer Typ enthält ein extern sichtbares schreibgeschütztes Feld, bei dem es sich um einen änderbaren Referenztyp handelt.

## <a name="rule-description"></a>Regelbeschreibung

Ein änderbarer Typ ist ein Typ, dessen Instanzdaten geändert werden können. Die <xref:System.Text.StringBuilder?displayProperty=fullName> -Klasse ist ein Beispiel für einen änderbaren Referenztyp. Sie enthält Member, die den Wert einer Instanz der-Klasse ändern können. Ein Beispiel für einen unveränderlichen Verweistyp ist die <xref:System.String?displayProperty=fullName> -Klasse. Nachdem Sie instanziiert wurde, kann sich der Wert nie ändern.

Der schreibgeschützte Modifizierer (Schreib geschützter in C#, [Schreib](/dotnet/visual-basic/language-reference/modifiers/readonly) [geschützter in Visual Basic](/dotnet/csharp/language-reference/keywords/readonly) und [Konstanten](/cpp/cpp/const-cpp) in C++) in einem Verweistyp Feld (oder Zeiger in C++) verhindert, dass das Feld durch eine andere Instanz des Verweis Typs ersetzt wird. Der-Modifizierer verhindert jedoch nicht, dass die Instanzdaten des Felds durch den Verweistyp geändert werden.

Diese Regel zeigt möglicherweise versehentlich einen Verstoß gegen einen Typ an, der tatsächlich unveränderlich ist. In diesem Fall ist es sicher, die Warnung zu unterdrücken.

Felder mit Schreib geschütztem Array sind von dieser Regel ausgenommen, führen jedoch zu [einem Verstoß gegen CA2105: Array Felder dürfen nicht schreibgeschützt sein](../code-quality/ca2105-array-fields-should-not-be-read-only.md) .

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie den schreibgeschützten Modifizierer, oder ersetzen Sie das Feld durch einen unveränderlichen Typ, wenn ein Breaking Change akzeptabel ist.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn der Feldtyp unveränderlich ist.

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt eine Feld Deklaration, die einen Verstoß gegen diese Regel verursacht:

[!code-cpp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CPP/ca2104-do-not-declare-read-only-mutable-reference-types_1.cpp)]
[!code-csharp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CSharp/ca2104-do-not-declare-read-only-mutable-reference-types_1.cs)]
[!code-vb[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/VisualBasic/ca2104-do-not-declare-read-only-mutable-reference-types_1.vb)]