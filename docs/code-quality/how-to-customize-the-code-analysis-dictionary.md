---
title: 'Gewusst wie: Anpassen des Codeanalysewörterbuchs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- code analysis dictionary
- custom dictionary, code analysis
- dictionary, code analysis
ms.assetid: 667e3b4e-beff-48be-b3d1-376e1716a895
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b4a6c94f5784d57a90dd31f21f8829b3141140d0
ms.sourcegitcommit: 1507baf3a336bbb6511d4c3ce73653674831501b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72349591"
---
# <a name="how-to-customize-the-code-analysis-dictionary"></a>Gewusst wie: Anpassen des Codeanalysewörterbuchs

Bei der Code Analyse wird ein integriertes Wörterbuch verwendet, um Bezeichner in Ihrem Code auf Fehler in der Schreibweise, in grammatischem Fall und in anderen Benennungs Konventionen der .net-Entwurfs Richtlinien zu überprüfen. Sie können eine benutzerdefinierte Wörterbuch-XML-Datei erstellen, um Begriffe, Abkürzungen und Akronyme zum integrierten Wörterbuch hinzuzufügen, zu entfernen oder zu ändern.

Angenommen, Ihr Code enthielt eine Klasse mit dem Namen " **doorklokker**". Bei der Code Analyse wird der Name als Verbund mit zwei Wörtern identifiziert: **Door** und **klokker**. Anschließend wird eine Warnung ausgegeben, dass " **klokker** " nicht richtig geschrieben wurde. Um die Code Analyse zu erzwingen, um die Rechtschreibprüfung zu erkennen, können Sie dem Benutzerwörterbuch den Begriff " **klokker** " hinzufügen

## <a name="to-create-a-custom-dictionary"></a>So erstellen Sie ein Benutzerwörterbuch

Erstellen Sie eine Datei mit dem Namen " **CustomDictionary. XML**".

Definieren Sie die benutzerdefinierten Wörter mit der folgenden XML-Struktur:

```xml
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

## <a name="custom-dictionary-elements"></a>Benutzerdefinierte Wörterbuch Elemente

Sie können das Verhalten des Code Analyse Wörterbuchs ändern, indem Sie Begriffe als inneren Text der folgenden Elemente im Benutzerwörterbuch hinzufügen:

- [Wörterbuch/Wörter/erkannt/Word](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsRecognizedWord)

- [Wörterbuch/Wörter/nicht erkannt/Word](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsUnrecognizedWord)

- [Wörterbuch/Wörter/veraltet/Begriff [@PreferredAlternate]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDeprecatedTermPreferredAlternate)

- [Wörterbuch/Wörter/Verbund/Begriff [@CompoundAlternate]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsCompoundTermCompoundAlternate)

- [Dictionary/Words/diskreteexceptions/Term](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDiscreteExceptionsTerm)

- [Dictionary/Akronyme/CasingExceptions/Akronym](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryAcronymsCasingExceptionsAcronym)

### <a name="BKMK_DictionaryWordsRecognizedWord"></a>Wörterbuch/Wörter/erkannt/Word

Fügen Sie den Begriff als inneren Text eines Dictionary/Words/erkannten/Word-Elements hinzu, um einen Begriff in die Liste der Begriffe einzuschließen, die von der Code Analyse als ordnungsgemäß geschrieben identifiziert werden. Bei Begriffen mit Wörterbuch/Wörtern/erkannten/Word-Elementen wird die Groß-/Kleinschreibung nicht beachtet.

**Beispiel**

```xml
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

Begriffe in Wörterbuch/Wörtern/erkannten Knoten werden auf die folgenden Code Analyse Regeln angewendet:

