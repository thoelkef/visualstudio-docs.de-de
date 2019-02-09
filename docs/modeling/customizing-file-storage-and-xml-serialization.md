---
title: Anpassen von Dateispeicher und XML-Serialisierung
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.xmlbehavior
helpviewer_keywords:
- Domain-Specific Language, serialization
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 07efe6f73047efe389722bdeac8fa28ca4448cf1
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55944935"
---
# <a name="customize-file-storage-and-xml-serialization"></a>Anpassen von Dateispeicher und XML-Serialisierung

Wenn der Benutzer eine Instanz, speichert oder *Modell*, der eine domänenspezifische Sprache (DSL) in Visual Studio, eine XML-Datei erstellt oder aktualisiert wurde. Die Datei kann neu geladen werden, um das Modell in den Store neu zu erstellen.

Sie können das Serialisierungsschema anpassen, indem Sie die Einstellungen unter Anpassen **XML-Serialisierungsverhalten** im DSL-Explorer. Es gibt ein Knoten unter **XML-Serialisierungsverhalten** für jede Domänenklasse, die Eigenschaft und die Beziehung. Die Beziehungen befinden sich unter der Quellklassen. Es gibt auch Knoten an die Form, Connector und diagrammklassen entsprechen.

Sie können auch den Programmcode für eine erweiterte Anpassung schreiben.

> [!NOTE]
> Wenn das Modell in einem bestimmten Format gespeichert werden soll, aber Sie nicht über dieses Formular erneut laden müssen, sollten Sie mithilfe von Textvorlagen Ausgabe aus dem Modell, anstatt eine benutzerdefinierte Serialisierung-Schema zu generieren. Weitere Informationen finden Sie unter [Generieren von Code aus einer domänenspezifischen Sprache](../modeling/generating-code-from-a-domain-specific-language.md).

## <a name="model-and-diagram-files"></a>Modell und die Diagrammdateien

Jedes Modell wird in der Regel in zwei Dateien gespeichert:

-   Die Modelldatei hat einen Namen, z. B. **Model1.mydsl**. Sie speichert die Modellelemente und Beziehungen und deren Eigenschaften. Die Dateierweiterung, z. B. **.mydsl** richtet sich nach der **FileExtension** Eigenschaft der **Editor** Knoten in der DSL-Definition.

-   Die Diagrammdatei hat einen Namen, z. B. **Model1.mydsl.diagram**. Sie speichert die Formen, Connectors, und ihre Positionen, Farben, Strichstärken und andere Details der Darstellung des Diagramms. Wenn der Benutzer löscht eine **. Diagram** -Datei, die wichtige Informationen im Modell sind nicht verloren gegangen. Nur das Layout des Diagramms geht verloren. Wenn die Modelldatei geöffnet wird, wird ein Standardsatz von Formen und Connectors erstellt werden.

### <a name="to-change-the-file-extension-of-a-dsl"></a>So ändern Sie die Erweiterung einer DSL

1.  Öffnen Sie die DSL-Definition. Klicken Sie im DSL-Explorer auf den Knoten-Editor.

2.  Bearbeiten Sie im Fenster Eigenschaften die **FileExtension** Eigenschaft. Fügen Sie den ersten keine "." von der Erweiterung.

3.  Ändern Sie im Projektmappen-Explorer den Namen des in der zwei elementvorlagendateien **DslPackage\ProjectItemTemplates**. Diese Dateien haben Namen, die das folgende Format aufweisen:

     `myDsl.diagram`

     `myDsl.myDsl`

## <a name="the-default-serialization-scheme"></a>Das Standardschema für die Serialisierung

Um ein Beispiel für dieses Thema zu erstellen, wurde die folgende DSL-Definition verwendet.

