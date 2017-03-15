---
title: "Gewusst wie: Anpassen des Codeanalysew&#246;rterbuchs | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Codeanalysewörterbuch"
  - "Benutzerdefiniertes Wörterbuch, Codeanalyse"
  - "Wörterbuch, Codeanalyse"
ms.assetid: 667e3b4e-beff-48be-b3d1-376e1716a895
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 21
---
# Gewusst wie: Anpassen des Codeanalysew&#246;rterbuchs
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die Codeanalyse überprüft Bezeichner im Code mithilfe eines integrierten Wörterbuchs auf Fehler in der Rechtschreibung, den grammatischen Fällen und anderen Namenskonventionen der [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]\-Richtlinien.  Sie können eine XML\-Datei für ein Benutzerwörterbuch erstellen, um zusätzlich zum integrierten Wörterbuch Begriffe, Abkürzungen und Akronyme hinzuzufügen, zu entfernen oder zu ändern.  
  
 Beispiel: Ihr Code enthält eine Klasse mit dem Namen **DoorKnokker**.  Der Bezeichner wird von der Codeanalyse als Zusammensetzung von zwei Wörtern identifiziert: **door** und **knokker**.  Anschließend wird eine Warnung mit dem Hinweis ausgegeben, dass **knokker** nicht korrekt geschrieben ist.  Um in der Codeanalyse die Erkennung der Rechtschreibung zu erzwingen, können Sie dem Benutzerwörterbuch den Begriff **knokker** hinzufügen.  
  
## So erstellen Sie ein benutzerdefiniertes Wörterbuch  
 Erstellen Sie eine Datei mit dem Namen **CustomDictionary.xml**.  
  
 Definieren Sie die benutzerdefinierten Wörter unter Verwendung der folgenden XML\-Struktur:  
  
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
            <Term PreferredAlternate=""></Term>  
         </Deprecated>  
         <Compound>  
            <Term CompoundAlternate=""></Term>  
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
  
## Elemente im Benutzerwörterbuch  
 Sie können das Verhalten des Codeanalysewörterbuchs ändern, indem Sie Begriffe als inneren Text der folgenden Elemente im Benutzerwörterbuch hinzufügen:  
  
-   [Dictionary/Words/Recognized/Word](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsRecognizedWord)  
  
-   [Dictionary/Words/Unrecognized/Word](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsUnrecognizedWord)  
  
-   [Dictionary/Words/Deprecated/Term[@PreferredAlternate]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDeprecatedTermPreferredAlternate)  
  
-   [Dictionary/Words/Compound/Term[@CompoundAlternate]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsCompoundTermCompoundAlternate)  
  
-   [Dictionary/Words/DiscreteExceptions/Term](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDiscreteExceptionsTerm)  
  
-   [Dictionary/Acronyms/CasingExceptions/Acronym](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryAcronymsCasingExceptionsAcronym)  
  
###  <a name="BKMK_DictionaryWordsRecognizedWord"></a> Dictionary\/Words\/Recognized\/Word  
 Um einen Begriff in die Liste der Begriffe aufzunehmen, die die Codeanalyse als korrekt geschrieben identifiziert, fügen Sie den Begriff als inneren Text in einem Dictionary\/Words\/Recognized\/Word\-Element hinzu.  Bei Begriffen in Dictionary\/Words\/Recognized\/Word\-Elementen wird die Groß\-\/Kleinschreibung nicht beachtet.  
  
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
  
 Begriffe in Dictionary\/Words\/Recognized\-Knoten werden auf die folgenden Codeanalyseregeln angewendet:  
  
