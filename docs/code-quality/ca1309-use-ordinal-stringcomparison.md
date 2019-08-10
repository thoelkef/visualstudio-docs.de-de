---
title: 'CA1309: Ordinal-StringComparison verwenden.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- UseOrdinalStringComparison
- CA1309
helpviewer_keywords:
- UseOrdinalStringComparison
- CA1309
ms.assetid: 19be0854-cb6e-4efd-a4c8-a5c1fc6f7a71
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2c528266c54bbb2f3f0d9420461d700a46b09bd5
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922286"
---
# <a name="ca1309-use-ordinal-stringcomparison"></a>CA1309: Ordinal-StringComparison verwenden.

|||
|-|-|
|TypeName|UseOrdinalStringComparison|
|CheckId|CA1309|
|Kategorie|Microsoft.Globalization|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Bei einer nicht linguistischen Zeichen folgen Vergleichsoperation wird der <xref:System.StringComparison> -Parameter nicht auf **Ordinal** oder **OrdinalIgnoreCase**festgelegt.

## <a name="rule-description"></a>Regelbeschreibung
Viele Zeichen folgen Operationen, vor allem <xref:System.String.Compare%2A?displayProperty=fullName> die <xref:System.String.Equals%2A?displayProperty=fullName> -Methode und die-Methode, bieten nun <xref:System.StringComparison?displayProperty=fullName> eine Überladung, die einen-Enumerationswert als Parameter akzeptiert.

Wenn Sie **StringComparison. Ordinal** oder **StringComparison. OrdinalIgnoreCase**angeben, ist der Zeichen folgen Vergleich nicht linguistisch. Das heißt, die Features, die für die natürliche Sprache spezifisch sind, werden ignoriert, wenn Vergleichs Entscheidungen getroffen werden. Das Ignorieren von Features in natürlicher Sprache bedeutet, dass die Entscheidungen auf einfachen Byte vergleichen und nicht auf Groß-/Kleinschreibung oder Äquivalenz Tabellen basieren, die nach Kultur parametrisiert werden. Durch das explizite Festlegen des Parameters auf " **StringComparison. Ordinal** " oder " **StringComparison. OrdinalIgnoreCase**" erhöht der Code daher häufig Geschwindigkeit, steigert die Richtigkeit und wird zuverlässiger.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Um einen Verstoß gegen diese Regel zu beheben, ändern Sie die Methode für den Zeichen folgen Vergleich in <xref:System.StringComparison?displayProperty=fullName> eine Überladung, die die Enumeration als Parameter akzeptiert, und geben Sie entweder **Ordinal** oder **OrdinalIgnoreCase**an. Ändern Sie beispielsweise `String.Compare(str1, str2)` zu `String.Compare(str1, str2, StringComparison.Ordinal)`.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn die Bibliothek oder Anwendung für eine begrenzte lokale Zielgruppe bestimmt ist oder wenn die Semantik der aktuellen Kultur verwendet werden soll.

## <a name="see-also"></a>Siehe auch

- [Globalisierungswarnungen](../code-quality/globalization-warnings.md)
- [CA1307: StringComparison angeben](../code-quality/ca1307-specify-stringcomparison.md)