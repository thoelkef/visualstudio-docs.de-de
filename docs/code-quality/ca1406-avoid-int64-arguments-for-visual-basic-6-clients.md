---
title: 'CA1406: Int64-Argumente für Visual Basic 6-Clients vermeiden'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: f6eeda13b8dc7a05622613f719a6b2a85b61835a
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/13/2018
ms.locfileid: "45546875"
---
# <a name="ca1406-avoid-int64-arguments-for-visual-basic-6-clients"></a>CA1406: Int64-Argumente für Visual Basic 6-Clients vermeiden

|||
|-|-|
|TypeName|AvoidInt64ArgumentsForVB6Clients|
|CheckId|CA1406|
|Kategorie|Microsoft.Interoperability|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein Typ, der ausdrücklich zum Component Object Model (COM) als sichtbar markiert ist einen Member deklariert, nimmt eine <xref:System.Int64?displayProperty=fullName> Argument.

## <a name="rule-description"></a>Regelbeschreibung
 Visual Basic 6-COM-Clients können nicht auf 64-Bit-Ganzzahlen zugreifen.

 Standardmäßig sind die folgenden für COM sichtbar: Assemblys, öffentliche Typen, öffentliche Member in öffentlichen Typen und alle Mitglieder der öffentliche Werttypen. Um falsch positive Ergebnisse zu reduzieren, erfordert mit dieser Regel jedoch die COM-Sichtbarkeit des Typs explizit angegeben werden; die übergeordnete Assembly muss markiert sein, mit der <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> festgelegt `false` und der Typ markiert werden muss, mit der <xref:System.Runtime.InteropServices.ComVisibleAttribute> festgelegt `true`.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel für einen Parameter zu beheben, dessen Wert immer als 32-Bit-Ganzzahl ausgedrückt werden, ändern Sie den Parametertyp in <xref:System.Int32?displayProperty=fullName>. Wenn der Wert des Parameters größer sein als als 32-Bit-Ganzzahl dargestellt werden kann, ändern Sie den Parametertyp in <xref:System.Decimal?displayProperty=fullName>. Beachten Sie, dass beide <xref:System.Single?displayProperty=fullName> und <xref:System.Double?displayProperty=fullName> Genauigkeitsverlust die oberen Bereiche der der <xref:System.Int64> -Datentyp. Wenn der Member nicht für COM sichtbar sein soll, markieren Sie sie mit der <xref:System.Runtime.InteropServices.ComVisibleAttribute> festgelegt `false`.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Es ist sicher eine Warnung dieser Regel zu unterdrücken, wenn sicher ist, dass Visual Basic 6-COM-Clients nicht auf den Typ zugreifen.

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