---
title: Erste Schritte mit domänenspezifischen Sprachen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 024392a2-2c04-404f-a27b-7273553c3b60
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: fc0cf72be3fccbfdafd5ab3a7570ea6aac900f11
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49251978"
---
# <a name="getting-started-with-domain-specific-languages"></a>Erste Schritte mit domänenspezifischen Sprachen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Thema wird erläutert, die grundlegenden Konzepte in definieren und verwenden eine domänenspezifische Sprache (DSL) mit der Modellierungs-SDK für Visual Studio erstellt wird.  
  
 Wenn Sie noch nicht mit DSLs sind, es wird empfohlen, dass Sie über arbeiten die **DSL-Tools Lab**, finden Sie auf dieser Website: [Visualisierungs- und Modellierungs-SDK](http://go.microsoft.com/fwlink/?LinkID=186128)  
  
## <a name="what-can-you-do-with-a-domain-specific-language"></a>Was können Sie mit einer domänenspezifischen Sprache?  
 Eine domänenspezifische Sprache ist eine Notation, normalerweise eine grafische Darstellung, die für einen bestimmten Zweck verwendet werden soll. Im Gegensatz dazu sind Sprachen wie z. B. UML allgemeinen. In einer DSL können Sie definieren die Typen von Modellelement und ihre Beziehungen und wie sie auf dem Bildschirm dargestellt werden.  
  
 Wenn Sie eine DSL entworfen haben, können Sie ihn als Teil eines Pakets für Visual Studio Integration Extension (VSIX) verteilen. Benutzer mit der DSL im arbeiten [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]:  
  
 ![Stammstrukturdiagramm, Toolbox und Explorer](../modeling/media/familyt-instance.png "FamilyT_Instance")  
  
 Die Notation ist nur ein Teil einer DSL. Zusammen mit der Bezeichnung enthält Ihre VSIX-Paket für Tools, mit denen Benutzer anwenden können, um Ihnen zu helfen, bearbeiten und Generieren von Material aus ihren Modellen.  
  
 Eine der Prinzipal Anwendungen von DSLs ist Programmcode, Konfigurationsdateien und andere Artefakte generieren. Insbesondere in großen Projekten und Produktlinien, wobei mehrere Varianten eines Produkts erstellt wird, kann viele der der Variablen Aspekte von DSLs generieren eine erheblich größere Zuverlässigkeit und eine sehr schnelle Reaktion auf anforderungsänderungen bereitstellen.  
  
 Der Rest dieser Übersicht ist eine exemplarische Vorgehensweise, die zum Erstellen und verwenden eine domänenspezifische Sprache, in die grundlegenden Vorgänge eingeführt werden [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Zur Definition einer DSL müssen folgende Komponenten installiert sein:  
  
|||  
|-|-|  
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185579](http://go.microsoft.com/fwlink/?LinkId=185579)|  
|[!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185580](http://go.microsoft.com/fwlink/?LinkId=185580)|  
|Modellierungs-SDK für Visual Studio|[Herunterladen von MSDK](http://www.microsoft.com/download/details.aspx?id=40754)|  
  
## <a name="creating-a-dsl-solution"></a>Erstellen eine DSL-Projektmappe  
 Um eine neue domänenspezifische Sprache zu erstellen, erstellen Sie ein neues [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Lösung mithilfe der Projektvorlage einer domänenspezifischen Sprache.  
  
#### <a name="to-create-a-dsl-solution"></a>So erstellen Sie eine DSL-Projektmappe  
  
1.  Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.  
  
2.  Klicken Sie unter **Projekttypen**, erweitern Sie die **andere Projekttypen** Knoten, und klicken Sie auf **Erweiterbarkeit**.  
  
3.  Klicken Sie auf **domänenspezifischen Sprachdesigner**.  
  
     ![DSL-Dialogfeld "erstellen"](../modeling/media/create-dsldialog.png "Create_DSLDialog")  
  
4.  In der **Namen** geben **FamilyTree**. Klicken Sie auf **OK**.  
  
     Die **Domain-Specific Language Assistenten** wird geöffnet und zeigt eine Liste der Vorlagen-DSL-Projektmappen.  
  
     Klicken Sie auf die einzelnen Vorlagen, um eine Beschreibung anzuzeigen,  
  
     Die Vorlagen eignen sich Startpunkte. Jedes davon bietet es sich um eine vollständig funktionsfähige DSL, die Sie bearbeiten können, um Ihren Anforderungen entsprechend. Normalerweise würden Sie durch auswählen die Vorlage am nächsten liegt, was Sie erstellen möchten.  
  
5.  Wählen Sie in dieser exemplarischen Vorgehensweise die **minimale Sprache** Vorlage.  
  
6.  Geben Sie auf der entsprechenden Seite des Assistenten eine Dateinamenerweiterung für die DSL ein. Diese Erweiterung wird für Dateien mit Instanzen Ihrer DSL verwendet.  
  
    -   Wählen Sie eine Erweiterung, die nicht in der bezieht sich auf jede Anwendung auf Ihrem Computer oder auf einem Computer, in dem Sie die DSL installieren möchten. Z. B. **Docx** und **Htm** wäre akzeptablen Dateinamenerweiterungen.  
  
    -   Der Assistent warnt Sie, wenn die eingegebene Erweiterung bereits als DSL verwendet wird. Verwenden Sie nach Möglichkeit eine andere Dateinamenerweiterung. Sie können die experimentelle Instanz des Visual Studio SDK auch zurücksetzen, um alte experimentelle Designer zu löschen. Klicken Sie auf **starten**, klicken Sie auf **Programme**, **Microsoft Visual Studio 2010 SDK**, **Tools**, und klicken Sie dann **Microsoft zurücksetzen Instanz von Visual Studio 2010 experimentell**.  
  
7.  Überprüfen Sie die anderen Seiten, und klicken Sie dann auf **Fertig stellen**.  
  
     Eine Projektmappe wird generiert, die zwei Projekte enthält. Sie werden Dsl "und" DslPackage bezeichnet. Eine Diagrammdatei wird geöffnet, auf benannte "DslDefinition.DSL" aus.  
  
    > [!NOTE]
    >  Großteil des Codes, die Sie in den Ordnern in beiden Projekten sehen können, wird aus "DslDefinition.DSL" generiert. Aus diesem Grund sind die meisten Änderungen an Ihrer DSL in dieser Datei hergestellt.  
  
 Die Benutzeroberfläche gleicht nun der folgenden Abbildung.  
  
 ![DSL-Designers](../modeling/media/dsl-designer.png "Dsl_designer")  
  
 Diese Projektmappe definiert eine domänenspezifische Sprache. Weitere Informationen finden Sie unter [Überblick über die Benutzeroberfläche für domänenspezifische Sprachtools](../modeling/overview-of-the-domain-specific-language-tools-user-interface.md).  
  
## <a name="the-important-parts-of-the-dsl-solution"></a>Die wichtigen Teile der DSL-Projektmappe  
 Beachten Sie die folgenden Aspekte der neuen Projektmappe ein.  
  
-   **Dsl\DslDefinition.DSL** Dies ist die Datei, Sie sehen, wenn Sie eine DSL-Projektmappe erstellen. Fast der gesamte Code in der Lösung wird aus dieser Datei generiert, und die meisten der Änderungen, die Sie an einer DSL-Definition vorgenommen werden hier vorgenommen werden. Weitere Informationen finden Sie unter Verwendung der [arbeiten mit dem DSL-Definitionsdiagramm](../modeling/working-with-the-dsl-definition-diagram.md).  
  
-   **DSL-Projekt** dieses Projekt enthält Code, die einer domänenspezifischen Sprache definiert.  
  
-   **DslPackage-Projekt** dieses Projekt enthält Code, der Instanzen der DSL geöffnet und bearbeitet werden kann [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
##  <a name="Debugging"></a> Die DSL ausführen  
 Sie können die DSL-Projektmappe ausführen, sobald Sie es erstellt haben. Später können Sie die DSL-Definition nach und nach Ausführen der Projektmappe nach jeder Änderung erneut ändern.  
  
#### <a name="to-experiment-with-the-dsl"></a>Zum Experimentieren mit der DSL  
  
1.  Klicken Sie auf **alle Vorlagen transformieren** auf der Symbolleiste des Projektmappen-Explorer. Dies wird erneut die meisten der Quellcode von "DslDefinition.DSL" generiert.  
  
    > [!NOTE]
    >  Wenn Sie "DslDefinition.DSL" ändern, klicken Sie auf **alle Vorlagen transformieren** , bevor Sie die Projektmappe neu erstellen. Dieser Schritt kann automatisiert werden. Weitere Informationen finden Sie unter [wie alle Vorlagen transformieren automatisieren](http://msdn.microsoft.com/en-us/b63cfe20-fe5e-47cc-9506-59b29bca768a).  
  
2.  Drücken Sie F5, oder auf die **Debuggen** Menü klicken Sie auf **Debuggen starten**.  
  
     Die DSL erstellt und ist in der experimentellen Instanz von installiert [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
     Eine experimentelle Instanz von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] wird gestartet. Die experimentelle Instanz nimmt seine Einstellungen aus der Registrierung, eine separate Unterstruktur, in denen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Erweiterungen zu Debugzwecken registriert sind. Normale Instanzen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] haben keinen Zugriff auf Erweiterungen, die es registriert.  
  
3.  In der experimentellen Instanz von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], öffnen Sie die Modelldatei mit dem Namen **Test** aus **Projektmappen-Explorer**.  
  
     \- oder –  
  
     Mit der rechten Maustaste in den Debugging-Projekt, zeigen Sie auf **hinzufügen**, und klicken Sie dann auf **Element**. In der **Element hinzufügen** wählen Sie im Dialogfeld Geben Sie die Datei Ihrer DSL.  
  
     Die Modelldatei wird als ein leeres Diagramm geöffnet.  
  
     Die Toolbox wird geöffnet und zeigt Tools, die das Diagramm entspricht.  
  
4.  Verwenden Sie die Tools, um Formen und Konnektoren im Diagramm zu erstellen.  
  
    1.  Ziehen Sie aus dem Beispiel-Shape-Tool auf das Diagramm, um Formen zu erstellen.  
  
    2.  Um zwei Formen verbinden, klicken Sie auf die Beispiel-Connector-Tool, klicken Sie auf der ersten Form, und klicken Sie dann auf die zweite Form.  
  
5.  Klicken Sie auf die Bezeichnungen der Formen ändern.  
  
 Gleicht die experimentelle [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] wird im folgende Beispiel ähneln:  
  
 ![](../modeling/media/dsl-min.png "DSL_min")  
  
### <a name="the-content-of-a-model"></a>Der Inhalt eines Modells  
 Wird aufgerufen, der Inhalt der Datei, die eine Instanz einer DSL ist eine *Modell*. Das Modell enthält *Modell ** Elemente* und *Links* zwischen den Elementen. Die DSL-Definition gibt an, welche Arten von Modellelementen und Links können im Modell vorhanden sind. Z. B. in einer DSL, die aus der Vorlage für die minimale Sprache erstellt, ist es eine Art von Modellelement und eine Art von Link.  
  
 Die DSL-Definition kann angeben, wie das Modell in einem Diagramm angezeigt wird. Sie können aus verschiedensten Arten von Formen und Konnektoren auswählen. Sie können angeben, dass einige Formen innerhalb anderer Formen angezeigt werden.  
  
 Sie können ein Modell anzeigen, wie eine Struktur in der **Explorer** anzeigen, während Sie ein Modell bearbeitet werden. Das Diagramm, Hinzufügen von Formen die Modellelemente werden auch im Explorer angezeigt. Im Explorer kann verwendet werden, auch wenn es kein Diagramm.  
  
 Wenn in der Debuginstanz von im Explorer nicht angezeigt wird [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]auf die **Ansicht** zeigen Sie im Menü auf **andere Windows**, und klicken Sie dann auf  *\<Ihre Sprache >* **Explorer**.  
  
### <a name="the-api-of-your-dsl"></a>Die API Ihrer DSL  
 Die DSL generiert eine API, die Ihnen die Möglichkeit zum Lesen und Aktualisieren von Modellen, die Instanzen der DSL. Eine Anwendung der API ist zum Generieren von Textdateien aus einem Modell. Weitere Informationen finden Sie unter [Design-Time Code Generation mithilfe von T4-Textvorlagen](../modeling/design-time-code-generation-by-using-t4-text-templates.md).  
  
 Öffnen Sie die Vorlagendateien mit der Erweiterung "tt", in der Projektmappe debuggen. Diese Beispiele veranschaulichen, wie Sie Text aus Modellen generiert, und ermöglichen es Ihnen, die die API Ihrer DSL zu testen. Eines der Beispiele ist in geschrieben [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], die andere im [!INCLUDE[csprcs](../includes/csprcs-md.md)].  
  
 Unter jeder Vorlage ist die Datei die Datei, die es generiert. Erweitern Sie die Vorlagendatei im Projektmappen-Explorer, und öffnen Sie die generierte Datei.  
  
 Die Vorlagendatei enthält ein kurzes Stück Code, der alle Elemente im Modell enthält.  
  
 Die generierte Datei enthält das Ergebnis an.  
  
 Wenn Sie eine Datei des Modells ändern, sehen Sie entsprechende Änderungen in der generierten Dateien nach dem Sie die Dateien erneut generieren.  
  
##### <a name="to-regenerate-text-files-after-you-change-the-model-file"></a>Text-Dateien neu generieren, nach dem Ändern der Modelldatei  
  
1.  In der experimentellen Instanz von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], speichern Sie das Modell.  
  
2.  Stellen Sie sicher, dass die File-Name-Parameter in den einzelnen TT-Dateien auf die Modelldatei bezieht, die Sie für Experimente verwenden. Speichern Sie die TT-Datei.  
  
3.  Klicken Sie auf **alle Vorlagen transformieren** auf der Symbolleiste des **Projektmappen-Explorer**.  
  
     \- oder –  
  
     Mit der rechten Maustaste in der Vorlagen, die Sie verwenden möchten, generieren, und klicken Sie dann auf **benutzerdefiniertes Tool ausführen**.  
  
 Sie können eine beliebige Anzahl von Textvorlagendateien zu einem Projekt hinzufügen. Jede Vorlage generiert eine Ergebnisdatei an.  
  
> [!NOTE]
>  Wenn Sie die DSL-Definition ändern, funktioniert der Textvorlagencode Beispiel nicht, sofern die Aktualisierung.  
  
 Weitere Informationen finden Sie unter [Generieren von Code aus einer domänenspezifischen Sprache](../modeling/generating-code-from-a-domain-specific-language.md) und [Schreiben von Code zum Anpassen einer domänenspezifischen Sprache](../modeling/writing-code-to-customise-a-domain-specific-language.md).  
  
## <a name="customizing-the-dsl"></a>Anpassen der DSL  
 Wenn Sie die DSL-Definition ändern möchten, schließen Sie die experimentelle Instanz, und Aktualisieren der Definition im Hauptfenster [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Instanz.  
  
> [!NOTE]
>  Nachdem Sie die DSL-Definition geändert haben, verlieren Sie möglicherweise Informationen in den Test-Modellen, die Sie erstellt haben, die mit früheren Versionen.  Die debugprojektmappe enthält beispielsweise eine Datei mit dem Namen Beispiel enthält einige Formen und Konnektoren. Nach dem Starten Ihrer DSL-Definition zu entwickeln, werden sie nicht angezeigt, und sie gehen verloren, wenn Sie die Datei speichern.  
  
 Sie können eine Vielzahl von Erweiterungen Ihrer DSL vornehmen. In den folgenden Beispielen erhalten Sie einen Eindruck von den Möglichkeiten.  
  
 Klicken Sie nach jeder Änderung, speichern Sie die DSL-Definition auf **alle Vorlagen transformieren** in **Projektmappen-Explorer**, und drücken Sie dann die **F5** zum Experimentieren mit der geänderten DSL.  
  
### <a name="rename-the-types-and-tools"></a>Benennen Sie die Typen und -Tools  
 Benennen Sie die vorhandenen Domänenklassen und Beziehungen. Beispielsweise konnte beginnend mit einer Dsl-Definition aus der Vorlage für die minimale Sprache erstellt, Sie die folgenden Vorgänge umbenennen, um die DSL Familie Strukturen darstellen machen ausgeführt werden.  
  
##### <a name="to-rename-domain-classes-relationships-and-tools"></a>So benennen Sie um Domänenklassen, Beziehungen und tools  
  
1.  Benennen Sie im Diagramm DslDefinition **ExampleModel** zu **FamilyTreeModel**, **ExampleElement** zu **Person**,  **Ziele** zu **Eltern**, und **Quellen** zu **untergeordneten**. Sie können jede Bezeichnung aus, um dies zu ändern klicken.  
  
     ![DSL-Definitionsdiagramm &#45; stammstrukturmodell](../modeling/media/familyt-person.png "FamilyT_Person")  
  
2.  Benennen Sie die Element- und -Connector-Tools.  
  
    1.  Öffnen Sie das DSL-Explorer-Fenster, indem Sie auf der Registerkarte "im Projektmappen-Explorer. Wenn Sie es nicht angezeigt der **Ansicht** zeigen Sie im Menü auf **Other Windows** , und klicken Sie dann auf **DSL-Explorer**. DSL-Explorer ist sichtbar, nur, wenn die DSL-Definitionsdiagramm das aktive Fenster ist.  
  
    2.  Öffnen Sie das Fenster "Eigenschaften", und positionieren Sie es, damit Sie die DSL-Explorer und Eigenschaften zur gleichen Zeit finden.  
  
    3.  Erweitern Sie im DSL-Explorer **Editor**, **Toolboxregisterkarten**,  *\<Ihrer DSL >*, und klicken Sie dann **Tools**.  
  
    4.  Klicken Sie auf **ExampleElement**. Dies ist das Toolboxelement, das zum Erstellen von Elementen verwendet wird.  
  
    5.  Ändern Sie im Fenster Eigenschaften die **Namen** Eigenschaft **Person**.  
  
         Beachten Sie, dass die **Beschriftung** Eigenschaft ändert sich ebenfalls.  
  
    6.  Ändern Sie den Namen der in die gleiche Weise die **ExampleConnector** -tool in **ParentLink**. Ändern der **Beschriftung** Eigenschaft, damit es nicht um eine Kopie des Name-Eigenschaft ist. Geben Sie z. B. **übergeordneter Link**.  
  
3.  Erstellen Sie die DSL neu.  
  
    1.  Speichern Sie die DSL-Definitionsdatei.  
  
    2.  Klicken Sie auf **alle Vorlagen transformieren** auf der Symbolleiste des Projektmappen-Explorer  
  
    3.  Drücken Sie F5. Warten Sie, bis der experimentellen Instanz von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] angezeigt wird.  
  
4.  In der Projektmappe debuggen, in der experimentellen Instanz von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], öffnen Sie eine Testdatei für das Modell. Ziehen Sie Elemente auf sie aus der Toolbox. Beachten Sie, dass die Tool-Beschriftungen und die Typnamen im DSL-Explorer geändert haben.  
  
5.  Speichern Sie die Modelldatei.  
  
6.  Öffnen Sie eine TT-Datei und Ersetzen von Vorkommen der alten Namen und die Eigenschaften mit den neuen Namen.  
  
7.  Stellen Sie sicher, dass der Dateiname, der in der TT-Datei angegeben ist Ihr Testmodell angibt.  
  
8.  Speichern Sie die TT-Datei. Öffnen Sie die generierte Datei, um das Ergebnis der Ausführung des Codes in der TT-Datei anzuzeigen. Stellen Sie sicher, dass er korrekt ist.  
  
### <a name="add-domain-properties-to-classes"></a>Hinzufügen von Domäneneigenschaften zu Klassen  
 Fügen Sie Eigenschaften auf eine Domänenklasse, z. B. zur Darstellung der Jahre Geburtsdatum und Tod einer Person hinzu.  
  
 Um die neuen Eigenschaften im Diagramm sichtbar zu machen, müssen Sie hinzufügen, *Decorator-Elemente* auf die Form, in dem das Modellelement angezeigt. Sie müssen auch die Eigenschaften der Decorator-Elementen zuordnen.  
  
##### <a name="to-add-properties-and-display-them"></a>Hinzufügen von Eigenschaften und anzeigen  
  
1.  Fügen Sie die Eigenschaften an.  
  
    1.  In der DSL-Definitionsdiagramm mit der Maustaste der **Person** Domänenklasse, zeigen Sie auf **hinzufügen**, und klicken Sie dann auf **Domäneneigenschaft**.  
  
    2.  Geben Sie eine Liste der neuen Eigenschaftennamen, z. B. **Geburtsdatum** und **Tod**. Drücken Sie **EINGABETASTE** nach jeder Eingabe.  
  
2.  Hinzufügen von Decorator-Elemente, die die Eigenschaften in der Form angezeigt werden.  
  
    1.  Führen Sie die graue Linie, die von der Person-Domänenklasse der anderen Seite des Diagramms erweitert. Dies ist einer diagrammelementzuordnung. Die Domänenklasse verknüpft mit einer formklasse.  
  
    2.  Mit der rechten Maustaste in dieser formklasse, zeigen Sie auf **hinzufügen**, und klicken Sie dann auf **Text-Decorator**.  
  
    3.  Fügen Sie zwei Decorator-Elemente mit Namen wie z. B. **BirthDecorator** und **DeathDecorator**.  
  
    4.  Wählen Sie jedes neue Decorator-Element, und legen Sie im Fenster Eigenschaften die **Position** Feld. Dies bestimmt, in der Eigenschaftswert für die Domäne in der Form angezeigt werden soll. Legen Sie z. B. **InnerBottomLeft** und **InnerBottomRight**.  
  
         ![Depot-formdefinition](../modeling/media/familyt-compartment.png "FamilyT_Compartment")  
  
3.  Ordnen Sie die Eigenschaften der Decorator-Elemente.  
  
    1.  Öffnen Sie das Fenster "DSL-Details" ein. Es ist in der Regel auf einer Registerkarte neben dem Fenster "Ausgabe". Wenn Sie es nicht angezeigt der **Ansicht** , zeigen Sie auf **Other Windows**, und klicken Sie dann auf **DSL-Details**.  
  
    2.  Klicken Sie auf die DSL-Definitionsdiagramm auf der Verbindungslinie der **Person** Domänenklasse der Shape-Klasse.  
  
    3.  In **DSL-Details**auf die **Decorator-Zuordnungen** Registerkarte, klicken Sie auf das Kontrollkästchen auf einem nicht zugeordneten Decorator-Element. In **Anzeigeeigenschaft**, wählen Sie die Eigenschaft "Domain", er zugeordnet soll. Beispielsweise **BirthDecorator** zu **Geburtsdatum**.  
  
4.  Speichern Sie die DSL, klicken Sie auf alle Vorlagen transformieren, und drücken Sie F5.  
  
5.  In einem Diagramm für den Beispiel-Modell stellen Sie sicher, dass Sie können jetzt klicken Sie auf die Positionen, die Sie ausgewählt haben, und geben Sie Werte in diesen. Darüber hinaus bei der Auswahl einer **Person** Form, die Fenster "Eigenschaften" zeigt die neuen Eigenschaften, Geburtsdatum und Tod.  
  
6.  In einer TT-Datei können Sie Code hinzufügen, die die Eigenschaften jeder Person erhält.  
  
 ![Stammstrukturdiagramm, Toolbox und Explorer](../modeling/media/familyt-instance.png "FamilyT_Instance")  
  
### <a name="define-new-classes"></a>Neue Klassen definieren  
 Sie können die Domänenklassen und Beziehungen zu einem Modell hinzufügen. Beispielsweise könnten Sie eine neue Klasse zum Darstellen von Metropolen und eine neue Beziehung aus, um darzustellen, dass eine Person in einer Stadt kurzlebig erstellen.  
  
 Um die verschiedenen Typen in einem Modelldiagramm unterschiedliche zu machen, können Sie die Domänenklassen verschiedene Arten von Formen oder Formen mit anderen Geometrie und Farben zuordnen.  
  
##### <a name="to-add-and-display-a-new-domain-class"></a>Beim Hinzufügen und Anzeigen einer neuen Domänenklasse  
  
1.  Hinzufügen einer Domänenklasse aus, und legen Sie sie ein untergeordnetes Element des Modellstamms.  
  
    1.  Klicken Sie in der DSL-Definitionsdiagramm auf die **einbettende Beziehung** tool, klicken Sie auf die Stammklasse **FamilyTreeModel**, und klicken Sie dann auf einen leeren Bereich des Diagramms auf.  
  
         Eine neue Domänenklasse wird angezeigt, die mit der FamilyTreeModel mit einer einbettenden Beziehung verbunden ist.  
  
         Legen Sie dessen Namen, z. B. **Town**.  
  
        > [!NOTE]
        >  Jede Domänenklasse mit Ausnahme des Stamms des Modells muss das Ziel mindestens einer einbettenden Beziehung sein, oder es muss eine Klasse, die das Ziel einer Einbettung erben. Aus diesem Grund ist es häufig praktisch eine Domänenklasse erstellen, mit dem Tool für die einbettende Beziehung.  
  
    2.  Fügen Sie eine Domäneneigenschaft auf die neue Klasse, z. B. **Namen**.  
  
2.  Fügen Sie eine verweisbeziehung zwischen Person "und" Town hinzu.  
  
    1.  Klicken Sie auf die **Verweisbeziehung** tool, klicken Sie auf die Person und klicken Sie dann auf Stadt.  
  
         ![DSL-definitionsfragment: stammstrukturstamm](../modeling/media/familyt-root.png "FamilyT_Root")  
  
        > [!NOTE]
        >  Verweisbeziehungen darstellen Querverweise von einem Teil der Modellstruktur auf einen anderen.  
  
3.  Fügen Sie eine Form vom Typ zur Darstellung von Städten in den Diagrammen Modell hinzu.  
  
    1.  Ziehen Sie eine **Geometrie-Form** aus der Toolbox auf das Diagramm und benennen Sie sie, z. B. **TownShape**.  
  
    2.  Legen Sie im Fenster Eigenschaften die Felder der Darstellung der neuen Form, wie z. B. Füllfarbe "und" Geometry.  
  
    3.  Fügen Sie ein Decorator-Element um den Namen der Stadt anzuzeigen, und benennen Sie sie NameDecorator. Legen Sie dessen Eigenschaft "Position" an.  
  
4.  Ordnen Sie die Domänenklasse für die Stadt der TownShape.  
  
    1.  Klicken Sie auf die **Diagrammelementzuordnung** tool, und klicken Sie auf die Domänenklasse für die Stadt, und klicken Sie dann die TownShape Shape-Klasse.  
  
    2.  In der **Decorator-Zuordnungen** Registerkarte die **DSL-Details** Fenster mit dem Connector für die Karte ausgewählt, NameDecorator überprüfen und festlegen **Anzeigeeigenschaft** Namen.  
  
5.  Erstellen Sie einen Connector aus, um die Beziehung zwischen Personen und Städten anzuzeigen.  
  
    1.  Ziehen Sie einen Connector aus der Toolbox in das Diagramm ein. Benennen Sie sie aus, und legen Sie seine Darstellungseigenschaften.  
  
    2.  Verwenden der **Diagrammelementzuordnung** Tool, um den neuen Connector auf die Beziehung zwischen Person "und" Stadt zu verknüpfen.  
  
         ![Stammstrukturdefinition mit formzuordnung](../modeling/media/familyt-shapemap.png "FamilyT_ShapeMap")  
  
6.  Erstellen Sie ein Elementtool dafür eine neue Stadt ein.  
  
    1.  In **DSL-Explorer**, erweitern Sie **Editor** dann **Toolboxregisterkarten**.  
  
    2.  Mit der rechten Maustaste  *\<Ihrer DSL >* , und klicken Sie dann auf **neues Elementtool hinzufügen**.  
  
    3.  Legen Sie die **Namen** Eigenschaft der neuen Tools, und legen Sie dessen **Klasse** Eigenschaft als Administrator verwenden könnte.  
  
    4.  Legen Sie die **Toolboxsymbol** Eigenschaft. Klicken Sie auf **[...]**  und klicken Sie in der **Dateiname** Feld, wählen Sie eine Symboldatei.  
  
7.  Erstellen Sie ein konnektortool dafür eine Verknüpfung zwischen Stadt und Personen.  
  
    1.  Mit der rechten Maustaste  *\<Ihrer DSL >* , und klicken Sie dann auf **Hinzufügen neuer Verbinder**.  
  
    2.  Legen Sie die Name-Eigenschaft des neuen Tools.  
  
    3.  In der **ConnectionBuilder** -Eigenschaft, wählen Sie den Generator, der den Namen der Person-Stadt Beziehung enthält.  
  
    4.  Legen Sie die **Toolboxsymbol**.  
  
8.  Speichern Sie die DSL-Definition, klicken Sie auf **alle Vorlagen transformieren**, und drücken Sie dann die **F5**.  
  
9. In der experimentellen Instanz von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], öffnen Sie eine Testdatei für das Modell. Verwenden Sie die neuen Tools zum Erstellen von Metropolen und Verknüpfungen zwischen Stadt und Personen ein. Beachten Sie, dass Sie nur die Links zwischen Element den korrekten Objekttypen erstellen können.  
  
10. Erstellen Sie Code, der die Stadt enthält, in der jede Person, die sich befindet. Textvorlagen werden mit einer der Bereiche, in dem Sie diesen Code ausführen können. Z. B. konnten Sie die vorhandene Sample.tt-Datei in der Projektmappe debuggen ändern, sodass sie den folgenden Code enthält:  
  
    ```  
    <#@ template inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" debug="true" #>  
    <#@ output extension=".txt" #>  
    <#@ FamilyTree processor="FamilyTreeDirectiveProcessor" requires="fileName='Sample.ftree'" #>  
  
    <#  
      foreach (Person person in this.FamilyTreeModel.People)  
      {  
    #>  
        <#= person.Name #><#if (person.Town != null) {#> of <#= person.Town.Name #> <#}#>  
  
    <#  
          foreach (Person child in person.Children)  
      {  
    #>  
                <#= child.Name #>  
    <#  
      }  
      }  
    #>  
  
    ```  
  
     Wenn Sie die TT-Datei speichern, erstellt er eine untergeordnete Datei, die die Liste der Personen und deren Wohngebäude enthält. Weitere Informationen finden Sie unter [Generieren von Code aus einer domänenspezifischen Sprache](../modeling/generating-code-from-a-domain-specific-language.md).  
  
## <a name="validation-and-commands"></a>Überprüfung und Befehle  
 Sie können diese DSL weiter entwickeln, durch das Hinzufügen von validierungseinschränkungen. Diese Einschränkungen sind Methoden, die Sie definieren können, und sicherstellen, dass das Modell in einem korrekten Zustand befindet. Beispielsweise können Sie eine Einschränkung, um sicherzustellen, definieren, die das Geburtsdatum des ein untergeordnetes Element höher als die des übergeordneten ist. Die Überprüfungsfunktion zeigt eine Warnung aus, wenn die DSL-Benutzer versucht, ein Modell zu speichern, die Einschränkungen beeinträchtigen. Weitere Informationen finden Sie unter [Validierung in einer domänenspezifischen Sprache](../modeling/validation-in-a-domain-specific-language.md).  
  
 Sie können auch die Befehle im Menü definieren, die der Benutzer aufrufen können. Befehle können das Modell ändern. Sie können auch mit anderen Modellen interagieren [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] und mit externen Ressourcen. Weitere Informationen finden Sie unter [Vorgehensweise: Ändern eines Menübefehls Standard](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).  
  
## <a name="deploying-the-dsl"></a>Bereitstellen von der DSL  
 Um andere Benutzer zum Verwenden der domänenspezifischen Sprache zu ermöglichen, verteilen Sie ein [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Extension (VSIX)-Datei. Dies wird erstellt, wenn Sie die DSL-Projektmappe zu erstellen.  
  
 Suchen Sie die VSIX-Datei im Ordner "bin" der Projektmappe ein. Kopieren sie auf dem Computer, auf dem Sie sie installieren möchten. Doppelklicken Sie auf dem Computer auf die VSIX-Datei. Die DSL kann verwendet werden, in allen Instanzen des [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] auf diesem Computer.  
  
 Sie können das gleiche Verfahren verwenden, auf die DSL auf Ihrem eigenen Computer installieren, sodass Sie nicht verfügen, verwenden Sie die experimentelle Instanz von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
 Weitere Informationen finden Sie unter [Bereitstellen von domänenspezifischen Sprachlösungen](../modeling/deploying-domain-specific-language-solutions.md).  
  
##  <a name="Reset"></a> Entfernen alte experimentelle DSLs  
 Wenn Sie experimentelle DSLs erstellt haben Sie nicht mehr benötigen, Sie können sie von Ihrem Computer entfernen, indem Sie das Zurücksetzen der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] experimentelle Instanz.  
  
 Dies wird von Ihrem Computer entfernt, alle experimentellen DSLs und andere experimentelle [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Erweiterungen. Hierbei handelt es sich um Erweiterungen, die im Debugmodus ausgeführt wurden.  
  
 Diese Prozedur entfernt keine DSLs oder andere [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Erweiterungen, die vollständig installiert wurde, indem Sie die VSIX-Datei ausführen.  
  
#### <a name="to-reset-the-visual-studio-experimental-instance"></a>Die experimentelle Instanz Visual Studio zurücksetzen  
  
1.  Klicken Sie auf **starten**, klicken Sie auf **Programme**, **Microsoft Visual Studio 2010 SDK**, **Tools**, und klicken Sie dann **Microsoft zurücksetzen Instanz von Visual Studio 2010 experimentell**.  
  
2.  Erstellen Sie experimentelle DSLs oder andere experimentelle neu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Erweiterungen, die Sie weiterhin verwenden möchten.  
  
## <a name="see-also"></a>Siehe auch  
 [Grundlegendes zu Modellen, Klassen und Beziehungen](../modeling/understanding-models-classes-and-relationships.md)   
 [Gewusst wie: Definieren Sie eine domänenspezifische Sprache](../modeling/how-to-define-a-domain-specific-language.md)   
 [Visualisierungs- und Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=186128)



