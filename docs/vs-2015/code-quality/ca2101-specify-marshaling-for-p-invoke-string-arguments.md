---
title: ': Ca2101 Marshalling für P / Invoke-Zeichenfolgenargumente | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SpecifyMarshalingForPInvokeStringArguments
- CA2101
helpviewer_keywords:
- CA2101
- SpecifyMarshalingForPInvokeStringArguments
ms.assetid: 9d1abfc3-d320-41e0-9f6e-60cefe6ffe1b
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2ff14e50af33b5b779244109916c91abff2663c3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49238681"
---
# <a name="ca2101-specify-marshaling-for-pinvoke-string-arguments"></a>CA2101: Marshalling für P/Invoke-Zeichenfolgenargumente festlegen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
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

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Methode, die gegen diese Regel verstößt, und anschließend wird der Verstoß zu beheben.

 [!code-csharp[FxCop.Security.PinvokeAnsiUnicode#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PinvokeAnsiUnicode/cs/FxCop.Security.PinvokeAnsiUnicode.cs#1)]