![DSL-Definitionsdiagramm &#45; stammstrukturmodell](../modeling/media/familyt_person.png)

Diese DSL wurde zum Erstellen eines Modells mit dem folgenden Aussehen auf dem Bildschirm verwendet.

![Stammstrukturdiagramm, Toolbox und Explorer](../modeling/media/familyt_instance.png)

Dieses Modell wurde gespeichert, und klicken Sie dann erneut in die XML-Text-Editor geöffnet:

```xml
<?xml version="1.0" encoding="utf-8"?>
<familyTreeModel xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0" Id="f817b728-e920-458e-bb99-98edc469d78f" xmlns="http://schemas.microsoft.com/dsltools/FamilyTree">
  <people>
    <person name="Henry VIII" birthYear="1491" deathYear="1547" age="519">
      <children>
        <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Elizabeth I" />
        <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Mary" />
      </children>
    </person>
    <person name="Elizabeth I" birthYear="1533" deathYear="1603" age="477" />
    <person name="Mary" birthYear="1515" deathYear="1558" age="495" />
  </people>
</familyTreeModel>
```

Beachten Sie, dass die folgenden Punkte zu das serialisierte Modell:

-   Dieser XML-Knoten hat einen Namen, der einen Domänennamen für die Klasse, identisch ist, mit dem Unterschied, dass der erste Buchstabe der klein geschrieben ist. Beispiel: `familyTreeModel` und `person`.

-   Domäneneigenschaften wie Name und BirthYear werden in die XML-Knoten als Attribute serialisiert. In diesem Fall wird das erste Zeichen von der Eigenschaftenname in Kleinbuchstaben konvertiert.

-   Jede Beziehung wird als ein XML-Knoten, die das Quellende der Beziehung geschachtelt serialisiert. Der Knoten besitzt den gleichen Namen wie die Quelleigenschaft für die Rolle, jedoch mit einem anfänglichen Kleinbuchstaben.

     Z. B. in der DSL-Definition eine Rolle mit dem Namen **Personen** ist bezogen auf die **FamilyTree** Klasse.  In der XML, wird dies durch die Knoten mit dem Namen `people` in geschachtelt die `familyTreeModel` Knoten.

-   Das Zielende jeder einbettenden Beziehung wird als Knoten unter die Beziehung geschachtelt serialisiert. Z. B. die `people` Knoten enthält mehrere `person` Knoten.

-   Das Zielende der einzelnen verweisbeziehung wird als serialisiert eine *Moniker*, einen Verweis auf das Zielelement codiert.

     Beispielsweise unter einem `person` Knoten kann ein `children` Beziehung. Dieser Knoten enthält die Moniker wie z.B.:

    ```xml
    <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Elizabeth I" />
    ```

## <a name="understand-monikers"></a>Verstehen von Monikern

Moniker werden verwendet, um Querverweise zwischen verschiedenen Teilen der Dateien Modell und dem Diagramm darzustellen. Sie werden auch verwendet, der `.diagram` Datei zum Verweisen auf Knoten in der Datei des Modells. Es gibt zwei Arten von Moniker:

-   *ID-Moniker* die GUID des Target-Elements Angebot. Zum Beispiel:

    ```xml
    <personShapeMoniker Id="f79734c0-3da1-4d72-9514-848fa9e75157" />
    ```

-   *Wichtige Moniker qualifizierten* Target-Elements zu identifizieren, indem Sie den Wert einer bestimmten Domäne-Eigenschaft, die der monikerschlüssel aufgerufen. Der Moniker des Target-Elements ist der Moniker des übergeordneten Elements in der Struktur einbettender Beziehungen vorangestellt.

     Die folgenden Beispiele stammen aus eine, die DSL in dem es gibt eine Domänenklasse, die mit dem Namen Album, mit einer einbettenden Beziehung zu einer Domäne benannten "Song"-Klasse:

    ```xml
    <albumMoniker title="/My Favorites/Jazz after Teatime" />
    <songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />
    ```

     Qualifizierten Key Moniker verwendet werden, wenn die Zielklasse eine Domäneneigenschaft für den hat die Option **wird der Monikerschlüssel** nastaven NA hodnotu `true` in **XML-Serialisierungsverhalten**. Im Beispiel ist diese Option für die Domäneneigenschaften, die mit dem Namen "Title" in den Domänenklassen "Album" und "Song" festgelegt.

Qualifizierte Key Moniker sind einfacher zu lesen als ID-Moniker. Wenn der XML-Code der Modelldateien von Personen gelesen werden soll, sollten erwägen Sie, qualifizierte Key Moniker zu verwenden. Allerdings ist es möglich, dass der Benutzer mehr als ein Element auf dem gleichen Moniker Schlüssel festlegen. Doppelte Schlüssel können dazu führen, dass die Datei nicht ordnungsgemäß laden. Aus diesem Grund, wenn Sie eine Domänenklasse, die mit qualifizierten Key Moniker verwiesen wird definieren, sollten Sie Methoden zum verhindern, dass der Benutzer Speichern einer Datei, die doppelte Moniker verfügt.

### <a name="to-set-a-domain-class-to-be-referenced-by-id-monikers"></a>Festlegen eine Domänenklasse von ID-Moniker verwiesen wird

1.  Stellen Sie sicher, dass **wird der Monikerschlüssel** ist `false` für jede Domäneneigenschaft in der Klasse und ihre Basisklassen.

    1.  Erweitern Sie im DSL-Explorer **XML-Serialisierungsdaten Behavior\Class\\\<der Domänenklasse > \Element Daten**.

    2.  Überprüfen Sie, ob **wird der Monikerschlüssel** ist `false` für jede Domäneneigenschaft.

    3.  Wenn die Domänenklasse eine Basisklasse verfügt, wiederholen Sie das Verfahren in dieser Klasse.

2.  Legen Sie **Id Serialisieren**  =  `true` für die Domänenklasse.

     Diese Eigenschaft finden Sie unter **XML-Serialisierungsverhalten**.

### <a name="to-set-a-domain-class-to-be-referenced-by-qualified-key-monikers"></a>Festlegen eine Domänenklasse von qualifizierten Key Moniker verwiesen wird

-   Legen Sie **wird der Monikerschlüssel** für eine Domäneneigenschaft einer vorhandenen Domäne-Klasse. Der Typ der Eigenschaft muss `string`.

    1.  Erweitern Sie im DSL-Explorer **XML-Serialisierungsdaten Behavior\Class\\\<der Domänenklasse > \Element Daten**, und wählen Sie dann die Eigenschaft "Domain".

    2.  Legen Sie im Eigenschaftenfenster **wird der Monikerschlüssel** zu `true`.

-   \- oder –

     Erstellen Sie eine neue Domäne-Klasse, mit der **benannte Domänenklasse** Tool.

     Dieses Tool erstellt eine neue Klasse mit einer Domäneneigenschaft als Name bezeichnet. Die **ist Elementname** und **wird der Monikerschlüssel** Eigenschaften dieser Domäneneigenschaft werden initialisiert, um `true`.

-   \- oder –

     Erstellen Sie eine Vererbungsbeziehung besteht aus der Domänenklasse an eine andere Klasse, die über eine Schlüsseleigenschaft Moniker verfügt.

### <a name="avoid-duplicate-monikers"></a>Vermeiden Sie doppelte Moniker

Wenn Sie qualifizierte Key Moniker verwenden, ist es möglich, dass zwei Elemente im Modell für einen Benutzer den gleichen Wert in die Schlüsseleigenschaft verfügen können. Verfügt Ihre DSL für eine Person-Klasse, die eine Name-Eigenschaft verfügt, kann der Benutzer z. B. die Namen von zwei Elementen identisch festlegen. Obwohl Sie möglicherweise das Modell in Datei gespeichert, es wäre nicht erneut lädt, richtig.

Es gibt mehrere Methoden, die dieses Problem zu vermeiden:

-   Legen Sie **ist Elementname**  =  `true` für die wichtigsten Domäneneigenschaft. Wählen Sie die Eigenschaft "Domain" im DSL-Definitionsdiagramm, und legen Sie den Wert im Fenster Eigenschaften.

     Wenn der Benutzer eine neue Instanz der Klasse erstellt wird, bewirkt dieser Wert der Eigenschaft "Domain" automatisch einen anderen Wert zugewiesen werden soll. Standardmäßig fügt eine Zahl am Ende den Namen der Klasse. Dies verhindert, dass des Benutzers nicht den Namen ändern, um ein Duplikat, aber in die Groß-/Kleinschreibung unterstützt, wenn der Benutzer vor dem Speichern des Modells nicht den Wert festgelegt.

-   Aktivieren Sie die Validierung für die DSL. Klicken Sie im DSL-Explorer wählen editor\validierung, und legen die **verwendet...**  Eigenschaften `true`.

     Es gibt eine automatisch generierte Überprüfungsmethode, die überprüft, für Mehrdeutigkeiten. Die Methode wird in der `Load` Überprüfung Kategorie. Dadurch wird sichergestellt, dass der Benutzer gewarnt werden, wenn es möglicherweise nicht möglich, die Datei erneut zu öffnen.

     Weitere Informationen finden Sie unter [Validierung in einer domänenspezifischen Sprache](../modeling/validation-in-a-domain-specific-language.md).

### <a name="moniker-paths-and-qualifiers"></a>Der Moniker-Pfade und Qualifizierer

Ein qualifizierter Key Moniker endet mit dem monikerschlüssel und ein vorangestelltes mit dem Moniker, der das übergeordnete Element in der einbettenden Struktur. Angenommen, wenn der Moniker, der ein Album ist:

```xml
<albumMoniker title="/My Favorites/Jazz after Teatime" />
```

Klicken Sie dann möglicherweise einen Titel im jeweiligen Album zu sehen:

```xml
<songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />
```

Jedoch wenn Alben nach ID verwiesen werden, würde dann die Moniker wie folgt lauten:

```xml
<albumMoniker Id="77472c3a-9bf9-4085-976a-d97a4745237c" />
<songMoniker title="/77472c3a-9bf9-4085-976a-d97a4745237c/Hot tea" />
```

Beachten Sie, da eine GUID eindeutig ist, sie nie den Moniker des übergeordneten Objekts vorangestellt wird.

Wenn Sie wissen, dass eine bestimmte Domäne-Eigenschaft immer über einen eindeutigen Wert in einem Modell hat, legen Sie **Monikerqualifizierer ist** zu `true` für diese Eigenschaft. Dadurch wird es als ein Qualifizierer, verwendet werden kann, ohne den Moniker des übergeordneten Elements verursacht. Z. B., wenn Sie beide Optionen festlegen **Monikerqualifizierer ist** und **wird der Monikerschlüssel** für die Title-Eigenschaft der Domäne der Album-Klasse, Namen\noder Bezeichner des Modells wird nicht verwendet in Monikern Album und seine eingebetteten untergeordnete Elemente:

```xml
<albumMoniker name="Jazz after Teatime" />
<songMoniker title="/Jazz after Teatime/Hot tea" />
```

## <a name="customize-the-structure-of-the-xml"></a>Anpassen der XML-Struktur

Um die folgenden Anpassungen vorzunehmen, erweitern Sie die **XML-Serialisierungsverhalten** Knoten im DSL-Explorer. Erweitern Sie den Elementdaten-Knoten, um die Liste der Eigenschaften und Beziehungen, die auf diese Klasse erstellt werden, unter einer Domänenklasse. Wählen Sie eine Beziehung, und passen Sie die Optionen im Fenster Eigenschaften.

-   Legen Sie **Element weglassen** auf true festlegen, um der Rolle Quellknoten, verlassen einfach die Liste der Zielelemente zu unterdrücken. Sie sollten diese Option nicht festgelegt, wenn mehr als eine Beziehung zwischen den Quell- und Zielklassen vorhanden ist.

    ```xml
    <familyTreeModel ...>
      <!-- The following node is omitted by using Omit Element: -->
      <!-- <people> -->
        <person name="Henry VIII" .../>
        <person name="Elizabeth I" .../>
      <!-- </people> -->
    </familyTreeModel>
    ```

-   Legen Sie **verwenden vollständiger Form** zum Einbetten von Zielknoten in Knoten die Beziehungsinstanzen darstellt. Diese Option wird automatisch festgelegt, wenn Sie die Domäneneigenschaften einer domänenbeziehung hinzufügen.

    ```xml
    <familyTreeModel ...>
      <people>
        <!-- The following node is inserted by using Use Full Form: -->
        <familyTreeModelHasPeople myRelationshipProperty="x1">
          <person name="Henry VIII" .../>
        </familyTreeModelHasPeople>
        <familyTreeModelHasPeople myRelationshipProperty="x2">
          <person name="Elizabeth I" .../>
        </familyTreeModelHasPeople>
      </people>
    </familyTreeModel>
    ```

-   Legen Sie **Darstellung** = **Element** eine Domäneneigenschaft als ein Element nicht als Attributwerte gespeichert haben.

    ```xml
    <person name="Elizabeth I" birthYear="1533">
      <deathYear>1603</deathYear>
    </person>
    ```

-   Klicken Sie zum Ändern der Reihenfolge, in denen Attribute und Beziehungen werden serialisiert, mit der rechten Maustaste unter Elementdaten ein Element, und Verwenden der **nach oben** oder **nach unten** Menübefehle.

## <a name="major-customization-using-program-code"></a>Wichtige Anpassung, die mithilfe von Programmcode

Sie können teilweise oder vollständig von der Serialisierung Algorithmen ersetzen.

Es wird empfohlen, dass Sie den Code in untersuchen **Dsl\Generated Code\Serializer.cs** und **SerializationHelper.cs**.

### <a name="to-customize-the-serialization-of-a-particular-class"></a>Um die Serialisierung einer bestimmten Klasse anzupassen

1.  Legen Sie **ist Benutzerdefiniert** im Knoten für diese Klasse unter **XML-Serialisierungsverhalten**.

2.  Transformieren Sie alle Vorlagen, erstellen Sie die Projektmappe, und untersuchen Sie die resultierende Kompilierungsfehler. Kommentare in der Nähe von jeder Fehler wird erläutert, Sie angeben müssen, welchen Code.

### <a name="to-provide-your-own-serialization-for-the-whole-model"></a>Um eigene Serialisierung für das gesamte Modell bereitzustellen.

1.  Überschreiben Sie Methoden in Dsl\GeneratedCode\SerializationHelper.cs

## <a name="options-in-xml-serialization-behavior"></a>Optionen im XML-Serialisierungsverhalten

Im DSL-Explorer enthält die XML-Serialisierungsverhalten-Knoten einen untergeordneter Knoten für jede Domänenklasse, die Beziehung, die Form, Connector und Diagrammklasse. Unter diesen Knoten die ist eine Liste der Eigenschaften und Beziehungen, die auf dieses Element aus. Beziehungen werden sich genommen schon sowohl unter ihrer Datenquelle Klassen dargestellt.

Die folgende Tabelle enthält die Optionen, die Sie in diesem Abschnitt der DSL-Definition festlegen können. Klicken Sie in jedem Fall wählen Sie ein Element im DSL-Explorer, und legen Sie die Optionen im Fenster Eigenschaften.

### <a name="xml-class-data"></a>XML-Klassendaten

Diese Elemente finden Sie im DSL-Explorer unter **XML-Serialisierungsdaten Behavior\Class**.

|||
|-|-|
|Eigenschaft|Beschreibung|
|Hat benutzerdefiniertes Elementschema|True gibt an, dass die Domänenklasse ein benutzerdefiniertes elementschema besitzt.|
|Benutzerdefinierte|Legen Sie diesen **"true"** Wenn eigene Serialisierung und Deserialisierung Code für diese Domänenklasse geschrieben werden soll.<br /><br /> Erstellen Sie die Projektmappe, und untersuchen Sie die Fehler, um ausführliche Anweisungen zu ermitteln.|
|Domänenklasse|Die Domänenklasse für die diese Klasse Datenknoten gilt. Schreibgeschützt.|
|Elementname|XML-Knoten-Name für Elemente dieser Klasse. Der Standardwert ist eine lower-case-Version des Domänennamens-Klasse.|
|Der Moniker-Attributname|Der Name des Attributs in der Moniker-Elemente verwendet, um den Verweis enthält. Wenn Sie leer ist, wird der Name der Schlüsseleigenschaft oder -Id verwendet.<br /><br /> In diesem Beispiel ist es, "name":  `<personMoniker name="/Mike Nash"/>`|
|Monikerelementname|Der Name des XML-Elements für den Moniker, die Elemente dieser Klasse verweisen, verwendet.<br /><br /> Der Standardwert ist der Klassenname "Moniker" als Suffix in Kleinbuchstaben. Beispielsweise `personMoniker`.|
|Der Moniker-Typname|Der Name des Xsd-Typs für Moniker für Elemente dieser Klasse generiert. XSD-Code befindet sich in **Dsl\Generated Code\\\*Schema.xsd**|
|Id serialisieren|Wenn "true", das GUID-Element in der Datei enthalten ist. Dies erfüllt sein, wenn keine Eigenschaft, die markiert ist **wird der Monikerschlüssel** und die DSL definiert verweisbeziehungen für diese Klasse.|
|Typname|Der Name des Xml-Datentyps in der XSD-Datei aus der angegebenen Domänenklasse generiert.|
|Hinweise|Informelle Hinweise, die mit diesem Element verknüpft sind|

### <a name="xml-property-data"></a>XML-Daten

Eigenschaft "XML"-Knoten befinden sich unter den Knoten für die Klasse.

|||
|-|-|
|Eigenschaft|Beschreibung|
|Eigenschaft "Domain"|Die Eigenschaft, die Xml-serialisierungskonfigurationsdaten gelten. Schreibgeschützt.|
|Wird der Monikerschlüssel|Bei "true", dient die Eigenschaft als Schlüssel für das Erstellen von Monikern, die Instanzen dieser Domänenklasse verweisen.|
|Is Moniker Qualifier|Wenn True, wird die Eigenschaft zum Erstellen des Qualifizierers in Monikern verwendet. Wenn "false", und SerializeId nicht "true" für diese Domänenklasse ist, werden Moniker durch den Moniker, der das übergeordnete Element in der einbettenden Struktur qualifiziert.|
|Darstellung|Wenn das Attribut, das die Eigenschaft als XML-Attribut serialisiert wird; Wenn das Element, es ist als ein Element serialisiert Falls Sie nicht serialisiert.|
|XML-Name|Namen für die XML-Attribut oder Element, das die Eigenschaft darstellt. Standardmäßig ist dies eine lower-case-Version vom Namen Domäne.|
|Hinweise|Informelle Hinweise, die mit diesem Element verknüpft sind|

### <a name="xml-role-data"></a>Rolle des XML-Daten

Rolle Datenknoten befinden sich unter den Knoten der Source-Klasse.

|Eigenschaft|Beschreibung|
|-|-|
|Hat benutzerdefinierte Moniker|Legen Sie diese auf "true", wenn Sie möchten, geben Sie Ihren eigenen Code zum Generieren und Auflösen von Monikern, die diese Beziehung zu durchlaufen.<br /><br /> Ausführliche Anweisungen dazu erstellen Sie die Projektmappe, und doppelklicken Sie dann auf die Fehlermeldungen.|
|Domänenbeziehung|Gibt die Beziehung zu der diese Optionen gelten. Schreibgeschützt.|
|Element weglassen|Wenn "true", wird der XML-Knoten, der die die Quellrolle entspricht, aus dem Schema ausgelassen.<br /><br /> Liegt mehr als eine Beziehung zwischen den Quell- und Zielklassen, unterscheidet sich dieser rollenknoten zwischen Links, die die beiden Beziehungen angehören. Aus diesem Grund wird empfohlen, dass Sie diese Option nicht in diesem Fall festgelegt.|
|Rollenname-Element|Gibt den Namen des XML-Elements, das der Quellrolle abgeleitet ist. Der Standardwert ist der Eigenschaftsname der Rolle.|
|Verwenden Sie vollständige Format|Bei "true", wird jede Target-Element oder Moniker in ein XML-Knoten, die die Beziehung darstellt eingeschlossen. Dies sollte festgelegt werden, auf "true", wenn die Beziehung über eigene Domäneneigenschaften verfügt.|

## <a name="see-also"></a>Siehe auch

- [Navigieren in und Aktualisieren von Modellen im Programmcode](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Generieren von Code für eine domänenspezifische Sprache](../modeling/generating-code-from-a-domain-specific-language.md)