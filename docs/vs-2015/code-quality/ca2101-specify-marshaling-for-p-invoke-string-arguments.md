---
title: 'CA2101: Marshalling für P-Aufruf Zeichen folgen Argumente angeben | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SpecifyMarshalingForPInvokeStringArguments
- CA2101
helpviewer_keywords:
- CA2101
- SpecifyMarshalingForPInvokeStringArguments
ms.assetid: 9d1abfc3-d320-41e0-9f6e-60cefe6ffe1b
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ae65e922d1b4946300155bbf148abac574a2ec2a
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544377"
---
# <a name="ca2101-specify-marshaling-for-pinvoke-string-arguments"></a>CA2101: Marshalling für P/Invoke-Zeichenfolgenargumente festlegen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|SpecifyMarshalingForPInvokeStringArguments|
|CheckId|CA2101|
|Category|Microsoft. Globalization|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein Platt Form Aufruf-Member ermöglicht teilweise vertrauenswürdigen Aufrufern, verfügt über einen Zeichen folgen Parameter und führt die Zeichenfolge nicht explizit aus.

## <a name="rule-description"></a>Beschreibung der Regel
 Wenn Sie von Unicode in ANSI konvertieren, ist es möglich, dass nicht alle Unicode-Zeichen in einer bestimmten ANSI-Codepage dargestellt werden können. Die Zuordnung mit einer *optimalen Anpassung* versucht, dieses Problem zu lösen, indem ein Zeichen für das Zeichen ersetzt wird, das nicht dargestellt werden kann. Die Verwendung dieser Funktion kann ein potenzielles Sicherheitsrisiko darstellen, da Sie das gewählte Zeichen nicht steuern können. Beispielsweise könnte bösartiger Code absichtlich eine Unicode-Zeichenfolge erstellen, die Zeichen enthält, die nicht in einer bestimmten Codepage gefunden werden, die in Sonderzeichen für das Dateisystem konvertiert werden, z. b. "..". oder "/". Beachten Sie auch, dass Sicherheitsüberprüfungen für Sonderzeichen häufig auftreten, bevor die Zeichenfolge in ANSI konvertiert wird.

 Die Zuordnung mit der optimalen Anpassung ist die Standardeinstellung für die nicht verwaltete Konvertierung (WChar zu MB). Wenn Sie die Zuordnung mit der optimalen Anpassung nicht explizit deaktivieren, kann Ihr Code aufgrund dieses Problems ein Sicherheitsrisiko darstellen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, müssen Sie Zeichen folgen Datentypen explizit Mars Hallen.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Methode, die gegen diese Regel verstößt, und zeigt dann, wie Sie die Verletzung beheben.

 [!code-csharp[FxCop.Security.PinvokeAnsiUnicode#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PinvokeAnsiUnicode/cs/FxCop.Security.PinvokeAnsiUnicode.cs#1)]
