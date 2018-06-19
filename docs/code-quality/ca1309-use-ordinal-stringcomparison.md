---
title: 'CA1309: Ordinal-StringComparison verwenden'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ebea0208beddebb82484297eb990baa9b22c58e8
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31899058"
---
# <a name="ca1309-use-ordinal-stringcomparison"></a>CA1309: Ordinal-StringComparison verwenden
|||
|-|-|
|TypeName|UseOrdinalStringComparison|
|CheckId|CA1309|
|Kategorie|Microsoft.Globalization|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Die durch einen nicht linguistischen Zeichenfolgenvergleich wird nicht festgelegt. die <xref:System.StringComparison> Parameter entweder **Ordnungszahl** oder **OrdinalIgnoreCase**.

## <a name="rule-description"></a>Regelbeschreibung
 Viele Zeichenfolgenoperationen, vor allem die <xref:System.String.Compare%2A?displayProperty=fullName> und <xref:System.String.Equals%2A?displayProperty=fullName> Methoden bieten jetzt eine Überladung, die akzeptiert eine <xref:System.StringComparison?displayProperty=fullName> -Enumerationswert als Parameter.

 Wenn Sie entweder angeben **StringComparison.Ordinal** oder **StringComparison.OrdinalIgnoreCase**, einen nicht linguistischen Zeichenfolgenvergleich werden. D. h. werden die Funktionen, die spezifisch für natürliche Sprache sind beim Vergleich Entscheidungen getroffen werden ignoriert. Dies bedeutet, dass die Entscheidungen basieren auf einfache bytevergleiche und ignorieren die Groß-/Kleinschreibung oder Äquivalenz Tabellen, die nach Kultur parametrisierten entsprechungstabellen. Daher durch explizites Festlegen des Parameters auf entweder dem **StringComparison.Ordinal** oder **StringComparison.OrdinalIgnoreCase**, des Codes häufig Geschwindigkeit erlangt, erhöht die Richtigkeit, und wird zuverlässiger.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie die Methode zum Zeichenfolgenvergleich an eine Überladung, die akzeptiert die <xref:System.StringComparison?displayProperty=fullName> -Enumeration als Parameter, und geben Sie entweder **Ordnungszahl** oder **OrdinalIgnoreCase**. Ändern Sie beispielsweise `String.Compare(str1, str2)` zu `String.Compare(str1, str2, StringComparison.Ordinal)`.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Sie können ruhig auf eine Warnung dieser Regel zu unterdrücken, wenn die Bibliothek oder Anwendung vorgesehen ist, für eine begrenzte lokale Zielgruppe oder wenn die Semantik der aktuellen Kultur verwendet werden soll.

## <a name="see-also"></a>Siehe auch
 [Globalisierungswarnungen](../code-quality/globalization-warnings.md) [CA1307: StringComparison angeben](../code-quality/ca1307-specify-stringcomparison.md)