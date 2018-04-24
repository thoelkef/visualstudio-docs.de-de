---
title: 'CA2104: Schreibgeschützte änderbare Referenztypen nicht deklarieren'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fcf9379f9950264aca5c76355867ccb44ba40282
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="ca2104-do-not-declare-read-only-mutable-reference-types"></a>CA2104: Schreibgeschützte änderbare Referenztypen nicht deklarieren
|||
|-|-|
|TypeName|DoNotDeclareReadOnlyMutableReferenceTypes|
|CheckId|CA2104|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein extern sichtbarer Typ enthält ein extern sichtbares schreibgeschütztes Feld, bei dem es sich um einen änderbaren Referenztyp handelt.

## <a name="rule-description"></a>Regelbeschreibung
 Ein änderbarer Typ ist ein Typ, dessen Instanzdaten geändert werden können. Die <xref:System.Text.StringBuilder?displayProperty=fullName> Klasse ist ein Beispiel für einen änderbaren Referenztyp. Es enthält Elemente, die den Wert einer Instanz der Klasse ändern können. Ein Beispiel für einen nicht änderbaren Referenztyp ist der <xref:System.String?displayProperty=fullName> Klasse. Nachdem es instanziiert wurde, kann ihr Wert nie ändern.

 Den schreibgeschützten Modifizierer ([Readonly](/dotnet/csharp/language-reference/keywords/readonly) in c# [ReadOnly](/dotnet/visual-basic/language-reference/modifiers/readonly) in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], und [const](/cpp/cpp/const-cpp) in C++) auf einen Referenztyp darstellt (Zeiger in C++) verhindert das Feld durch eine andere Instanz des Verweistyps ersetzt. Allerdings verhindert der Modifizierer die Instanzdaten des Felds nicht, die durch den Verweistyp geändert wird.

 Schreibgeschützte Arrayfelder sind von dieser Regel ausgenommen, verursachen jedoch stattdessen einen Verstoß gegen die [CA2105: Arrayfelder soll nicht nur lesen](../code-quality/ca2105-array-fields-should-not-be-read-only.md) Regel.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie den schreibgeschützten Modifizierer oder, wenn eine unterbrechende Änderung zulässig ist, ersetzen Sie das Feld durch ein unveränderlicher Typ.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Sie können ruhig zum Unterdrücken einer Warnung dieser Regel, wenn der Typ des Felds unveränderlich ist.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Felddeklaration, die bewirkt, einen Verstoß gegen diese Regel dass.

 [!code-cpp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CPP/ca2104-do-not-declare-read-only-mutable-reference-types_1.cpp)]
 [!code-csharp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CSharp/ca2104-do-not-declare-read-only-mutable-reference-types_1.cs)]
 [!code-vb[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/VisualBasic/ca2104-do-not-declare-read-only-mutable-reference-types_1.vb)]