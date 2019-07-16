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
ms.openlocfilehash: eee81a96e6841aa77e2056a95bd18979724b62e5
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65842395"
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

Dies ist jedoch standardmäßig diese Regel nur untersucht öffentliche Enumerationen [konfigurierbare](#configurability).

## <a name="rule-description"></a>Regelbeschreibung

Eine Enumeration ist ein Werttyp, der einen Satz verwandter benannter Konstanten definiert. In der Standardeinstellung die <xref:System.Int32?displayProperty=fullName> -Datentyp wird verwendet, um den konstanten Wert zu speichern. Auch wenn Sie dies zugrunde liegende Typ ändern können, ist es nicht notwendig oder empfehlenswert für die meisten Szenarien. Keine erhebliche Leistungszunahme erfolgt über einen Datentyp, der kleiner ist als <xref:System.Int32>. Wenn Sie den Standarddatentyp verwenden können, verwenden Sie eine von der Common Language-System (CLS)-kompatiblen ganzzahligen Typen <xref:System.Byte>, <xref:System.Int16>, <xref:System.Int32>, oder <xref:System.Int64> um sicherzustellen, dass alle Werte der Enumeration dargestellt werden können CLS-kompatible Programmiersprachen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, wenn Probleme mit der Größe oder Kompatibilität vorhanden sind, verwenden Sie <xref:System.Int32>. Für Situationen, in denen <xref:System.Int32> ist nicht groß genug, um die Werte aufnehmen, verwenden Sie <xref:System.Int64>. Wenn die Abwärtskompatibilität mit einen kleineren Datentyp erforderlich ist, verwenden Sie <xref:System.Byte> oder <xref:System.Int16>.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Unterdrücken Sie eine Warnung dieser Regel nur, wenn Sie Abwärtskompatibilität erforderlich ist. In Anwendungen ist nicht in der Regel mit dieser Regel entsprechen keine Probleme verursachen. Bibliotheken, in denen Interoperabilität erforderlich ist, kann der Fehler, die mit dieser Regel kompatibel Ihre Benutzer beeinträchtigen.

## <a name="configurability"></a>Konfigurierbarkeit

Wenn Sie diese Regel aus ausführen, [FxCop-Analysen](install-fxcop-analyzers.md) (und nicht über die Analyse von statischem Code), können Sie konfigurieren, welche Teile Ihrer Codebasis, um die Ausführung dieser Regel auf, um basierend auf deren Barrierefreiheit. Z. B. um anzugeben, dass die Regel nur für die nicht öffentlichen API-Oberfläche ausgeführt werden soll, fügen Sie die folgenden Schlüssel-Wert-Paar in einer editorconfig-Datei in Ihrem Projekt:

```ini
dotnet_code_quality.ca1028.api_surface = private, internal
```

Sie können diese Option, die für diese eine Regel, für alle Regeln oder für alle Regeln in dieser Kategorie (Entwurf) konfigurieren. Weitere Informationen finden Sie unter [konfigurieren FxCop-Analysetools](configure-fxcop-analyzers.md).

## <a name="example-of-a-violation"></a>Beispiel eines Verstoßes

Das folgende Beispiel zeigt zwei Enumerationen, die nicht den empfohlenen zugrunde liegenden Datentyp verwenden.

[!code-vb[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_1.vb)]
[!code-csharp[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_1.cs)]

## <a name="example-of-how-to-fix"></a>Beispiel für die Behebung

Im folgenden Beispiel wird der vorherige Verstoß durch ändern den zugrunde liegenden Datentyp, korrigiert <xref:System.Int32>.

[!code-csharp[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_2.cs)]
[!code-vb[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_2.vb)]

## <a name="related-rules"></a>Verwandte Regeln

- [CA1008: -Enumerationen sollten NULL-Wert aufweisen.](../code-quality/ca1008-enums-should-have-zero-value.md)
- [CA1027: Enumerationen mit FlagsAttribute markieren](../code-quality/ca1027-mark-enums-with-flagsattribute.md)
- [CA2217: Nicht Enumerationen mit FlagsAttribute markieren](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)
- [CA1700: Enumerationswerte nicht mit "Reserviert" benennen](../code-quality/ca1700-do-not-name-enum-values-reserved.md)
- [CA1712: Führen Sie keine Präfixe für Enumerationswerte mit Typnamen](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

## <a name="see-also"></a>Siehe auch

- <xref:System.Byte?displayProperty=fullName>
- <xref:System.Int16?displayProperty=fullName>
- <xref:System.Int32?displayProperty=fullName>
- <xref:System.Int64?displayProperty=fullName>