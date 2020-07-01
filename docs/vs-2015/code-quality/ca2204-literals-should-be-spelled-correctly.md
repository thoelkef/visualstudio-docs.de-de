---
title: 'CA2204: Literale sollten korrekt geschrieben werden | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- Literals should be spelled correctly
- CA2204
- LiteralsShouldBeSpelledCorrectly
helpviewer_keywords:
- CA2204
ms.assetid: b0bbcbb6-c92d-4c14-8ef7-9c8b38c791a6
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ecf829251cbeab600cb95f8f0c0b0173cd7338d4
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546275"
---
# <a name="ca2204-literals-should-be-spelled-correctly"></a>CA2204: Literale sollten eine korrekte Rechtschreibung aufweisen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|Literalsdbespelledrichtig|
|CheckId|CA2204|
|Category|Microsoft. Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Eine Methode übergibt eine Literalzeichenfolge an, die in einem Parameter oder einer Eigenschaft verwendet wird, für die eine lokalisierte Zeichenfolge erforderlich ist, und die Literalzeichenfolge enthält mindestens ein Wort, das von der Bibliothek der Microsoft-Rechtschreibprüfung

## <a name="rule-description"></a>Beschreibung der Regel
 Diese Regel überprüft eine Literalzeichenfolge, die als Wert an einen Parameter oder eine Eigenschaft übergeben wird, wenn mindestens einer der folgenden Fälle zutrifft:

- Das- <xref:System.ComponentModel.LocalizableAttribute> Attribut des-Parameters oder der-Eigenschaft ist auf true festgelegt.

- Der Parameter-oder Eigenschaftsname enthält "Text", "Message" oder "Caption".

- Der Name des Zeichen folgen Parameters, der an eine Console. Write-oder Console. Write teline-Methode übergeben wird, ist entweder "Value" oder "Format".

  Diese Regel analysiert die Literalzeichenfolge in Wörter, fasst zusammengesetzte Wörter um und überprüft die Schreibweise der einzelnen Wörter/Token. Weitere Informationen zum Algorithmus für die Verarbeitung finden Sie unter [CA1704: Bezeichner sollten korrekt geschrieben werden](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

  Standardmäßig wird die englische Version (en) der Rechtschreibprüfung verwendet.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, korrigieren Sie die Schreibweise des Worts, oder fügen Sie das Wort einem benutzerdefinierten Wörterbuch hinzu. Weitere Informationen zum Verwenden von benutzerdefinierten Wörterbüchern finden Sie unter Gewusst [wie: Anpassen des Code Analyse Wörterbuchs](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel. Korrekt geschriebene Wörter reduzieren die für neue Software Bibliotheken erforderliche Lernkurve.

## <a name="related-rules"></a>Verwandte Regeln
 [CA1704: Bezeichner sollten korrekt geschrieben werden.](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

 [CA1703: Ressourcenzeichenfolgen sollten korrekt geschrieben werden.](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)
