---
title: 'CA1008: Enumerationswerte sollten einen Wert von NULL aufweisen. Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1008
- EnumsShouldHaveZeroValue
helpviewer_keywords:
- CA1008
- EnumsShouldHaveZeroValue
ms.assetid: 3503a73c-360c-416d-8ee4-c2aa44365a05
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: fbc7775d4ec41822b866868a6db6bceb353af989
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668932"
---
# <a name="ca1008-enums-should-have-zero-value"></a>CA1008: Enumerationen müssen einen Wert von 0 (null) aufweisen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|EnumsShouldHaveZeroValue|
|CheckId|CA1008|
|Kategorie|Microsoft. Design|
|Unterbrechende Änderung|Nicht unterbrechend: Wenn Sie aufgefordert werden, einen " **None** "-Wert zu einer nicht-Flag-Enumeration hinzuzufügen. Unterbrechen: Wenn Sie aufgefordert werden, Enumerationswerte umzubenennen oder zu entfernen.|

## <a name="cause"></a>Ursache
 Eine Enumeration ohne angewendete <xref:System.FlagsAttribute?displayProperty=fullName> definiert keinen Member, der den Wert 0 (null) aufweist. oder eine Enumeration, die über einen angewendeten <xref:System.FlagsAttribute> definiert einen Member, der den Wert 0 (null) aufweist, aber sein Name nicht ' none ' ist, oder die Enumeration definiert mehrere Member mit 0 (null).

## <a name="rule-description"></a>Regelbeschreibung
 Der Standardwert einer nicht initialisierten Enumeration, ebenso wie andere Werttypen, ist 0 (null). Eine nicht auf Flags festgeschriebene Enumeration sollte einen Member mit dem Wert 0 (null) definieren, sodass der Standardwert ein gültiger Wert der-Enumeration ist. Wenn erforderlich, benennen Sie den Member "None". Andernfalls sollten Sie dem am häufigsten verwendeten Member NULL zuweisen. Beachten Sie, dass der Wert des ersten Enumerationsmembers standardmäßig NULL ist, wenn der Wert des ersten Enumerationsmembers nicht in der Deklaration festgelegt ist.

 Wenn eine Enumeration mit dem <xref:System.FlagsAttribute> einen Member mit 0 (null) aufweist, muss der Name "None" lauten, um anzugeben, dass keine Werte in der Enumeration festgelegt wurden. Die Verwendung eines Elements mit einem Wert von 0 (null) für andere Zwecke steht im Gegensatz zur Verwendung des <xref:System.FlagsAttribute>, da die-und-und-oder bitweisen Operatoren für den Member nutzlos sind. Dies impliziert, dass nur einem Member der Wert 0 (null) zugewiesen werden soll. Beachten Sie Folgendes: Wenn mehrere Member, die den Wert 0 aufweisen, in einer durch Flags attributierten Enumeration auftreten, gibt `Enum.ToString()` falsche Ergebnisse für Member zurück, die nicht NULL sind.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel für nicht-Flags-attributierte Enumerationen zu beheben, definieren Sie einen Member, der den Wert 0 (null) aufweist. Dabei handelt es sich um einen nicht Breaking Change. Für Flags-attributierte Enumerationen, die einen Null-wertigen Member definieren, benennen Sie den Member "None", und löschen Sie alle anderen Member, die den Wert 0 (null) aufweisen. Dies ist eine Breaking Change.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel, außer bei von Flags attributierten Enumerationen, die zuvor ausgeliefert wurden.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt zwei Enumerationen, die die Regel erfüllen, und eine Enumeration, `BadTraceOptions`, die gegen die Regel verstößt.

 [!code-cpp[FxCop.Design.EnumsZeroValue#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumsZeroValue/cpp/FxCop.Design.EnumsZeroValue.cpp#1)]
 [!code-csharp[FxCop.Design.EnumsZeroValue#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumsZeroValue/cs/FxCop.Design.EnumsZeroValue.cs#1)]
 [!code-vb[FxCop.Design.EnumsZeroValue#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EnumsZeroValue/vb/FxCop.Design.EnumsZeroValue.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA2217: Enumerationen nicht mit FlagsAttribute markieren](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

 [CA1700: Enumerationswerte nicht mit "Reserviert" benennen](../code-quality/ca1700-do-not-name-enum-values-reserved.md)

 [CA1712: Keine Typnamen als Präfixe für Enumerationswerte verwenden](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

 [CA1028: Der Enumerationsspeicher sollte Int32 sein.](../code-quality/ca1028-enum-storage-should-be-int32.md)

 [CA1027: Enumerationen mit FlagsAttribute markieren](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Siehe auch
 <xref:System.Enum?displayProperty=fullName>
