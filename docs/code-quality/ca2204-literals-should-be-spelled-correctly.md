---
title: 'CA2204: Literale sollten eine korrekte Rechtschreibung aufweisen'
ms.date: 03/28/2018
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- Literals should be spelled correctly
- CA2204
- LiteralsShouldBeSpelledCorrectly
helpviewer_keywords:
- CA2204
ms.assetid: b0bbcbb6-c92d-4c14-8ef7-9c8b38c791a6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e23ab1c1c245a03e88b05fb15259193bb508b69a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53944310"
---
# <a name="ca2204-literals-should-be-spelled-correctly"></a>CA2204: Literale sollten eine korrekte Rechtschreibung aufweisen

|||
|-|-|
|TypeName|LiteralsShouldBeSpelledCorrectly|
|CheckId|CA2204|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache

Eine Literalzeichenfolge als Argument für einen lokalisierbaren Parameter oder einer lokalisierbaren Eigenschaft übergeben wird, und die Zeichenfolge enthält eine oder mehrere Wörter, die von der Rechtschreibprüfung aus der Microsoft-Bibliothek nicht erkannt werden.

## <a name="rule-description"></a>Regelbeschreibung

Diese Regel prüft eine Literalzeichenfolge, die als Wert übergeben wird, auf einen Parameter oder eine Eigenschaft, wenn eine oder mehrere der folgenden Fälle zutreffen:

- Die <xref:System.ComponentModel.LocalizableAttribute> Attribut des Parameters oder der Eigenschaft wird festgelegt auf "true".

- Der Parameter oder die Eigenschaft Name enthält "Text", "Message" oder "Beschriftung".

- Der Name des String-Variable, die an eine <xref:System.Console.Write%2A> oder <xref:System.Console.WriteLine> Methode ist "Value" oder "format".

Diese Regel analysiert die Literalzeichenfolge in Wörter, die mit Token versehen zusammengesetzte Wörter und überprüft die Rechtschreibung jedes Wort oder Token. Informationen zu den Analysealgorithmus, finden Sie unter [CA1704: Bezeichner sollten korrekt geschrieben werden](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

## <a name="language"></a>Sprache

Die Rechtschreibprüfung überprüft, zurzeit nur für die Kultur auf Englisch basierenden Wörterbücher. Sie können die Kultur des Projekts in der Projektdatei ändern, durch das Hinzufügen der **CodeAnalysisCulture** Element.

Zum Beispiel:

```xml
<Project ...>
  <PropertyGroup>
    <CodeAnalysisCulture>en-AU</CodeAnalysisCulture>
```

> [!IMPORTANT]
> Wenn Sie die Kultur auf etwas anderes als eine Kultur auf Englisch basierenden festlegen, ist diese Codeanalyse-Regelsätze im Hintergrund deaktiviert.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, korrigieren Sie die Schreibweise des Worts, oder fügen Sie es zu einem Benutzerwörterbuch. Weitere Informationen zur Verwendung von benutzerdefinierten Wörterbüchern finden Sie unter [Vorgehensweise: Anpassen des Codeanalysewörterbuchs](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Unterdrücken Sie keine Warnung dieser Regel. Ordnungsgemäß zu geschriebene Wörter der Lernaufwand für neue Softwarebibliotheken reduzieren.

## <a name="related-rules"></a>Verwandte Regeln

- [CA1704: Bezeichner sollten korrekt geschrieben werden](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)
- [CA1703: Ressourcenzeichenfolgen sollten korrekt geschrieben werden](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)