- [CA1701: Bei zusammengesetzten Begriffen in Ressourcenzeichenfolgen sollte die Groß-/Kleinschreibung beachtet werden](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

- [CA1702: Bei zusammengesetzten Begriffen sollte die Groß-/Kleinschreibung beachtet werden](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

- [CA1703: Ressourcenzeichenfolgen sollten korrekt geschrieben werden](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

- [CA1704: Bezeichner sollten korrekt geschrieben werden](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

- [CA1709: Bei Bezeichnern sollte die Groß-/Kleinschreibung beachtet werden](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

- [CA1726: Bevorzugte Begriffe verwenden](../code-quality/ca1726-use-preferred-terms.md)

- [CA2204: Literale sollten eine korrekte Rechtschreibung aufweisen](../code-quality/ca2204.md)

### <a name="BKMK_DictionaryWordsUnrecognizedWord"></a>Wörterbuch/Wörter/nicht erkannt/Word

Um einen Begriff aus der Liste der Begriffe auszuschließen, die von der Code Analyse als richtig geschrieben identifiziert werden, fügen Sie den auszuschließenden Begriff als inneren Text eines Dictionary/Words/unbekanntes/Word-Elements hinzu. Bei Begriffen in Wörterbuch/Wörtern/unbekannten/Word-Elementen wird die Groß-/Kleinschreibung nicht beachtet.

**Beispiel**

```xml
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

Die Begriffe im Wörterbuch/Wörter/nicht erkannten Knoten werden auf die folgenden Code Analyse Regeln angewendet:

- [CA1701: Bei zusammengesetzten Begriffen in Ressourcenzeichenfolgen sollte die Groß-/Kleinschreibung beachtet werden](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

- [CA1702: Bei zusammengesetzten Begriffen sollte die Groß-/Kleinschreibung beachtet werden](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

- [CA1703: Ressourcenzeichenfolgen sollten korrekt geschrieben werden](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

- [CA1704: Bezeichner sollten korrekt geschrieben werden](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

- [CA1709: Bei Bezeichnern sollte die Groß-/Kleinschreibung beachtet werden](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

- [CA1726: Bevorzugte Begriffe verwenden](../code-quality/ca1726-use-preferred-terms.md)

- [CA2204: Literale sollten eine korrekte Rechtschreibung aufweisen](../code-quality/ca2204.md)

### <a name="BKMK_DictionaryWordsDeprecatedTermPreferredAlternate"></a>Wörterbuch/Wörter/veraltet/Begriff [@PreferredAlternate]

Wenn Sie einen Begriff in die Liste der Begriffe einschließen möchten, die von der Code Analyse als veraltet identifiziert werden, fügen Sie den Begriff als inneren Text eines Dictionary/Words/deprecated/Term-Elements hinzu. Ein als veraltet markierte Begriff ist ein Wort, das korrekt geschrieben ist, aber nicht verwendet werden sollte.

Um einen vorgeschlagenen Alternativen Begriff in der Warnung einzuschließen, geben Sie die Alternative im preferredalternate-Attribut des Begriffs Elements an. Sie können den Attribut Wert leer lassen, wenn Sie keine Alternative vorschlagen möchten.

- Beim veralteten Begriff "Dictionary/Words/veraltet/Term Element" wird die Groß-/Kleinschreibung nicht beachtet.

- Beim preferredalternate-Attribut Wert wird die Groß-/Kleinschreibung beachtet. Verwenden Sie Pascal Case für Verbund Alternativen.

**Beispiel**

```xml
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

Begriffe im Wörterbuch/Wörter/deprecated-Knoten werden auf die folgenden Code Analyse Regeln angewendet:

- [CA1701: Bei zusammengesetzten Begriffen in Ressourcenzeichenfolgen sollte die Groß-/Kleinschreibung beachtet werden](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

- [CA1702: Bei zusammengesetzten Begriffen sollte die Groß-/Kleinschreibung beachtet werden](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

- [CA1703: Ressourcenzeichenfolgen sollten korrekt geschrieben werden](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

- [CA1704: Bezeichner sollten korrekt geschrieben werden](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

- [CA1726: Bevorzugte Begriffe verwenden](../code-quality/ca1726-use-preferred-terms.md)

### <a name="BKMK_DictionaryWordsCompoundTermCompoundAlternate"></a>Wörterbuch/Wörter/Verbund/Begriff [@CompoundAlternate]

Mit dem integrierten Wörterbuch werden einige Begriffe als einzelne, diskrete Begriffe und nicht als zusammengesetzter Begriff identifiziert. Fügen Sie den Begriff als inneren Text eines Dictionary/Words/Compound/Term-Elements hinzu, um einen Begriff in die Liste der Begriffe einzuschließen, die die Code Analyse als zusammengesetztes Wort identifiziert, und um die richtige Schreibweise der Bezeichnung anzugeben. Geben Sie im compoundalternate-Attribut des Begriffs Elements die einzelnen Wörter an, aus denen der zusammengesetzte Begriff besteht, indem Sie den ersten Buchstaben der einzelnen Wörter (Pascal-Fall) groß machen. Beachten Sie, dass der im inneren Text angegebene Begriff automatisch der Wörterbuch/Words/diskreteexceptions-Liste hinzugefügt wird.

- Beim zusammengesetzten Begriff im Dictionary/Words/Compound/Term-Element wird die Groß-/Kleinschreibung nicht beachtet.

- Beim compoundalternate-Attribut Wert wird die Groß-/Kleinschreibung beachtet. Verwenden Sie Pascal Case für Verbund Alternativen.

**Beispiel**

```xml
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

Begriffe im Wörterbuch/Wörter/Verbund Knoten werden auf die folgenden Code Analyse Regeln angewendet:

- [CA1701: Bei zusammengesetzten Begriffen in Ressourcenzeichenfolgen sollte die Groß-/Kleinschreibung beachtet werden](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

- [CA1702: Bei zusammengesetzten Begriffen sollte die Groß-/Kleinschreibung beachtet werden](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

- [CA1703: Ressourcenzeichenfolgen sollten korrekt geschrieben werden](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

- [CA1704: Bezeichner sollten korrekt geschrieben werden](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

### <a name="BKMK_DictionaryWordsDiscreteExceptionsTerm"></a>Dictionary/Words/diskreteexceptions/Term

Um einen Begriff in der Liste der Begriffe auszuschließen, die die Code Analyse als einzelnes, diskretes Wort identifiziert, wenn der Begriff durch die Regeln der Groß-/Kleinschreibung für zusammengesetzte Wörter geprüft wird, fügen Sie den Begriff als inneren Text eines Dictionary/Words/diskreteexceptions/Term-Elements hinzu. Beim Begriff "Dictionary/Words/diskreteexceptions/Term Element" wird die Groß-/Kleinschreibung nicht beachtet.

**Beispiel**

```xml
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

Die Begriffe im Knoten Wörterbuch/Wörter/diskreteexceptions werden auf die folgenden Code Analyse Regeln angewendet:

- [CA1701: Bei zusammengesetzten Begriffen in Ressourcenzeichenfolgen sollte die Groß-/Kleinschreibung beachtet werden](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

- [CA1702: Bei zusammengesetzten Begriffen sollte die Groß-/Kleinschreibung beachtet werden](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

### <a name="BKMK_DictionaryAcronymsCasingExceptionsAcronym"></a>Dictionary/Akronyme/CasingExceptions/Akronym

Wenn Sie ein Akronym in die Liste der Begriffe einschließen möchten, die von der Code Analyse als richtig geschrieben identifiziert werden, und um anzugeben, wie das Akronym, wenn der Begriff durch die Regeln der Groß-und Kleinschreibung für Verbund Wörter geprüft wird, den Begriff als inneren Text eines Wörterbuchs/Akronymen/CasingExceptions/ Akronym-Element. Beim Akronym im Wörterbuch/Akronyme/CasingExceptions/Akronym-Element wird die Groß-/Kleinschreibung beachtet.

**Beispiel**

```xml
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

Begriffe im Knoten "Dictionary/acronyme/CasingExceptions" werden auf die folgenden Code Analyse Regeln angewendet:

- [CA1709: Bei Bezeichnern sollte die Groß-/Kleinschreibung beachtet werden](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

## <a name="BKMK_ToApplyACustomDictionaryToAProject"></a>So verwenden Sie ein benutzerdefiniertes Wörterbuch auf ein Projekt

1. Verwenden Sie in **Projektmappen-Explorer**eines der folgenden Verfahren:

2. Klicken Sie mit der rechten Maustaste auf den Projektnamen, und klicken Sie dann auf **Vorhandenes Element hinzufügen**. Geben Sie die Datei im Dialogfeld **Vorhandenes Element hinzufügen** an.

3. Wenn Sie ein Wörterbuch hinzufügen möchten, das von zwei oder mehr Projekten gemeinsam verwendet wird, suchen Sie im Dialogfeld **Vorhandenes Element hinzufügen** die Datei, die Sie freigeben möchten, klicken Sie auf die Schaltfläche **Hinzufügen** und dann auf **als Link hinzu**fügen.

4. Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf den Dateinamen **CustomDictionary. XML** , und klicken Sie dann auf **Eigenschaften**.

5. Wählen Sie in **der Liste** Buildvorgang die Option **codeanalysisdictionary**aus.

6. Wählen Sie **in der Liste in Ausgabeverzeichnis kopieren** die Option **nicht kopieren**aus.
