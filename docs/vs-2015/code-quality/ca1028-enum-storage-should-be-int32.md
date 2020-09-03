---
title: 'CA1028: der Aufzählungs Speicher sollte Int32 lauten | Microsoft-Dokumentation'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0b2e8ebcc7720f5cd9dc6c700bcc08b68f89e275
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85542492"
---
# <a name="ca1028-enum-storage-should-be-int32"></a>CA1028: Der Enumerationsspeicher sollte Int32 sein.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|value|
|-|-|
|TypName|EnumStorageShouldBeInt32|
|CheckId|CA1028|
|Category|Microsoft. Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Der zugrunde liegende Typ einer öffentlichen Enumeration ist nicht <xref:System.Int32?displayProperty=fullName> .

## <a name="rule-description"></a>Beschreibung der Regel
 Eine Enumeration ist ein Werttyp, der einen Satz verwandter benannter Konstanten definiert. Standardmäßig wird der- <xref:System.Int32?displayProperty=fullName> Datentyp verwendet, um den konstanten Wert zu speichern. Obwohl Sie diesen zugrunde liegenden Typ ändern können, ist es für die meisten Szenarien nicht notwendig oder empfehlenswert. Beachten Sie, dass kein erheblicher Leistungsgewinn erreicht wird, indem ein-Datentyp verwendet wird, der kleiner als ist <xref:System.Int32> . Wenn Sie den Standard Datentyp nicht verwenden können, sollten Sie einen der CLS-kompatiblen ganzzahligen Typen (Common Language System),,, oder verwenden, <xref:System.Byte> <xref:System.Int16> <xref:System.Int32> <xref:System.Int64> um sicherzustellen, dass alle Werte der-Enumeration in CLS-kompatiblen Programmiersprachen dargestellt werden können.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Verwenden Sie, um einen Verstoß gegen diese Regel zu beheben, sofern keine Größen-oder Kompatibilitätsprobleme vorhanden sind <xref:System.Int32> . Verwenden Sie für Situationen, in denen <xref:System.Int32> nicht groß genug ist, um die Werte zu speichern <xref:System.Int64> . Wenn die Abwärtskompatibilität einen kleineren Datentyp erfordert, verwenden Sie <xref:System.Byte> oder <xref:System.Int16> .

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrückt eine Warnung aus dieser Regel nur, wenn dies bei Problemen mit der Abwärtskompatibilität erforderlich ist. In-Anwendungen verursacht die fehlgeschlagene Einhaltung dieser Regel keine Probleme. In Bibliotheken, bei denen die sprach Interoperabilität erforderlich ist, kann sich die Einhaltung dieser Regel nicht negativ auf die Benutzer auswirken.

## <a name="example-of-a-violation"></a>Beispiel für eine Verletzung

### <a name="description"></a>BESCHREIBUNG
 Das folgende Beispiel zeigt zwei Enumerationen, die den empfohlenen zugrunde liegenden Datentyp nicht verwenden.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Design.EnumIntegralType#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralType/cs/FxCop.Design.EnumIntegralType.cs#1)]
 [!code-vb[FxCop.Design.EnumIntegralType#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralType/vb/FxCop.Design.EnumIntegralType.vb#1)]

## <a name="example-of-how-to-fix"></a>Beispiel für das Beheben von

### <a name="description"></a>BESCHREIBUNG
 Im folgenden Beispiel wird der vorherige Verstoß korrigiert, indem der zugrunde liegende-Datentyp in geändert wird <xref:System.Int32> .

### <a name="code"></a>Code
 [!code-csharp[FxCop.Design.EnumIntegralTypeFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralTypeFixed/cs/FxCop.Design.EnumIntegralTypeFixed.cs#1)]
 [!code-vb[FxCop.Design.EnumIntegralTypeFixed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralTypeFixed/vb/FxCop.Design.EnumIntegralTypeFixed.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1008: Enumerationen müssen einen Wert von 0 (null) aufweisen.](../code-quality/ca1008-enums-should-have-zero-value.md)

 [CA1027: Enumerationen mit FlagsAttribute markieren.](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217: Enumerationen nicht mit FlagsAttribute markieren.](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

 [CA1700: Enumerationswerte nicht mit "Reserviert" benennen.](../code-quality/ca1700-do-not-name-enum-values-reserved.md)

 [CA1712: Keine Typnamen als Präfixe für Enumerationswerte verwenden.](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

## <a name="see-also"></a>Weitere Informationen
 <xref:System.Byte?displayProperty=fullName> <xref:System.Int16?displayProperty=fullName>
 <xref:System.Int32?displayProperty=fullName>
 <xref:System.Int64?displayProperty=fullName>
