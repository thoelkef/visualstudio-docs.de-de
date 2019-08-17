---
title: 'CA1008: Enumerationen müssen einen Wert von 0 (null) aufweisen.'
ms.date: 03/11/2019
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
ms.openlocfilehash: 502033d2adffd640d2af6ee8d36b0c0f3cd71472
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547930"
---
# <a name="ca1008-enums-should-have-zero-value"></a>CA1008: Enumerationen müssen einen Wert von 0 (null) aufweisen.

|||
|-|-|
|TypeName|EnumsShouldHaveZeroValue|
|CheckId|CA1008|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Nicht unterbrechend: Wenn Sie aufgefordert werden, einen " **None** "-Wert zu einer nicht-Flag-Enumeration hinzuzufügen. Unterbrechen: Wenn Sie aufgefordert werden, Enumerationswerte umzubenennen oder zu entfernen.|

## <a name="cause"></a>Ursache

Eine Enumeration ohne angewendete <xref:System.FlagsAttribute?displayProperty=fullName> definiert keinen Member, der den Wert 0 (null) aufweist. Oder eine Enumeration, die über einen angewendeten <xref:System.FlagsAttribute> verfügt, definiert einen Member, der den Wert 0 (null) aufweist, der Name jedoch nicht "None" ist. Oder die-Enumeration definiert mehrere Member mit dem Wert 0 (null).

Standardmäßig prüft diese Regel nur extern sichtbare Enumerationen, dies ist jedoch [konfigurierbar](#configurability).

## <a name="rule-description"></a>Regelbeschreibung

Der Standardwert einer nicht initialisierten Enumeration, ebenso wie andere Werttypen, ist 0 (null). Eine Enumeration, die nicht mit Flags versehen ist, sollte einen Member mit dem Wert 0 (null) definieren, sodass der Standardwert ein gültiger Wert der-Enumeration ist. Wenn erforderlich, benennen Sie den Member "None". Andernfalls sollten Sie dem am häufigsten verwendeten Member NULL zuweisen. Wenn der Wert des ersten Enumerationsmembers nicht in der Deklaration festgelegt ist, ist der Wert standardmäßig auf 0 festgelegt.

Wenn eine Enumeration mit dem <xref:System.FlagsAttribute> angewendeten einen Member mit einem Wert von 0 (null) definiert, sollte der Name "None" lauten, um anzugeben, dass in der Enumeration keine Werte festgelegt wurden. Die Verwendung eines Elements mit einem Wert von 0 (null) für andere Zwecke steht im <xref:System.FlagsAttribute> Gegensatz zur Verwendung von in, da die-und-oder-oder bitweisen Operatoren mit dem-Member nutzlos sind. Dies impliziert, dass nur einem Member der Wert 0 (null) zugewiesen werden soll. Wenn mehrere Member mit dem Wert 0 (null) in einer durch Flags attributierten Enumeration auftreten, `Enum.ToString()` gibt falsche Ergebnisse für Member zurück, die nicht 0 (null) sind.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel für Enumerationen mit nicht-Flags-Attributen zu beheben, definieren Sie einen Member, der den Wert 0 (null) aufweist. Dabei handelt es sich um einen nicht Breaking Change. Für Flags-attributierte Enumerationen, die einen Null-wertigen Member definieren, benennen Sie den Member "None", und löschen Sie alle anderen Member, die den Wert 0 (null) aufweisen. Dies ist eine Breaking Change.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Unterdrücken Sie keine Warnung dieser Regel, außer bei von Flags attributierten Enumerationen, die zuvor ausgeliefert wurden.

## <a name="configurability"></a>Konfigurierbarkeit

Wenn Sie diese Regel von [FxCop](install-fxcop-analyzers.md) Analyzer (und nicht mit der Legacy Analyse) ausführen, können Sie basierend auf ihrer Barrierefreiheit konfigurieren, für welche Teile Ihrer Codebasis diese Regel ausgeführt werden soll. Um z. b. anzugeben, dass die Regel nur für die nicht öffentliche API-Oberfläche ausgeführt werden soll, fügen Sie das folgende Schlüssel-Wert-Paar in eine Editor config-Datei in Ihrem Projekt ein:

```ini
dotnet_code_quality.ca1008.api_surface = private, internal
```

Sie können diese Option nur für diese Regel, für alle Regeln oder für alle Regeln in dieser Kategorie (Entwurf) konfigurieren. Weitere Informationen finden Sie unter [Konfigurieren von FxCop-Analysen](configure-fxcop-analyzers.md).

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt zwei Enumerationen, die die Regel erfüllen, und eine Enumeration `BadTraceOptions`, die gegen die Regel verstößt.

[!code-cpp[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CPP/ca1008-enums-should-have-zero-value_1.cpp)]
[!code-csharp[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CSharp/ca1008-enums-should-have-zero-value_1.cs)]
[!code-vb[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/VisualBasic/ca1008-enums-should-have-zero-value_1.vb)]

## <a name="related-rules"></a>Verwandte Regeln

- [CA2217: Auffüge Zeichen nicht mit FlagsAttribute markieren](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)
- [CA1700: Enumerationswerte "reserviert" nicht benennen](../code-quality/ca1700-do-not-name-enum-values-reserved.md)
- [CA1712: Enumerationswerte nicht mit Typname als Präfix versehen](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)
- [CA1028: Der Aufzählungs Speicher muss Int32 lauten.](../code-quality/ca1028-enum-storage-should-be-int32.md)
- [CA1027: Markierungen mit FlagsAttribute markieren](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Siehe auch

- <xref:System.Enum?displayProperty=fullName>