-   [CA1701: Bei zusammengesetzten Begriffen in Ressourcenzeichenfolgen sollte die Groß\-\/Kleinschreibung beachtet werden](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
-   [CA1702: Bei zusammengesetzten Begriffen sollte die Groß\-\/Kleinschreibung beachtet werden](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
-   [CA1703: Ressourcenzeichenfolgen sollten korrekt geschrieben werden](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
-   [CA1704: Bezeichner sollten korrekt geschrieben werden](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
-   [CA1709: Bei Bezeichnern sollte die Groß\-\/Kleinschreibung beachtet werden](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
-   [CA1726: Bevorzugte Begriffe verwenden](../code-quality/ca1726-use-preferred-terms.md)  
  
-   [CA2204: Literale sollten eine korrekte Rechtschreibung aufweisen](../code-quality/ca2204-literals-should-be-spelled-correctly.md)  
  
###  <a name="BKMK_DictionaryWordsUnrecognizedWord"></a> Dictionary\/Words\/Unrecognized\/Word  
 Um einen Begriff aus der Liste der Begriffe auszuschließen, die die Codeanalyse als korrekt geschrieben identifiziert, fügen Sie den auszuschließenden Begriff als inneren Text in einem Dictionary\/Words\/Unrecognized\/Word\-Element hinzu.  Bei Begriffen in Dictionary\/Words\/Unrecognized\/Word\-Elementen wird die Groß\-\/Kleinschreibung nicht beachtet.  
  
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
  
 Begriffe im Dictionary\/Words\/Unrecognized\-Knoten werden auf die folgenden Codeanalyseregeln angewendet:  
  
-   [CA1701: Bei zusammengesetzten Begriffen in Ressourcenzeichenfolgen sollte die Groß\-\/Kleinschreibung beachtet werden](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
-   [CA1702: Bei zusammengesetzten Begriffen sollte die Groß\-\/Kleinschreibung beachtet werden](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
-   [CA1703: Ressourcenzeichenfolgen sollten korrekt geschrieben werden](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
-   [CA1704: Bezeichner sollten korrekt geschrieben werden](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
-   [CA1709: Bei Bezeichnern sollte die Groß\-\/Kleinschreibung beachtet werden](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
-   [CA1726: Bevorzugte Begriffe verwenden](../code-quality/ca1726-use-preferred-terms.md)  
  
-   [CA2204: Literale sollten eine korrekte Rechtschreibung aufweisen](../code-quality/ca2204-literals-should-be-spelled-correctly.md)  
  
###  <a name="BKMK_DictionaryWordsDeprecatedTermPreferredAlternate"></a> Dictionary\/Words\/Deprecated\/Term\[@PreferredAlternate\]  
 Um einen Begriff in die Liste der Begriffe aufzunehmen, die die Codeanalyse als veraltet identifiziert, fügen Sie den Begriff als inneren Text in einem Dictionary\/Words\/Deprecated\/Term\-Element hinzu.  Ein veralteter Begriff ist ein Wort, das ordnungsgemäß geschrieben ist, aber nicht mehr verwendet werden sollte.  
  
 Um einen Alternativvorschlag für den Begriff in der Warnung anzugeben, geben Sie die Alternative im PreferredAlternate\-Attribut des Term\-Elements an.  Sie können den Attributwert leer lassen, wenn Sie keine Alternative vorschlagen möchten.  
  
-   Bei veralteten Begriffen in Dictionary\/Words\/Deprecated\/Term\-Elementen wird die Groß\-\/Kleinschreibung nicht beachtet.  
  
-   Beim PreferredAlternate\-Attributwert wird die Groß\-\/Kleinschreibung beachtet.  Verwenden Sie Pascal\-Schreibweise für zusammengesetzte Alternativen.  
  
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
  
 Begriffe im Dictionary\/Words\/Deprecated\-Knoten werden auf die folgenden Codeanalyseregeln angewendet:  
  
-   [CA1701: Bei zusammengesetzten Begriffen in Ressourcenzeichenfolgen sollte die Groß\-\/Kleinschreibung beachtet werden](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
-   [CA1702: Bei zusammengesetzten Begriffen sollte die Groß\-\/Kleinschreibung beachtet werden](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
-   [CA1703: Ressourcenzeichenfolgen sollten korrekt geschrieben werden](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
-   [CA1704: Bezeichner sollten korrekt geschrieben werden](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
-   [CA1726: Bevorzugte Begriffe verwenden](../code-quality/ca1726-use-preferred-terms.md)  
  
###  <a name="BKMK_DictionaryWordsCompoundTermCompoundAlternate"></a> Dictionary\/Words\/Compound\/Term\[@CompoundAlternate\]  
 Das integrierte Wörterbuch identifiziert einige bestimmte Begriffe als einen Begriff anstatt als zusammengesetzten Begriff.  Um einen Begriff in die Liste der Begriffe aufzunehmen, die die Codeanalyse als zusammengesetzten Begriff identifiziert, und um die korrekte Groß\-\/Kleinschreibung des Begriffs festzulegen, fügen Sie den Begriff als inneren Text in einem Dictionary\/Words\/Compound\/Term\-Element hinzu.  Geben Sie im CompoundAlternate\-Attribut des Term\-Elements die einzelnen Wörter an, die den zusammengesetzten Begriff bilden, indem Sie den ersten Buchstaben jedes Worts groß schreiben \(Pascal\-Schreibweise\).  Beachten Sie, dass der im inneren Text angegebene Begriff automatisch der Dictionary\/Words\/DiscreteExceptions\-Liste hinzugefügt wird.  
  
-   Bei veralteten Begriffen in Dictionary\/Words\/Deprecated\/Term\-Elementen wird die Groß\-\/Kleinschreibung nicht beachtet.  
  
-   Beim PreferredAlternate\-Attributwert wird die Groß\-\/Kleinschreibung beachtet.  Verwenden Sie Pascal\-Schreibweise für zusammengesetzte Alternativen.  
  
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
  
 Begriffe im Dictionary\/Words\/Compound\-Knoten werden auf die folgenden Codeanalyseregeln angewendet:  
  
-   [CA1701: Bei zusammengesetzten Begriffen in Ressourcenzeichenfolgen sollte die Groß\-\/Kleinschreibung beachtet werden](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
-   [CA1702: Bei zusammengesetzten Begriffen sollte die Groß\-\/Kleinschreibung beachtet werden](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
-   [CA1703: Ressourcenzeichenfolgen sollten korrekt geschrieben werden](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
-   [CA1704: Bezeichner sollten korrekt geschrieben werden](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
###  <a name="BKMK_DictionaryWordsDiscreteExceptionsTerm"></a> Dictionary\/Words\/DiscreteExceptions\/Term  
 Um einen Begriff aus der Liste der Begriffe auszuschließen, die die Codeanalyse bei der Überprüfung von zusammengesetzten Begriffen anhand der Groß\-\/Kleinschreibung als einzelnes Wort identifiziert, fügen Sie den Begriff als inneren Text eines Dictionary\/Words\/DiscreteExceptions\/Term\-Element hinzu.  Bei Begriffen in Dictionary\/Words\/DiscreteExceptions\/Term\-Elementen wird die Groß\-\/Kleinschreibung nicht beachtet.  
  
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
  
 Begriffe im Dictionary\/Words\/DiscreteExceptions\-Knoten werden auf die folgenden Codeanalyseregeln angewendet:  
  
-   [CA1701: Bei zusammengesetzten Begriffen in Ressourcenzeichenfolgen sollte die Groß\-\/Kleinschreibung beachtet werden](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
-   [CA1702: Bei zusammengesetzten Begriffen sollte die Groß\-\/Kleinschreibung beachtet werden](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
###  <a name="BKMK_DictionaryAcronymsCasingExceptionsAcronym"></a> Dictionary\/Acronyms\/CasingExceptions\/Acronym  
 Um ein Akronym in die Liste der Begriffe aufzunehmen, die die Codeanalyse als korrekt geschrieben identifiziert, und um anzugeben, wie das Akronym bei der Prüfung von zusammengesetzten Wörtern behandelt wird, fügen Sie den Begriff als inneren Text eines Dictionary\/Acronyms\/CasingExceptions\/Acronym\-Elements hinzu.  Bei Akronymen in Dictionary\/Acronyms\/CasingExceptions\/Acronym\-Elementen wird die Groß\-\/Kleinschreibung beachtet.  
  
 **Beispiel**  
  
```  
<Dictionary>  
      <Acronyms>  
         <CasingExceptions>  
            <Acronym>NESW</Acronym>   <!-- North East South West -->  
            ...  
         </CasingExceptions>  
         ...  
      </Acronyms>  
      ...  
</Dictionary>  
  
```  
  
 Begriffe im Dictionary\/Acronyms\/CasingExceptions\-Knoten werden auf die folgenden Codeanalyseregeln angewendet:  
  
-   [CA1709: Bei Bezeichnern sollte die Groß\-\/Kleinschreibung beachtet werden](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
##  <a name="BKMK_ToApplyACustomDictionaryToAProject"></a> So wenden Sie ein benutzerdefiniertes Wörterbuch auf ein Projekt an  
  
1.  Verwenden Sie im Projektmappen\-Explorer eine der folgenden Prozeduren:  
  
2.  Um einem einzelnen Projekt ein Wörterbuch hinzuzufügen, klicken Sie mit der rechten Maustaste auf den Projektnamen, und klicken Sie dann auf **Vorhandenes Element hinzufügen**.  Geben Sie im Dialogfeld **Vorhandenes Element hinzufügen** die gewünschte Datei an.  
  
3.  Suchen Sie im Dialogfeld **Vorhandenes Element hinzufügen** nach der gewünschten Datei, klicken Sie auf den Abwärtspfeil der Schaltfläche **Hinzufügen**, und klicken Sie anschließend auf **Als Link hinzufügen**, um ein für mehrere Projekte freigegebenes Wörterbuch hinzuzufügen.  
  
4.  Klicken Sie im Projektmappen\-Explorer mit der rechten Maustaste auf den Dateinamen **CustomDictionary.xml**, und klicken Sie auf **Eigenschaften**.  
  
5.  Wählen Sie in der Liste **Buildvorgang** die Option **CodeAnalysisDictionary** aus.  
  
6.  Wählen Sie in der Liste **In Ausgabeverzeichnis kopieren** die Option **Nicht kopieren** aus.