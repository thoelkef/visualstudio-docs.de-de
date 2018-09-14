---
title: 'CA1307: StringComparison angeben'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 67f0d5152dcdef5ffa3abb76d92e68fd99f9b637
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/13/2018
ms.locfileid: "45550413"
---
# <a name="ca1307-specify-stringcomparison"></a>CA1307: StringComparison angeben

|||
|-|-|
|TypeName|SpecifyStringComparison|
|CheckId|CA1307|
|Kategorie|Microsoft.Globalization|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein Zeichenfolgenvergleich verwendet eine methodenüberladung, die nicht festgelegt ist eine <xref:System.StringComparison> Parameter.

## <a name="rule-description"></a>Regelbeschreibung
 Viele Zeichenfolgenoperationen, vor allem die <xref:System.String.Compare%2A> und <xref:System.String.Equals%2A> Methoden, stellen Sie eine Überladung, die akzeptiert eine <xref:System.StringComparison> Enumerationswert als Parameter.

 Jedes Mal, wenn eine Überladung vorhanden ist, wird eine <xref:System.StringComparison> Parameter, und sollte verwendet werden, anstatt eine Überladung, die dieser Parameter nicht akzeptiert. Durch diesen Parameter explizit festlegen, ist der Code häufig verständlicher und einfacher zu verwalten.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie Methoden zum Zeichenfolgenvergleich für Überladungen, die akzeptieren die <xref:System.StringComparison> -Enumeration als Parameter. Zum Beispiel: Ändern Sie `String.Compare(str1, str2)` zu `String.Compare(str1, str2, StringComparison.Ordinal)`.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Es ist sicher, unterdrücken Sie eine Warnung dieser Regel aus, wenn die Bibliothek oder Anwendung für eine begrenzte lokale Zielgruppe vorgesehen ist und daher nicht lokalisiert werden wird.

## <a name="see-also"></a>Siehe auch

- [Globalisierungswarnungen](../code-quality/globalization-warnings.md)
- [CA1309: Ordinal-StringComparison verwenden](../code-quality/ca1309-use-ordinal-stringcomparison.md)