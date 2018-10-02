---
title: 'CA1307: StringComparison angeben | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1307
- SpecifyStringComparison
helpviewer_keywords:
- CA1307
- SpecifyStringComparison
ms.assetid: 9b0d5e71-1683-4a0d-bc4a-68b2fbd8af71
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2c96b8c895106337a8578b6662c0e61830b38f55
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589991"
---
# <a name="ca1307-specify-stringcomparison"></a>CA1307: StringComparison angeben
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [CA1307: StringComparison angeben](https://docs.microsoft.com/visualstudio/code-quality/ca1307-specify-stringcomparison).

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

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, unterdrücken Sie eine Warnung dieser Regel aus, wenn die Bibliothek oder Anwendung für eine begrenzte lokale Zielgruppe vorgesehen ist und daher nicht lokalisiert werden wird.

## <a name="see-also"></a>Siehe auch
 [Globalisierungswarnungen](../code-quality/globalization-warnings.md) [CA1309: ordinal-StringComparison verwenden](../code-quality/ca1309-use-ordinal-stringcomparison.md)



