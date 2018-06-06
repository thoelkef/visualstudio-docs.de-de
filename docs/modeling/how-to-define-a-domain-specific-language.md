---
title: So definieren Sie eine domänenspezifische Sprache
ms.date: 11/04/2016
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: f870bce3abea444d6a04c0076d7110345c55ea7c
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34750427"
---
# <a name="how-to-define-a-domain-specific-language"></a>So definieren Sie eine domänenspezifische Sprache
Um eine domänenspezifische Sprache (DSL) zu definieren, erstellen Sie eine Visual Studio-Projektmappe aus einer Vorlage aus. Der zentrale Bestandteil der Projektmappe ist das DSL-Definitionsdiagramm, das in "DslDefinition.dsl" gespeichert wird. Die DSL-Definition definiert die Klassen und Formen der DSL. Nachdem Sie diese Elemente geändert und weitere hinzugefügt haben, können Sie Programmcode hinzufügen, um die DSL weiter anzupassen.

Wenn Sie konzentriert vertraut sind, es wird empfohlen, dass Sie über arbeiten die **DSL-Tools Lab**, das Sie an diesem Standort zugreifen können: [Visualizaton und Modellierungs-SDKS](http://go.microsoft.com/fwlink/?LinkID=186128)

##  <a name="templates"></a> Auswählen einer Vorlagenlösung
 Zur Definition einer DSL müssen folgende Komponenten installiert sein:

|||
|-|-|
|Visual Studio|[http://go.microsoft.com/fwlink/?LinkId=185579](http://go.microsoft.com/fwlink/?LinkId=185579)|
|[!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185580](http://go.microsoft.com/fwlink/?LinkId=185580)|
|Visual Studio Visualization and Modeling SDK||


[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]


 Um eine neue domänenspezifische Sprache zu erstellen, erstellen Sie eine neue Visual Studio-Projektmappe mithilfe der Projektvorlage einer domänenspezifischen Sprache.

#### <a name="to-create-a-dsl-solution"></a>So erstellen Sie eine DSL-Projektmappe

1.  Erstellen Sie eine Projektmappe mit der **einer domänenspezifischen Sprache** Vorlage, die sich unter **andere Projekttypen/Erweiterungen** in der **neues Projekt** (Dialogfeld).

     ![Dialogfeld „DSL erstellen“](../modeling/media/create_dsldialog.png)

     Beim Klicken auf **OK**, **einer domänenspezifischen Sprache Assistenten** wird geöffnet und zeigt eine Liste der DSL Vorlagenprojektmappen.

2.  Klicken Sie auf die einzelnen Vorlagen, um eine Beschreibung anzuzeigen. Wählen Sie die Projektmappe aus, die Ihren Vorstellungen am nächsten kommt.

     Jede DSL-Vorlage definiert eine grundlegende, funktionsfähige DSL. Sie bearbeiten diese DSL nach Ihren Anforderungen.

     Klicken Sie auf die Beispiele, um weitere Informationen anzuzeigen.

    -   Wählen Sie **Datenflusstask** DSL zu erstellen, Verantwortlichkeitsbereiche verfügt. Verantwortlichkeitsbereiche sind vertikale oder horizontale Bereiche des Diagramms.

    -   Wählen Sie **Komponentenmodelle** DSL erstellen, die Ports sind. Anschlüsse sind kleine Formen am Rand einer größeren Form.

    -   Wählen Sie **Klassendiagramme** DSL definieren mit Depot-Formen. Depot-Formen enthalten Listen von Elementen.

    -   Wählen Sie **minimale Sprache** in anderen Fällen, oder wenn Sie unsicher sind.

    -   Wählen Sie **minimale WinForm-Designer** oder **minimale WPF-Designer** DSL erstellen, die auf einer Windows Forms- oder WPF-Oberfläche angezeigt wird. Sie müssen Code zur Definition des Editors schreiben. Weitere Informationen finden Sie unter den folgenden Themen:

         [Erstellen einer Windows Forms-basierten domänenspezifischen Sprache](../modeling/creating-a-windows-forms-based-domain-specific-language.md)

         [Erstellen einer WPF-basierten domänenspezifischen Sprache](../modeling/creating-a-wpf-based-domain-specific-language.md)

3.  Geben Sie auf der entsprechenden Seite des Assistenten eine Dateinamenerweiterung für die DSL ein. Diese Erweiterung wird für Dateien mit Instanzen Ihrer DSL verwendet.

    -   Wählen Sie eine Dateinamenerweiterung, die keiner Anwendung auf Ihrem Computer bzw. auf einem Computer, auf dem Sie die DSL installieren möchten, zugeordnet ist. Beispielsweise **Docx** und **Htm** wäre nicht akzeptabel Datei Dateinamenerweiterungen.

    -   Der Assistent warnt Sie, wenn die eingegebene Erweiterung bereits als DSL verwendet wird. Verwenden Sie nach Möglichkeit eine andere Dateinamenerweiterung. Sie können die experimentelle Instanz des Visual Studio SDK auch zurücksetzen, um alte experimentelle Designer zu löschen. Klicken Sie auf **starten**, klicken Sie auf **Programme**, **Microsoft Visual Studio 2010 SDK**, **Tools**, und klicken Sie dann **Microsoft zurücksetzen Visual Studio 2010 experimentelle Instanz**.

4.  Auf den anderen Seiten können Sie Einstellungen anpassen oder die Standardwerte übernehmen.

5.  Klicken Sie auf **Fertig stellen**.

     Der Assistent erstellt eine Projektmappe mit zwei oder drei Projekten und generiert Code aus der DSL-Definition.

 Die Benutzeroberfläche gleicht nun der folgenden Abbildung.

 ![DSL-Designer](../modeling/media/dsl_designer.png)

 Diese Projektmappe definiert eine domänenspezifische Sprache. Weitere Informationen finden Sie unter [Überblick über die Benutzeroberfläche von einer domänenspezifischen Sprache Tools](../modeling/overview-of-the-domain-specific-language-tools-user-interface.md).

### <a name="test-the-solution"></a>Testen der Projektmappe
 Die Vorlagenprojektmappe enthält eine funktionsfähige DSL, die Sie ändern oder direkt verwenden können.

 Drücken Sie F5 oder STRG+F5, um die Projektmappe zu testen. Eine neue Instanz von Visual Studio wird im Testmodus geöffnet.

 Öffnen Sie in der neuen Instanz von Visual Studio im Projektmappen-Explorer die Beispieldatei. Sie wird als Diagramm mit einem Werkzeugkasten geöffnet.

 Wenn Sie eine Projektmappe ausführen haben Sie aus der **minimale Sprache** der experimentellen Visual Studio-Vorlage wird im folgende Beispiel ähneln:

 ![](../modeling/media/dsl_min.png)

 Experimentieren Sie mit den Werkzeugen. Erstellen Sie Elemente, und verbinden Sie sie.

 Schließen Sie die experimentelle Instanz von Visual Studio.

> [!NOTE]
>  Wenn Sie die DSL geändert haben, können Sie die Formen in der "Sample"-Testdatei nicht mehr sehen. Sie können aber neue Elemente erstellen.

### <a name="modifying-the-template-dsl"></a>Ändern der Vorlagen-DSL
 Benennen Sie einige oder alle Domänenklassen und Formklassen der Vorlagen-DSL-Definition um, und behalten Sie sie bei. Die neuen Klassennamen sollten gültige CLR-Namen ohne Leerzeichen oder Interpunktionszeichen sein.

 Die Beibehaltung der folgenden Klassen ist besonders sinnvoll:

-   Die Stammklasse erscheint auf der linken oberen Ecke der DSL-Definitionsdiagramm unter **Klassen und Beziehungen**. Benennen Sie sie in einen von der DSL verschiedenen Namen um. Z. B. eine DSL, die mit dem Namen **MusicLibrary** möglicherweise eine Stammklasse, die mit dem Namen **Musik**.

-   Die Diagramm-Klasse auf der unteren rechten Ecke der DSL-Definitionsdiagramm wird angezeigt, der **Diagrammelemente** Spalte. Möglicherweise müssen Sie einen Bildlauf nach rechts durchführen, um sie zu sehen. Es ist in der Regel mit dem Namen * YourDsl ***Diagramm**.

-   Bei Verwendung der **Datenflusstask** Vorlage und Erstellen von Diagrammen mit Verantwortlichkeitsbereiche, beibehalten, und benennen Sie die Domänenklasse Akteur und ActorSwimlane Form möchten.

 Löschen Sie andere Klassen nach Bedarf, oder benennen Sie sie um.

##  <a name="patterns"></a> Muster zum Definieren einer DSL
 Es ist empfehlenswert, beim Entwickeln einer DSL nur jeweils ein oder zwei Features gleichzeitig hinzuzufügen bzw. anzupassen. Fügen Sie ein Feature hinzu, führen Sie die DSL aus und testen Sie sie. Fügen Sie dann ein oder zwei weitere Features hinzu. Ein typisches Feature Ihrer DSL könnte folgendermaßen aussehen:

-   Eine Domänenklasse, die einbettende Beziehung, die das Element mit dem Modell verbindet, die erforderliche Form zum Anzeigen von Elementen der Klasse im Diagramm sowie das Elementwerkzeug, mit dem Benutzer Elemente erstellen können.

-   Die Domäneneigenschaften einer Domänenklasse und die Decorator-Elemente, die sie in einer Form anzeigen.

-   Eine Verweisbeziehung und der Konnektor, der sie im Diagramm anzeigt, sowie das Konnektorwerkzeug, mit dem Benutzer Verbindungen erstellen können.

-   Eine Anpassung, die Programmcode erfordert, wie z. B. eine Validierungseinschränkung oder ein Menübefehl.

 In den folgenden Abschnitten wird die Erstellung der nützlichsten DSL-Features beschrieben. Es gibt viele andere Muster, nach denen eine DSL erstellt werden kann, aber die folgenden sind die gängigsten.

> [!NOTE]
>  Nach dem Hinzufügen einer Funktion, vergessen Sie nicht auf **alle Vorlagen transformieren** auf der Symbolleiste des Projektmappen-Explorer überprüfen Sie vor dem Erstellen und Ausführen der DSL.

 In der folgenden Abbildung sind die Klassen und Beziehungen der DSL dargestellt, die in diesem Thema als Beispiel verwendet wird.

 ![Einbetten von und Verweisen auf Beziehungen](../modeling/media/music_classes.png)

 Die nächste Abbildung zeigt ein Beispielmodell dieser DSL:

 ![Instanzmodell für generierte DSL](../modeling/media/music_instance.png)

> [!NOTE]
>  "Modell" bezieht sich auf eine Instanz Ihrer DSL, die Benutzer erstellen. Sie wird üblicherweise als Diagramm dargestellt. In diesem Thema werden das DSL-Definitionsdiagramm und die Modelldiagramme erläutert, die bei Verwendung der DSL angezeigt werden.

##  <a name="classes"></a> Definieren von Domänenklassen
 Domänenklassen stellen die Konzepte der DSL dar. Die Instanzen sind *Modellelementen*. Z. B. in einem **MusicLibrary** DSL Sie möglicherweise mit dem Namen Domänenklassen **Album** und **Musiktitel**.

 Um eine Domänenklasse zu erstellen, können Sie aus ziehen die **Domänenklasse namens** -tool in das Diagramm, und benennen Sie die Klasse.

 Weitere Informationen finden Sie unter [Eigenschaften Domänenklassen](../modeling/properties-of-domain-classes.md).

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

 Um einer Domänenklasse und ihre einbetten gleichzeitig zu erstellen, klicken Sie auf die **einbetten Beziehung** tool, klicken Sie auf die übergeordnete Klasse, und klicken Sie dann auf einen leeren Bereich des Diagramms.

 In der Regel müssen Sie den Namen der einbettenden Beziehung und ihrer Rollen nicht anpassen, da automatisch die Klassennamen verwendet werden.

 Weitere Informationen finden Sie unter [Eigenschaften Domänenbeziehungen](../modeling/properties-of-domain-relationships.md) und [Eigenschaften Domänenfunktionen](../modeling/properties-of-domain-roles.md).

> [!NOTE]
>  Einbettung ist nicht identisch mit Vererbung. Die untergeordneten Elemente in einer einbettenden Beziehung erben keine Features von ihren übergeordneten Elementen.

### <a name="add-domain-properties-to-each-domain-class"></a>Hinzufügen von Domäneneigenschaften zu den einzelnen Domänenklassen
 In Domäneneigenschaften werden Werte gespeichert. Beispiele: Name, Titel, Veröffentlichungsdatum.

 Klicken Sie auf **Domäneneigenschaften** in der Klasse, die EINGABETASTE drücken, und geben Sie den Namen einer Eigenschaft. Der Standardtyp einer Domäneneigenschaft lautet String. Wenn Sie den Typ ändern möchten, wählen Sie die Eigenschaft "Domain", und legen Sie die **Typ** in der **Eigenschaften** Fenster. Wenn der Typ des nicht in der Dropdown-Liste enthalten ist, finden Sie unter [Eigenschaftentypen hinzufügen](#addTypes).

 **Legen Sie eine Elementnamen-Eigenschaft.** Wählen Sie eine Eigenschaft "Domain", die zum Identifizieren von Elementen im Explorer Sprache verwendet werden kann. Beispielsweise könnten Sie in der "Song"-Domänenklasse die "Titel"-Domäneneigenschaft auswählen. In der **Eigenschaften** legen **Elementname ist** auf `true`.

### <a name="create-derived-domain-classes"></a>Erstellen abgeleiteter Domänenklassen
 Soll eine Domänenklasse Varianten aufweisen, die ihre Eigenschaften und Beziehungen erben, erstellen Sie von der Domänenklasse abgeleitete Klassen. "Album" könnte z. B. die abgeleiteten Klassen WMA und MP3 haben.

 Erstellen Sie mit der abgeleiteten Klasse die **Domänenklasse** Tool.

 Klicken Sie auf die **Vererbung** -tool, klicken Sie auf die abgeleitete Klasse, und klicken Sie dann auf die Basisklasse.

 Legen Sie die **Inheritance Modifier** von der Basisklasse **abstrakte**. Wenn Sie voraussichtlich Instanzen der Basisklasse benötigen, können Sie stattdessen eine gesonderte abgeleitete Klasse für diese erstellen.

 Abgeleitete Klassen erben die Eigenschaften und Rollen ihrer Basisklassen.

### <a name="tidy-the-dsl-definition-diagram"></a>Bereinigen des DSL-Definitionsdiagramms
 Wenn Sie Beziehungen hinzufügen, erscheinen einige Klassen an mehreren Stellen. Zum Verringern der Anzahl der eindeutigkeitsmetrik, und stellen das Diagramm breiter, mit der rechten Maustaste der Zielklasse einer Beziehung, und klicken Sie dann auf **Struktur hier schalten**. Den gegenteiligen Effekt mit der rechten Maustaste der Zielklasse einer Beziehung, und klicken Sie auf **Teilung Struktur**. Wenn diese Menübefehle nicht angezeigt werden, vergewissern Sie sich, dass nur die Domänenklasse ausgewählt ist.

 Verwenden Sie STRG+NACH OBEN und STRG+NACH UNTEN, um Domänenklassen und Formklassen zu verschieben.

### <a name="test-the-domain-classes"></a>Testen der Domänenklassen

##### <a name="to-test-the-new-domain-classes"></a>So testen Sie die neuen Domänenklassen

1.  **Klicken Sie auf alle Vorlagen transformieren** auf der Symbolleiste des Projektmappen-Explorer, um den DSL-Designer-Code zu generieren. Dieser Schritt kann automatisiert werden. Weitere Informationen finden Sie unter [wie alle Vorlagen transformieren automatisieren](http://msdn.microsoft.com/b63cfe20-fe5e-47cc-9506-59b29bca768a).

2.  **Erstellen und Ausführen der DSL.** Drücken Sie F5 oder STRG + F5, um eine neue Instanz von Visual Studio im Testmodus ausgeführt. Klicken Sie in der experimentellen Instanz von Visual Studio öffnen Sie, oder erstellen Sie eine Datei mit der Erweiterung der DSL.

3.  **Öffnen Sie den Explorer an.** AT die Seite des Diagramms ist der Language-Explorer-Fenster, das normalerweise heißt *YourLanguage* Explorer. Sollten Sie das Fenster nicht sehen, befindet es sich möglicherweise auf einer Registerkarte unter dem Projektmappen-Explorer. Findet Sie es, auf die **Ansicht** Sie im Menü **Weitere Fenster**, und klicken Sie dann auf *YourLanguage* **Explorer**.

     Im Explorer wird eine Strukturansicht des Modells dargestellt.

4.  **Erstellen Sie neue Elemente.** Mit der rechten Maustaste oben auf des Stammknoten, und klicken Sie dann auf **neuer *** YourClass*.

     Im Sprach-Explorer wird eine neue Instanz Ihrer Klasse angezeigt.

5.  Überprüfen Sie beim Erstellen neuer Instanzen, ob jede Instanz einen anderen Namen hat. Dies geschieht nur, wenn Sie festgelegt haben die **Elementname ist** -Flag auf eine Eigenschaft "Domain".

6.  **Untersuchen Sie die Domäneneigenschaften. Mit einer Instanz der Klasse ausgewählt haben** Eigenschaftenfenster überprüfen. Es sollte die Domäneneigenschaften zeigen, die Sie für die Domänenklasse definiert haben.

7.  **Speichern Sie die Datei, schließen Sie es und öffnen Sie es erneut**. Nachdem Sie die Knoten erweitert haben, sollten alle erstellten Instanzen im Explorer sichtbar sein.

##  <a name="shapes"></a> Definieren von Formen im Diagramm
 Sie können Klassen von Elementen definieren, die in einem Diagramm als Rechtecke, Ellipsen oder Symbole erscheinen.

#### <a name="to-define-a-class-of-elements-that-appear-as-shapes-on-a-diagram"></a>So definieren Sie eine Klasse von Elementen, die in einem Diagramm als Formen dargestellt werden

1.  **Definieren und testen eine Domänenklasse wie beschrieben in**[Domänenklassen definieren](#classes) **.**

    -   Das übergeordnete Element der Klasse sollte die Stammklasse sein. Es sollte also eine einbettende Beziehung zwischen der Stammklasse und der neuen Domänenklasse bestehen.

    -   Wenn das Diagramm Verantwortlichkeitsbereiche enthält, kann das übergeordnete Element die Domänenklasse sein, die einem Verantwortlichkeitsbereich zugeordnet ist. Bevor Sie mit dieser Prozedur fortfahren, finden Sie unter [definieren eine DSL, die Verantwortlichkeitsbereiche](#swimlanes).

2.  **Fügen Sie eine Form vom Typ Klasse** zur Darstellung der Elemente im Modelldiagramm. Ziehen Sie eines der folgenden Werkzeuge in das DSL-Definitionsdiagramm:

    -   **Form "Geometry"** enthält ein Rechteck oder eine Ellipse.

    -   **Bild-Form** zeigt ein Bild, das Sie bereitstellen.

    -   **Depot-Form** ist ein Rechteck, das eine oder mehrere Listen von Elementen enthält.

     Benennen Sie die Formklasse um, die rechts im DSL-Definitionsdiagramm unter "Formen und Konnektoren" angezeigt wird.

3.  **Definieren Sie ein Bild aus, wenn Sie eine Form "Image" erstellt**.

    1.  Erstellen Sie eine Bilddatei beliebiger Größe. Die Formate BMP, JPEG, GIF und EMF werden unterstützt.

    2.  Fügen Sie die Datei im Projektmappen-Explorer der Projektmappe unter Dsl\Ressourcen hinzu.

    3.  Kehren Sie zum DSL-Definitionsdiagramm zurück, und wählen Sie die neue Bild-Formklasse aus.

    4.  Klicken Sie im Eigenschaftenfenster auf die **Image** Eigenschaft.

    5.  In der **Bild auswählen** Dialogfeld klicken Sie auf das Dropdown-Menü unter **Dateiname**, und wählen Sie das Bild.

4.  **Fügen Sie Text Decorator-Elementen mit der Form, um die Domäneneigenschaften anzuzeigen.**

     Sie benötigen wahrscheinlich mindestens ein Text-Decorator-Element, um den Namen oder Titel des Modellelements anzuzeigen.

     Mit der rechten Maustaste in des Headers der Shape-Klasse, zeigen Sie auf **hinzufügen**, und klicken Sie dann auf **Text Decorator**. Legen Sie den Namen des der Decorator-Element, und klicken Sie im Satz im Fenster Eigenschaften die **Position**.

5.  **Verbinden Sie jede Form mit einer Karte Diagramm-Element, auf die Domänenklasse, die angezeigt werden soll**.

     Klicken Sie auf die **Diagramm Element Zuordnung** tool, klicken Sie auf die Domänenklasse, dann klicken Sie auf die Form "-Klasse.

6.  **Ordnen Sie die Eigenschaften der Text Decorators.**

    1.  Wählen Sie die graue Linie zwischen der Domänenklasse und der Formklasse aus, die die Diagrammelementzuordnung darstellt.

    2.  In der **DSL-Detailfenster** Fenster, klicken Sie auf die **Decorator-Zuordnungen** Registerkarte. Wenn Sie nicht sehen die **DSL-Detailfenster** Fenster auf die **Ansicht** Startmenü nacheinander auf **Weitere Fenster** , und klicken Sie dann auf **DSL-Detailfenster**. Häufig muss der obere Rand des Fensters angehoben werden, um den gesamten Inhalt anzuzeigen.

    3.  Wählen Sie den Namen eines Decorator-Elements aus. Klicken Sie unter **Anzeigeeigenschaft**, wählen Sie den Namen einer Eigenschaft der Domänenklasse. Wiederholen Sie dies für jedes Decorator-Element.

         Wenn Sie eine Eigenschaft eines verknüpften Elements anzeigen möchten, klicken Sie auf den Dropdown-Struktur-Navigator unter **Pfad anzuzeigende Eigenschaft**.

    4.  Stellen Sie sicher, dass neben jedem Decorator-Namen ein Häkchen angezeigt wird.

     ![Formzuordnungen und DSL-Detailfenster](../modeling/media/dsldetailswindow.png)

7.  **Stellen Sie ein Toolboxelement zum Erstellen von Elementen der Domänenklasse.**

    1.  In **Explorer für DSL**, erweitern Sie die **Editor** Knoten und dessen untergeordnete Knoten.

    2.  Mit der rechten Maustaste unter des Knotens **Toolboxregisterkarten** , die den gleichen Namen wie der DSL, z. B. MusicLibrary besitzt. Klicken Sie auf **Elementtool hinzufügen**.

        > [!NOTE]
        >  Wenn Sie mit der rechten Maustaste die **Tools** Knoten nicht sehen Sie **Tool zum Hinzufügen eines Element**. Klicken Sie stattdessen auf den übergeordneten Knoten.

    3.  Legen Sie im Fenster Eigenschaften mit dem neuen Elementtool ausgewählt **Klasse** auf die Domänenklasse, die Sie vor kurzem hinzugefügt haben.

    4.  Legen Sie **Beschriftung** und **QuickInfo**.

    5.  Legen Sie **Symbol "Toolbox"** auf ein Symbol, das in der Toolbox angezeigt werden. Sie können ein neues Symbol oder ein bereits für ein anderes Werkzeug verwendetes Symbol angeben.

         Öffnen Sie zum Erstellen eines Symbol "neuen" Dsl\Resources in **Projektmappen-Explorer**. Kopieren Sie eine der vorhandenen BMP-Dateien für Elementwerkzeuge, und fügen Sie sie ein. Benennen Sie die eingefügte Kopie um, und doppelklicken Sie dann darauf, um sie zu öffnen.

         Kehren Sie zu der DSL-Definitionsdiagramm zurück, wählen Sie das Tool und klicken Sie im Eigenschaftenfenster auf **[...]**  in **Symbol "Toolbox"**. In der **wählen Bitmap** wählen Sie im Dialogfeld die. BMP-Datei aus dem Dropdown-Menü.

 Weitere Informationen finden Sie unter [Eigenschaften von Geometry Formen](../modeling/properties-of-geometry-shapes.md) und [Eigenschaften des Image Formen](../modeling/properties-of-image-shapes.md).

#### <a name="to-test-shapes"></a>So testen Sie Formen

1.  **Klicken Sie auf alle Vorlagen transformieren** auf der Symbolleiste des Projektmappen-Explorer, um den DSL-Designer-Code zu generieren.

2.  **Erstellen und Ausführen der DSL.** Drücken Sie F5 oder STRG + F5, um eine neue Instanz von Visual Studio im Testmodus ausgeführt. Klicken Sie in der experimentellen Instanz von Visual Studio öffnen Sie, oder erstellen Sie eine Datei mit der Erweiterung der DSL.

3.  **Stellen Sie sicher, dass die Elementtools in der Toolbox angezeigt werden.**

4.  **Erstellen von Shapes** von einem Tool im Modell-Diagramm ziehen.

5.  **Stellen Sie sicher, dass jede Decorator Text angezeigt wird,** und:

    1.  Sie bearbeiten können, es sei denn, Sie festgelegt haben die **ist UI Read Only** Flag für die Eigenschaft "Domain".

    2.  Wenn Sie die Eigenschaft im Eigenschaftenfenster oder im Decorator bearbeiten, wird die jeweils andere Ansicht aktualisiert.

 Nach dem ersten Test einer Form möchten Sie unter Umständen einige Eigenschaften anpassen und erweiterte Features hinzufügen. Weitere Informationen finden Sie unter [anpassen und Erweitern einer domänenspezifischen Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md).

##  <a name="references"></a> Definieren von Verweisbeziehungen
 Sie können eine Verweisbeziehung zwischen einer Quelldomänenklasse und einer Zieldomänenklasse definieren. Verweisbeziehungen werden in einem Diagramm üblicherweise als Konnektoren, also als Linien zwischen Formen, angezeigt.

 Wenn beispielsweise Alben und Interpreten als Formen in einem Diagramm dargestellt werden, könnten Sie eine Beziehung namens "ArtistsAppearedOnAlbums" definieren, die Interpreten mit den Alben verknüpft, an denen sie mitgewirkt haben. Siehe das Beispiel in der Abbildung.

 ![Instanzmodell für generierte DSL](../modeling/media/music_instance.png)

 Verweisbeziehungen können auch Elemente desselben Typs verbinden. So ist in einer DSL, die einen Familienstammbaum darstellt, die Beziehung zwischen Eltern und Kindern eine Verweisbeziehung von Person zu Person.

### <a name="define-a-reference-relationship"></a>Definieren einer Verweisbeziehung
 Klicken Sie auf das Werkzeug "Verweisbeziehung", auf die Quelldomänenklasse der Beziehung und dann auf die Zieldomänenklasse. Die Zielklasse kann mit der Quellklasse übereinstimmen.

 Jede Beziehung hat zwei Rollen, die durch die Linien auf beiden Seiten des Beziehungsfelds dargestellt werden. Sie können jede Rolle auswählen und ihre Eigenschaften im Eigenschaftenfenster festlegen.

 **Betrachten Sie die Rollen umbenennen**. In einer Beziehung zwischen Personen könnten Sie z. B. die Standardnamen in Eltern und Kinder, Manager und Mitarbeiter, Lehrer und Schüler usw. ändern.

 **Passen Sie die Multiplizitäten jeder Rolle**, wenn es erforderlich ist. Soll jede Person höchstens einen Manager haben, legen Sie die Multiplizität (unter der Beschriftung "Manager") im Diagramm auf 0..1 fest.

 **Die Beziehung Domäneneigenschaften hinzufügen.** In der Abbildung weist die Interpret-Album Beziehung eine Eigenschaft der Rolle.

 **Legen Sie die Eigenschaft ermöglicht es, um Duplikate der Beziehung,** Wenn mehr als einen Link in der gleichen Klasse zwischen demselben Dateipaar Modellelemente vorhanden sein kann. Beispielsweise könnten Sie zulassen, dass ein Lehrer einen Schüler in mehreren Fächern unterrichtet.

 ![Formzuordnungen für Verbindungen](../modeling/media/music_connector.png)

 Weitere Informationen finden Sie unter [Eigenschaften Domänenbeziehungen](../modeling/properties-of-domain-relationships.md) und [Eigenschaften Domänenfunktionen](../modeling/properties-of-domain-roles.md).

### <a name="define-a-connector-to-display-the-relationship"></a>Definieren eines Konnektors zur Darstellung der Beziehung
 Ein Konnektor stellt eine Linie zwischen zwei Formen im Modelldiagramm dar.

 Ziehen Sie die **Connector** Tool auf der DSL-Definitionsdiagramm.

 Fügen Sie Text-Decorator-Elemente hinzu, falls Beschriftungen auf dem Konnektor angezeigt werden sollen. Legen Sie deren Positionen fest. Damit den Benutzer einen Decorator-Text Element verschieben können, legen Sie dessen **verschoben wird** Eigenschaft.

 Verwenden der **Diagramm Element Zuordnung** Tool, um den Connector mit der verweisbeziehung zu verknüpfen.

 Öffnen Sie mit der Zuordnung von Diagramm Element ausgewählt, die **DSL-Detailfenster** Fenster, und Öffnen der **Decorator-Zuordnungen** Registerkarte.

 Wählen Sie die einzelnen **Decorator** und **Anzeigeeigenschaft** an die richtige Domäneneigenschaft.

 Stellen Sie sicher, dass ein neben jedem Element in Häkchen der **Decorators** Liste.

### <a name="define-a-connection-builder-tool"></a>Definieren eines Werkzeugs "Verbindungs-Generator"
 In der **Explorer für DSL** Fenster, erweitern Sie die **Editor** Knoten und alle zugehörigen untergeordneten Knoten.

 Mit der rechten Maustaste des Knotens mit dem gleichen Namen wie der DSL, und klicken Sie dann auf **neue Verbindungstool hinzufügen**.

 Führen Sie, während das neue Werkzeug ausgewählt ist, im Eigenschaftenfenster Folgendes aus:

-   Legen Sie die **Beschriftung** und **QuickInfo**.

-   Klicken Sie auf **Verbindungsgenerator** , und wählen Sie den entsprechenden Generator für die neue Beziehung.

-   Legen Sie **Symbol "Toolbox"** auf das Symbol, das in der Toolbox angezeigt werden sollen. Sie können ein neues Symbol oder ein bereits für ein anderes Werkzeug verwendetes Symbol angeben.

     Öffnen Sie zum Erstellen eines Symbol "neuen" Dsl\Resources in **Projektmappen-Explorer**. Kopieren Sie eine der vorhandenen BMP-Dateien für Elementwerkzeuge, und fügen Sie sie ein. Benennen Sie die eingefügte Kopie um, und doppelklicken Sie dann darauf, um sie zu öffnen.

     Kehren Sie zu der DSL-Definitionsdiagramm zurück, wählen Sie das Tool und klicken Sie im Eigenschaftenfenster auf **[...]**  in **Symbol "Toolbox"**. In der **wählen Bitmap** wählen Sie im Dialogfeld die. BMP-Datei aus dem Dropdown-Menü.

##### <a name="to-test-a-reference-relationship-and-connector"></a>So testen Sie eine Verweisbeziehung und einen Konnektor

1.  **Klicken Sie auf alle Vorlagen transformieren** auf der Symbolleiste des Projektmappen-Explorer, um den DSL-Designer-Code zu generieren.

2.  **Erstellen und Ausführen der DSL.** Drücken Sie F5 oder STRG + F5, um eine neue Instanz von Visual Studio im Testmodus ausgeführt. Klicken Sie in der experimentellen Instanz von Visual Studio öffnen Sie, oder erstellen Sie eine Datei mit der Erweiterung der DSL.

3.  **Stellen Sie sicher, dass in der Toolbox das Verbindungstool angezeigt wird.**

4.  **Erstellen von Shapes** von einem Tool im Modell-Diagramm ziehen.

5.  **Erstellen von Verbindungen** zwischen den Formen. Klicken Sie auf das Konnektorwerkzeug, auf eine Form und dann auf eine andere Form.

6.  **Stellen Sie sicher, dass Sie Verbindungen zwischen ungeeigneten Klassen erstellen können.** Beispielsweise ist die Beziehung zwischen Alben und Künstler, überprüfen Sie, ob Künstler Künstler verknüpft werden können.

7.  **Stellen Sie sicher, dass die Multiplizitäten richtig sind. Beispielsweise stellen Sie sicher, dass eine Person mehrere Manager hergestellt werden kann.**

8.  **Stellen Sie sicher, dass jede Decorator Text angezeigt wird,** und:

    1.  Sie bearbeiten können, es sei denn, Sie festgelegt haben die **ist UI Read Only** Flag für die Eigenschaft "Domain".

    2.  Wenn Sie die Eigenschaft im Eigenschaftenfenster oder im Decorator bearbeiten, wird die jeweils andere Ansicht aktualisiert.

 Nach dem ersten Test eines Konnektors möchten Sie unter Umständen einige Eigenschaften anpassen und erweiterte Features hinzufügen. Weitere Informationen finden Sie unter [anpassen und Erweitern einer domänenspezifischen Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md).

##  <a name="compartments"></a> Definieren von Formen, die Listen enthalten:-Fach Formen
 Eine Depot-Form enthält mindestens eine Liste von Elementen. In einer DSL für eine Musikbibliothek würden Sie z. B. Depot-Formen verwenden, um Musikalben darzustellen. Jedes Album enthält eine Liste von Songs.

 ![Depot-Form](../modeling/media/compartmentshape.png)

 Am einfachsten erzielen Sie diesen Effekt in einer DSL-Definition, indem Sie eine Domänenklasse für den Container und eine Domänenklasse für jede Liste definieren. Die Containerklasse wird der Depot-Form zugeordnet.

 ![Formzuordnung](../modeling/media/music_mapcomp.png)

 Weitere Informationen finden Sie unter [Eigenschaften von Depot Formen](../modeling/properties-of-compartment-shapes.md).

#### <a name="to-define-a-compartment-shape"></a>So definieren Sie eine Depot-Form

1.  **Erstellen Sie die Container-Domänenklasse**. Klicken Sie auf die **einbetten Beziehung** -tool, klicken Sie auf die Stammklasse des Modells, und klicken Sie dann auf einen leeren Teil der DSL-Definitionsdiagramm. Dadurch wird in der Beispielabbildung die Domänenklasse namens "Album" erstellt.

     Alternativ können Sie den Container statt in die Stammklasse auch in eine Domänenklasse einbetten, die einem Verantwortlichkeitsbereich zugeordnet ist.

     Die Klasse eine Eigenschaft "Domain" z. B. Namen hinzu, und legen Sie dessen **Elementname ist** Flag im Eigenschaftenfenster angezeigt.

2.  **Erstellen Sie die Liste Domäne Elementklasse**. Klicken Sie auf die **einbetten Beziehung** -tool, klicken Sie auf die Container-Klasse (Album), und klicken Sie dann auf einen leeren Bereich des Diagramms. Dadurch wird in der Beispielabbildung die Domänenklasse namens "Song" erstellt.

     Fügen Sie eine Eigenschaft "Domain" z. B. den Titel aus, um die Klasse, und legen seine **Elementname ist** Flag.

     Fügen Sie weitere Domäneneigenschaften hinzu.

     Fügen Sie eine weitere Domänenklasse für Listenelemente jeder Liste hinzu, die Sie anzeigen möchten.

3.  **Zum Mischen von verschiedenen Typen des Elements in der Liste**, Erstellen von Klassen, die aus der List-Klasse erben. Der List-Klasse abstrakt machen, indem seine **Inheritance Modifier**.

     Möchten Sie beispielsweise klassische Musik nach Komponisten statt nach Interpreten sortieren, könnten Sie zwei Unterklassen von Song erstellen: ClassicalSong und NonClassicalSong.

4.  **Erstellen Sie die Form "Depot"**. Ziehen Sie aus der **Depot-Form** Tool auf der DSL-Definitionsdiagramm.

     Fügen Sie ein Text-Decorator-Element hinzu, und legen Sie seinen Namen fest.

     Fügen Sie ein Depot hinzu, und legen Sie seinen Namen fest.

5.  Damit können die Benutzer Ausblenden von Depots in der Liste der rechten Maustaste auf die Depot-Form-Klasse, zeigen Sie auf **hinzufügen**, und klicken Sie dann auf **erweitern/reduzieren-Decorator**. Legen Sie im Eigenschaftenfenster die Position des Decorator-Elements fest.

6.  Klicken Sie auf die **Diagramm Element Zuordnung** -tool, klicken Sie auf der Containerklasse für die Domäne und klicken Sie dann auf die Form "Depot".

7.  Wählen Sie den Diagrammelementzuordnungs-Link zwischen der Domänenklasse und der Form aus. In der **DSL-Detailfenster** Fenster:

    1.  Klicken Sie auf die **Decorators** Registerkarte. Klicken Sie auf den Namen des der Decorator-Element, und wählen Sie dann das entsprechende Element unter **Anzeigeeigenschaft**. Stellen Sie sicher, dass neben dem Namen des Decorator-Elements ein Häkchen angezeigt wird.

    2.  Klicken Sie auf die **Depot Maps** Registerkarte.

         Klicken Sie auf den Namen des Depots.

         Klicken Sie unter **angezeigte Elemente Sammlungspfad**, navigieren Sie zu der Liste Elementklasse (Titel). Klicken Sie auf den Dropdownpfeil, um das Navigatorwerkzeug zu verwenden.

         Klicken Sie unter **Anzeigeeigenschaft**, wählen Sie die Eigenschaft, die in der Liste angezeigt werden sollen. Im Beispiel ist dies "Titel".

> [!NOTE]
>  Mithilfe der Pfadfelder in der Decorator-Zuordnung und der Depot-Zuordnung können Sie komplexere Beziehungen zwischen der Domänenklasse und der Depot-Form erstellen.

#### <a name="to-define-a-tool-for-creating-the-shape"></a>So definieren Sie ein Werkzeug zum Erstellen der Form

1.  **Stellen Sie ein Toolboxelement zum Erstellen von Elementen der Domänenklasse.**

2.  In **Explorer für DSL**, erweitern Sie die **Editor** Knoten und dessen untergeordnete Knoten.

3.  Mit der rechten Maustaste unter des Knotens **Toolboxregisterkarten** , die den gleichen Namen wie der DSL, z. B. MusicLibrary besitzt. Klicken Sie auf **Elementtool hinzufügen**.

    > [!NOTE]
    >  Wenn Sie mit der rechten Maustaste die **Tools** Knoten nicht sehen Sie **Tool zum Hinzufügen eines Element**. Klicken Sie stattdessen auf den übergeordneten Knoten.

4.  Legen Sie im Fenster Eigenschaften mit dem neuen Elementtool ausgewählt **Klasse** auf die Domänenklasse, die Sie vor kurzem hinzugefügt haben.

5.  Legen Sie **Beschriftung** und **QuickInfo**.

6.  Legen Sie **Symbol "Toolbox"** auf ein Symbol, das in der Toolbox angezeigt werden. Sie können ein neues Symbol oder ein bereits für ein anderes Werkzeug verwendetes Symbol angeben.

     Öffnen Sie zum Erstellen eines Symbol "neuen" Dsl\Resources in **Projektmappen-Explorer**. Kopieren Sie eine der vorhandenen BMP-Dateien für Elementwerkzeuge, und fügen Sie sie ein. Benennen Sie die eingefügte Kopie um, und doppelklicken Sie dann darauf, um sie zu öffnen.

     Kehren Sie zu der DSL-Definitionsdiagramm zurück, wählen Sie das Tool und klicken Sie im Eigenschaftenfenster auf **[...]**  in **Symbol "Toolbox"**. In der **wählen Bitmap** Dialogfeld wählen die BMP-Datei aus dem Dropdown-Menü.

#### <a name="to-test-a-compartment-shape"></a>So testen Sie eine Depot-Form

1.  **Klicken Sie auf alle Vorlagen transformieren** auf der Symbolleiste des Projektmappen-Explorer, um den DSL-Designer-Code zu generieren.

2.  **Erstellen und Ausführen der DSL.** Drücken Sie F5 oder STRG + F5, um eine neue Instanz von Visual Studio im Testmodus ausgeführt. Klicken Sie in der experimentellen Instanz von Visual Studio öffnen Sie, oder erstellen Sie eine Datei mit der Erweiterung der DSL.

3.  **Stellen Sie sicher, dass das Tool in der Toolbox angezeigt wird.**

4.  Ziehen Sie das Werkzeug in das Modelldiagramm. Eine Form wird erstellt.

     Überprüfen Sie, ob der Name des Elements angezeigt und automatisch auf einen Standardwert festgelegt wird.

5.  Mit der rechten Maustaste in des Headers der neuen Form, und klicken Sie dann auf Hinzufügen *Your Listenelement.* Im Beispiel lautet der Befehl "Song hinzufügen".

     Überprüfen Sie, ob ein Element mit einem neuen Namen in der Liste erscheint.

6.  Klicken Sie auf eines der Listenelemente, und betrachten Sie das Eigenschaftenfenster. Es sollten die Eigenschaften der Listenelemente angezeigt werden.

7.  Öffnen Sie den Sprach-Explorer. Überprüfen Sie, ob die Containerknoten mit darin enthaltenen Listenelementknoten angezeigt werden.

 ![Generierter Explorer für DSL](../modeling/media/music_explorer.png)

 Nach dem ersten Test einer Depot-Form möchten Sie unter Umständen einige Eigenschaften anpassen und erweiterte Features hinzufügen. Weitere Informationen finden Sie unter [anpassen und Erweitern einer domänenspezifischen Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md).

### <a name="displaying-a-reference-link-in-a-compartment"></a>Anzeigen eines Verweislinks in einem Depot
 Normalerweise ist ein in einem Depot angezeigtes Element ein untergeordnetes Element des Elements, das durch die Depot-Form dargestellt wird. Aber manchmal soll ein Element angezeigt werden, das durch eine Verweisbeziehung damit verbunden ist.

 Wir könnten z. B. ein zweites Depot zu AlbumShape hinzufügen, in dem eine Liste der mit dem Album verbundenen Interpreten angezeigt wird.

 In diesem Fall sollte das Depot statt des Elements, auf das verwiesen wird, den Link anzeigen. Denn wenn der Benutzer das Element im Depot auswählt und ENTF drückt, soll der Link gelöscht werden und nicht das Element, auf das verwiesen wird.

 Dennoch kann der Name des Elements, auf das verwiesen wird, im Depot erscheinen.

 Im folgenden Verfahren wird vorausgesetzt, dass Sie bereits die Domänenklasse, die Verweisbeziehung, die Depot-Form und die Diagrammelementzuordnung erstellt haben, wie weiter oben in diesem Abschnitt beschrieben.

##### <a name="to-display-a-reference-link-in-a-compartment"></a>So zeigen Sie einen Verweislink in einem Depot an

1.  **Fügen Sie einem Depot mit der Form "Depot"**. DSL-Definitionsdiagramm Maustaste Depot-Form-Klasse, zeigen Sie auf **hinzufügen**, und klicken Sie dann auf **Depot**.

2.  Legen Sie **angezeigte Elemente Sammlungspfad** auf den Link, anstatt seine Target-Element zu navigieren. Klicken Sie auf das Dropdownmenü, und verwenden Sie die Strukturansicht, um die Verweisbeziehung statt ihres Ziels auszuwählen. Im Beispiel wird die Beziehung **ArtistAppearedOnAlbums**.

3.  Legen Sie **Pfad zur Anzeigeeigenschaft** über den Link zu den Target-Element zu navigieren. In diesem Beispiel ist dies **Interpreten**.

4.  Legen Sie **Anzeigeeigenschaft** der entsprechenden Eigenschaft des Target-Element, z. B. **Namen**.

5.  **Transformieren aller Vorlagen**, erstellen und Ausführen der DSL und ein Testmodell zu öffnen.

6.  Erstellen Sie in dem Modelldiagramm die entsprechenden Formklassen, legen Sie ihre Namen fest, und erstellen Sie einen Link zwischen ihnen. In der Depot-Form sollten die Namen der verbundenen Elemente angezeigt werden.

7.  Wählen Sie entweder den Link oder das Element in der Depot-Form aus. Sowohl der Link als auch das Element sollte angezeigt werden.

##  <a name="ports"></a> Definieren von Ports für die Begrenzung einer anderen Form
 Ein Anschluss ist eine Form, die sich am Rand einer anderen Form befindet.

 Anschlüsse können auch verwendet werden, um einen festen Verbindungspunkt an einer anderen Form bereitzustellen, zu dem der Benutzer Konnektoren zeichnen kann. In diesem Fall können Sie die Anschluss-Form transparent machen.

 Ein Beispiel finden Sie die Ports verwendet die **Komponentendiagramm** Vorlage bei der Erstellung einer neuen DSL-Projektmappe. Dieses Beispiel zeigt die wesentlichen Punkte, die Sie bei der Definition von Anschlüssen berücksichtigen können:

-   Es gibt eine Domänenklasse, die den Container der Anschlüsse darstellt: `Component`.

-   Es gibt eine Domänenklasse, die Anschlüsse darstellt. Im Beispiel ist dies `ComponentPort`.

-   Es gibt eine einbettende Beziehung von der Container-Domänenklasse zur Anschluss-Domänenklasse. Weitere Informationen finden Sie unter [Domänenklassen definieren](#classes).

-   Wenn verschiedene Anschlusstypen in demselben Container gemischt werden sollen, können Sie Unterklassen der Anschluss-Domänenklasse erstellen. In dem Beispiel erben `InPort` und `OutPort` von `ComponentPort`.

-   Die Container-Domänenklasse kann jeder beliebigen Form zugeordnet werden. Im Beispiel ist dies `ComponentShape`. Weitere Informationen finden Sie unter [Formen definieren](#shapes).

-   Die Anschluss-Domänenklassen werden Anschluss-Formen zugeordnet. Sie können entweder die abgeleiteten Klassen verschiedenen Anschluss-Formklassen zuordnen oder die Basisklasse einer Anschluss-Formklasse zuordnen.

 Formen vom Typ Port in anderer Hinsicht Verhalten sich wie beschrieben in [Formen definieren](#shapes).

 Weitere Informationen finden Sie unter [Eigenschaften von Port Formen](../modeling/properties-of-port-shapes.md).

##  <a name="swimlanes"></a> Eine DSL definieren, das die Verantwortlichkeitsbereiche hat
 Verantwortlichkeitsbereiche sind vertikale oder horizontale Bereiche eines Diagramms. Jeder Verantwortlichkeitsbereich entspricht einem Modellelement. Ihre DSL-Definition muss eine Domänenklasse für die Verantwortlichkeitsbereich-Elemente enthalten.

 Am besten lässt sich eine DSL mit Verantwortlichkeitsbereichen erstellen, indem Sie eine neue DSL-Projektmappe erstellen und die Projektmappenvorlage "Aufgabenfluss" auswählen. In der DSL-Definition ist die Actor-Klasse die Domänenklasse, die dem Verantwortlichkeitsbereich zugeordnet wird. Benennen Sie diese und die anderen Klassen nach den Anforderungen Ihres Projekts um.

 Um eine Klasse hinzuzufügen, die als Form innerhalb eines Verantwortlichkeitsbereichs angezeigt wird, erstellen Sie eine einbettende Beziehung zwischen der Klasse des Verantwortlichkeitsbereichs und Ihrer neuen Klasse. Benutzer können Elemente von einem Verantwortlichkeitsbereich in einen anderen ziehen, aber jedes Element befindet sich immer innerhalb eines bestimmten Verantwortlichkeitsbereichs. In der Projektmappenvorlage "Aufgabenfluss" ist "FlowElement" ein untergeordnetes Element der Verantwortlichkeitsbereich-Klasse.

 Um eine Klasse hinzuzufügen, die als Form unabhängig von Verantwortlichkeitsbereichen angezeigt wird, erstellen Sie eine einbettende Beziehung zwischen der Stammklasse und Ihrer neuen Klasse. Benutzer können diese Formen beliebig im Diagramm platzieren, auch über die Grenzen von Verantwortlichkeitsbereichen hinweg und außerhalb von Verantwortlichkeitsbereichen. In der Projektmappenvorlage "Aufgabenfluss" ist "Comment" ein untergeordnetes Element der Stammklasse.

 Weitere Informationen finden Sie unter [Eigenschaften von Verantwortlichkeitsbereichen](../modeling/properties-of-swimlanes.md).

##  <a name="addTypes"></a> Hinzufügen von Eigenschaftentypen

### <a name="domain-enumerations-and-literals"></a>Domänenenumerationen und Literale
 Eine Domänenenumeration ist ein Typ mit mehreren Literalwerten.

 Zum Hinzufügen einer Domäne Enumeration Maustaste den Stamm des Modells in der **Explorer für DSL** , und klicken Sie dann auf **Hinzufügen der neuen Domäne-Enumeration**. Das Element erscheint der **Explorer für DSL** unter der **Domänentypen** Knoten. Das Element erscheint nicht im Diagramm.

 Um der Domäne Enumeration Enumeration Literale hinzuzufügen, Maustaste die Aufzählung der Domäne in der **Explorer für DSL** , und klicken Sie dann auf **fügen neue Enumeration Literale**.

 Eine Eigenschaft, die einen Enumerationstyp besitzt, kann standardmäßig jeweils nur auf einen Wert der Enumeration festgelegt werden. Legen Sie gegebenenfalls Benutzer und -Programmierer in der Lage, eine beliebige Kombination von Werten - festgelegt sein als "Bitfeld" - die **IsFlags** Eigenschaft der Enumeration.

### <a name="external-types"></a>Externe Typen
 Beim Festlegen des Typs, der eine Eigenschaft "Domain", wenn Sie nicht den Typ finden Sie möchten, in der **Typ** Dropdown Liste können Sie einen externen Typ hinzufügen. Sie könnten z. B. Hinzufügen der **System.Drawing.Color** Typ in der Liste.

 Um einen Typ hinzuzufügen, mit der rechten Maustaste in den Stamm des Modells im DSL-Explorer, und klicken Sie dann auf **Hinzufügen neuer externer Typ**. Legen Sie im Fenster Eigenschaften den Namen zu **Farbe** und der Namespace, der **"System.Drawing"**. Dieser Typ wird jetzt im DSL-Explorer unter **Domänentypen**. Sie können ihn immer auswählen, wenn Sie den Typ einer Domäneneigenschaft festlegen.

##  <a name="custom"></a> Anpassen der DSL
 Mit den hier beschriebenen Verfahren können Sie schnell eine DSL mit einer Diagrammdarstellung, einem lesbaren XML-Format und den grundlegenden Tools erstellen, mit denen Code und andere Artefakte generiert werden.

 Die DSL-Definition kann auf zwei Arten erweitert werden:

1.  Optimieren Sie die DSL, indem Sie weitere Features in der DSL-Definition verwenden. Sie können beispielsweise ein einzelnes Konnektorwerkzeug erstellen, das verschiedene Typen von Konnektoren generieren kann, und Sie können die Regeln steuern, nach denen beim Löschen eines Elements auch verwandte Elemente gelöscht werden. Diese Verfahren bestehen meist im Festlegen von Werten in der DSL-Definition. Manche erfordern auch einige Zeilen Programmcode.

     Weitere Informationen finden Sie unter [anpassen und Erweitern einer domänenspezifischen Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md).

2.  Erweitern Sie Ihre Modellierungstools mit Programmcode, um kompliziertere Effekte zu erzielen. So können Sie z. B. Menübefehle erstellen, die das Modell ändern, und Sie können Tools erstellen, in denen zwei oder mehr DSLs integriert sind. VMSDK wurde speziell dafür entwickelt, die Integration Ihrer Erweiterungen in den Code zu vereinfachen, der aus der DSL-Definition generiert wird.  Weitere Informationen finden Sie unter [Schreiben von Code zum Anpassen einer domänenspezifischen Sprache](../modeling/writing-code-to-customise-a-domain-specific-language.md).

### <a name="changing-the-dsl-definition"></a>Ändern der DSL-Definition
 Wenn Sie ein Element in einer DSL-Definition erstellen, werden viele Standardwerte automatisch festgelegt. Diese Werte können Sie anschließend ändern. Dies vereinfacht die Entwicklung einer DSL und ermöglicht gleichzeitig wirkungsvolle Anpassungen.

 Wenn Sie beispielsweise eine Form einem Element zuordnen, wird der Pfad des übergeordneten Elements der Zuordnung automatisch entsprechend der einbettenden Beziehung der Domänenklasse festgelegt. Wenn Sie die einbettende Beziehung später ändern, wird der Pfad des übergeordneten Elements nicht automatisch geändert.

 Daher sollten Sie damit rechnen, dass nach einer Änderung von Beziehungen in der DSL-Definition häufig Fehler gemeldet werden, wenn Sie die Definition speichern oder "Alle Vorlagen transformieren" verwenden. Die meisten dieser Fehler sind leicht zu beheben. Doppelklicken Sie auf den Fehlerbericht, um den Ort des Fehlers zu ermitteln.

 Siehe auch [Vorgehensweise: Ändern Sie den Namespace einer domänenspezifischen Sprache](../modeling/how-to-change-the-namespace-of-a-domain-specific-language.md).

##  <a name="trouble"></a> Problembehandlung bei
 In der folgenden Tabelle sind einige der häufigsten Probleme, die beim Entwurf einer DSL auftreten, zusammen mit ihrer Lösung aufgeführt. Weitere Hinweise finden Sie auf der [Visualisierung Tools Extensibililty Forum](http://go.microsoft.com/fwlink/?LinkId=186074).

|Problem|Vorschlag|
|-------------|----------------|
|Die Änderungen, die ich an der DSL-Definition vorgenommen habe, wirken sich nicht aus.|Klicken Sie auf **alle Vorlagen transformieren** auf der Symbolleiste über den Projektmappen-Explorer, und klicken Sie dann neu erstellen der Projektmappe.|
|Formen zeigen statt des Eigenschaftenwerts den Namen eines Decorator-Elements an.|Richten Sie die Decorator-Zuordnung ein. Klicken Sie im DSL-Definitionsdiagramm auf die Diagrammelementzuordnung (die graue Linie zwischen der Domänenklasse und der Formklasse).<br /><br /> Öffnen der **DSL-Detailfenster** Fenster. Wenn Sie es, auf das Menü "Ansicht" angezeigt werden, zeigen Sie auf **Weitere Fenster**, und klicken Sie dann auf **DSL-Detailfenster**.<br /><br /> Klicken Sie auf die **Decorator-Zuordnungen** Registerkarte. Wählen Sie den Namen des Decorator-Elements aus. Vergewissern Sie sich, dass das Kontrollkästchen daneben aktiviert ist. Klicken Sie unter **Anzeigeeigenschaft**, wählen Sie den Namen der Eigenschaft "Domain" ein.<br /><br /> Weitere Informationen finden Sie unter [Formen im Diagramm](#shapes).|
|Ich kann in DSL-Explorer keine Auflistung hinzufügen. Zum Beispiel gibt es beim Rechtsklick auf "Werkzeuge" keinen "Tool hinzufügen"-Befehl im Menü.<br /><br /> Ich kann im Explorer für meine DSL kein Element zu einer Liste hinzufügen.|Klicken Sie mit der rechten Maustaste auf das Element über dem Knoten, den Sie testen. Wenn Sie etwas zu einer Liste hinzufügen möchten, befindet sich der Befehl zum Hinzufügen nicht im Listenknoten, sondern in seinem Besitzer.|
|Ich habe eine Domänenklasse erstellt, aber ich kann im Explorer der Sprache keine Instanzen erstellen.|Jede Domänenklasse mit Ausnahme des Stamms muss Ziel einer einbettenden Beziehung sein.|
|Im Explorer für meine DSL werden die Elemente nur mit ihren Typennamen angezeigt.|Wählen Sie in der DSL-Definition, eine Eigenschaft "Domain" der Klasse, und legen Sie im Eigenschaften-Fenster **Elementname ist** auf "true".|
|Meine DSL wird immer im XML-Editor geöffnet.|Das kann an einem Fehler beim Lesen der Datei liegen. Nachdem Sie den Fehler behoben haben, müssen Sie den Editor explizit als Ihren DSL-Designer zurücksetzen.<br /><br /> Mit der rechten Maustaste des Projektelements, klicken Sie auf **Öffnen mit** , und wählen Sie * YourLanguage ***Designer (Standard)**.|
|Der Werkzeugkasten meiner DSL wird nicht angezeigt, nachdem ich die Assemblynamen geändert habe.|Überprüfen und aktualisieren Sie **DslPackage\GeneratedCode\Package.tt** Weitere Informationen finden Sie unter [Vorgehensweise: Ändern Sie den Namespace einer domänenspezifischen Sprache](../modeling/how-to-change-the-namespace-of-a-domain-specific-language.md).|
|Der Werkzeugkasten meiner DSL wird nicht angezeigt, obwohl ich die Assemblynamen nicht geändert habe.<br /><br /> Oder es wird in einem Meldungsfeld gemeldet, dass eine Erweiterung nicht geladen werden konnte.|Setzen Sie die experimentelle Instanz zurück, und erstellen Sie die Projektmappe neu.<br /><br /> 1.  Starten Sie Windows im Menü unter **Programme**, erweitern Sie [!INCLUDE[vssdk_current_long](../misc/includes/vssdk_current_long_md.md)], klicken Sie dann **Tools**, und klicken Sie dann auf **Zurücksetzen der Microsoft Visual Studio experimentellen Instanz**.<br />2.  Visual Studio**erstellen** Menü klicken Sie auf **Projektmappe neu erstellen**.|

## <a name="see-also"></a>Siehe auch

- [Erste Schritte mit domänenspezifischen Sprachen](../modeling/getting-started-with-domain-specific-languages.md)
- [Erstellen einer Windows Forms-basierten domänenspezifischen Sprache](../modeling/creating-a-windows-forms-based-domain-specific-language.md)
- [Erstellen einer WPF-basierten domänenspezifischen Sprache](../modeling/creating-a-wpf-based-domain-specific-language.md)