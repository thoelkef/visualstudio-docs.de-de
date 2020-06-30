---
title: 'CA1307: StringComparison angeben | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1307
- SpecifyStringComparison
helpviewer_keywords:
- CA1307
- SpecifyStringComparison
ms.assetid: 9b0d5e71-1683-4a0d-bc4a-68b2fbd8af71
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 033d8f0e22ec040ffb10821993a5a9c647ee401e
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85538917"
---
# <a name="ca1307-specify-stringcomparison"></a>CA1307: StringComparison angeben.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|SpecifyStringComparison|
|CheckId|CA1307|
|Category|Microsoft. Globalization|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Eine Zeichen folgen Vergleichsoperation verwendet eine Methoden Überladung, die keinen Parameter festgelegt hat <xref:System.StringComparison> .

## <a name="rule-description"></a>Beschreibung der Regel
 Viele Zeichen folgen Operationen, die am wichtigsten die <xref:System.String.Compare%2A> -und- <xref:System.String.Equals%2A> Methoden sind, stellen eine Überladung bereit, die einen- <xref:System.StringComparison> Enumerationswert als Parameter akzeptiert.

 Wenn eine Überladung vorhanden ist, die einen- <xref:System.StringComparison> Parameter annimmt, sollte Sie anstelle einer-Überladung verwendet werden, die diesen Parameter nicht annimmt. Wenn Sie diesen Parameter explizit festlegen, wird der Code häufig übersichtlicher und leichter zu verwalten.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie Zeichen folgen Vergleichsmethoden in über Ladungen, die die- <xref:System.StringComparison> Enumeration als Parameter akzeptieren. Beispiel: ändern `String.Compare(str1, str2)` Sie in `String.Compare(str1, str2, StringComparison.Ordinal)` .

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn die Bibliothek oder Anwendung für eine begrenzte lokale Zielgruppe vorgesehen ist und daher nicht lokalisiert wird.

## <a name="see-also"></a>Weitere Informationen
 [Globalisierungs Warnungen](../code-quality/globalization-warnings.md) [CA1309: Ordnungszahl-StringComparison verwenden](../code-quality/ca1309-use-ordinal-stringcomparison.md)
