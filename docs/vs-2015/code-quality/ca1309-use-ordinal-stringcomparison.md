---
title: 'CA1309: Ordnungszahl-StringComparison verwenden | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseOrdinalStringComparison
- CA1309
helpviewer_keywords:
- UseOrdinalStringComparison
- CA1309
ms.assetid: 19be0854-cb6e-4efd-a4c8-a5c1fc6f7a71
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 34054f6f444e503077c1e81da9f08ae2832d635a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661430"
---
# <a name="ca1309-use-ordinal-stringcomparison"></a>CA1309: Ordinal-StringComparison verwenden
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseOrdinalStringComparison|
|CheckId|CA1309|
|Kategorie|Microsoft. Globalization|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Bei einer nicht linguistischen Zeichen folgen Vergleichsoperation wird der <xref:System.StringComparison>-Parameter nicht entweder auf **Ordinal** oder **OrdinalIgnoreCase**festgelegt.

## <a name="rule-description"></a>Regelbeschreibung
 Viele Zeichen folgen Operationen, die für die Methoden <xref:System.String.Compare%2A?displayProperty=fullName> und <xref:System.String.Equals%2A?displayProperty=fullName> am wichtigsten sind, bieten jetzt eine Überladung, die einen <xref:System.StringComparison?displayProperty=fullName>-Enumerationswert als Parameter akzeptiert.

 Wenn Sie **StringComparison. Ordinal** oder **StringComparison. OrdinalIgnoreCase**angeben, ist der Zeichen folgen Vergleich nicht linguistisch. Das heißt, die Features, die für die natürliche Sprache spezifisch sind, werden ignoriert, wenn Vergleichs Entscheidungen getroffen werden. Dies bedeutet, dass die Entscheidungen auf einfachen Byte vergleichen basieren und die Groß-/Kleinschreibung oder Äquivalenz Tabellen ignorieren, die nach Kultur parametrisiert werden. Durch das explizite Festlegen des Parameters auf " **StringComparison. Ordinal** " oder " **StringComparison. OrdinalIgnoreCase**" erhöht der Code daher häufig Geschwindigkeit, steigert die Richtigkeit und wird zuverlässiger.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie die Methode für den Zeichen folgen Vergleich in eine Überladung, die die <xref:System.StringComparison?displayProperty=fullName>-Enumeration als Parameter akzeptiert, und geben Sie entweder **Ordinal** oder **OrdinalIgnoreCase**an. Ändern Sie beispielsweise `String.Compare(str1, str2)` zu `String.Compare(str1, str2, StringComparison.Ordinal)`.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn die Bibliothek oder Anwendung für eine begrenzte lokale Zielgruppe bestimmt ist oder wenn die Semantik der aktuellen Kultur verwendet werden soll.

## <a name="see-also"></a>Siehe auch
 [Globalisierungs Warnungen](../code-quality/globalization-warnings.md) [CA1307: StringComparison angeben](../code-quality/ca1307-specify-stringcomparison.md)
