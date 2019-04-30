---
title: 'CA2101: Marshalling für P/Invoke-Zeichenfolgenargumente festlegen.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SpecifyMarshalingForPInvokeStringArguments
- CA2101
helpviewer_keywords:
- CA2101
- SpecifyMarshalingForPInvokeStringArguments
ms.assetid: 9d1abfc3-d320-41e0-9f6e-60cefe6ffe1b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 622097e4dd1408c46863098a8f29fe6666b64b2a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62808275"
---
# <a name="ca2101-specify-marshaling-for-pinvoke-string-arguments"></a>CA2101: Marshalling für P/Invoke-Zeichenfolgenargumente festlegen.

|||
|-|-|
|TypeName|SpecifyMarshalingForPInvokeStringArguments|
|CheckId|CA2101|
|Kategorie|Microsoft.Globalization|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Einen Plattformaufruf Plattformaufrufmember lässt teilweise vertrauenswürdige Aufrufer enthält einen Zeichenfolgenparameter und führt kein explizites Marshalling die Zeichenfolge.

## <a name="rule-description"></a>Regelbeschreibung
 Wenn Sie von Unicode in ANSI konvertieren, ist es möglich, dass nicht alle Unicode-Zeichen in einer bestimmten ANSI-Codepage dargestellt werden können. *Zuordnung mit ähnlichen Zeichen* versucht, dieses Problem zu beheben, ersetzen Sie ein Zeichen für das Zeichen, das nicht dargestellt werden kann. Die Verwendung dieses Features kann ein potenzielles Sicherheitsrisiko führen, da Sie nicht das Zeichen steuern können, das ausgewählt wird. Beispielsweise könnte bösartiger Code absichtlich eine Unicodezeichenfolge mit Zeichen, die in einer bestimmten Codepage nicht gefunden werden die speziellen Zeichen, z. B. konvertiert werden erstellen '..' oder "/". Beachten Sie, dass die sicherheitsüberprüfungen für Sonderzeichen häufig auftreten, bevor die Zeichenfolge in ANSI konvertiert wird.

 Zuordnung mit ähnlichen Zeichen ist die Standardeinstellung für den nicht verwalteten Konvertierung von WChar in MB an. Es sei denn, Sie explizit die Zuordnung mit ähnlichen Zeichen deaktivieren, kann Ihr Code einen ausnutzbaren Sicherheitsrisiko aufgrund dieses Problems enthalten.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, müssen Marshallen Sie explizit Zeichenfolgen-Datentypen.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Methode, die gegen diese Regel verstößt, und anschließend wird der Verstoß zu beheben.

 [!code-csharp[FxCop.Security.PinvokeAnsiUnicode#1](../code-quality/codesnippet/CSharp/ca2101-specify-marshaling-for-p-invoke-string-arguments_1.cs)]