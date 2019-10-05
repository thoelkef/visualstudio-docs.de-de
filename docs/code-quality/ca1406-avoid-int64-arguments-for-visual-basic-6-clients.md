---
title: 'CA1406: Int64-Argumente für Visual Basic 6-Clients vermeiden.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AvoidInt64ArgumentsForVB6Clients
- CA1406
helpviewer_keywords:
- AvoidInt64ArgumentsForVB6Clients
- CA1406
ms.assetid: d5d0d3fc-f105-43da-be5b-923ab023309c
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 82a8b1ea389c37dc63a9fe7366208a2a3028efb8
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234799"
---
# <a name="ca1406-avoid-int64-arguments-for-visual-basic-6-clients"></a>CA1406: Int64-Argumente für Visual Basic 6-Clients vermeiden.

|||
|-|-|
|TypeName|AvoidInt64ArgumentsForVB6Clients|
|CheckId|CA1406|
|Kategorie|Microsoft.Interoperability|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
Ein Typ, der speziell für Component Object Model (com) als sichtbar gekennzeichnet ist, deklariert einen Member, <xref:System.Int64?displayProperty=fullName> der ein-Argument annimmt.

## <a name="rule-description"></a>Regelbeschreibung
Visual Basic 6-COM-Clients können nicht auf 64-Bit-Ganzzahlen zugreifen.

Standardmäßig sind die folgenden Elemente für com sichtbar: Assemblys, öffentliche Typen, öffentliche Instanzmember in öffentlichen Typen und alle Member der öffentlichen Werttypen. Um falsch positive Ergebnisse zu reduzieren, erfordert diese Regel jedoch, dass die COM-Sichtbarkeit des Typs explizit angegeben wird. die <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> enthaltende Assembly muss mit dem auf festgelegten festgelegt werden, `false` und der Typ muss <xref:System.Runtime.InteropServices.ComVisibleAttribute> mit dem `true`auf festgelegten Wert gekennzeichnet werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Um einen Verstoß gegen diese Regel für einen Parameter zu beheben, dessen Wert immer als 32-Bit-Ganzzahl ausgedrückt werden kann, ändern Sie <xref:System.Int32?displayProperty=fullName>den Parametertyp in. Wenn der Wert des-Parameters größer sein kann als 32-Bit-Ganzzahl, ändern Sie den Parametertyp in <xref:System.Decimal?displayProperty=fullName>. Beachten Sie, <xref:System.Single?displayProperty=fullName> dass <xref:System.Double?displayProperty=fullName> sowohl als auch <xref:System.Int64> die Genauigkeit in den oberen Bereichen des Datentyps verlieren. Wenn der Member nicht für com sichtbar sein soll, markieren Sie ihn mit dem <xref:System.Runtime.InteropServices.ComVisibleAttribute> auf `false`festgelegten.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn sicher ist, dass Visual Basic 6 com-Clients nicht auf den Typ zugreifen.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt einen Typ, der gegen die Regel verstößt.

[!code-csharp[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/CSharp/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.cs)]
[!code-vb[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/VisualBasic/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.vb)]

## <a name="related-rules"></a>Verwandte Regeln
[CA1413: Nicht öffentliche Felder in für COM sichtbaren Werttypen vermeiden](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

[CA1407: Statische Member in für COM sichtbaren Typen vermeiden](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

[CA1017: Assemblys mit ComVisibleAttribute markieren](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Siehe auch

- [Interoperabilität mit nicht verwaltetem Code](/dotnet/framework/interop/index)
- [Long-Datentyp](/dotnet/visual-basic/language-reference/data-types/long-data-type)