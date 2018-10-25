---
title: 'CA1704: Bezeichner sollten korrekt geschrieben werden | Microsoft-Dokumentation'
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
- CA1704
- IdentifiersShouldBeSpelledCorrectly
helpviewer_keywords:
- CA1704
- IdentifiersShouldBeSpelledCorrectly
ms.assetid: f2c7a44d-1690-44ca-9cd0-681b04b12b2a
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c1e31917356e3d55a7db38ba7aabc9258af1deb0
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49827544"
---
# <a name="ca1704-identifiers-should-be-spelled-correctly"></a>CA1704: Bezeichner sollten korrekt geschrieben werden
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

  Standardmäßig wird die Englisch (En) Version der Rechtschreibprüfung verwendet. Keine andere Sprachwörterbücher sind derzeit verfügbar.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, korrigieren Sie die Schreibweise des Worts, oder fügen Sie das Wort, um ein benutzerdefiniertes Wörterbuch mit dem Namen CustomDictionary.xml. Legen Sie das Wörterbuch, in das Installationsverzeichnis des Tools zum Projektverzeichnis ein, oder in das Verzeichnis, das das Tool unter dem Profil des Benutzers zugeordnet ist (%USERPROFILE%\Application Daten\\...). Erfahren, wie ein Projekt in das benutzerdefinierte Wörterbuch hinzuzufügende [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], finden Sie unter [wie: Anpassen des Codeanalysewörterbuchs](../code-quality/how-to-customize-the-code-analysis-dictionary.md)

- Hinzufügen von Wörtern, die nicht zu einer Verletzung unter dem Pfad Dictionary/Wörter/Recognized führt sollte.

- Fügen Sie ein Wort, die auftreten eine Verletzung unter dem Pfad Wörterbuch/Wörter/nicht erkannt werden soll.

- Fügen Sie Wörter, die gekennzeichnet werden soll als veraltet, unter dem Wörterbuch/Wörter/veraltet-Pfad hinzu. Finden Sie im Thema zugehörige Regel [CA1726: Bevorzugte Begriffe verwenden](../code-quality/ca1726-use-preferred-terms.md)für Weitere Informationen.

- Ausnahmen, die Regeln der Groß-und Kleinschreibung Abkürzung zum Wörterbuch/Akronyme/CasingExceptions Pfad hinzufügen.

  Folgendes ist ein Beispiel für die Struktur einer Datei des benutzerdefinierten Wörterbuchs.

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
 Unterdrücken Sie eine Warnung dieser Regel nur, wenn das Wort absichtlich falsch geschrieben ist und das Wort, die auf eine begrenzte Anzahl von der Bibliothek angewendet wird. Geschriebene Wörter reduzieren ordnungsgemäß die Lernkurve, die für neue Softwarebibliotheken erforderlich ist.

## <a name="related-rules"></a>Verwandte Regeln
 [CA2204: Literale sollten eine korrekte Rechtschreibung aufweisen](../code-quality/ca2204-literals-should-be-spelled-correctly.md)

 [CA1703: Ressourcenzeichenfolgen sollten korrekt geschrieben werden](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

 [CA1709: Bei Bezeichnern sollte die Groß-/Kleinschreibung beachtet werden](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: Bezeichner sollten sich nicht nur durch die Groß-/Kleinschreibung unterscheiden](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

 [CA1707: Bezeichner sollten keine Unterstriche enthalten](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)

 [CA1726: Bevorzugte Begriffe verwenden](../code-quality/ca1726-use-preferred-terms.md)

## <a name="see-also"></a>Siehe auch
 [Gewusst wie: Anpassen des Codeanalysewörterbuchs](../code-quality/how-to-customize-the-code-analysis-dictionary.md)



