---
title: 'Gewusst wie: Anpassen des Codeanalysewörterbuchs'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis dictionary
- custom dictionary, code analysis
- dictionary, code analysis
ms.assetid: 667e3b4e-beff-48be-b3d1-376e1716a895
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 544343a701909957ff0c16a49beeaf081cf256b8
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-customize-the-code-analysis-dictionary"></a>Gewusst wie: Anpassen des Codeanalysewörterbuchs
Codeanalyse verwendet ein integriertes Wörterbuch Bezeichner in den Code auf Fehler hinsichtlich des Verbindungstyps richtig eingegeben haben, Grammatikfehler Groß-/Kleinschreibung und andere Namenskonventionen der Überprüfen der [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] Richtlinien. Sie können eine benutzerdefiniertes Wörterbuch XML-Datei hinzufügen, entfernen oder Ändern von Begriffe und Abkürzungen Akronyme, die dem integrierten Wörterbuch erstellen.

 Nehmen wir beispielsweise an Ihrem Code enthalten, eine Klasse namens **DoorKnokker**. Codeanalyse würde den Namen identifiziert, als eine Zusammensetzung von zwei Wörtern: **Tür** und **Knokker**. Es würde dann eine Warnung auslösen, **Knokker** nicht richtig eingegeben wurde. Sie können zum Erzwingen der Codeanalyse erkennen Sie die Schreibweise den Begriff hinzufügen **Knokker** Benutzerwörterbuch.

## <a name="to-create-a-custom-dictionary"></a>So erstellen ein benutzerdefiniertes Wörterbuch
 Erstellen Sie eine Datei mit dem Namen **CustomDictionary.xml**.

 Definieren Sie die benutzerdefinierten Wörter mithilfe der folgenden XML-Struktur:

```
<Dictionary>
      <Words>
         <Unrecognized>
            <Word>knokker</Word>
         </Unrecognized>
         <Recognized>
            <Word></Word>
         </Recognized>
         <Deprecated>
            <Term PreferredAlternate=""></Term>
         </Deprecated>
         <Compound>
            <Term CompoundAlternate=""></Term>
         </Compound>
         <DiscreteExceptions>
            <Term></Term>
         </DiscreteExceptions>
      </Words>
      <Acronyms>
         <CasingExceptions>
            <Acronym></Acronym>
         </CasingExceptions>
      </Acronyms>
   </Dictionary>
```

## <a name="custom-dictionary-elements"></a>Benutzerdefiniertes Wörterbuchelemente
 Sie können das Verhalten des Codeanalysewörterbuchs ändern, indem Sie Begriffe als inneren Text in der folgenden Elemente im benutzerdefinierten Wörterbuch hinzufügen:

-   [Wörterbuch/Wörter/erkannt/Word](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsRecognizedWord)

-   [Wörterbuch/Wörter/unbekannte/Word](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsUnrecognizedWord)

-   [/ Wörter/veraltet/Wörterbucheinträge [@PreferredAlternate]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDeprecatedTermPreferredAlternate)

-   [Wörterbuch/Wörter/Compound/Term [@CompoundAlternate]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsCompoundTermCompoundAlternate)

-   [Wörterbuch/Wörter/DiscreteExceptions/Term](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDiscreteExceptionsTerm)

-   [Wörterbuch/Akronyme/CasingExceptions/Akronym](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryAcronymsCasingExceptionsAcronym)

###  <a name="BKMK_DictionaryWordsRecognizedWord"></a> Wörterbuch/Wörter/erkannt/Word
 Um einen Begriff in der Liste der Begriffe enthalten, die Codeanalyse als korrekt bezeichnet geschrieben, fügen Sie den Begriff als inneren Text in einem Wörterbuch/Wörter/erkannt/Word-Element hinzu. Begriffe im Wörterbuch/Wörter/erkannt/Word-Elementen wird die Groß-/Kleinschreibung nicht berücksichtigt.

 **Beispiel**

```
<Dictionary>
      <Words>
         <Recognized>
            <Word>knokker</Word>
            ...
         </Recognized>
         ...
      </Words>
      ...
</Dictionary>

```

 Begriffe im Wörterbuch/Wörter/erkannt Knoten werden mit den folgenden Code Analysis-Regeln angewendet:

