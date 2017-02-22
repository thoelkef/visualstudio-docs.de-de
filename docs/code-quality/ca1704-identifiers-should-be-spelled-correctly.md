---
title: "CA1704: Bezeichner sollten korrekt geschrieben werden | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1704"
  - "IdentifiersShouldBeSpelledCorrectly"
helpviewer_keywords: 
  - "CA1704"
  - "IdentifiersShouldBeSpelledCorrectly"
ms.assetid: f2c7a44d-1690-44ca-9cd0-681b04b12b2a
caps.latest.revision: 25
caps.handback.revision: 25
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1704: Bezeichner sollten korrekt geschrieben werden
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IdentifiersShouldBeSpelledCorrectly|  
|CheckId|CA1704|  
|Kategorie \(Category\)|Microsoft.Naming|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Der Name eines Bezeichners enthält mindestens ein Wort, das von der Rechtschreibprüfung aus der Microsoft\-Bibliothek nicht erkannt wird.  Durch diese Regel werden keine Konstruktoren oder mit speziellen Namen versehene Member wie get\- und set\-Eigenschaftenaccessoren überprüft.  
  
## Regelbeschreibung  
 Durch diese Regel wird der Bezeichner in Token unterteilt und die Rechtschreibung der einzelnen Token überprüft.  Der Analysealgorithmus führt die folgenden Transformationen aus:  
  
-   Durch Großbuchstaben wird ein neues Token gestartet.  Beispiel: MyNameIsJoe wird in die Token "My", "Name", "Is" und "Joe" unterteilt.  
  
-   Wenn mehrere Großbuchstaben vorhanden sind, fängt das neue Token mit dem letzten Großbuchstaben an.  Beispiel: GUIEditor wird in die Token "GUI" und "Editor" unterteilt.  
  
-   Führende und nachfolgende Apostrophs werden entfernt.  Beispiel: 'Absender' wird zum Token "Absender".  
  
-   Unterstriche geben das Ende eines Tokens an und werden entfernt.  Beispiel: Hello\_world wird in die Token "Hello" und "world" unterteilt.  
  
-   Eingebettete kaufmännische Und\-Zeichen werden entfernt.  Beispielsweise zerlegt Format &"zu formatieren".  
  
 Standardmäßig wird die englische Version \(EN\) der Rechtschreibprüfung verwendet.  Derzeit sind keine anderen Sprachwörterbücher verfügbar.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, korrigieren Sie die Schreibung des Wortes oder fügen es einem benutzerdefinierten Wörterbuch mit dem Namen CustomDictionary.xml hinzu.  Legen Sie das Wörterbuch im Installationsverzeichnis des Tools, im Projektverzeichnis oder im Verzeichnis ab, das dem Tool unter dem Profil des Benutzers \(%USERPROFILE%\\Anwendungsdaten\\...\) zugeordnet wurde.  Um zu erfahren, wie das Benutzerwörterbuch einem Projekt in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] hinzugefügt wird, lesen Sie [Gewusst wie: Anpassen des Codeanalysewörterbuchs](../code-quality/how-to-customize-the-code-analysis-dictionary.md)  
  
-   Fügen Sie Wörter, die keinen Verstoß verursachen sollen, unter dem Pfad Dictionary\/Words\/Recognized hinzu.  
  
-   Fügen Sie Wörter, die einen Verstoß verursachen sollen, unter dem Pfad Dictionary\/Words\/Unrecognized hinzu.  
  
-   Fügen Sie Wörter, die als veraltet gekennzeichnet werden sollen, unter dem Pfad Dictionary\/Words\/Deprecated hinzu.  Weitere Informationen finden Sie im Thema zur verwandten Regel [CA1726: Bevorzugte Begriffe verwenden](../code-quality/ca1726-use-preferred-terms.md).  
  
-   Fügen Sie Ausnahmen für die Regeln zur Groß\-\/Kleinschreibung von Akronymen unter dem Pfad Dictionary\/Acronyms\/CasingExceptions hinzu.  
  
 Im Folgenden sehen Sie ein Beispiel für den Aufbau einer benutzerdefinierten Wörterbuchdatei.  
  
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
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie eine Warnung dieser Regel nur dann, wenn das Wort absichtlich falsch geschrieben ist und sich auf einen Teilbereich der Bibliothek bezieht.  Durch fehlerfreie Begriffe wird der Lernaufwand für neue Softwarebibliotheken verringert.  
  
## Verwandte Regeln  
 [CA2204: Literale sollten eine korrekte Rechtschreibung aufweisen](../code-quality/ca2204-literals-should-be-spelled-correctly.md)  
  
 [CA1703: Ressourcenzeichenfolgen sollten korrekt geschrieben werden](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
 [CA1709: Bei Bezeichnern sollte die Groß\-\/Kleinschreibung beachtet werden](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: Bezeichner sollten sich nicht nur durch die Groß\-\/Kleinschreibung unterscheiden](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
 [CA1707: Bezeichner sollten keine Unterstriche enthalten](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)  
  
 [CA1726: Bevorzugte Begriffe verwenden](../code-quality/ca1726-use-preferred-terms.md)  
  
## Siehe auch  
 [Gewusst wie: Anpassen des Codeanalysewörterbuchs](../code-quality/how-to-customize-the-code-analysis-dictionary.md)