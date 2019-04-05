---
title: 'CA1028: Enumerationsspeicher sollte Int32 sein. | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1028
- EnumStorageShouldBeInt32
helpviewer_keywords:
- EnumStorageShouldBeInt32
- CA1028
ms.assetid: 87160825-9f39-4142-8d7f-a31fe7ac7b84
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e79eb7e0ed33184103cc772c13515959cf973ecc
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58959360"
---
# <a name="ca1028-enum-storage-should-be-int32"></a>CA1028: Der Enumerationsspeicher sollte Int32 sein.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|EnumStorageShouldBeInt32|
|CheckId|CA1028|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Der zugrunde liegende Typ eine öffentliche Enumeration ist nicht <xref:System.Int32?displayProperty=fullName>.

## <a name="rule-description"></a>Regelbeschreibung
 Eine Enumeration ist ein Werttyp, der einen Satz verwandter benannter Konstanten definiert. In der Standardeinstellung die <xref:System.Int32?displayProperty=fullName> -Datentyp wird verwendet, um den konstanten Wert zu speichern. Auch wenn Sie dies zugrunde liegende Typ ändern können, ist es nicht notwendig oder empfehlenswert für die meisten Szenarien. Beachten Sie, dass keine erhebliche Leistungszunahme erreicht wird, indem Sie einen Datentyp, der kleiner ist als <xref:System.Int32>. Wenn Sie den Standarddatentyp verwenden können, verwenden Sie eine von der Common Language-System (CLS)-kompatiblen ganzzahligen Typen <xref:System.Byte>, <xref:System.Int16>, <xref:System.Int32>, oder <xref:System.Int64> um sicherzustellen, dass alle Werte der Enumeration dargestellt werden können CLS-kompatible Programmiersprachen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, wenn Probleme mit der Größe oder Kompatibilität vorhanden sind, verwenden Sie <xref:System.Int32>. Für Situationen, in denen <xref:System.Int32> ist nicht groß genug, um die Werte aufnehmen, verwenden Sie <xref:System.Int64>. Wenn die Abwärtskompatibilität mit einen kleineren Datentyp erforderlich ist, verwenden Sie <xref:System.Byte> oder <xref:System.Int16>.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie eine Warnung dieser Regel nur, wenn Sie Abwärtskompatibilität erforderlich ist. In Anwendungen ist nicht in der Regel mit dieser Regel entsprechen keine Probleme verursachen. Bibliotheken, in denen Interoperabilität erforderlich ist, kann der Fehler, die mit dieser Regel kompatibel Ihre Benutzer beeinträchtigen.

## <a name="example-of-a-violation"></a>Beispiel eines Verstoßes

### <a name="description"></a>Beschreibung
 Das folgende Beispiel zeigt zwei Enumerationen, die nicht den empfohlenen zugrunde liegenden Datentyp verwenden.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Design.EnumIntegralType#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralType/cs/FxCop.Design.EnumIntegralType.cs#1)]
 [!code-vb[FxCop.Design.EnumIntegralType#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralType/vb/FxCop.Design.EnumIntegralType.vb#1)]

## <a name="example-of-how-to-fix"></a>Beispiel für die Fehlerbehebung

### <a name="description"></a>Beschreibung
 Im folgenden Beispiel wird der vorherige Verstoß durch ändern den zugrunde liegenden Datentyp, korrigiert <xref:System.Int32>.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Design.EnumIntegralTypeFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralTypeFixed/cs/FxCop.Design.EnumIntegralTypeFixed.cs#1)]
 [!code-vb[FxCop.Design.EnumIntegralTypeFixed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralTypeFixed/vb/FxCop.Design.EnumIntegralTypeFixed.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1008: -Enumerationen sollten NULL-Wert aufweisen.](../code-quality/ca1008-enums-should-have-zero-value.md)

 [CA1027: Enumerationen mit FlagsAttribute markieren](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217: Nicht Enumerationen mit FlagsAttribute markieren](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

 [CA1700: Enumerationswerte nicht mit "Reserviert" benennen](../code-quality/ca1700-do-not-name-enum-values-reserved.md)

 [CA1712: Führen Sie keine Präfixe für Enumerationswerte mit Typnamen](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

## <a name="see-also"></a>Siehe auch
 <xref:System.Byte?displayProperty=fullName> <xref:System.Int16?displayProperty=fullName>
 <xref:System.Int32?displayProperty=fullName>
 <xref:System.Int64?displayProperty=fullName>
