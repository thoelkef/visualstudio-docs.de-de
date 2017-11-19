---
title: 'CA1704: Bezeichner sollten korrekt geschrieben werden | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1704
- IdentifiersShouldBeSpelledCorrectly
helpviewer_keywords:
- CA1704
- IdentifiersShouldBeSpelledCorrectly
ms.assetid: f2c7a44d-1690-44ca-9cd0-681b04b12b2a
caps.latest.revision: "25"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e43e3340cdbc05ec00c909542e201692199ccfef
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
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
  
-   Großbuchstaben beginnen, ein neues Token. Zum Beispiel: MyNameIsJoe wird in "My", "Name", "Is", "Joe".  
  
-   Für mehrere Großbuchstaben startet der letzten Großbuchstabe ein neues Token. Zum Beispiel: GUIEditor "GUI", "Editor" ein.  
  
-   Führende und nachfolgende Apostrophe werden entfernt. Beispiel: "Absender" an "Absender".  
  
-   Unterstriche bezeichnen das Ende eines Tokens und entfernt werden. Der zu indizierende Hello_world z. B. auf "Hello", "World".  
  
-   Eingebettete kaufmännische und-Zeichen werden entfernt. Z. B. für & Mat wird zum "formatieren" Token.  
  
 Standardmäßig wird die Englisch (En) Version der Rechtschreibprüfung verwendet. Keine anderen Wörterbücher sind derzeit verfügbar.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, korrigieren Sie die Schreibweise des Worts oder fügen Sie das Wort ein benutzerdefiniertes Wörterbuch mit dem Namen CustomDictionary.xml hinzu. Legen Sie das Wörterbuch in das Installationsverzeichnis des Tools, Projektverzeichnis ein, oder in das Verzeichnis, das das Tool unter dem Profil des Benutzers zugeordnet ist (%USERPROFILE%\Application Daten\\...). Um zu erfahren, wie ein Projekt in das Benutzerwörterbuch hinzugefügt [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], finden Sie unter [wie: Anpassen des Codeanalysewörterbuchs](../code-quality/how-to-customize-the-code-analysis-dictionary.md)  
  
-   Fügen Sie ein Wort, die nicht zu einer Verletzung unter dem Pfad Wörterbuch/Wörter/erkannt führt sollten hinzu.  
  
-   Fügen Sie ein Wort, die auftreten eine Verletzung unter dem Pfad Wörterbuch/Wörter/nicht erkannt werden soll.  
  
-   Fügen Sie Wörter, die gekennzeichnet werden soll, als unter dem Pfad Dictionary/Words/Deprecated veraltet. Finden Sie im Thema zugehörige Regel [CA1726: Bevorzugte Begriffe verwenden](../code-quality/ca1726-use-preferred-terms.md) für Weitere Informationen.  
  
-   Die Regeln der Groß-und Kleinschreibung Akronym für den Pfad Wörterbuch/Akronyme/CasingExceptions Ausnahmen hinzufügen.  
  
 Im folgenden ist ein Beispiel für die Struktur eine Benutzerwörterbuchdatei.  
  
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
 Unterdrücken Sie eine Warnung dieser Regel nur, wenn das Wort absichtlich falsch geschrieben ist und das Wort für eine begrenzte Anzahl von der Bibliothek gilt. Geschriebene Wörter reduzieren ordnungsgemäß die Lernkurve, die für neue Softwarebibliotheken erforderlich ist.  
  
## <a name="related-rules"></a>Verwandte Regeln  
 [CA2204: Literale sollten eine korrekte Rechtschreibung aufweisen](../code-quality/ca2204-literals-should-be-spelled-correctly.md)  
  
 [CA1703: Ressourcenzeichenfolgen sollten korrekt geschrieben werden](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
 [CA1709: Bei Bezeichnern sollte die Groß-/Kleinschreibung beachtet werden](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: Bezeichner sollten sich nicht nur durch die Groß-/Kleinschreibung unterscheiden](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
 [CA1707: Bezeichner sollten keine Unterstriche enthalten](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)  
  
 [CA1726: Bevorzugte Begriffe verwenden](../code-quality/ca1726-use-preferred-terms.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Gewusst wie: Anpassen des Codeanalysewörterbuchs](../code-quality/how-to-customize-the-code-analysis-dictionary.md)
