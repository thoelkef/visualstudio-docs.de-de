---
title: 'CA1008: Enumerationen müssen einen Wert von 0 (null) aufweisen.'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1008
- EnumsShouldHaveZeroValue
helpviewer_keywords:
- CA1008
- EnumsShouldHaveZeroValue
ms.assetid: 3503a73c-360c-416d-8ee4-c2aa44365a05
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 9264b37992885ff3d93aba4802d8d7f0cee535aa
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54992905"
---
# <a name="ca1008-enums-should-have-zero-value"></a>CA1008: Enumerationen müssen einen Wert von 0 (null) aufweisen.

|||
|-|-|
|TypeName|EnumsShouldHaveZeroValue|
|CheckId|CA1008|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Nicht unterbrechend – Wenn Sie aufgefordert werden, Hinzufügen einer **keine** Wert, der eine nicht-Flagenumeration. Wichtige – Wenn Sie aufgefordert werden, umbenennen oder entfernen alle Enumerationswerte.|

## <a name="cause"></a>Ursache

Eine Enumeration ohne eine angewendeten <xref:System.FlagsAttribute?displayProperty=fullName> definiert sich nicht auf einen Member mit dem Wert 0 (null); oder eine Enumeration, die eine angewendet wurde <xref:System.FlagsAttribute> definiert ein Element mit dem Wert 0 (null), aber der Name ist nicht 'None' oder die Enumeration definiert mehrere NULL-Werten Elemente.

## <a name="rule-description"></a>Regelbeschreibung

Der Standardwert einer nicht initialisierten Enumeration ist, genau wie anderer Werttypen ist 0 (null). Eine Enumeration ohne Flags-Attribut sollten Mitglied definieren, mit dem Wert 0 (null), damit der Standardwert ein gültiger Wert der Enumeration ist. Bei Bedarf, nennen Sie das Element 'None'. Ordnen Sie andernfalls 0 (null), auf den am häufigsten verwendeten Member. Wenn der Wert des ersten Elements der Enumeration nicht in der Deklaration festgelegt ist, ist der Wert in der Standardeinstellung 0 (null).

Wenn eine Enumeration, die die <xref:System.FlagsAttribute> angewendet definiert den Member NULL-Wert, der Name muss 'None', um anzugeben, dass in der Enumeration keine Werte festgelegt wurden. Verwenden einen NULL-Member, für andere Zwecke im Gegensatz zum Ergebnis der Verwendung von ist das <xref:System.FlagsAttribute> , AND und bitweise Operatoren sind nutzlos, mit dem Element. Dies bedeutet, dass nur ein Member den Wert 0 (null) zugewiesen werden soll. Wenn mehrere Elemente, die den Wert 0 (null) haben in einer Enumeration Flags-Attribut auftreten `Enum.ToString()` gibt falsche Ergebnisse für Elemente, die nicht 0 (null) zurück.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Definieren Sie einen Member mit dem Wert 0 (null), um einen Verstoß gegen diese Regel für nicht-Enumerationen zu beheben. Dies ist eine nicht unterbrechende Änderung. Namen Sie für Enumerationen, die einen 0 (null) Member definieren dieses Element den "None", und löschen Sie anderer Elemente, die den Wert 0 (null) aufweisen; Dies ist eine unterbrechende Änderung.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Unterdrücken Sie keine Warnung dieser Regel, mit Ausnahme von Enumerationen, die zuvor veröffentlicht haben.

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt zwei Enumerationen, die die Regel erfüllen und eine Enumeration, `BadTraceOptions`, die gegen die Regel verstößt.

[!code-cpp[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CPP/ca1008-enums-should-have-zero-value_1.cpp)]
[!code-csharp[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CSharp/ca1008-enums-should-have-zero-value_1.cs)]
[!code-vb[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/VisualBasic/ca1008-enums-should-have-zero-value_1.vb)]

## <a name="related-rules"></a>Verwandte Regeln

- [CA2217: Nicht Enumerationen mit FlagsAttribute markieren](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)
- [CA1700: Enumerationswerte nicht mit "Reserviert" benennen](../code-quality/ca1700-do-not-name-enum-values-reserved.md)
- [CA1712: Führen Sie keine Präfixe für Enumerationswerte mit Typnamen](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)
- [CA1028: Enumerationsspeicher sollte Int32 sein.](../code-quality/ca1028-enum-storage-should-be-int32.md)
- [CA1027: Enumerationen mit FlagsAttribute markieren](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Siehe auch

- <xref:System.Enum?displayProperty=fullName>