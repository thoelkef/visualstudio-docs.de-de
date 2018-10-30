---
title: 'CA1027: Enumerationen mit FlagsAttribute markieren | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- MarkEnumsWithFlags
- CA1027
helpviewer_keywords:
- CA1027
- MarkEnumsWithFlags
ms.assetid: 249e882c-8cd1-4c00-a2de-7b6bdc1849ff
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b8cebc05fa58c589f07beed70ab222d31bc8553a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49879219"
---
# <a name="ca1027-mark-enums-with-flagsattribute"></a>CA1027: Enumerationen mit FlagsAttribute markieren
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkEnumsWithFlags|
|CheckId|CA1027|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Die Werte der eine öffentliche Enumeration sind Potenzen von 2 oder Kombinationen von anderen Werten, die in der Enumeration definiert sind und die <xref:System.FlagsAttribute?displayProperty=fullName> Attribut ist nicht vorhanden. Um falsch positive Ergebnisse zu reduzieren, meldet diese Regel keinen Verstoß für Enumerationen, die aufeinander folgender Werte aufweisen.

## <a name="rule-description"></a>Regelbeschreibung
 Eine Enumeration ist ein Werttyp, der einen Satz verwandter benannter Konstanten definiert. Anwenden <xref:System.FlagsAttribute> auf eine Enumeration, wenn deren benannten Konstanten sinnvoll kombiniert werden können. Betrachten Sie beispielsweise eine Enumeration der Tage der Woche in einer Anwendung, die überwacht die Tag-Ressourcen verfügbar sind. Wenn die Verfügbarkeit der einzelnen Ressourcen codiert ist, mit der Enumeration, die <xref:System.FlagsAttribute> vorhanden, eine beliebige Kombination von Tagen dargestellt werden kann. Ohne das Attribut kann nur ein Tag der Woche dargestellt werden.

 Für Felder, die mit den flexibel kombinierbaren Enumerationen zu speichern, werden die einzelnen Enumerationswerte als Gruppen von Bits in das Feld behandelt. Aus diesem Grund diese Felder werden manchmal als bezeichnet *Bitfelder*. Enumerationswerte für die Speicherung in einem Bitfeld zu kombinieren, verwenden Sie die boolesche bedingten Operatoren. Verwenden Sie die booleschen logischen Operatoren, zum Testen ein Bitfeld, um festzustellen, ob ein bestimmtes Enumerationswert vorhanden ist. Für ein Bitfeld zum Speichern und Abrufen von kombinierten Enumerationswerte ordnungsgemäß muss jeder Wert, der in der Enumeration definiert ist, eine Potenz von zwei sein. Wenn dies der Fall ist, werden die booleschen logischen Operatoren nicht extrahieren, die einzelnen Enumerationswerte, die in das Feld gespeichert werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, fügen <xref:System.FlagsAttribute> der Enumeration.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie eine Warnung dieser Regel, wenn Sie nicht, dass die Enumerationswerte kombinierbar sein möchten.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel `DaysEnumNeedsFlags` ist eine Enumeration, die erfüllt die Anforderungen für die Verwendung von <xref:System.FlagsAttribute>, aber nicht vorhanden. Die `ColorEnumShouldNotHaveFlag` Enumeration keine Werte, die Potenzen von 2 sind, aber falsch gibt <xref:System.FlagsAttribute>. Dies verstößt gegen die Regel [CA2217: Enumerationen mit FlagsAttribute nicht markieren](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md).

 [!code-csharp[FxCop.Design.EnumFlags#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumFlags/cs/FxCop.Design.EnumFlags.cs#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA2217: Enumerationen nicht mit FlagsAttribute markieren](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Siehe auch
 <xref:System.FlagsAttribute?displayProperty=fullName>



