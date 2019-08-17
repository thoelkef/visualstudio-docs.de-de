---
title: 'CA2217: Enumerationen nicht mit FlagsAttribute markieren.'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- DoNotMarkEnumsWithFlags
- CA2217
helpviewer_keywords:
- DoNotMarkEnumsWithFlags
- CA2217
dev_langs:
- VB
- CSharp
- CPP
ms.assetid: 1b6f626c-66bf-45b0-a3e2-7c41ee9ceda7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 377188183acdaa9aa86ae3344c8f6d5727b82ccc
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2019
ms.locfileid: "69546840"
---
# <a name="ca2217-do-not-mark-enums-with-flagsattribute"></a>CA2217: Enumerationen nicht mit FlagsAttribute markieren.

|||
|-|-|
|TypeName|DoNotMarkEnumsWithFlags|
|CheckId|CA2217|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache

Eine Enumeration ist mit <xref:System.FlagsAttribute> markiert, und Sie verfügt über einen oder mehrere Werte, die nicht aus zwei oder einer Kombination der anderen definierten Werte für die Enumeration bestehen.

Standardmäßig prüft diese Regel nur extern sichtbare Enumerationen, dies ist jedoch [konfigurierbar](#configurability).

## <a name="rule-description"></a>Regelbeschreibung

Eine Enumeration sollte nur <xref:System.FlagsAttribute> vorhanden sein, wenn jeder in der-Enumeration definierte Wert eine Potenz von zwei oder einer Kombination von definierten Werten ist.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, <xref:System.FlagsAttribute> entfernen Sie aus der-Enumeration.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Unterdrücken Sie keine Warnung dieser Regel.

## <a name="configurability"></a>Konfigurierbarkeit

Wenn Sie diese Regel von [FxCop](install-fxcop-analyzers.md) Analyzer (und nicht mit der Legacy Analyse) ausführen, können Sie basierend auf ihrer Barrierefreiheit konfigurieren, für welche Teile Ihrer Codebasis diese Regel ausgeführt werden soll. Um z. b. anzugeben, dass die Regel nur für die nicht öffentliche API-Oberfläche ausgeführt werden soll, fügen Sie das folgende Schlüssel-Wert-Paar in eine Editor config-Datei in Ihrem Projekt ein:

```ini
dotnet_code_quality.ca2217.api_surface = private, internal
```

Sie können diese Option nur für diese Regel, für alle Regeln oder für alle Regeln in dieser Kategorie (Verwendung) konfigurieren. Weitere Informationen finden Sie unter [Konfigurieren von FxCop-Analysen](configure-fxcop-analyzers.md).

## <a name="examples"></a>Beispiele

Der folgende Code zeigt eine Enumeration `Color`, die den Wert 3 enthält. 3 ist keine Potenz von zwei oder eine Kombination aus den definierten Werten. Die `Color` Enumeration sollte nicht mit <xref:System.FlagsAttribute>markiert werden.

[!code-cpp[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/CPP/ca2217-do-not-mark-enums-with-flagsattribute_1.cpp)]
[!code-csharp[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/CSharp/ca2217-do-not-mark-enums-with-flagsattribute_1.cs)]
[!code-vb[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/VisualBasic/ca2217-do-not-mark-enums-with-flagsattribute_1.vb)]

Der folgende Code zeigt eine Enumeration, `Days`die die Anforderungen erfüllt, die mit <xref:System.FlagsAttribute>markiert werden sollen:

[!code-cpp[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/CPP/ca2217-do-not-mark-enums-with-flagsattribute_2.cpp)]
[!code-csharp[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/CSharp/ca2217-do-not-mark-enums-with-flagsattribute_2.cs)]
[!code-vb[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/VisualBasic/ca2217-do-not-mark-enums-with-flagsattribute_2.vb)]

## <a name="related-rules"></a>Verwandte Regeln

[CA1027: Markierungen mit FlagsAttribute markieren](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Siehe auch

- <xref:System.FlagsAttribute?displayProperty=fullName>
