---
title: 'CA2204: Literale sollten eine korrekte Rechtschreibung aufweisen'
ms.date: 03/28/2018
ms.prod: visual-studio-dev15
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6f86658978a105c1fa4f3c4602b5c838f4c80726
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31918422"
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