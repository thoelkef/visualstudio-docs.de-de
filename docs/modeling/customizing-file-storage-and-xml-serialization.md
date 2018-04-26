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
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: d9722bed4bcf20fbdba322bea7cd3aab4328fa7e
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="customize-file-storage-and-xml-serialization"></a>Speichern von Dateien und XML-Serialisierung anpassen

Wenn der Benutzer eine Instanz speichert oder *Modell*, der eine domänenspezifische Sprache (DSL) in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], eine XML-Datei erstellt oder aktualisiert wird. Die Datei kann neu geladen werden, um das Modell im Speicher neu zu erstellen.

Sie können das Serialisierungsschema anpassen, indem Sie die Einstellungen unter Anpassen **XML-Serialisierungsverhalten** im Explorer für DSL. Es ist ein Knoten unter **XML-Serialisierungsverhalten** für jede Domänenklasse, die Eigenschaft und die Beziehung. Die Beziehungen befinden sich unter ihrer Quellklassen. Es gibt auch Knoten an die Form, Connectors und Diagramm Klassen entsprechen.

Sie können auch den Programmcode für die erweiterte Anpassung schreiben.

> [!NOTE]
> Wenn das Modell in einem bestimmten Format gespeichert werden soll, aber Sie nicht erneut aus, die dieses Formular zu laden müssen, sollten Sie mithilfe von Textvorlagen-Ausgabe aus dem Modell, anstatt eine benutzerdefinierte Serialisierungsschema zu generieren. Weitere Informationen finden Sie unter [Generieren von Code aus einer domänenspezifischen Sprache](../modeling/generating-code-from-a-domain-specific-language.md).

## <a name="model-and-diagram-files"></a>Modell- und Diagrammdateien

Jedes Modell wird in der Regel in zwei Dateien gespeichert:

-   Die Modelldatei hat einen Namen, z. B. **Model1.mydsl**. Sie speichert die betroffenen Modellelemente und Beziehungen und ihre Eigenschaften. Die Dateierweiterung, z. B. **.mydsl** richtet sich nach der **FileExtension** Eigenschaft von der **Editor** Knoten in der DSL-Definition.

-   Die Diagrammdatei hat einen Namen, z. B. **Model1.mydsl.diagram**. Sie speichert die Formen, Connectors und ihre Positionen, Farben, Zeile Dicke und andere Details der Darstellung des Diagramms. Wenn der Benutzer löscht eine **.diagram** Datei, die wichtige Informationen im Modell geht nicht verloren. Nur das Layout des Diagramms geht verloren. Wenn die Datei geöffnet wird, eine Standardsammlung von Formen und Connectors erstellt werden.

### <a name="to-change-the-file-extension-of-a-dsl"></a>So ändern Sie die Erweiterung der DSL

1.  Öffnen Sie die DSL-Definition. DSL-Explorer klicken Sie auf den Knoten-Editor.

2.  Bearbeiten Sie im Fenster Eigenschaften die **FileExtension** Eigenschaft. Schließen Sie nicht den ersten "." von der Erweiterung.

3.  Ändern Sie im Projektmappen-Explorer den Namen von zwei Elementen Vorlagendateien in **DslPackage\ProjectItemTemplates**. Diese Dateien haben Namen, die das folgende Format aufweisen:

     `myDsl.diagram`

     `myDsl.myDsl`

## <a name="the-default-serialization-scheme"></a>Das Standardschema für die Serialisierung

Um ein Beispiel für dieses Thema zu erstellen, wurde die folgende DSL-Definition verwendet.