-   [CA1701: Bei zusammengesetzten Begriffen in Ressourcenzeichenfolgen sollte die Groß-/Kleinschreibung beachtet werden](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

-   [CA1702: Bei zusammengesetzten Begriffen sollte die Groß-/Kleinschreibung beachtet werden](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

-   [CA1703: Ressourcenzeichenfolgen sollten korrekt geschrieben werden](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

-   [CA1704: Bezeichner sollten korrekt geschrieben werden](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

-   [CA1709: Bei Bezeichnern sollte die Groß-/Kleinschreibung beachtet werden](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

-   [CA1726: Bevorzugte Begriffe verwenden](../code-quality/ca1726-use-preferred-terms.md)

-   [CA2204: Literale sollten eine korrekte Rechtschreibung aufweisen](../code-quality/ca2204-literals-should-be-spelled-correctly.md)

###  <a name="BKMK_DictionaryWordsUnrecognizedWord"></a> Wörterbuch/Wörter/unbekannte/Word
 Fügen Sie den Begriff als innerer Text eines Elements Dictionary/Words/nicht erkanntes/Word ausschließen, zum Ausschließen eines Begriffs aus der Liste von Begriffen, die Codeanalyse identifiziert, die als richtig geschrieben. Begriffe im Wörterbuch/Wörter/nicht erkanntes/Word-Elementen wird die Groß-/Kleinschreibung nicht berücksichtigt.

 **Beispiel**

```
<Dictionary>
      <Words>
         <Unrecognized>
            <Word>meth</Word>
            ...
         </Unrecognized>
         ...
      </Words>
      ...
</Dictionary>

```

 Begriffe im Knoten "Wörterbuch/Wörter/nicht erkannt" werden mit den folgenden Code Analysis-Regeln angewendet:

-   [CA1701: Bei zusammengesetzten Begriffen in Ressourcenzeichenfolgen sollte die Groß-/Kleinschreibung beachtet werden](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

-   [CA1702: Bei zusammengesetzten Begriffen sollte die Groß-/Kleinschreibung beachtet werden](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

-   [CA1703: Ressourcenzeichenfolgen sollten korrekt geschrieben werden](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

-   [CA1704: Bezeichner sollten korrekt geschrieben werden](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

-   [CA1709: Bei Bezeichnern sollte die Groß-/Kleinschreibung beachtet werden](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

-   [CA1726: Bevorzugte Begriffe verwenden](../code-quality/ca1726-use-preferred-terms.md)

-   [CA2204: Literale sollten eine korrekte Rechtschreibung aufweisen](../code-quality/ca2204-literals-should-be-spelled-correctly.md)

###  <a name="BKMK_DictionaryWordsDeprecatedTermPreferredAlternate"></a> / Wörter/veraltet/Wörterbucheinträge [@PreferredAlternate]
 Um einen Begriff in der Liste der Begriffe enthalten, die als veraltet Codeanalyse identifiziert, fügen Sie den Begriff als inneren Text in einem Wörterbuch/Wörter/Deprecated/Term-Element hinzu. Ein veralteter Begriff ist ein Wort, das richtig geschrieben ist, aber nicht verwendet werden soll.

 Um einen alternativen vorgeschlagenen Begriff in der Warnung einzuschließen, geben Sie die alternative im PreferredAlternate-Attribut des Elements Begriff aus. Sie können den Attributwert leer lassen, wenn Sie keine alternative vorschlagen möchten.

-   Die als veraltet markierten Ausdruck in Wörterbucheinträge / / Deprecated/Term-Element ist nicht in der Groß-/Kleinschreibung beachtet.

-   Der Attributwert PreferredAlternate wird Groß-/Kleinschreibung beachtet. Verwenden Sie Pascal-Schreibweise für zusammengesetzte alternativen.

 **Beispiel**

```
<Dictionary>
      <Words>
         <Deprecated>
            <Term PreferredAlternate="LogOn">login</Term>
            ...
         </Deprecated>
         ...
      </Words>
      ...
</Dictionary>

```

 Begriffe im Dictionary/Words/Deprecated-Knoten werden auf die folgenden Codeanalyseregeln angewendet:

-   [CA1701: Bei zusammengesetzten Begriffen in Ressourcenzeichenfolgen sollte die Groß-/Kleinschreibung beachtet werden](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

-   [CA1702: Bei zusammengesetzten Begriffen sollte die Groß-/Kleinschreibung beachtet werden](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

-   [CA1703: Ressourcenzeichenfolgen sollten korrekt geschrieben werden](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

-   [CA1704: Bezeichner sollten korrekt geschrieben werden](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

-   [CA1726: Bevorzugte Begriffe verwenden](../code-quality/ca1726-use-preferred-terms.md)

###  <a name="BKMK_DictionaryWordsCompoundTermCompoundAlternate"></a> Wörterbuch/Wörter/Compound/Term [@CompoundAlternate]
 Das integrierte Wörterbuch identifiziert einige Begriffe als einzelne, diskrete Begriffe statt einer zusammengesetzten Begriff. Um einen Begriff in der Liste der Begriffe enthalten, die Codeanalyse als ein zusammengesetztes Wort identifiziert und geben Sie die richtige Groß-/Kleinschreibung des Begriffs, fügen Sie den Begriff als inneren Text in einem Wörterbuch/Wörter/Compound/Term-Element hinzu. Geben Sie in das CompoundAlternate-Attribut des Elements Begriff die einzelne Wörter, die den zusammengesetzten Begriff bilden, durch die Großschreibung des ersten Buchstabens der einzelne Wörter (Pascal-Schreibweise). Beachten Sie, dass der Begriff in der innere Text angegebenen Wörterbuch/Wörter/DiscreteExceptions Liste automatisch hinzugefügt wird.

-   Die als veraltet markierten Ausdruck in Wörterbucheinträge / / Deprecated/Term-Element ist nicht in der Groß-/Kleinschreibung beachtet.

-   Der Attributwert PreferredAlternate wird Groß-/Kleinschreibung beachtet. Verwenden Sie Pascal-Schreibweise für zusammengesetzte alternativen.

 **Beispiel**

```
<Dictionary>
      <Words>
         <Compound>
            <Term CompoundAlternate="CheckBox">checkbox</Term>
            ...
         </Compound>
         ...
      </Words>
      ...
</Dictionary>

```

 Begriffe im Wörterbuch/Wörter/Compound-Knoten werden auf die folgenden Codeanalyseregeln angewendet:

-   [CA1701: Bei zusammengesetzten Begriffen in Ressourcenzeichenfolgen sollte die Groß-/Kleinschreibung beachtet werden](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

-   [CA1702: Bei zusammengesetzten Begriffen sollte die Groß-/Kleinschreibung beachtet werden](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

-   [CA1703: Ressourcenzeichenfolgen sollten korrekt geschrieben werden](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

-   [CA1704: Bezeichner sollten korrekt geschrieben werden](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

###  <a name="BKMK_DictionaryWordsDiscreteExceptionsTerm"></a> Wörterbuch/Wörter/DiscreteExceptions/Term
 Um einen Begriff in der Liste der Begriffe auszuschließen, die als einzelner Codeanalyse identifiziert, diskrete Wort, wenn der Begriff durch die Regeln der Groß-und Kleinschreibung für zusammengesetzte Wörter aktiviert ist den Begriff als innerer Text eines Elements Dictionary/Words/DiscreteExceptions/Term hinzufügen. Der Begriff im Wörterbuch/Words/DiscreteExceptions/Term-Element ist nicht in der Groß-/Kleinschreibung beachtet.

 **Beispiel**

```
<Dictionary>
      <Words>
         <DiscreteExceptions>
            <Term>checkbox</Term>
            ...
         </DiscreteExceptions>
         ...
      </Words>
      ...
</Dictionary>

```

 Begriffe im Dictionary/Words/DiscreteExceptions-Knoten werden auf die folgenden Codeanalyseregeln angewendet:

-   [CA1701: Bei zusammengesetzten Begriffen in Ressourcenzeichenfolgen sollte die Groß-/Kleinschreibung beachtet werden](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

-   [CA1702: Bei zusammengesetzten Begriffen sollte die Groß-/Kleinschreibung beachtet werden](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

###  <a name="BKMK_DictionaryAcronymsCasingExceptionsAcronym"></a> Wörterbuch/Akronyme/CasingExceptions/Akronym
 Den Begriff als inneren Text in einem Wörterbuch/Akronyme/CasingExceptions hinzufügen, um ein Akronym in der Liste der Begriffe enthalten, die als richtig geschrieben Codeanalyse identifiziert und anzugeben, wie das Akronym, wenn der Begriff durch die Groß-/Kleinschreibung aktiviert ist für zusammengesetzte Wörter Regeln, / Acronym-Element. Die Abkürzung in das Wörterbuch/Akronyme/CasingExceptions/Acronym-Element wird Groß-/Kleinschreibung beachtet.

 **Beispiel**

```
<Dictionary>
      <Acronyms>
         <CasingExceptions>
            <Acronym>NESW</Acronym>   <!-- North East South West -->
            ...
         </CasingExceptions>
         ...
      </Acronyms>
      ...
</Dictionary>

```

 Begriffe im Wörterbuch/Akronyme/CasingExceptions-Knoten werden auf die folgenden Codeanalyseregeln angewendet:

-   [CA1709: Bei Bezeichnern sollte die Groß-/Kleinschreibung beachtet werden](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

##  <a name="BKMK_ToApplyACustomDictionaryToAProject"></a> Um einem Benutzerwörterbuch für ein Projekt gelten.

1.  In **Projektmappen-Explorer**, verwenden Sie eine der folgenden Verfahren:

2.  Um ein Wörterbuch in ein einzelnes Projekt hinzuzufügen, mit der rechten Maustaste des Projektnamens, und klicken Sie dann auf **vorhandenes Element hinzufügen**. Geben Sie die Datei in die **vorhandenes Element hinzufügen** (Dialogfeld).

3.  Um ein Wörterbuch hinzufügen, die von zwei oder mehreren Projekten gemeinsam verwendet wird, suchen Sie die Datei zur Freigabe in der **vorhandenes Element hinzufügen** Dialogfeld klicken Sie auf den Pfeil nach unten auf der **hinzufügen** Schaltfläche, und klicken Sie dann auf **als Link hinzufügen** .

4.  In **Projektmappen-Explorer**, mit der rechten Maustaste die **CustomDictionary.xml** Dateinamen und klicken Sie auf **Eigenschaften**.

5.  Aus der **Buildvorgang** Liste **CodeAnalysisDictionary**.

6.  Aus der **in Ausgabeverzeichnis kopieren** Liste **nicht kopieren**.