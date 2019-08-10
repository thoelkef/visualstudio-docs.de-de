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
ms.openlocfilehash: ce2da2c1ff5b2f74d8b4d6341050c1895b68955a
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922293"
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