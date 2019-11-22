---
title: How to Define a Domain-Specific Language | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.domainrelationship
- vs.dsltools.dsldesigner.domainclass
- vs.dsltools.dsldesigner.domaintype
helpviewer_keywords:
- Domain-Specific Language, domain class
- Domain-Specific Language, external types
- Domain-Specific Language, relationships
- Domain-Specific Language, domain properties
ms.assetid: d1772463-0eb1-40a5-b7c0-9a008bc76760
caps.latest.revision: 45
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b4bcd1f1f023c9e439fb870c9e31f07aa5be215d
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299551"
---
# <a name="how-to-define-a-domain-specific-language"></a>So definieren Sie eine domänenspezifische Sprache
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Um eine domänenspezifische Sprache (DSL) zu definieren, erstellen Sie eine [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Projektmappe von einer Vorlage. Der zentrale Bestandteil der Projektmappe ist das DSL-Definitionsdiagramm, das in "DslDefinition.dsl" gespeichert wird. Die DSL-Definition definiert die Klassen und Formen der DSL. Nachdem Sie diese Elemente geändert und weitere hinzugefügt haben, können Sie Programmcode hinzufügen, um die DSL weiter anzupassen.

 If you are new to DSLs, we recommend that you work through the **DSL Tools Lab**, which you can find in this site: [Visualizaton and Modeling SDK](https://go.microsoft.com/fwlink/?LinkID=186128)

## <a name="templates"></a> Selecting a Template Solution
 Zur Definition einer DSL müssen folgende Komponenten installiert sein:

|||
|-|-|
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185579](https://go.microsoft.com/fwlink/?LinkId=185579)|
|[!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185580](https://go.microsoft.com/fwlink/?LinkId=185580)|
|Visual Studio Visualization and Modeling SDK|[http://go.microsoft.com/fwlink/?LinkID=186128](https://go.microsoft.com/fwlink/?LinkID=186128)|

 Um eine neue domänenspezifische Sprache zu erstellen, erstellen Sie eine neue [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Projektmappe von der Projektvorlage "Domänenspezifische Sprache".

#### <a name="to-create-a-dsl-solution"></a>So erstellen Sie eine DSL-Projektmappe

1. Create a solution with the **Domain-Specific Language** template, which can be found under **Other Project Types/Extensibility** in the **New Project** dialog box.

    ![Create DSL dialog](../modeling/media/create-dsldialog.png "Create_DSLDialog")

    When you click **OK**, the **Domain-Specific Language Wizard** opens and displays a list of template DSL solutions.

2. Klicken Sie auf die einzelnen Vorlagen, um eine Beschreibung anzuzeigen. Wählen Sie die Projektmappe aus, die Ihren Vorstellungen am nächsten kommt.

    Jede DSL-Vorlage definiert eine grundlegende, funktionsfähige DSL. Sie bearbeiten diese DSL nach Ihren Anforderungen.

    Klicken Sie auf die Beispiele, um weitere Informationen anzuzeigen.

   - Select **Task Flow** to create a DSL that has swimlanes. Verantwortlichkeitsbereiche sind vertikale oder horizontale Bereiche des Diagramms.

   - Select **Component Models** to create a DSL that has ports. Anschlüsse sind kleine Formen am Rand einer größeren Form.

   - Select **Class Diagrams** to define a DSL that has compartment shapes. Depot-Formen enthalten Listen von Elementen.

   - Select **Minimal Language** in other cases, or if you are uncertain.

       > [!NOTE]
       > Wenn Sie ein Klassendiagramm oder ein Komponentendiagramm erstellen möchten, können Sie auch UML-Modelle verwenden. Die UML-Modellierungstools stellen einen Satz von Diagrammen bereit, die um ein einzelnes Modell herum integriert sind. Sie sind erweiterbar und können über ModelBus in Ihre DSL integriert werden. For more information, see [Create models for your app](../modeling/create-models-for-your-app.md).

   - Select **Minimal WinForm Designer** or **Minimal WPF Designer** to create a DSL that is displayed on a Windows Forms or WPF surface. Sie müssen Code zur Definition des Editors schreiben. Weitere Informationen finden Sie unter den folgenden Themen:

        [Erstellen einer Windows Forms-basierten domänenspezifischen Sprache](../modeling/creating-a-windows-forms-based-domain-specific-language.md)

        [Erstellen einer WPF-basierten domänenspezifischen Sprache](../modeling/creating-a-wpf-based-domain-specific-language.md)

3. Geben Sie auf der entsprechenden Seite des Assistenten eine Dateinamenerweiterung für die DSL ein. Diese Erweiterung wird für Dateien mit Instanzen Ihrer DSL verwendet.

   - Wählen Sie eine Dateinamenerweiterung, die keiner Anwendung auf Ihrem Computer bzw. auf einem Computer, auf dem Sie die DSL installieren möchten, zugeordnet ist. For example, **docx** and **htm** would be unacceptable file name extensions.

   - Der Assistent warnt Sie, wenn die eingegebene Erweiterung bereits als DSL verwendet wird. Verwenden Sie nach Möglichkeit eine andere Dateinamenerweiterung. Sie können die experimentelle Instanz des Visual Studio SDK auch zurücksetzen, um alte experimentelle Designer zu löschen. Click **Start**, click **All Programs**, **Microsoft Visual Studio 2010 SDK**, **Tools**, and then **Reset the Microsoft Visual Studio 2010 Experimental instance**.

4. Auf den anderen Seiten können Sie Einstellungen anpassen oder die Standardwerte übernehmen.

5. Klicken Sie auf **Fertig stellen**.

    Der Assistent erstellt eine Projektmappe mit zwei oder drei Projekten und generiert Code aus der DSL-Definition.

   Die Benutzeroberfläche gleicht nun der folgenden Abbildung.

   ![DSL-Designer](../modeling/media/dsl-designer.png "dsl_designer")

   Diese Projektmappe definiert eine domänenspezifische Sprache. For more information, see [Overview of the Domain-Specific Language Tools User Interface](../modeling/overview-of-the-domain-specific-language-tools-user-interface.md).

### <a name="test-the-solution"></a>Testen der Projektmappe
 Die Vorlagenprojektmappe enthält eine funktionsfähige DSL, die Sie ändern oder direkt verwenden können.

 Drücken Sie F5 oder STRG+F5, um die Projektmappe zu testen. Eine neue Instanz von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] wird im Testmodus gestartet.

 Öffnen Sie in der neuen Instanz von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] im Projektmappen-Explorer die "Sample"-Datei. Sie wird als Diagramm mit einem Werkzeugkasten geöffnet.

 If you run a solution that you have created from the **Minimal Language** template, your experimental [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] will resemble the following example:

 ![](../modeling/media/dsl-min.png "DSL_min")

 Experimentieren Sie mit den Werkzeugen. Erstellen Sie Elemente, und verbinden Sie sie.

 Schließen Sie die experimentelle Instanz von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

> [!NOTE]
> Wenn Sie die DSL geändert haben, können Sie die Formen in der "Sample"-Testdatei nicht mehr sehen. Sie können aber neue Elemente erstellen.

### <a name="modifying-the-template-dsl"></a>Ändern der Vorlagen-DSL
 Benennen Sie einige oder alle Domänenklassen und Formklassen der Vorlagen-DSL-Definition um, und behalten Sie sie bei. Die neuen Klassennamen sollten gültige CLR-Namen ohne Leerzeichen oder Interpunktionszeichen sein.

 Die Beibehaltung der folgenden Klassen ist besonders sinnvoll:

- The root class appears at the upper-left of the DSL Definition diagram, under **Classes and Relationships**. Benennen Sie sie in einen von der DSL verschiedenen Namen um. For example, a DSL named **MusicLibrary** might have a root class named **Music**.

- The diagram class appears at the lower right of the DSL Definition diagram, in the **Diagram Elements** column. Möglicherweise müssen Sie einen Bildlauf nach rechts durchführen, um sie zu sehen. It is typically named _YourDsl_**Diagram**.

- If you used the **Task Flow** template and you want to create diagrams with swimlanes, keep and rename the Actor domain class and ActorSwimlane shape.

  Löschen Sie andere Klassen nach Bedarf, oder benennen Sie sie um.

## <a name="patterns"></a> Patterns for Defining a DSL
 Es ist empfehlenswert, beim Entwickeln einer DSL nur jeweils ein oder zwei Features gleichzeitig hinzuzufügen bzw. anzupassen. Fügen Sie ein Feature hinzu, führen Sie die DSL aus und testen Sie sie. Fügen Sie dann ein oder zwei weitere Features hinzu. Ein typisches Feature Ihrer DSL könnte folgendermaßen aussehen:

- Eine Domänenklasse, die einbettende Beziehung, die das Element mit dem Modell verbindet, die erforderliche Form zum Anzeigen von Elementen der Klasse im Diagramm sowie das Elementwerkzeug, mit dem Benutzer Elemente erstellen können.

- Die Domäneneigenschaften einer Domänenklasse und die Decorator-Elemente, die sie in einer Form anzeigen.

- Eine Verweisbeziehung und der Konnektor, der sie im Diagramm anzeigt, sowie das Konnektorwerkzeug, mit dem Benutzer Verbindungen erstellen können.

- Eine Anpassung, die Programmcode erfordert, wie z. B. eine Validierungseinschränkung oder ein Menübefehl.

  In den folgenden Abschnitten wird die Erstellung der nützlichsten DSL-Features beschrieben. Es gibt viele andere Muster, nach denen eine DSL erstellt werden kann, aber die folgenden sind die gängigsten.

> [!NOTE]
> After adding a feature, do not forget to click **Transform All Templates** in the toolbar of Solution Explorer before you build and running your DSL.

 In der folgenden Abbildung sind die Klassen und Beziehungen der DSL dargestellt, die in diesem Thema als Beispiel verwendet wird.

 ![Embedding and Reference relationships](../modeling/media/music-classes.png "Music_Classes")

 Die nächste Abbildung zeigt ein Beispielmodell dieser DSL:

 ![Instance model of generated DSL](../modeling/media/music-instance.png "Music_Instance")

> [!NOTE]
> "Modell" bezieht sich auf eine Instanz Ihrer DSL, die Benutzer erstellen. Sie wird üblicherweise als Diagramm dargestellt. In diesem Thema werden das DSL-Definitionsdiagramm und die Modelldiagramme erläutert, die bei Verwendung der DSL angezeigt werden.

## <a name="classes"></a> Defining Domain Classes
 Domänenklassen stellen die Konzepte der DSL dar. The instances are *model elements*. For example in a **MusicLibrary** DSL you might have Domain Classes named **Album** and **Song**.

 To create a domain class, you can drag from the **Named Domain Class** tool to the diagram, and then rename the class.

 For more information, see [Properties of Domain Classes](../modeling/properties-of-domain-classes.md).

### <a name="create-an-embedding-relationship-for-each-domain-class"></a>Erstellen einer einbettenden Beziehung für jede Domänenklasse
 Jede Domänenklasse mit Ausnahme der Stammklasse muss Ziel mindestens einer einbettenden Beziehung sein, oder sie muss von einer Klasse erben, die Ziel einer einbettenden Beziehung ist.

 Jedes Modellelement in einem Modell ist ein Knoten in einer einzelnen Struktur einbettender Beziehungen. Quelle und Ziel einer einbettenden Beziehung werden häufig als übergeordnetes und untergeordnetes Element bezeichnet.

 Die Auswahl eines übergeordneten Elements für eine Domänenklasse hängt davon ab, wie die Lebensdauer ihrer Elemente von anderen Elementen abhängen soll. Wenn ein Knoten einer Struktur gelöscht wird, wird auch seine Unterstruktur gelöscht. Daher werden Klassen von Elementen, deren Existenz nicht von anderen abhängt, direkt unter der Stammklasse eingebettet.

 Wenn Sie ein Element innerhalb eines anderen Elements anzeigen, möchten Sie normalerweise eine Besitzerbeziehung darstellen. In diesem Fall wird als übergeordnete Klasse am besten die Klasse des Containers gewählt. Dies gilt jedoch nicht, wenn das in einem Container dargestellte Element tatsächlich nur ein Verweislink auf ein unabhängiges Element ist. In diesem Fall wird beim Löschen des Containers der Verweis gelöscht, aber nicht sein Ziel.

 In den hier beschriebenen DSL-Definitionsmustern wird vorausgesetzt, dass beim Löschen eines Containers die in dem Container dargestellten Elemente ebenfalls gelöscht werden. Komplexere Schemas können durch Definieren von Regeln erzielt werden.

|Darstellung des Elements|Übergeordnete (einbettende) Klasse|Beispiel in DSL-Projektmappenvorlage|
|------------------------------|--------------------------------|--------------------------------------|
|Form im Diagramm<br /><br /> Verantwortlichkeitsbereich|Stammklasse der DSL|Minimale Sprache<br /><br /> Aufgabenfluss: Actor-Klasse|
|Form in Verantwortlichkeitsbereich|Domänenklasse von Elementen, die als Verantwortlichkeitsbereiche dargestellt werden.|Aufgabenfluss: Task-Klasse|
|Element in Liste in Form, das zusammen mit Container gelöscht wird.<br /><br /> Anschluss am Rand einer Form|Der Containerform zugeordnete Domänenklasse|Klassendiagramm: Attribute-Klasse<br /><br /> Komponentendiagramm: Port-Klasse|
|Element in Liste, nicht zusammen mit Container gelöscht|Stammklasse der DSL<br /><br /> Die Liste enthält Verweislinks.||
|Nicht direkt angezeigt|Die Klasse, von der es Bestandteil ist||

 Im Beispiel "Musikbibliothek" werden Alben als Rechtecke dargestellt, in denen die Titel von Songs aufgelistet sind. Daher ist das übergeordnete Element von "Album" die Stammklasse "Musik", und das übergeordnete Element von "Song" ist "Album".

 To create a domain class and its embedding at the same time, click the **Embedding Relationship** tool, then click the parent class, and then click on a blank part of the diagram.

 In der Regel müssen Sie den Namen der einbettenden Beziehung und ihrer Rollen nicht anpassen, da automatisch die Klassennamen verwendet werden.

 For more information, see [Properties of Domain Relationships](../modeling/properties-of-domain-relationships.md) and [Properties of Domain Roles](../modeling/properties-of-domain-roles.md).

> [!NOTE]
> Einbettung ist nicht identisch mit Vererbung. Die untergeordneten Elemente in einer einbettenden Beziehung erben keine Features von ihren übergeordneten Elementen.

### <a name="add-domain-properties-to-each-domain-class"></a>Hinzufügen von Domäneneigenschaften zu den einzelnen Domänenklassen
 In Domäneneigenschaften werden Werte gespeichert. Beispiele: Name, Titel, Veröffentlichungsdatum.

 Click **Domain Properties** in the class, press the ENTER key, and then type the name of a property. Der Standardtyp einer Domäneneigenschaft lautet String. If you want to change the type, select the domain property, and set the **Type** in the **Properties** window. If the type that you want is not in the drop-down list, see [Adding Property Types](#addTypes).

 **Set an Element Name property.** Select a domain property that can be used to identify elements in the language explorer. Beispielsweise könnten Sie in der "Song"-Domänenklasse die "Titel"-Domäneneigenschaft auswählen. In the **Properties** window, set **Is Element Name** to `true`.

### <a name="create-derived-domain-classes"></a>Erstellen abgeleiteter Domänenklassen
 Soll eine Domänenklasse Varianten aufweisen, die ihre Eigenschaften und Beziehungen erben, erstellen Sie von der Domänenklasse abgeleitete Klassen. "Album" könnte z. B. die abgeleiteten Klassen WMA und MP3 haben.

 Create the derived class using the **Domain Class** tool.

 Click the **Inheritance** tool, click the derived class, and then click the base class.

 Consider setting the **Inheritance Modifier** of the base class to **abstract**. Wenn Sie voraussichtlich Instanzen der Basisklasse benötigen, können Sie stattdessen eine gesonderte abgeleitete Klasse für diese erstellen.

 Abgeleitete Klassen erben die Eigenschaften und Rollen ihrer Basisklassen.

### <a name="tidy-the-dsl-definition-diagram"></a>Bereinigen des DSL-Definitionsdiagramms
 Wenn Sie Beziehungen hinzufügen, erscheinen einige Klassen an mehreren Stellen. To reduce the number of appearances and make the diagram wider, right-click the target class of a relationship, and then click **Bring Tree Here**. For the opposite effect, right-click the target class of a relationship and click **Split Tree**. Wenn diese Menübefehle nicht angezeigt werden, vergewissern Sie sich, dass nur die Domänenklasse ausgewählt ist.

 Verwenden Sie STRG+NACH OBEN und STRG+NACH UNTEN, um Domänenklassen und Formklassen zu verschieben.

### <a name="test-the-domain-classes"></a>Testen der Domänenklassen

##### <a name="to-test-the-new-domain-classes"></a>So testen Sie die neuen Domänenklassen

1. **Click Transform All Templates** in the toolbar of Solution Explorer, to generate the DSL designer code. Dieser Schritt kann automatisiert werden. For more information, see [How to Automate Transform All Templates](https://msdn.microsoft.com/b63cfe20-fe5e-47cc-9506-59b29bca768a).

2. **Build and run the DSL.** Press F5 or CTRL+F5 to run a new instance of [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] in experimental mode. Öffnen oder erstellen Sie in der experimentellen Instanz von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] eine Datei mit der Dateinamenerweiterung Ihrer DSL.

3. **Open the Explorer.** At the side of the diagram is the language explorer window, which is usually named *YourLanguage* Explorer. Sollten Sie das Fenster nicht sehen, befindet es sich möglicherweise auf einer Registerkarte unter dem Projektmappen-Explorer. If you cannot find it, on the **View** menu, point to **Other Windows**, and then click _YourLanguage_**Explorer**.

     Im Explorer wird eine Strukturansicht des Modells dargestellt.

4. **Create new elements.** Right-click the root node at the top, and then click **Add New**_YourClass_.

     Im Sprach-Explorer wird eine neue Instanz Ihrer Klasse angezeigt.

5. Überprüfen Sie beim Erstellen neuer Instanzen, ob jede Instanz einen anderen Namen hat. This will occur only if you have set the **Is Element Name** flag on a domain property.

6. **Examine the domain properties. With an instance of your class selected,** inspect the Properties window. Es sollte die Domäneneigenschaften zeigen, die Sie für die Domänenklasse definiert haben.

7. **Save the file, close it, and re-open it**. Nachdem Sie die Knoten erweitert haben, sollten alle erstellten Instanzen im Explorer sichtbar sein.

## <a name="shapes"></a> Defining Shapes on the Diagram
 Sie können Klassen von Elementen definieren, die in einem Diagramm als Rechtecke, Ellipsen oder Symbole erscheinen.

#### <a name="to-define-a-class-of-elements-that-appear-as-shapes-on-a-diagram"></a>So definieren Sie eine Klasse von Elementen, die in einem Diagramm als Formen dargestellt werden

1. **Define and test a domain class as described in**  [Defining Domain Classes](#classes) **.**

   - Das übergeordnete Element der Klasse sollte die Stammklasse sein. Es sollte also eine einbettende Beziehung zwischen der Stammklasse und der neuen Domänenklasse bestehen.

   - Wenn das Diagramm Verantwortlichkeitsbereiche enthält, kann das übergeordnete Element die Domänenklasse sein, die einem Verantwortlichkeitsbereich zugeordnet ist. Before continuing with this procedure, see [Defining a DSL that has Swimlanes](#swimlanes).

2. **Add a shape class** to represent the elements on the model diagram. Ziehen Sie eines der folgenden Werkzeuge in das DSL-Definitionsdiagramm:

   - **Geometry Shape** provides a rectangle or ellipse.

   - **Image Shape** displays an image that you provide.

   - **Compartment Shape** is a rectangle that contains one or more lists of items.

     Benennen Sie die Formklasse um, die rechts im DSL-Definitionsdiagramm unter "Formen und Konnektoren" angezeigt wird.

3. **Define an image, if you created an image shape**.

   1. Erstellen Sie eine Bilddatei beliebiger Größe. Die Formate BMP, JPEG, GIF und EMF werden unterstützt.

   2. Fügen Sie die Datei im Projektmappen-Explorer der Projektmappe unter Dsl\Ressourcen hinzu.

   3. Kehren Sie zum DSL-Definitionsdiagramm zurück, und wählen Sie die neue Bild-Formklasse aus.

   4. In the Properties window, click the **Image** property.

   5. In the **Select Image** dialog box, click the drop-down menu under **File name**, and select the image.

4. **Add text decorators to the shape, to display the domain properties.**

    Sie benötigen wahrscheinlich mindestens ein Text-Decorator-Element, um den Namen oder Titel des Modellelements anzuzeigen.

    Right-click the header of the shape class, point to **Add**, and then click **Text Decorator**. Set the name of the decorator, and in the Properties window set its **Position**.

5. **Connect each shape with a Diagram Element Map to the domain class that it should display**.

    Click the **Diagram Element Map** tool, then click the domain class, then click the shape class.

6. **Map the properties to the text decorators.**

   1. Wählen Sie die graue Linie zwischen der Domänenklasse und der Formklasse aus, die die Diagrammelementzuordnung darstellt.

   2. In the **DSL Details** window, click the **Decorator Maps** tab. If you do not see the **DSL Details** window, on the **View** menu, point to **Other Windows** and then click **DSL Details**. Häufig muss der obere Rand des Fensters angehoben werden, um den gesamten Inhalt anzuzeigen.

   3. Wählen Sie den Namen eines Decorator-Elements aus. Under **Display property**, select the name of a property of the domain class. Wiederholen Sie dies für jedes Decorator-Element.

       If you want to display a property of a related element, click the drop-down tree navigator under **Path to display property**.

   4. Stellen Sie sicher, dass neben jedem Decorator-Namen ein Häkchen angezeigt wird.

      ![Shape Mappings and DSL Details window](../modeling/media/dsldetailswindow.png "DslDetailsWindow")

7. **Make a toolbox item for creating elements of the domain class.**

   1. In **DSL Explorer**, expand the **Editor** node and all its sub-nodes.

   2. Right-click the node under **Toolbox Tabs** that has the same name as your DSL, for example MusicLibrary. Click **Add Element Tool**.

       > [!NOTE]
       > If you right-click the **Tools** node, you will not see **Add Element Tool**. Klicken Sie stattdessen auf den übergeordneten Knoten.

   3. In the Properties window with the new element tool selected, set **Class** to the domain class that you have recently added.

   4. Set **Caption** and **Tooltip**.

   5. Set **Toolbox Icon** to an icon that will appear in the toolbox. Sie können ein neues Symbol oder ein bereits für ein anderes Werkzeug verwendetes Symbol angeben.

        To create a new icon, open Dsl\Resources in **Solution Explorer**. Kopieren Sie eine der vorhandenen BMP-Dateien für Elementwerkzeuge, und fügen Sie sie ein. Benennen Sie die eingefügte Kopie um, und doppelklicken Sie dann darauf, um sie zu öffnen.

        Return to the DSL Definition diagram, select the tool, and in the Properties window click **[...]** in **Toolbox Icon**. In the **Select Bitmap** dialog box, select your .BMP file from the drop-down menu.

   For more information, see [Properties of Geometry Shapes](../modeling/properties-of-geometry-shapes.md) and [Properties of Image Shapes](../modeling/properties-of-image-shapes.md).

#### <a name="to-test-shapes"></a>So testen Sie Formen

1. **Click Transform All Templates** in the toolbar of Solution Explorer, to generate the DSL designer code.

2. **Build and run the DSL.** Press F5 or CTRL+F5 to run a new instance of [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] in experimental mode. Öffnen oder erstellen Sie in der experimentellen Instanz von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] eine Datei mit der Dateinamenerweiterung Ihrer DSL.

3. **Verify that the element tools appear on the toolbox.**

4. **Create shapes** by dragging from a tool onto the model diagram.

5. **Verify that each text decorator appears,** and that:

   1. You can edit it, unless you have set the **Is UI Read Only** flag on the domain property.

   2. Wenn Sie die Eigenschaft im Eigenschaftenfenster oder im Decorator bearbeiten, wird die jeweils andere Ansicht aktualisiert.

   Nach dem ersten Test einer Form möchten Sie unter Umständen einige Eigenschaften anpassen und erweiterte Features hinzufügen. For more information, see [Customizing and Extending a Domain-Specific Language](../modeling/customizing-and-extending-a-domain-specific-language.md).

## <a name="references"></a> Defining Reference Relationships
 Sie können eine Verweisbeziehung zwischen einer Quelldomänenklasse und einer Zieldomänenklasse definieren. Verweisbeziehungen werden in einem Diagramm üblicherweise als Konnektoren, also als Linien zwischen Formen, angezeigt.

 Wenn beispielsweise Alben und Interpreten als Formen in einem Diagramm dargestellt werden, könnten Sie eine Beziehung namens "ArtistsAppearedOnAlbums" definieren, die Interpreten mit den Alben verknüpft, an denen sie mitgewirkt haben. Siehe das Beispiel in der Abbildung.

 ![Instance model of generated DSL](../modeling/media/music-instance.png "Music_Instance")

 Verweisbeziehungen können auch Elemente desselben Typs verbinden. So ist in einer DSL, die einen Familienstammbaum darstellt, die Beziehung zwischen Eltern und Kindern eine Verweisbeziehung von Person zu Person.

### <a name="define-a-reference-relationship"></a>Definieren einer Verweisbeziehung
 Klicken Sie auf das Werkzeug "Verweisbeziehung", auf die Quelldomänenklasse der Beziehung und dann auf die Zieldomänenklasse. Die Zielklasse kann mit der Quellklasse übereinstimmen.

 Jede Beziehung hat zwei Rollen, die durch die Linien auf beiden Seiten des Beziehungsfelds dargestellt werden. Sie können jede Rolle auswählen und ihre Eigenschaften im Eigenschaftenfenster festlegen.

 **Consider renaming the roles**. In einer Beziehung zwischen Personen könnten Sie z. B. die Standardnamen in Eltern und Kinder, Manager und Mitarbeiter, Lehrer und Schüler usw. ändern.

 **Adjust the multiplicities of each role**, if it is necessary. Soll jede Person höchstens einen Manager haben, legen Sie die Multiplizität (unter der Beschriftung "Manager") im Diagramm auf 0..1 fest.

 **Add domain properties to the relationship.** In the figure, the Artist-Album relationship has a property of role.

 **Set the Allows Duplicates property of the relationship,** if more than one link of the same class can exist between the same pair of model elements. Beispielsweise könnten Sie zulassen, dass ein Lehrer einen Schüler in mehreren Fächern unterrichtet.

 ![Shape maps for connectors](../modeling/media/music-connector.png "Music_Connector")

 For more information, see [Properties of Domain Relationships](../modeling/properties-of-domain-relationships.md) and [Properties of Domain Roles](../modeling/properties-of-domain-roles.md).

### <a name="define-a-connector-to-display-the-relationship"></a>Definieren eines Konnektors zur Darstellung der Beziehung
 Ein Konnektor stellt eine Linie zwischen zwei Formen im Modelldiagramm dar.

 Drag the **Connector** tool onto the DSL definition diagram.

 Fügen Sie Text-Decorator-Elemente hinzu, falls Beschriftungen auf dem Konnektor angezeigt werden sollen. Legen Sie deren Positionen fest. To let the user move a text decorator, set its **Is Moveable** property.

 Use the **Diagram Element Map** tool to link the connector to the reference relationship.

 With the diagram element map selected, open the **DSL Details** window, and open the **Decorator Maps** tab.

 Select each **Decorator** and set **Display property** to the correct domain property.

 Make sure that a check mark appears next to each item in the **Decorators** list.

### <a name="define-a-connection-builder-tool"></a>Definieren eines Werkzeugs "Verbindungs-Generator"
 In the **DSL Explorer** window, expand the **Editor** node and all its subnodes.

 Right-click the node that has the same name as your DSL, and then click **Add New Connection Tool**.

 Führen Sie, während das neue Werkzeug ausgewählt ist, im Eigenschaftenfenster Folgendes aus:

- Set the **Caption** and **Tooltip**.

- Click **Connection Builder** and select the appropriate builder for the new relationship.

- Set **Toolbox Icon** to the icon that you want to appear in the toolbox. Sie können ein neues Symbol oder ein bereits für ein anderes Werkzeug verwendetes Symbol angeben.

     To create a new icon, open Dsl\Resources in **Solution Explorer**. Kopieren Sie eine der vorhandenen BMP-Dateien für Elementwerkzeuge, und fügen Sie sie ein. Benennen Sie die eingefügte Kopie um, und doppelklicken Sie dann darauf, um sie zu öffnen.

     Return to the DSL Definition diagram, select the tool, and in the Properties window click **[...]** in **Toolbox Icon**. In the **Select Bitmap** dialog box, select your .BMP file from the drop-down menu.

##### <a name="to-test-a-reference-relationship-and-connector"></a>So testen Sie eine Verweisbeziehung und einen Konnektor

1. **Click Transform All Templates** in the toolbar of Solution Explorer, to generate the DSL designer code.

2. **Build and run the DSL.** Press F5 or CTRL+F5 to run a new instance of [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] in experimental mode. Öffnen oder erstellen Sie in der experimentellen Instanz von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] eine Datei mit der Dateinamenerweiterung Ihrer DSL.

3. **Verify that the connection tool appears on the toolbox.**

4. **Create shapes** by dragging from a tool onto the model diagram.

5. **Create connections** between the shapes. Klicken Sie auf das Konnektorwerkzeug, auf eine Form und dann auf eine andere Form.

6. **Verify that you cannot create connections between inappropriate classes.** For example, if your relationship is between Albums and Artists, verify that you cannot link Artists to Artists.

7. **Verify that the multiplicities are correct. For example, verify that you cannot connect a Person to more than one manager.**

8. **Verify that each text decorator appears,** and that:

   1. You can edit it, unless you have set the **Is UI Read Only** flag on the domain property.

   2. Wenn Sie die Eigenschaft im Eigenschaftenfenster oder im Decorator bearbeiten, wird die jeweils andere Ansicht aktualisiert.

   Nach dem ersten Test eines Konnektors möchten Sie unter Umständen einige Eigenschaften anpassen und erweiterte Features hinzufügen. For more information, see [Customizing and Extending a Domain-Specific Language](../modeling/customizing-and-extending-a-domain-specific-language.md).

## <a name="compartments"></a> Defining Shapes that Contain Lists: Compartment Shapes
 Eine Depot-Form enthält mindestens eine Liste von Elementen. In einer DSL für eine Musikbibliothek würden Sie z. B. Depot-Formen verwenden, um Musikalben darzustellen. Jedes Album enthält eine Liste von Songs.

 ![Compartment Shape](../modeling/media/compartmentshape.png "CompartmentShape")

 Am einfachsten erzielen Sie diesen Effekt in einer DSL-Definition, indem Sie eine Domänenklasse für den Container und eine Domänenklasse für jede Liste definieren. Die Containerklasse wird der Depot-Form zugeordnet.

 ![Shape map](../modeling/media/music-mapcomp.png "Music_MapComp")

 For more information, see [Properties of Compartment Shapes](../modeling/properties-of-compartment-shapes.md).

#### <a name="to-define-a-compartment-shape"></a>So definieren Sie eine Depot-Form

1. **Create the container domain class**. Click the **Embedding Relationship** tool, click the root class of the model, and then click a blank part of the DSL definition diagram. Dadurch wird in der Beispielabbildung die Domänenklasse namens "Album" erstellt.

     Alternativ können Sie den Container statt in die Stammklasse auch in eine Domänenklasse einbetten, die einem Verantwortlichkeitsbereich zugeordnet ist.

     Add a domain property such as Name to the class, and set its **Is Element Name** flag in the Properties window.

2. **Create the list item domain class**. Click the **Embedding Relationship** tool, click the container class (Album) and then click a blank part of the diagram. Dadurch wird in der Beispielabbildung die Domänenklasse namens "Song" erstellt.

     Add a domain property such as Title to the class, and set its **Is Element Name** flag.

     Fügen Sie weitere Domäneneigenschaften hinzu.

     Fügen Sie eine weitere Domänenklasse für Listenelemente jeder Liste hinzu, die Sie anzeigen möchten.

3. **To mix several types of item in the list**, create classes that inherit from the list class. Make the list class abstract by setting its **Inheritance Modifier**.

     Möchten Sie beispielsweise klassische Musik nach Komponisten statt nach Interpreten sortieren, könnten Sie zwei Unterklassen von Song erstellen: ClassicalSong und NonClassicalSong.

4. **Create the compartment shape**. Drag from the **Compartment Shape** tool onto the DSL definition diagram.

     Fügen Sie ein Text-Decorator-Element hinzu, und legen Sie seinen Namen fest.

     Fügen Sie ein Depot hinzu, und legen Sie seinen Namen fest.

5. To let the user hide the list compartments, right-click the compartment shape class, point to **Add**, and then click **Expand/Collapse Decorator**. Legen Sie im Eigenschaftenfenster die Position des Decorator-Elements fest.

6. Click the **Diagram Element Map** tool, click the container domain class, and then click the compartment shape.

7. Wählen Sie den Diagrammelementzuordnungs-Link zwischen der Domänenklasse und der Form aus. In the **DSL Details** window:

    1. Click the **Decorators** tab. Click the name of the decorator and then select the appropriate item under **Display Property**. Stellen Sie sicher, dass neben dem Namen des Decorator-Elements ein Häkchen angezeigt wird.

    2. Click the **Compartment Maps** tab.

         Klicken Sie auf den Namen des Depots.

         Under **Displayed elements collection path**, navigate to the list element class (Song). Klicken Sie auf den Dropdownpfeil, um das Navigatorwerkzeug zu verwenden.

         Under **Display Property**, select the property that should be displayed in the list. Im Beispiel ist dies "Titel".

> [!NOTE]
> Mithilfe der Pfadfelder in der Decorator-Zuordnung und der Depot-Zuordnung können Sie komplexere Beziehungen zwischen der Domänenklasse und der Depot-Form erstellen.

#### <a name="to-define-a-tool-for-creating-the-shape"></a>So definieren Sie ein Werkzeug zum Erstellen der Form

1. **Make a toolbox item for creating elements of the domain class.**

2. In **DSL Explorer**, expand the **Editor** node and all its sub-nodes.

3. Right-click the node under **Toolbox Tabs** that has the same name as your DSL, for example MusicLibrary. Click **Add Element Tool**.

    > [!NOTE]
    > If you right-click the **Tools** node, you will not see **Add Element Tool**. Klicken Sie stattdessen auf den übergeordneten Knoten.

4. In the Properties window with the new element tool selected, set **Class** to the domain class that you have recently added.

5. Set **Caption** and **Tooltip**.

6. Set **Toolbox Icon** to an icon that will appear in the toolbox. Sie können ein neues Symbol oder ein bereits für ein anderes Werkzeug verwendetes Symbol angeben.

     To create a new icon, open Dsl\Resources in **Solution Explorer**. Kopieren Sie eine der vorhandenen BMP-Dateien für Elementwerkzeuge, und fügen Sie sie ein. Benennen Sie die eingefügte Kopie um, und doppelklicken Sie dann darauf, um sie zu öffnen.

     Return to the DSL Definition diagram, select the tool, and in the Properties window click **[...]** in **Toolbox Icon**. In the **Select Bitmap** dialog box, select your BMP file from the drop-down menu.

#### <a name="to-test-a-compartment-shape"></a>So testen Sie eine Depot-Form

1. **Click Transform All Templates** in the toolbar of Solution Explorer, to generate the DSL designer code.

2. **Build and run the DSL.** Press F5 or CTRL+F5 to run a new instance of [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] in experimental mode. Öffnen oder erstellen Sie in der experimentellen Instanz von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] eine Datei mit der Dateinamenerweiterung Ihrer DSL.

3. **Verify that the tool appears on the toolbox.**

4. Ziehen Sie das Werkzeug in das Modelldiagramm. Eine Form wird erstellt.

    Überprüfen Sie, ob der Name des Elements angezeigt und automatisch auf einen Standardwert festgelegt wird.

5. Right-click the header of the new shape, and then click Add *Your List Item.* Im Beispiel lautet der Befehl "Song hinzufügen".

    Überprüfen Sie, ob ein Element mit einem neuen Namen in der Liste erscheint.

6. Klicken Sie auf eines der Listenelemente, und betrachten Sie das Eigenschaftenfenster. Es sollten die Eigenschaften der Listenelemente angezeigt werden.

7. Öffnen Sie den Sprach-Explorer. Überprüfen Sie, ob die Containerknoten mit darin enthaltenen Listenelementknoten angezeigt werden.

   ![Generated explorer of DSL](../modeling/media/music-explorer.png "Music_Explorer")

   Nach dem ersten Test einer Depot-Form möchten Sie unter Umständen einige Eigenschaften anpassen und erweiterte Features hinzufügen. For more information, see [Customizing and Extending a Domain-Specific Language](../modeling/customizing-and-extending-a-domain-specific-language.md).

### <a name="displaying-a-reference-link-in-a-compartment"></a>Anzeigen eines Verweislinks in einem Depot
 Normalerweise ist ein in einem Depot angezeigtes Element ein untergeordnetes Element des Elements, das durch die Depot-Form dargestellt wird. Aber manchmal soll ein Element angezeigt werden, das durch eine Verweisbeziehung damit verbunden ist.

 Wir könnten z. B. ein zweites Depot zu AlbumShape hinzufügen, in dem eine Liste der mit dem Album verbundenen Interpreten angezeigt wird.

 In diesem Fall sollte das Depot statt des Elements, auf das verwiesen wird, den Link anzeigen. Denn wenn der Benutzer das Element im Depot auswählt und ENTF drückt, soll der Link gelöscht werden und nicht das Element, auf das verwiesen wird.

 Dennoch kann der Name des Elements, auf das verwiesen wird, im Depot erscheinen.

 Im folgenden Verfahren wird vorausgesetzt, dass Sie bereits die Domänenklasse, die Verweisbeziehung, die Depot-Form und die Diagrammelementzuordnung erstellt haben, wie weiter oben in diesem Abschnitt beschrieben.

##### <a name="to-display-a-reference-link-in-a-compartment"></a>So zeigen Sie einen Verweislink in einem Depot an

1. **Add a compartment to the compartment shape**. On the DSL Definition diagram, right-click the compartment shape class, point to **Add**, and then click **Compartment**.

2. Set **Displayed elements collection path** to navigate to the link, instead of its target element. Klicken Sie auf das Dropdownmenü, und verwenden Sie die Strukturansicht, um die Verweisbeziehung statt ihres Ziels auszuwählen. In the example, the relationship is **ArtistAppearedOnAlbums**.

3. Set **Path to Display Property** to navigate from the link to the target element. In the example, this is **Artist**.

4. Set **Display Property** to the appropriate property of the target element, for example **Name**.

5. **Transform All Templates**, build and run the DSL, and open a test model.

6. Erstellen Sie in dem Modelldiagramm die entsprechenden Formklassen, legen Sie ihre Namen fest, und erstellen Sie einen Link zwischen ihnen. In der Depot-Form sollten die Namen der verbundenen Elemente angezeigt werden.

7. Wählen Sie entweder den Link oder das Element in der Depot-Form aus. Sowohl der Link als auch das Element sollte angezeigt werden.

## <a name="ports"></a> Defining Ports on the Boundary of another Shape
 Ein Anschluss ist eine Form, die sich am Rand einer anderen Form befindet.

 Anschlüsse können auch verwendet werden, um einen festen Verbindungspunkt an einer anderen Form bereitzustellen, zu dem der Benutzer Konnektoren zeichnen kann. In diesem Fall können Sie die Anschluss-Form transparent machen.

 To see an example that uses ports, select the **Component Diagram** template when you create a new DSL solution. Dieses Beispiel zeigt die wesentlichen Punkte, die Sie bei der Definition von Anschlüssen berücksichtigen können:

- Es gibt eine Domänenklasse, die den Container der Anschlüsse darstellt: `Component`.

- Es gibt eine Domänenklasse, die Anschlüsse darstellt. Im Beispiel ist dies `ComponentPort`.

- Es gibt eine einbettende Beziehung von der Container-Domänenklasse zur Anschluss-Domänenklasse. For more information, see [Defining Domain Classes](#classes).

- Wenn verschiedene Anschlusstypen in demselben Container gemischt werden sollen, können Sie Unterklassen der Anschluss-Domänenklasse erstellen. In dem Beispiel erben `InPort` und `OutPort` von `ComponentPort`.

- Die Container-Domänenklasse kann jeder beliebigen Form zugeordnet werden. Im Beispiel ist dies `ComponentShape`. For more information, see [Defining Shapes](#shapes).

- Die Anschluss-Domänenklassen werden Anschluss-Formen zugeordnet. Sie können entweder die abgeleiteten Klassen verschiedenen Anschluss-Formklassen zuordnen oder die Basisklasse einer Anschluss-Formklasse zuordnen.

  In other respects, port shapes behave as described in [Defining Shapes](#shapes).

  For more information, see [Properties of Port Shapes](../modeling/properties-of-port-shapes.md).

## <a name="swimlanes"></a> Defining a DSL that has Swimlanes
 Verantwortlichkeitsbereiche sind vertikale oder horizontale Bereiche eines Diagramms. Jeder Verantwortlichkeitsbereich entspricht einem Modellelement. Ihre DSL-Definition muss eine Domänenklasse für die Verantwortlichkeitsbereich-Elemente enthalten.

 Am besten lässt sich eine DSL mit Verantwortlichkeitsbereichen erstellen, indem Sie eine neue DSL-Projektmappe erstellen und die Projektmappenvorlage "Aufgabenfluss" auswählen. In der DSL-Definition ist die Actor-Klasse die Domänenklasse, die dem Verantwortlichkeitsbereich zugeordnet wird. Benennen Sie diese und die anderen Klassen nach den Anforderungen Ihres Projekts um.

 Um eine Klasse hinzuzufügen, die als Form innerhalb eines Verantwortlichkeitsbereichs angezeigt wird, erstellen Sie eine einbettende Beziehung zwischen der Klasse des Verantwortlichkeitsbereichs und Ihrer neuen Klasse. Benutzer können Elemente von einem Verantwortlichkeitsbereich in einen anderen ziehen, aber jedes Element befindet sich immer innerhalb eines bestimmten Verantwortlichkeitsbereichs. In der Projektmappenvorlage "Aufgabenfluss" ist "FlowElement" ein untergeordnetes Element der Verantwortlichkeitsbereich-Klasse.

 Um eine Klasse hinzuzufügen, die als Form unabhängig von Verantwortlichkeitsbereichen angezeigt wird, erstellen Sie eine einbettende Beziehung zwischen der Stammklasse und Ihrer neuen Klasse. Benutzer können diese Formen beliebig im Diagramm platzieren, auch über die Grenzen von Verantwortlichkeitsbereichen hinweg und außerhalb von Verantwortlichkeitsbereichen. In der Projektmappenvorlage "Aufgabenfluss" ist "Comment" ein untergeordnetes Element der Stammklasse.

 For more information, see [Properties of Swimlanes](../modeling/properties-of-swimlanes.md).

## <a name="addTypes"></a> Adding Property Types

### <a name="domain-enumerations-and-literals"></a>Domänenenumerationen und Literale
 Eine Domänenenumeration ist ein Typ mit mehreren Literalwerten.

 To add a domain enumeration, right-click the root of the model in the **DSL Explorer** and then click **Add New Domain Enumeration**. The element will appear in the **DSL Explorer** under the **Domain Types** node. Das Element erscheint nicht im Diagramm.

 To add enumeration literals to the domain enumeration, right-click the domain enumeration in the **DSL Explorer** and then click **Add New Enumeration Literal**.

 Eine Eigenschaft, die einen Enumerationstyp besitzt, kann standardmäßig jeweils nur auf einen Wert der Enumeration festgelegt werden. If you want users and programmers to be able to set any combination of values - a "bit field" - set the **IsFlags** property of the Enumeration.

### <a name="external-types"></a>Externe Typen
 When you set the type of a domain property, if you do not find the type you want in the **Type** drop-down list, you can add an external type. For example, you could add the **System.Drawing.Color** type to the list.

 To add a type, right-click the root of the model in DSL Explorer, and then click **Add New External Type**. In the Properties window, set the name to **Color** and the namespace to **System.Drawing**. This type now appears in DSL Explorer under **Domain Types**. Sie können ihn immer auswählen, wenn Sie den Typ einer Domäneneigenschaft festlegen.

## <a name="custom"></a> Customizing the DSL
 Mit den hier beschriebenen Verfahren können Sie schnell eine DSL mit einer Diagrammdarstellung, einem lesbaren XML-Format und den grundlegenden Tools erstellen, mit denen Code und andere Artefakte generiert werden.

 Die DSL-Definition kann auf zwei Arten erweitert werden:

1. Optimieren Sie die DSL, indem Sie weitere Features in der DSL-Definition verwenden. Sie können beispielsweise ein einzelnes Konnektorwerkzeug erstellen, das verschiedene Typen von Konnektoren generieren kann, und Sie können die Regeln steuern, nach denen beim Löschen eines Elements auch verwandte Elemente gelöscht werden. Diese Verfahren bestehen meist im Festlegen von Werten in der DSL-Definition. Manche erfordern auch einige Zeilen Programmcode.

     For more information, see [Customizing and Extending a Domain-Specific Language](../modeling/customizing-and-extending-a-domain-specific-language.md).

2. Erweitern Sie Ihre Modellierungstools mit Programmcode, um kompliziertere Effekte zu erzielen. So können Sie z. B. Menübefehle erstellen, die das Modell ändern, und Sie können Tools erstellen, in denen zwei oder mehr DSLs integriert sind. VMSDK wurde speziell dafür entwickelt, die Integration Ihrer Erweiterungen in den Code zu vereinfachen, der aus der DSL-Definition generiert wird.  For more information, see [Writing Code to Customise a Domain-Specific Language](../modeling/writing-code-to-customise-a-domain-specific-language.md).

### <a name="changing-the-dsl-definition"></a>Ändern der DSL-Definition
 Wenn Sie ein Element in einer DSL-Definition erstellen, werden viele Standardwerte automatisch festgelegt. Diese Werte können Sie anschließend ändern. Dies vereinfacht die Entwicklung einer DSL und ermöglicht gleichzeitig wirkungsvolle Anpassungen.

 Wenn Sie beispielsweise eine Form einem Element zuordnen, wird der Pfad des übergeordneten Elements der Zuordnung automatisch entsprechend der einbettenden Beziehung der Domänenklasse festgelegt. Wenn Sie die einbettende Beziehung später ändern, wird der Pfad des übergeordneten Elements nicht automatisch geändert.

 Daher sollten Sie damit rechnen, dass nach einer Änderung von Beziehungen in der DSL-Definition häufig Fehler gemeldet werden, wenn Sie die Definition speichern oder "Alle Vorlagen transformieren" verwenden. Die meisten dieser Fehler sind leicht zu beheben. Doppelklicken Sie auf den Fehlerbericht, um den Ort des Fehlers zu ermitteln.

 See also [How to: Change the Namespace of a Domain-Specific Language](../modeling/how-to-change-the-namespace-of-a-domain-specific-language.md).

## <a name="trouble"></a> Troubleshooting
 In der folgenden Tabelle sind einige der häufigsten Probleme, die beim Entwurf einer DSL auftreten, zusammen mit ihrer Lösung aufgeführt. More advice is available on the [Visualization Tools Extensibililty Forum](https://go.microsoft.com/fwlink/?LinkId=186074).

|Problem|Vorschlag|
|-------------|----------------|
|Die Änderungen, die ich an der DSL-Definition vorgenommen habe, wirken sich nicht aus.|Click **Transform All Templates** in the toolbar above Solution Explorer, and then rebuild the solution.|
|Formen zeigen statt des Eigenschaftenwerts den Namen eines Decorator-Elements an.|Richten Sie die Decorator-Zuordnung ein. Klicken Sie im DSL-Definitionsdiagramm auf die Diagrammelementzuordnung (die graue Linie zwischen der Domänenklasse und der Formklasse).<br /><br /> Open the **DSL Details** window. If you cannot see it, on the View menu, point to **Other Windows**, and then click **DSL Details**.<br /><br /> Click the **Decorator Maps** tab. Select the name of the decorator. Vergewissern Sie sich, dass das Kontrollkästchen daneben aktiviert ist. Under **Display property**, select the name of a domain property.<br /><br /> For more information, see [Shapes on the Diagram](#shapes).|
|Ich kann in DSL-Explorer keine Auflistung hinzufügen. Zum Beispiel gibt es beim Rechtsklick auf "Werkzeuge" keinen "Tool hinzufügen"-Befehl im Menü.<br /><br /> Ich kann im Explorer für meine DSL kein Element zu einer Liste hinzufügen.|Klicken Sie mit der rechten Maustaste auf das Element über dem Knoten, den Sie testen. Wenn Sie etwas zu einer Liste hinzufügen möchten, befindet sich der Befehl zum Hinzufügen nicht im Listenknoten, sondern in seinem Besitzer.|
|Ich habe eine Domänenklasse erstellt, aber ich kann im Explorer der Sprache keine Instanzen erstellen.|Jede Domänenklasse mit Ausnahme des Stamms muss Ziel einer einbettenden Beziehung sein.|
|Im Explorer für meine DSL werden die Elemente nur mit ihren Typennamen angezeigt.|In the DSL Definition, select a domain property of the class and in the Properties window, set **Is Element Name** to true.|
|Meine DSL wird immer im XML-Editor geöffnet.|Das kann an einem Fehler beim Lesen der Datei liegen. Nachdem Sie den Fehler behoben haben, müssen Sie den Editor explizit als Ihren DSL-Designer zurücksetzen.<br /><br /> Right-click the project item, click **Open With** and select _YourLanguage_**Designer (Default)** .|
|Der Werkzeugkasten meiner DSL wird nicht angezeigt, nachdem ich die Assemblynamen geändert habe.|Inspect and update **DslPackage\GeneratedCode\Package.tt** For more information, see [How to: Change the Namespace of a Domain-Specific Language](../modeling/how-to-change-the-namespace-of-a-domain-specific-language.md).|
|Der Werkzeugkasten meiner DSL wird nicht angezeigt, obwohl ich die Assemblynamen nicht geändert habe.<br /><br /> Oder es wird in einem Meldungsfeld gemeldet, dass eine Erweiterung nicht geladen werden konnte.|Setzen Sie die experimentelle Instanz zurück, und erstellen Sie die Projektmappe neu.<br /><br /> 1.  At the Windows Start menu, under **All Programs**, expand [!INCLUDE[vssdk_current_long](../includes/vssdk-current-long-md.md)], then **Tools**, and then click **Reset the Microsoft Visual Studio Experimental Instance**.<br />2.  On the [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]**Build** menu, click **Rebuild Solution**.|

## <a name="see-also"></a>Siehe auch
 [Getting Started with Domain-Specific Languages](../modeling/getting-started-with-domain-specific-languages.md) [Creating a Windows Forms-Based Domain-Specific Language](../modeling/creating-a-windows-forms-based-domain-specific-language.md) [Creating a WPF-Based Domain-Specific Language](../modeling/creating-a-wpf-based-domain-specific-language.md)