![DSL-Definitionsdiagramm &#45; stammbaummodell](../modeling/media/familyt_person.png)

Diese DSL wurde verwendet, um ein Modell zu erstellen, die folgende Darstellung auf dem Bildschirm verfügt.

![Stammstrukturdiagramm, Toolbox und Explorer](../modeling/media/familyt_instance.png)

Dieses Modell wurde gespeichert, und klicken Sie dann erneut in der XML-Text-Editor geöffnet:

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

Beachten Sie die folgenden Punkte bezüglich der serialisierten Modell:

-   Jede XML-Knoten hat einen Namen, der einen Domäne-Namen identisch ist, mit dem Unterschied, dass der erste Buchstabe Kleinbuchstaben ist. Beispielsweise `familyTreeModel` und `person`.

-   Domäneneigenschaften wie Name und BirthYear werden in der XML-Knoten als Attribute serialisiert. Erneut wird neben dem Eigenschaftsnamen das erste Zeichen in Kleinbuchstaben konvertiert.

-   Jede Beziehung wird als ein XML-Knoten geschachtelt Quellenende der Beziehung serialisiert. Der Knoten besitzt den gleichen Namen wie die Rolle Quelleigenschaft, jedoch mit einem Kleinbuchstaben Anfangszeichen.

     Beispielsweise ist in der DSL-Definition einer Rolle mit dem Namen **Personen** wird zur Quelle der **FamilyTree** Klasse.  In der XML-Code wird dies durch die Knoten mit dem Namen `people` in geschachtelt die `familyTreeModel` Knoten.

-   Das Zielende jeder Einbetten von Beziehung wird als Knoten unter der Beziehung geschachtelt serialisiert. Z. B. die `people` Knoten enthält mehrere `person` Knoten.

-   Das Zielende jeder Verweis Beziehung wird als serialisiert eine *Moniker*, die einen Verweis auf das Zielelement codiert.

     Beispielsweise unter ein `person` Knoten kann ein `children` Beziehung. Dieser Knoten enthält Moniker wie z.B.:

    ```xml
    <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Elizabeth I" />
    ```

## <a name="understand-monikers"></a>Verstehen der Moniker

Moniker werden verwendet, um Querverweise zwischen verschiedenen Teilen der Dateien Modell und dem Diagramm darzustellen. Sie werden auch verwendet, der `.diagram` Datei auf Knoten in der Modelldatei verweisen. Es gibt zwei Formen der Moniker:

-   *ID-Moniker* Angebot die GUID des Target-Element. Zum Beispiel:

    ```xml
    <personShapeMoniker Id="f79734c0-3da1-4d72-9514-848fa9e75157" />
    ```

-   *Key-Moniker qualifiziert* Target-Element identifizieren, indem Sie den Wert einer bestimmten Domäne-Eigenschaft, die als Moniker Primary Key bezeichnet. Der Moniker des Target-Element ist der Moniker des übergeordneten Elements in der Struktur der Beziehungen Einbettung vorangestellt.

     In den folgenden Beispielen werden von entnommen, die DSL in dem es ist eine Domänenklasse, die mit dem Namen Album, besitzt eine Einbetten von Beziehung zu einer Domäne benannte Musiktitel Klasse:

    ```xml
    <albumMoniker title="/My Favorites/Jazz after Teatime" />
    <songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />
    ```

     Qualifizierte Key Moniker verwendet werden, verfügt die Zielklasse eine Eigenschaft "Domain" für die die Option **ist der Moniker-Schlüssel** festgelegt ist, um `true` in **XML-Serialisierungsverhalten**. Im Beispiel wird diese Option für Eigenschaften von Domänen mit dem Namen "Title" in der Domänenklassen "Album" und "Titel" festgelegt.

Qualifizierte Key Moniker sind einfacher zu lesen als ID-Moniker. Wenn der XML-Code der Modelldateien von Personen gelesen werden soll, sollten erwägen Sie, qualifizierte Key Moniker zu verwenden. Es ist jedoch möglich, dass der Benutzer mehr als ein Element auf dem gleichen Moniker Schlüssel festlegen. Doppelter Schlüssel verursachen können, dass die Datei nicht ordnungsgemäß laden. Aus diesem Grund, wenn Sie eine Domänenklasse, die mit qualifizierten Key Moniker verwiesen wird definieren, sollten Sie Möglichkeiten zum verhindern, dass der Benutzer Speichern einer Datei, die doppelte Moniker verfügt.

### <a name="to-set-a-domain-class-to-be-referenced-by-id-monikers"></a>Festlegen eine Domänenklasse von ID-Moniker verwiesen wird

1.  Stellen Sie sicher, dass **ist der Moniker-Schlüssel** ist `false` für jede Eigenschaft "Domain" in der Klasse und deren Basisklassen.

    1.  Erweitern Sie im Explorer für DSL, **XML-Serialisierungsdaten Behavior\Class\\\<die Domänenklasse > \Element Daten**.

    2.  Überprüfen Sie, ob **ist der Moniker-Schlüssel** ist `false` für jede Eigenschaft "Domain".

    3.  Wenn die Domänenklasse eine Basisklasse verfügt, wiederholen Sie das Verfahren in dieser Klasse aus.

2.  Legen Sie **serialisieren Id**  =  `true` für die Domänenklasse.

     Diese Eigenschaft finden Sie unter **XML-Serialisierungsverhalten**.

### <a name="to-set-a-domain-class-to-be-referenced-by-qualified-key-monikers"></a>Festlegen eine Domänenklasse von qualifizierten Key Moniker verwiesen wird

-   Legen Sie **ist der Moniker-Schlüssel** für eine Eigenschaft "Domain" für eine vorhandene Domänenklasse. Der Typ der Eigenschaft muss `string`.

    1.  Erweitern Sie im Explorer für DSL, **XML-Serialisierungsdaten Behavior\Class\\\<die Domänenklasse > \Element Daten**, und wählen Sie dann die Eigenschaft "Domain".

    2.  Legen Sie im Fenster Eigenschaften **ist der Moniker-Schlüssel** auf `true`.

-   \- oder –

     Erstellen Sie eine neue Domäne-Klasse, mit der **Domänenklasse namens** Tool.

     Dieses Tool erstellt eine neue Klasse, die eine Eigenschaft "Domain" Namen aufgerufen hat. Die **Elementname ist** und **ist der Moniker-Schlüssel** Eigenschaften von dieser Eigenschaft "Domain" werden initialisiert, um `true`.

-   \- oder –

     Erstellen Sie eine Vererbungsbeziehung besteht aus der Domänenklasse mit einer anderen Klasse, die über eine Schlüsseleigenschaft Moniker verfügt.

### <a name="avoid-duplicate-monikers"></a>Vermeiden Sie doppelte Moniker

Bei Verwendung von qualifizierten Key Moniker ist es möglich, dass zwei Elemente im Modell ein Benutzer den gleichen Wert in die wichtigste Eigenschaft möglicherweise. Beispielsweise konnte besitzt der DSL eine Klasse Person, die eine Name-Eigenschaft aufweist, der Benutzer die Namen von zwei Elementen, auf die gleichen festlegen. Obwohl das Modell sein konnte in Datei gespeichert, es würde nicht erneut lädt, ordnungsgemäß.

Es gibt mehrere Methoden, mit deren Hilfe diese Situation zu vermeiden:

-   Legen Sie **Elementname ist**  =  `true` für die Eigenschaft "Schlüssel Domain". Wählen Sie die Eigenschaft "Domain" DSL-Definitionsdiagramm, und legen Sie den Wert im Eigenschaftenfenster angezeigt.

     Wenn der Benutzer eine neue Instanz der Klasse erstellt, wird dieser Wert der Eigenschaft "Domain" automatisch einen anderen Wert zugewiesen werden. Das Standardverhalten Fügt eine Zahl an das Ende der Klassenname. Dies verhindert nicht die Benutzer den Namen ändern, um ein Duplikat, erleichtert aber im Fall der Benutzer kein Wert festgelegt wird, vor dem Speichern des Modells.

-   Aktivieren Sie die Überprüfung der DSL. DSL-Explorer, wählen Sie Editor\Validation, und legen die **verwendet...**  Eigenschaften `true`.

     Es kann Überprüfung automatisch generiert, die überprüft, für die Mehrdeutigkeiten. Die Methode wird in der `Load` Überprüfung Kategorie. Dadurch wird sichergestellt, dass der Benutzer gewarnt werden, wenn es möglicherweise nicht möglich, die Datei erneut zu öffnen.

     Weitere Informationen finden Sie unter [Überprüfung in einer domänenspezifischen Sprache](../modeling/validation-in-a-domain-specific-language.md).

### <a name="moniker-paths-and-qualifiers"></a>Moniker Pfade und Qualifizierer

Ein qualifizierter Key Moniker endet mit dem Moniker Schlüssel, und mit dem Moniker seines übergeordneten Elements in der Struktur Einbetten von vorangestellt wird. Wenn beispielsweise der Moniker, der ein Album ist:

```xml
<albumMoniker title="/My Favorites/Jazz after Teatime" />
```

Klicken Sie dann könnte eine der im Album Musiktitel sein:

```xml
<songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />
```

Jedoch wenn Alben stattdessen von ID verwiesen werden, würde dann der Moniker wie folgt lauten:

```xml
<albumMoniker Id="77472c3a-9bf9-4085-976a-d97a4745237c" />
<songMoniker title="/77472c3a-9bf9-4085-976a-d97a4745237c/Hot tea" />
```

Beachten Sie, da eine GUID eindeutig ist, es nie den Moniker des übergeordneten vorangestellt ist.

Wenn Sie wissen, dass eine bestimmte Domäne-Eigenschaft stets einen eindeutigen Wert innerhalb eines Modells, legen Sie **Moniker-Qualifizierer ist** auf `true` für diese Eigenschaft. Dadurch wird es als Qualifizierer verwendet werden kann, ohne den Moniker des übergeordneten Elements verursacht. Angenommen, wenn Sie beide Optionen festlegen **Moniker-Qualifizierer ist** und **ist der Moniker-Schlüssel** für die Title-Eigenschaft der Domäne der Album-Klasse, Namen\noder Bezeichner des Modells wird nicht in Moniker Album und verwendet die eingebettete untergeordnete Elemente:

```xml
<albumMoniker name="Jazz after Teatime" />
<songMoniker title="/Jazz after Teatime/Hot tea" />
```

## <a name="customize-the-structure-of-the-xml"></a>Anpassen der XML-Struktur

Um die folgenden Anpassungen vornehmen, erweitern Sie die **XML-Serialisierungsverhalten** Knoten im Explorer für DSL. Erweitern Sie den Elementdaten-Knoten, um die Liste der Eigenschaften und Beziehungen, die auf diese Klasse belegen, unter einer Domänenklasse. Wählen Sie eine Beziehung, und passen Sie die Optionen im Eigenschaftenfenster angezeigt.

-   Legen Sie **Element weglassen** auf "true", um die Rolle Quellknoten nur die Liste der Zielelemente verlassen zu unterdrücken. Diese Option sollte nicht festgelegt werden, wenn mehr als eine Beziehung zwischen den Quell- und Zielklassen vorhanden ist.

    ```xml
    <familyTreeModel ...>
      <!-- The following node is omitted by using Omit Element: -->
      <!-- <people> -->
        <person name="Henry VIII" .../>
        <person name="Elizabeth I" .../>
      <!-- </people> -->
    </familyTreeModel>
    ```

-   Legen Sie **vollständige Formular** So betten Sie ein Zielknoten im Knoten, die Beziehungsinstanzen darstellt. Diese Option wird automatisch festgelegt, wenn Sie einer domänenbeziehung Domäneneigenschaften hinzufügen.

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

-   Legen Sie **Darstellung** = **Element** eine Eigenschaft "Domain" als ein Element anstelle von als Attributwert gespeichert haben.

    ```xml
    <person name="Elizabeth I" birthYear="1533">
      <deathYear>1603</deathYear>
    </person>
    ```

-   Klicken Sie zum Ändern der Reihenfolge, in denen Attribute und Beziehungen werden serialisiert, mit der rechten Maustaste unter Elementdaten ein Element, und verwenden die **nach oben** oder **nach unten** Menübefehle.

## <a name="major-customization-using-program-code"></a>Wichtige Anpassung mithilfe von Programmcode

Sie können teilweise oder vollständig der Serialisierung Algorithmen ersetzen.

Es wird empfohlen, dass Sie den Code in untersuchen **Dsl\Generated Code\Serializer.cs** und **SerializationHelper.cs**.

### <a name="to-customize-the-serialization-of-a-particular-class"></a>Um die Serialisierung einer bestimmten Klasse anzupassen

1.  Legen Sie **ist Benutzerdefiniert** im Knoten für diese Klasse unter **XML-Serialisierungsverhalten**.

2.  Transformieren Sie aller Vorlagen, erstellen Sie die Projektmappe, und untersuchen Sie die resultierende Kompilierungsfehler. Kommentare in der Nähe von jeder Fehler wird erläutert, welcher Code muss angegeben werden.

### <a name="to-provide-your-own-serialization-for-the-whole-model"></a>Um eine eigene Serialisierung für das gesamte Modell bereitzustellen.

1.  Überschreiben von Methoden in Dsl\GeneratedCode\SerializationHelper.cs

## <a name="options-in-xml-serialization-behavior"></a>Optionen im XML-Serialisierungsverhalten

Im Explorer für DSL enthält der XML-Serialisierungsverhalten-Knoten einen untergeordneter Knoten für jede Domänenklasse, Beziehung, Form, Connectors und Diagramm-Klasse. Unter jedem dieser Knoten ist Sie eine Liste der Eigenschaften und Beziehungen, die auf dieses Element stammen. Beziehungen werden in ihre eigenen rechts sowohl unter ihrer Quellklassen dargestellt.

In der folgenden Tabelle werden die Optionen, die Sie in diesem Abschnitt der DSL-Definition festlegen können zusammengefasst. Wählen Sie in jedem Fall ein Element im Explorer für DSL, und legen Sie die Optionen im Eigenschaftenfenster angezeigt.

### <a name="xml-class-data"></a>Klasse von XML-Daten

Diese Elemente finden Sie im DSL-Explorer unter **XML-Serialisierungsdaten Behavior\Class**.

|||
|-|-|
|Eigenschaft|Beschreibung|
|Benutzerdefiniertes Element Schema aufweist|Bei "true", gibt an, dass die Domänenklasse ein benutzerdefiniertes Element Schema verfügt über|
|Benutzerdefinierte|Legen Sie **"true"** Wenn Sie Ihren eigenen Serialisierung und Deserialisierung für diese Domänenklasse schreiben möchten.<br /><br /> Erstellen Sie die Projektmappe, und untersuchen Sie die Fehler, um detaillierte Informationen zu ermitteln.|
|Domänenklasse|Domain-Klasse, für die diese Klasse Datenknoten gilt. Schreibgeschützt.|
|Elementname|XML-Knoten-Name für die Elemente dieser Klasse. Der Standardwert ist eine kleingeschriebene Version des Domänennamens-Klasse.|
|Monikername-Attribut|Der Name des Attributs in Moniker Elemente verwendet, um den Verweis enthält. Wenn leer, wird der Name der Schlüsseleigenschaft oder -Id verwendet.<br /><br /> In diesem Beispiel ist es "name":  `<personMoniker name="/Mike Nash"/>`|
|Monikername-Element|Der Name des XML-Elements für Moniker, die Elemente dieser Klasse verweisen, verwendet.<br /><br /> Der Standardwert ist der Klassenname mit dem Suffix "Moniker" in Kleinbuchstaben. Beispielsweise `personMoniker`.|
|Typ der Monikername|Der Name des XSD-Typs für Moniker auf Elemente dieser Klasse generiert. XSD-Code befindet sich im **Dsl\Generated Code\\\*Schema.xsd**|
|Serialisieren Sie Id|Bei "true", ist die GUID des Elements in der Datei enthalten. Diese Angabe muss "true", wenn keine Eigenschaft, die markiert ist **ist der Moniker-Schlüssel** und der DSL verweisbeziehungen diese Klasse definiert.|
|Typname|Der Name des Xml-Datentyps in der Xsd aus der angegebenen Domänenklasse generiert.|
|Hinweise|Informelle Anmerkungen im Zusammenhang mit diesem element|

### <a name="xml-property-data"></a>XML-Daten

XML-Eigenschaftsknoten befinden sich unter den Knoten für die Klasse.

|||
|-|-|
|Eigenschaft|Beschreibung|
|Eigenschaft "Domain"|Diese Eigenschaft die Konfigurationsdaten für XML-Serialisierung gilt. Schreibgeschützt.|
|Ist der Moniker Schlüssel|Bei "true", wird die Eigenschaft verwendet, als Schlüssel für die Erstellung der Moniker, die Instanzen dieser Domänenklasse verweisen.|
|Ist der Moniker-Qualifizierer|Bei "true", wird die Eigenschaft zum Erstellen des Qualifizierers in Moniker verwendet. Wenn "false", und SerializeId nicht für diese Domänenklasse "true" ist, werden Moniker durch den Moniker des übergeordneten Elements in der Struktur einbetten qualifiziert.|
|Darstellung|Wenn das Attribut, das die Eigenschaft als XML-Attribut serialisiert werden; Element, es wird serialisiert, als ein Element. Falls Sie nicht serialisiert.|
|XML-Name|Namen für die XML-Attribut oder Element, das die Eigenschaft darstellt. Standardmäßig ist dies eine kleingeschriebene Version des Domänennamens-Eigenschaft.|
|Hinweise|Informelle Anmerkungen im Zusammenhang mit diesem element|

### <a name="xml-role-data"></a>Rolle von XML-Daten

Rolle Datenknoten befinden sich unter den Quellknoten-Klasse.

|Eigenschaft|Beschreibung|
|--------------|-----------------|
|Benutzerdefinierte Moniker verfügt|Legen Sie diese auf "true", wenn Sie Ihren eigenen Code zum Generieren und Auflösen von Monikern, die diese Beziehung durchlaufen angeben möchten.<br /><br /> Ausführliche Anweisungen erstellen Sie die Projektmappe, und doppelklicken Sie dann auf die Fehlermeldungen.|
|Domänenbeziehung|Gibt die Beziehung zu der diese Optionen gelten. Schreibgeschützt.|
|Weglassen von Element|Bei "true", wird der XML-Knoten, der die Rolle "Quelle" entspricht, aus dem Schema weggelassen.<br /><br /> Ist es mehr als eine Beziehung zwischen den Quell- und Zielklassen, unterscheidet sich dieser rollenknoten zwischen Links, die die beiden Beziehungen angehören. Aus diesem Grund wird empfohlen, dass Sie diese Option nicht in diesem Fall festgelegt.|
|Rollenname-Element|Gibt den Namen des XML-Elements, das von der Rolle "Quelle" abgeleitet ist. Der Standardwert ist der Rollenname-Eigenschaft.|
|Full Form verwenden|Bei "true", wird jede Zielelement oder -Moniker in einen XML-Knoten, die die Beziehung darstellt eingeschlossen. Dies sollte festgelegt werden, auf "true", wenn die Beziehung über eigene Domäneneigenschaften verfügt.|

## <a name="see-also"></a>Siehe auch

- [Navigieren in und Aktualisieren von Modellen im Programmcode](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Generieren von Code für eine domänenspezifische Sprache](../modeling/generating-code-from-a-domain-specific-language.md)