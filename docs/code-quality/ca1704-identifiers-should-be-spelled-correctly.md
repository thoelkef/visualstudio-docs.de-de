---
title: 'CA1704: Bezeichner sollten korrekt geschrieben werden'
ms.date: 03/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 710e18f4ce8199c76c34683c510d3a64160544e6
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="ca1704-identifiers-should-be-spelled-correctly"></a>CA1704: Bezeichner sollten korrekt geschrieben werden

|||
|-|-|
|TypeName|IdentifiersShouldBeSpelledCorrectly|
|CheckId|CA1704|
|Kategorie|Microsoft.Naming|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache

Der Name eines Bezeichners enthält mindestens ein Wort, die von der Rechtschreibprüfung aus der Microsoft-Bibliothek nicht erkannt werden. Diese Regel nicht überprüfen, Konstruktoren oder mit dem Namen besondere Elemente wie z. B. Get und set-Eigenschaftenaccessoren.

## <a name="rule-description"></a>Regelbeschreibung

Diese Regel analysiert die Bezeichner in Token und die Schreibweise der einzelnen Token überprüft. Die Analyse Algorithmus führt die folgenden Transformationen:

- Großbuchstaben beginnen, ein neues Token. Zum Beispiel: MyNameIsJoe wird in "My", "Name", "Is", "Joe".

- Für mehrere Großbuchstaben startet der letzten Großbuchstabe ein neues Token. Zum Beispiel: GUIEditor "GUI", "Editor" ein.

- Führende und nachfolgende Apostrophe werden entfernt. Beispiel: "Absender" an "Absender".

- Unterstriche bezeichnen das Ende eines Tokens und entfernt werden. Der zu indizierende Hello_world z. B. auf "Hello", "World".

- Eingebettete kaufmännische und-Zeichen werden entfernt. Z. B. für & Mat wird zum "formatieren" Token.

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

Um einen Verstoß gegen diese Regel zu beheben, korrigieren Sie die Schreibweise des Worts oder eines Benutzerwörterbuchs fügen Sie das Wort hinzu.

### <a name="to-add-words-to-a-custom-dictionary"></a>Hinzufügen von Wörtern zu einem Benutzerwörterbuch

Nennen Sie die XML-Datei Benutzerwörterbuch *CustomDictionary.xml*. Legen Sie das Wörterbuch in das Installationsverzeichnis des Tools, Projektverzeichnis ein, oder in das Verzeichnis, das das Tool unter dem Profil des Benutzers zugeordnet ist (*%USERPROFILE%\Application Daten\\...* ). Zum Hinzufügen von benutzerdefinierten Wörterbuchs in ein Projekt in Visual Studio finden Sie unter [wie: Anpassen des Codeanalysewörterbuchs](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

- Fügen Sie ein Wort, die nicht zu einer Verletzung unter dem Pfad Wörterbuch/Wörter/erkannt führt sollten hinzu.

- Fügen Sie ein Wort, die auftreten eine Verletzung unter dem Pfad Wörterbuch/Wörter/nicht erkannt werden soll.

- Fügen Sie Wörter, die gekennzeichnet werden soll, als unter dem Pfad Dictionary/Words/Deprecated veraltet. Finden Sie im Thema zugehörige Regel [CA1726: Bevorzugte Begriffe verwenden](../code-quality/ca1726-use-preferred-terms.md) für Weitere Informationen.

- Die Regeln der Groß-und Kleinschreibung Akronym für den Pfad Wörterbuch/Akronyme/CasingExceptions Ausnahmen hinzufügen.

Im folgenden finden ein Beispiel für die Struktur eine Benutzerwörterbuchdatei:

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

## <a name="when-to-suppress-warnings"></a>Wenn Warnungen unterdrücken

Unterdrücken Sie eine Warnung dieser Regel nur, wenn das Wort absichtlich falsch geschrieben ist und das Wort für eine begrenzte Anzahl von der Bibliothek gilt. Geschriebene Wörter reduzieren ordnungsgemäß die Lernkurve, die für neue Softwarebibliotheken erforderlich ist.

## <a name="related-rules"></a>Verwandte Regeln

- [CA2204: Literale sollten eine korrekte Rechtschreibung aufweisen](../code-quality/ca2204-literals-should-be-spelled-correctly.md)
- [CA1703: Ressourcenzeichenfolgen sollten korrekt geschrieben werden](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)
- [CA1709: Bei Bezeichnern sollte die Groß-/Kleinschreibung beachtet werden](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708: Bezeichner sollten sich nicht nur durch die Groß-/Kleinschreibung unterscheiden](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
- [CA1707: Bezeichner sollten keine Unterstriche enthalten](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)
- [CA1726: Bevorzugte Begriffe verwenden](../code-quality/ca1726-use-preferred-terms.md)

## <a name="see-also"></a>Siehe auch

- [Gewusst wie: Anpassen des Codeanalysewörterbuchs](../code-quality/how-to-customize-the-code-analysis-dictionary.md)
