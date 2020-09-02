---
title: 'CA1027: Attribute mit FlagsAttribute markieren | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkEnumsWithFlags
- CA1027
helpviewer_keywords:
- CA1027
- MarkEnumsWithFlags
ms.assetid: 249e882c-8cd1-4c00-a2de-7b6bdc1849ff
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 774279dd05bd14c34df7f1d450f00599812d6a5b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544507"
---
# <a name="ca1027-mark-enums-with-flagsattribute"></a>CA1027: Enumerationen mit FlagsAttribute markieren.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|value|
|-|-|
|TypName|MarkEnumsWithFlags|
|CheckId|CA1027|
|Category|Microsoft. Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Die Werte einer öffentlichen Enumeration sind zwei oder Kombinationen aus anderen Werten, die in der-Enumeration definiert sind, und das- <xref:System.FlagsAttribute?displayProperty=fullName> Attribut ist nicht vorhanden. Um falsch positive Ergebnisse zu reduzieren, meldet diese Regel keinen Verstoß gegen Enumerationen, die zusammenhängende Werte aufweisen.

## <a name="rule-description"></a>Beschreibung der Regel
 Eine Enumeration ist ein Werttyp, der einen Satz verwandter benannter Konstanten definiert. Gilt <xref:System.FlagsAttribute> für eine Enumeration, wenn deren benannte Konstanten sinnvoll kombiniert werden können. Stellen Sie sich z. b. eine Enumeration der Wochentage in einer Anwendung vor, die nachverfolgen, welche Tages Ressourcen verfügbar sind. Wenn die Verfügbarkeit der einzelnen Ressourcen mithilfe der-Enumeration, die vorhanden ist, codiert ist <xref:System.FlagsAttribute> , kann eine beliebige Kombination von Tagen dargestellt werden. Ohne das-Attribut kann nur ein Wochentag dargestellt werden.

 Für Felder, die kombinierbare Enumerationen speichern, werden die einzelnen Enumerationswerte als Gruppen von Bits im Feld behandelt. Daher werden solche Felder manchmal auch als *Bitfelder*bezeichnet. Verwenden Sie zum Kombinieren von Enumerationswerten für den Speicher in einem Bitfeld die booleschen bedingten Operatoren. Um ein Bitfeld zu testen, um zu bestimmen, ob ein bestimmter Enumerationswert vorhanden ist, verwenden Sie die logischen booleschen Operatoren. Damit ein Bitfeld kombinierte Enumerationswerte ordnungsgemäß speichert und abruft, muss jeder in der-Enumeration definierte Wert eine Potenz von zwei sein. Sofern dies nicht der Fall ist, können die logischen booleschen Operatoren die einzelnen Enumerationswerte, die im Feld gespeichert sind, nicht extrahieren.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, fügen Sie <xref:System.FlagsAttribute> der-Enumeration hinzu.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie eine Warnung aus dieser Regel, wenn Sie nicht möchten, dass die Enumerationswerte kombinierbar sind.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel `DaysEnumNeedsFlags` ist eine Enumeration, die die Anforderungen für die Verwendung von erfüllt <xref:System.FlagsAttribute> , jedoch nicht. Die- `ColorEnumShouldNotHaveFlag` Enumeration weist keine Werte auf, die zwei Werte sind, aber falsch angeben <xref:System.FlagsAttribute> . Dies verstößt gegen Regel [CA2217: Markieren Sie keine Enumerationen mit FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md).

 [!code-csharp[FxCop.Design.EnumFlags#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumFlags/cs/FxCop.Design.EnumFlags.cs#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA2217: Enumerationen nicht mit FlagsAttribute markieren.](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Weitere Informationen
 <xref:System.FlagsAttribute?displayProperty=fullName>
