---
title: 'CA1700: Enumerationswerte &#39;nicht reserviert benennen&#39;'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1700
- DoNotNameEnumValuesReserved
helpviewer_keywords:
- DoNotNameEnumValuesReserved
- CA1700
ms.assetid: 7a7e01c3-ae7d-4c82-a646-91b58864a749
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5171123827481c99bbc35c10b04aaf942a15fabb
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234387"
---
# <a name="ca1700-do-not-name-enum-values-39reserved39"></a>CA1700: Enumerationswerte &#39;nicht reserviert benennen&#39;

|||
|-|-|
|TypeName|DoNotNameEnumValuesReserved|
|CheckId|CA1700|
|Kategorie|Microsoft.Naming|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache

Der Name eines Enumerationsmembers enthält das Wort "reserved".

## <a name="rule-description"></a>Regelbeschreibung

Bei dieser Regel wird vorausgesetzt, dass Enumerationsmember mit einem Namen, der "reserved" enthält, derzeit nicht verwendet werden, sondern Platzhalter sind, die in einer künftigen Version umbenannt oder entfernt werden sollen. Das Umbenennen oder Entfernen eines Members ist eine unterbrechende Änderung. Sie sollten nicht erwarten, dass Benutzer einen Member ignorieren, weil der Name "reserviert" enthält, und Sie dürfen sich nicht darauf verlassen, dass Benutzer die Dokumentation lesen oder befolgen. Da reservierte Member in Objekt Browsern und intelligenten integrierten Entwicklungsumgebungen angezeigt werden, können Sie darüber hinaus Verwirrung darüber verursachen, welche Member tatsächlich verwendet werden.

Fügen Sie der-Enumeration in der zukünftigen Version einen neuen Member hinzu, anstatt einen reservierten Member zu verwenden. In den meisten Fällen handelt es sich beim Hinzufügen des neuen Members nicht um eine Breaking Change, sofern die Addition nicht bewirkt, dass die Werte der ursprünglichen Member geändert werden.

In einer begrenzten Anzahl von Fällen ist das Hinzufügen eines Members eine Breaking Change, auch wenn die ursprünglichen Member ihre ursprünglichen Werte beibehalten. Vor allem kann der neue Member nicht aus vorhandenen Codepfade zurückgegeben werden, ohne Aufrufer [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]zu unterbrechen, die eine `switch` -Anweisung (`Select` in) für den Rückgabewert verwenden, der die gesamte Elementliste umfasst und eine Ausnahme im Standardfall. Ein sekundäres Problem ist, dass der Client Code die Änderung des Verhaltens von Reflektionsmethoden wie <xref:System.Enum.IsDefined%2A?displayProperty=fullName>nicht behandelt. Wenn das neue Element von vorhandenen Methoden zurückgegeben werden muss oder eine bekannte Anwendungs Inkompatibilität aufgrund einer schlechten Reflektionsverwendung auftritt, besteht die einzige Lösung in folgenden Gründen in folgenden Lösungen:

1. Fügen Sie eine neue-Enumeration hinzu, die die ursprünglichen und neuen Member enthält.

2. Markieren Sie die ursprüngliche Enumeration mit <xref:System.ObsoleteAttribute?displayProperty=fullName> dem-Attribut.

   Befolgen Sie dasselbe Verfahren für alle extern sichtbaren Typen oder Member, die die ursprüngliche Enumeration verfügbar machen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie den Member, oder benennen Sie ihn um.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Es ist sicher, eine Warnung aus dieser Regel für ein Element zu unterdrücken, das derzeit verwendet wird, oder für Bibliotheken, die zuvor ausgeliefert wurden.

## <a name="related-rules"></a>Verwandte Regeln

[CA2217: Auffüge Zeichen nicht mit FlagsAttribute markieren](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

[CA1712: Enumerationswerte nicht mit Typname als Präfix versehen](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

[CA1028: Der Aufzählungs Speicher muss Int32 lauten.](../code-quality/ca1028-enum-storage-should-be-int32.md)

[CA1008: Enumerationswerte sollten NULL-Werte aufweisen.](../code-quality/ca1008-enums-should-have-zero-value.md)

[CA1027: Markierungen mit FlagsAttribute markieren](../code-quality/ca1027-mark-enums-with-flagsattribute.md)