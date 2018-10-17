---
title: 'CA2104: Schreibgeschützte änderbare Referenztypen nicht deklarieren'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 80d40dd60b0a6b6e507b903fd7a6185c5419422e
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/13/2018
ms.locfileid: "45551687"
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
 Ein änderbarer Typ ist ein Typ, dessen Instanzdaten geändert werden können. Die <xref:System.Text.StringBuilder?displayProperty=fullName> Klasse ist ein Beispiel für einen änderbaren Referenztyp. Es enthält Elemente, die den Wert einer Instanz der Klasse ändern können. Ein Beispiel für einen unveränderlichen Referenztyp ist der <xref:System.String?displayProperty=fullName> Klasse. Nach der sie instanziiert wurde, kann ihr Wert niemals ändern.

 Die schreibgeschützten Modifizierer ([Readonly](/dotnet/csharp/language-reference/keywords/readonly) in c# [ReadOnly](/dotnet/visual-basic/language-reference/modifiers/readonly) in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], und [const](/cpp/cpp/const-cpp) in C++) auf einem Verweistyp (Zeiger in C++) verhindert, dass das Feld wird ersetzt durch eine andere Instanz des Verweistyps. Allerdings verhindert der Modifizierer der Instanzdaten des Felds nicht, die durch den Verweistyp geändert wird.

 Schreibgeschützte Arrayfelder sind von dieser Regel ausgenommen verursachen jedoch stattdessen einen Verstoß gegen die [CA2105: Arrayfelder sollte nicht schreibgeschützt sein](../code-quality/ca2105-array-fields-should-not-be-read-only.md) Regel.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie den schreibgeschützten Modifizierer oder, wenn eine wichtige Änderung akzeptabel ist, ersetzen Sie das Feld mit einem unveränderlichen Typ.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Es ist sicher eine Warnung dieser Regel zu unterdrücken, wenn der Feldtyp unveränderlich ist.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Felddeklaration, die bewirkt, einen Verstoß gegen diese Regel dass.

 [!code-cpp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CPP/ca2104-do-not-declare-read-only-mutable-reference-types_1.cpp)]
 [!code-csharp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CSharp/ca2104-do-not-declare-read-only-mutable-reference-types_1.cs)]
 [!code-vb[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/VisualBasic/ca2104-do-not-declare-read-only-mutable-reference-types_1.vb)]