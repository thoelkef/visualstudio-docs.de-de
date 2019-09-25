---
title: 'CA1307: StringComparison angeben.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1307
- SpecifyStringComparison
helpviewer_keywords:
- CA1307
- SpecifyStringComparison
ms.assetid: 9b0d5e71-1683-4a0d-bc4a-68b2fbd8af71
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e352eea1b7fcf82cb948315affeae6e30690a4aa
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234971"
---
# <a name="ca1307-specify-stringcomparison"></a>CA1307: StringComparison angeben.

|||
|-|-|
|TypeName|SpecifyStringComparison|
|CheckId|CA1307|
|Kategorie|Microsoft.Globalization|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
Eine Zeichen folgen Vergleichsoperation verwendet eine Methoden Überladung, die keinen <xref:System.StringComparison> Parameter festgelegt hat.

## <a name="rule-description"></a>Regelbeschreibung
Viele Zeichen folgen Operationen, die am <xref:System.String.Compare%2A> wichtigsten <xref:System.String.Equals%2A> die-und-Methoden sind, stellen <xref:System.StringComparison> eine Überladung bereit, die einen-Enumerationswert als Parameter akzeptiert.

Wenn eine Überladung vorhanden ist, <xref:System.StringComparison> die einen-Parameter annimmt, sollte Sie anstelle einer-Überladung verwendet werden, die diesen Parameter nicht annimmt. Wenn Sie diesen Parameter explizit festlegen, wird der Code häufig übersichtlicher und leichter zu verwalten.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Um einen Verstoß gegen diese Regel zu beheben, ändern Sie Zeichen folgen Vergleichsmethoden in über Ladungen <xref:System.StringComparison> , die die-Enumeration als Parameter akzeptieren. Beispiel: ändern `String.Compare(str1, str2)` Sie in `String.Compare(str1, str2, StringComparison.Ordinal)`.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn die Bibliothek oder Anwendung für eine begrenzte lokale Zielgruppe vorgesehen ist und daher nicht lokalisiert wird.

## <a name="see-also"></a>Siehe auch

- [Globalisierungswarnungen](../code-quality/globalization-warnings.md)
- [CA1309: Ordnungszahl-StringComparison verwenden](../code-quality/ca1309-use-ordinal-stringcomparison.md)