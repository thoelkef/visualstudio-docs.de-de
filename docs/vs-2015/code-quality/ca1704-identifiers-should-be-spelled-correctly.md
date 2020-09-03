---
title: 'CA1704: Bezeichner sollten korrekt geschrieben werden | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1704
- IdentifiersShouldBeSpelledCorrectly
helpviewer_keywords:
- CA1704
- IdentifiersShouldBeSpelledCorrectly
ms.assetid: f2c7a44d-1690-44ca-9cd0-681b04b12b2a
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b5e078fc1bb7fe247d541e7695e98c2de76c2466
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544065"
---
# <a name="ca1704-identifiers-should-be-spelled-correctly"></a>CA1704: Bezeichner sollten korrekt geschrieben werden.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|IdentifiersShouldBeSpelledCorrectly|
|CheckId|CA1704|
|Category|Microsoft.Naming|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Der Name eines Bezeichners enthält mindestens ein Wort, das von der Bibliothek der Microsoft-Rechtschreibprüfung nicht erkannt wird. Diese Regel überprüft keine Konstruktoren oder Member mit besonderem Namen, wie z. b. Get-und Set-Eigenschaftenaccessoren.

## <a name="rule-description"></a>Beschreibung der Regel
 Diese Regel analysiert den Bezeichner in Token und überprüft die Schreibweise der einzelnen Token. Der-Algorithmus für die Verarbeitung führt die folgenden Transformationen aus:

- Großbuchstaben starten ein neues Token. MyNameIsJoe wird z. b. in "My", "Name", "is", "Joe", angezeigt.

- Bei mehreren Großbuchstaben startet der letzte Großbuchstabe ein neues Token. Beispielsweise wird "GUIEditor" in "GUI", "Editor", getottert.

- Führende und nachfolgende Apostrophe werden entfernt. Beispielsweise wird "Sender" zu "Absender".

- Unterstriche bezeichnen das Ende eines Tokens und werden entfernt. Hello_world z. b. auf "Hello", "World".

- Eingebettete kaufmännische werden entfernt. Beispielsweise wird für&-Matte das Format "Format" angezeigt.

  Standardmäßig wird die englische Version (en) der Rechtschreibprüfung verwendet. Zurzeit sind keine anderen sprach Wörterbücher verfügbar.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, korrigieren Sie die Schreibweise des Worts, oder fügen Sie das Wort einem benutzerdefinierten Wörterbuch mit dem Namen CustomDictionary.xml hinzu. Platzieren Sie das Wörterbuch im Installationsverzeichnis des Tools, im Projektverzeichnis oder in dem Verzeichnis, das dem Tool unter dem Profil des Benutzers zugeordnet ist (%USERPROFILE%\Anwendungsdaten \\ ...). Informationen zum Hinzufügen des benutzerdefinierten Wörterbuchs zu einem Projekt in finden Sie unter Gewusst [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [wie: Anpassen des Code Analyse Wörterbuchs](../code-quality/how-to-customize-the-code-analysis-dictionary.md) .

- Fügen Sie Wörter hinzu, die unter dem Wörterbuch/Wörter/erkannten Pfad keine Verletzung verursachen sollten.

- Fügen Sie Wörter hinzu, die eine Verletzung im Wörterbuch/Wörter/nicht erkannten Pfad verursachen sollten.

- Fügen Sie Wörter, die als veraltet gekennzeichnet werden sollen, unter dem Pfad Dictionary/Words/deprecated hinzu. Weitere Informationen finden Sie im Thema Verwandte Regel [CA1726: bevorzugte Begriffe verwenden](../code-quality/ca1726-use-preferred-terms.md).

- Fügen Sie dem Wörterbuch/Akronyme/CasingExceptions-Pfad Ausnahmen zu den Regeln für die Akronym-Schreibweise hinzu.

  Im folgenden finden Sie ein Beispiel für die Struktur einer benutzerdefinierten Wörterbuchdatei.

```
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

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrückt eine Warnung aus dieser Regel nur, wenn das Wort absichtlich falsch geschrieben ist und das Wort für eine begrenzte Menge der Bibliothek gilt. Korrekt geschriebene Wörter reduzieren die Lernkurve, die für neue Software Bibliotheken erforderlich ist.

## <a name="related-rules"></a>Verwandte Regeln
 [CA2204: Literale sollten eine korrekte Rechtschreibung aufweisen.](../code-quality/ca2204-literals-should-be-spelled-correctly.md)

 [CA1703: Ressourcenzeichenfolgen sollten korrekt geschrieben werden.](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

 [CA1709: Bei Bezeichnern sollte die Groß-/Kleinschreibung beachtet werden.](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: Bezeichner sollten sich nicht nur durch die Groß-/Kleinschreibung unterscheiden.](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

 [CA1707: Bezeichner sollten keine Unterstriche enthalten.](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)

 [CA1726: Bevorzugte Begriffe verwenden.](../code-quality/ca1726-use-preferred-terms.md)

## <a name="see-also"></a>Weitere Informationen
 [Gewusst wie: Anpassen des Codeanalysewörterbuchs](../code-quality/how-to-customize-the-code-analysis-dictionary.md)
