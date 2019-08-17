---
title: 'CA1028: Der Enumerationsspeicher sollte Int32 sein.'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1028
- EnumStorageShouldBeInt32
helpviewer_keywords:
- EnumStorageShouldBeInt32
- CA1028
ms.assetid: 87160825-9f39-4142-8d7f-a31fe7ac7b84
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: c91de575abe8b19a5d8f6fca864e2bc452da7cb2
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547646"
---
# <a name="ca1028-enum-storage-should-be-int32"></a>CA1028: Der Enumerationsspeicher sollte Int32 sein.

|||
|-|-|
|TypeName|EnumStorageShouldBeInt32|
|CheckId|CA1028|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache

Der zugrunde liegende Typ einer Enumeration ist nicht <xref:System.Int32?displayProperty=fullName>.

Standardmäßig untersucht diese Regel nur öffentliche Enumerationen, dies ist jedoch [konfigurierbar](#configurability).

## <a name="rule-description"></a>Regelbeschreibung

Eine Enumeration ist ein Werttyp, der einen Satz verwandter benannter Konstanten definiert. Standardmäßig wird der <xref:System.Int32?displayProperty=fullName> -Datentyp verwendet, um den konstanten Wert zu speichern. Obwohl Sie diesen zugrunde liegenden Typ ändern können, ist es für die meisten Szenarien nicht notwendig oder empfehlenswert. Durch die Verwendung eines-Datentyps, der kleiner als <xref:System.Int32>ist, wird kein erheblicher Leistungsgewinn erzielt. Wenn Sie den Standard Datentyp nicht verwenden können, sollten Sie einen der CLS-kompatiblen ganzzahligen Typen (Common Language System) <xref:System.Byte>, <xref:System.Int16> <xref:System.Int32>,, oder <xref:System.Int64> verwenden, um sicherzustellen, dass alle Werte der-Enumeration in CLS-kompatible Programmiersprachen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Verwenden <xref:System.Int32>Sie, um einen Verstoß gegen diese Regel zu beheben, sofern keine Größen-oder Kompatibilitätsprobleme vorhanden sind. <xref:System.Int32> Verwenden<xref:System.Int64>Sie für Situationen, in denen nicht groß genug ist, um die Werte zu speichern. Wenn die Abwärtskompatibilität einen kleineren Datentyp erfordert, <xref:System.Byte> verwenden <xref:System.Int16>Sie oder.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Unterdrückt eine Warnung aus dieser Regel nur, wenn dies bei Problemen mit der Abwärtskompatibilität erforderlich ist. In-Anwendungen verursacht die fehlgeschlagene Einhaltung dieser Regel keine Probleme. In Bibliotheken, bei denen die sprach Interoperabilität erforderlich ist, kann sich die Einhaltung dieser Regel nicht negativ auf die Benutzer auswirken.

## <a name="configurability"></a>Konfigurierbarkeit

Wenn Sie diese Regel von [FxCop](install-fxcop-analyzers.md) Analyzer (und nicht mit der Legacy Analyse) ausführen, können Sie basierend auf ihrer Barrierefreiheit konfigurieren, für welche Teile Ihrer Codebasis diese Regel ausgeführt werden soll. Um z. b. anzugeben, dass die Regel nur für die nicht öffentliche API-Oberfläche ausgeführt werden soll, fügen Sie das folgende Schlüssel-Wert-Paar in eine Editor config-Datei in Ihrem Projekt ein:

```ini
dotnet_code_quality.ca1028.api_surface = private, internal
```

Sie können diese Option nur für diese Regel, für alle Regeln oder für alle Regeln in dieser Kategorie (Entwurf) konfigurieren. Weitere Informationen finden Sie unter [Konfigurieren von FxCop-Analysen](configure-fxcop-analyzers.md).

## <a name="example-of-a-violation"></a>Beispiel für eine Verletzung

Das folgende Beispiel zeigt zwei Enumerationen, die den empfohlenen zugrunde liegenden Datentyp nicht verwenden.

[!code-vb[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_1.vb)]
[!code-csharp[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_1.cs)]

## <a name="example-of-how-to-fix"></a>Beispiel für das Beheben von

Im folgenden Beispiel wird der vorherige Verstoß korrigiert, indem der zugrunde liegende- <xref:System.Int32>Datentyp in geändert wird.

[!code-csharp[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_2.cs)]
[!code-vb[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_2.vb)]

## <a name="related-rules"></a>Verwandte Regeln

- [CA1008: Enumerationswerte sollten NULL-Werte aufweisen.](../code-quality/ca1008-enums-should-have-zero-value.md)
- [CA1027: Markierungen mit FlagsAttribute markieren](../code-quality/ca1027-mark-enums-with-flagsattribute.md)
- [CA2217: Auffüge Zeichen nicht mit FlagsAttribute markieren](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)
- [CA1700: Enumerationswerte "reserviert" nicht benennen](../code-quality/ca1700-do-not-name-enum-values-reserved.md)
- [CA1712: Enumerationswerte nicht mit Typname als Präfix versehen](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

## <a name="see-also"></a>Siehe auch

- <xref:System.Byte?displayProperty=fullName>
- <xref:System.Int16?displayProperty=fullName>
- <xref:System.Int32?displayProperty=fullName>
- <xref:System.Int64?displayProperty=fullName>