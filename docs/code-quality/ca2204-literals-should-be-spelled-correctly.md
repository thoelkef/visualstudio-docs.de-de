---
title: 'CA2204: Literale sollten korrekt geschrieben werden | Microsoft Docs'
ms.date: 03/28/2018
ms.technology: vs-ide-code-analysis
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
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: cdfee3a45035de83037122942144e154db35bd3b
ms.sourcegitcommit: efd8c8e0a9ba515d47efcc7bd370eaaf4771b5bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/03/2018
---
# <a name="ca2204-literals-should-be-spelled-correctly"></a>CA2204: Literale sollten eine korrekte Rechtschreibung aufweisen

|||
|-|-|
|TypeName|LiteralsShouldBeSpelledCorrectly|
|CheckId|CA2204|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache

Eine literale Zeichenfolge als Argument für eine lokalisierbare Parameter oder einer lokalisierbaren Eigenschaft übergeben wird, und die Zeichenfolge enthält mindestens ein Wort, die von der Rechtschreibprüfung aus der Microsoft-Bibliothek nicht erkannt werden.

## <a name="rule-description"></a>Regelbeschreibung

Diese Regel wird überprüft, ob eine literale Zeichenfolge, die als Wert übergeben wird, um einen Parameter oder eine Eigenschaft, wenn Sie eine oder mehrere der folgenden Fälle zutrifft:

- Die <xref:System.ComponentModel.LocalizableAttribute> Attribut des Parameters oder der Eigenschaft ist festgelegt auf "true".

- Der Parameter oder die Eigenschaft Name enthält "Text", "Message" oder "Caption".

- Der Name der Zeichenfolgenvariablen, die an eine <xref:System.Console.Write%2A> oder <xref:System.Console.WriteLine> Methode ist "Value" oder "format".

Diese Regel analysiert das Zeichenfolgenliteral in Wörter, versehen zusammengesetzte Wörter und die Schreibweise der jedes Wort oder ein Token überprüft. Informationen zum Analysieren Algorithmus finden Sie unter [CA1704: Bezeichner sollten korrekt geschrieben werden](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

## <a name="language"></a>Sprache

Die Rechtschreibprüfung wird derzeit nur für die Kultur Englisch-basierte Wörterbücher überprüft. Sie können die Kultur des Projekts in der Projektdatei ändern, indem die **CodeAnalysisCulture** Element.

Zum Beispiel:

```xml
<Project ...>
  <PropertyGroup>
    <CodeAnalysisCulture>en-AU</CodeAnalysisCulture>
```

> [!IMPORTANT]
> Wenn Sie die Kultur auf etwas anderes als eine Kultur Englisch-basierte festlegen, wird diese Regel zur Codeanalyse im Hintergrund deaktiviert.

## <a name="how-to-fix-violations"></a>Behandlung von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, korrigieren Sie die Schreibweise des Worts oder eines Benutzerwörterbuchs fügen Sie das Wort hinzu. Informationen zur Verwendung von benutzerdefinierten Wörterbüchern finden Sie unter [wie: Anpassen des Codeanalysewörterbuchs](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

## <a name="when-to-suppress-warnings"></a>Wenn Warnungen unterdrücken

Unterdrücken Sie keine Warnung dieser Regel. Geschriebene Wörter verringert der Lernaufwand für neue Softwarebibliotheken.

## <a name="related-rules"></a>Verwandte Regeln

- [CA1704: Bezeichner sollten korrekt geschrieben werden](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)
- [CA1703: Ressourcenzeichenfolgen sollten korrekt geschrieben werden](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)