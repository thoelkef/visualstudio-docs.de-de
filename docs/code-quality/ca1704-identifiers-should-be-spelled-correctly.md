---
title: 'CA1704: Bezeichner sollten korrekt geschrieben werden.'
ms.date: 03/28/2018
ms.topic: reference
f1_keywords:
- CA1704
- IdentifiersShouldBeSpelledCorrectly
helpviewer_keywords:
- CA1704
- IdentifiersShouldBeSpelledCorrectly
ms.assetid: f2c7a44d-1690-44ca-9cd0-681b04b12b2a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8dbfc8081f980b7b9e978da782f1627a88a716a3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62809407"
---
# <a name="ca1704-identifiers-should-be-spelled-correctly"></a>CA1704: Bezeichner sollten korrekt geschrieben werden.

|||
|-|-|
|TypeName|IdentifiersShouldBeSpelledCorrectly|
|CheckId|CA1704|
|Kategorie|Microsoft.Naming|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache

Der Name eines Bezeichners enthält eine oder mehrere Wörter, die von der Rechtschreibprüfung aus der Microsoft-Bibliothek nicht erkannt werden. Diese Regel nicht überprüfen, Konstruktoren oder speziellen Namen Elemente wie z. B. Get und set-Eigenschaftenaccessoren.

## <a name="rule-description"></a>Regelbeschreibung

Diese Regel analysiert die Bezeichner in Tokens und überprüft die Rechtschreibung jedes Token. Der Analysealgorithmus führt die folgenden Transformationen:

- Großbuchstaben beginnen, ein neues Token. Zum Beispiel: MyNameIsJoe wird "My", "Name", "Is", "Joe".

- Für mehrere Großbuchstaben startet der letzten Großbuchstabe ein neues Token. Zum Beispiel: GUIEditor wird "GUI", "Editor".

- Führende und nachfolgende Apostrophe werden entfernt. Z. B. der zu indizierende "Sender", "Sender".

- Unterstriche bezeichnen das Ende eines Tokens, und es werden entfernt. Beispiel: die "hello_world" mit "Hello", "World".

- Eingebettete kaufmännische und-Zeichen werden entfernt. Beispielsweise & Mat wird zum "format" Token.

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

Um einen Verstoß gegen diese Regel zu beheben, korrigieren Sie die Schreibweise des Worts, oder fügen Sie es zu einem Benutzerwörterbuch.

### <a name="to-add-words-to-a-custom-dictionary"></a>Zum Hinzufügen von Wörtern zu einem Benutzerwörterbuch

Nennen Sie die XML-Datei Benutzerwörterbuch *CustomDictionary.xml*. Legen Sie das Wörterbuch, in das Installationsverzeichnis des Tools zum Projektverzeichnis ein, oder in das Verzeichnis, das das Tool unter dem Profil des Benutzers zugeordnet ist (*%USERPROFILE%\Application Daten\\...* ). Gewusst wie: Hinzufügen von benutzerdefinierten Wörterbuchs in ein Projekt in Visual Studio finden Sie unter [Vorgehensweise: Anpassen des Codeanalysewörterbuchs](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

- Hinzufügen von Wörtern, die nicht zu einer Verletzung unter dem Pfad Dictionary/Wörter/Recognized führt sollte.

- Fügen Sie ein Wort, die auftreten eine Verletzung unter dem Pfad Wörterbuch/Wörter/nicht erkannt werden soll.

- Fügen Sie Wörter, die gekennzeichnet werden soll als veraltet, unter dem Wörterbuch/Wörter/veraltet-Pfad hinzu. Finden Sie im Thema zugehörige Regel [CA1726: Bevorzugte Begriffe verwenden](../code-quality/ca1726-use-preferred-terms.md) für Weitere Informationen.

- Ausnahmen, die Regeln der Groß-und Kleinschreibung Abkürzung zum Wörterbuch/Akronyme/CasingExceptions Pfad hinzufügen.

Im folgenden finden ein Beispiel für die Struktur der ein benutzerdefiniertes Wörterbuch-Datei:

```xml
<Dictionary>
   <Words>
      <Unrecognized>
         <Word>cb</Word>
      </Unrecognized>
      <Recognized>
         <Word>stylesheet</Word>
         <Word>GotDotNet</Word>
      </Recognized>
      <Deprecated>
         <Term PreferredAlternate="EnterpriseServices">ComPlus</Term>
      </Deprecated>
   </Words>
   <Acronyms>
      <CasingExceptions>
         <Acronym>CJK</Acronym>
         <Acronym>Pi</Acronym>
      </CasingExceptions>
   </Acronyms>
</Dictionary>
```

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Unterdrücken Sie eine Warnung dieser Regel nur, wenn das Wort absichtlich falsch geschrieben ist und das Wort, die auf eine begrenzte Anzahl von der Bibliothek angewendet wird. Geschriebene Wörter reduzieren ordnungsgemäß die Lernkurve, die für neue Softwarebibliotheken erforderlich ist.

## <a name="related-rules"></a>Verwandte Regeln

- [CA2204: Literale sollten eine korrekte Rechtschreibung aufweisen](../code-quality/ca2204-literals-should-be-spelled-correctly.md)
- [CA1703: Ressourcenzeichenfolgen sollten korrekt geschrieben werden](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)
- [CA1709: Bezeichner sollten beachtet werden](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708: Bezeichner sollten sich durch die Groß-/Kleinschreibung unterscheiden.](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
- [CA1707: Bezeichner sollten keine Unterstriche enthalten.](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)
- [CA1726: Bevorzugte Begriffe verwenden](../code-quality/ca1726-use-preferred-terms.md)

## <a name="see-also"></a>Siehe auch

- [Vorgehensweise: Anpassen des Codeanalysewörterbuchs](../code-quality/how-to-customize-the-code-analysis-dictionary.md)
