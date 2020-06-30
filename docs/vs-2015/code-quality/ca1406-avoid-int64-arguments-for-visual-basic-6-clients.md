---
title: 'CA1406: Vermeiden von Int64-Argumenten für Visual Basic 6-Clients | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidInt64ArgumentsForVB6Clients
- CA1406
helpviewer_keywords:
- AvoidInt64ArgumentsForVB6Clients
- CA1406
ms.assetid: d5d0d3fc-f105-43da-be5b-923ab023309c
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b6ab93c24cd97d498ae886c7a9184fd4a5f111f1
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85534913"
---
# <a name="ca1406-avoid-int64-arguments-for-visual-basic-6-clients"></a>CA1406: Int64-Argumente für Visual Basic 6-Clients vermeiden.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|AvoidInt64ArgumentsForVB6Clients|
|CheckId|CA1406|
|Category|Microsoft. Interoperabilität|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein Typ, der speziell für Component Object Model (com) als sichtbar gekennzeichnet ist, deklariert einen Member, der ein- <xref:System.Int64?displayProperty=fullName> Argument annimmt.

## <a name="rule-description"></a>Beschreibung der Regel
 Visual Basic 6-COM-Clients können nicht auf 64-Bit-Ganzzahlen zugreifen.

 Standardmäßig sind die folgenden Elemente für com sichtbar: Assemblys, öffentliche Typen, öffentliche Instanzmember in öffentlichen Typen und alle Member der öffentlichen Werttypen. Um falsch positive Ergebnisse zu reduzieren, erfordert diese Regel jedoch, dass die COM-Sichtbarkeit des Typs explizit angegeben wird. die enthaltende Assembly muss mit dem <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> auf festgelegten festgelegt werden, `false` und der Typ muss mit dem <xref:System.Runtime.InteropServices.ComVisibleAttribute> auf festgelegten Wert gekennzeichnet werden `true` .

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel für einen Parameter zu beheben, dessen Wert immer als 32-Bit-Ganzzahl ausgedrückt werden kann, ändern Sie den Parametertyp in <xref:System.Int32?displayProperty=fullName> . Wenn der Wert des-Parameters größer sein kann als 32-Bit-Ganzzahl, ändern Sie den Parametertyp in <xref:System.Decimal?displayProperty=fullName> . Beachten Sie, dass sowohl <xref:System.Single?displayProperty=fullName> als auch <xref:System.Double?displayProperty=fullName> die Genauigkeit in den oberen Bereichen des <xref:System.Int64> Datentyps verlieren. Wenn der Member nicht für com sichtbar sein soll, markieren Sie ihn mit dem <xref:System.Runtime.InteropServices.ComVisibleAttribute> auf festgelegten `false` .

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn sicher ist, dass Visual Basic 6 com-Clients nicht auf den Typ zugreifen.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ, der gegen die Regel verstößt.

 [!code-csharp[FxCop.Interoperability.LongArgument#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LongArgument/cs/FxCop.Interoperability.LongArgument.cs#1)]
 [!code-vb[FxCop.Interoperability.LongArgument#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LongArgument/vb/FxCop.Interoperability.LongArgument.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1413: Nicht öffentliche Felder in für COM sichtbaren Werttypen vermeiden.](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

 [CA1407: Statische Member in für COM sichtbaren Typen vermeiden.](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017: Assemblys mit ComVisibleAttribute markieren.](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Weitere Informationen
 Interoperabilität mit [Long-Datentyp](https://msdn.microsoft.com/library/b4770c34-1804-4f8c-b512-c10b0893e516) [von nicht verwaltetem Code](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
