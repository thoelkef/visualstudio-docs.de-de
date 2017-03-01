---
title: "Erste Schritte mit domänenspezifischen Sprachen | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 024392a2-2c04-404f-a27b-7273553c3b60
caps.latest.revision: 16
author: alancameronwills
ms.author: awills
manager: douge
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 3d07f82ea737449fee6dfa04a61e195654ba35fa
ms.openlocfilehash: 8bd2f054db2c69a99218af05ca8d12465731ebca
ms.lasthandoff: 02/22/2017

---
# <a name="getting-started-with-domain-specific-languages"></a>Erste Schritte mit domänenspezifischen Sprachen
Dieses Thema erläutert die grundlegenden Konzepte in definieren und verwenden eine domänenspezifische Sprache (DSL) mit dem Modeling SDK für Visual Studio erstellt.  


[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

  
 Wenn Sie mit DSLs vertraut sind, wird empfohlen, Sie über arbeiten die **DSL-Tools Lab**, die sich an diesem Standort: [Visualisierungs- und Modellierungs-SDK](http://go.microsoft.com/fwlink/?LinkID=186128)  
  
## <a name="what-can-you-do-with-a-domain-specific-language"></a>Was können Sie mit einer domänenspezifischen Sprache?  
 Eine domänenspezifische Sprache ist eine Notation, in der Regel Grafik, die für einen bestimmten Zweck verwendet werden soll. Im Gegensatz dazu sind Sprachen wie z. B. UML allgemeine. In einer DSL können Sie definieren die Typen von Modellelement und deren Beziehungen und wie sie auf dem Bildschirm angezeigt werden.  
  
 Wenn Sie eine DSL entworfen haben, können Sie es als Teil eines Pakets für Visual Studio Integration Extension (VSIX) verteilen. Benutzer mit der DSL im arbeiten [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]:  
  
 ![Stammbaumdiagramm, Toolbox und Explorer](../modeling/media/familyt_instance.png "FamilyT_Instance")  
  
 Die Notation ist nur ein Teil einer DSL. Zusammen mit der Bezeichnung enthält das VSIX-Paket Tools, die Benutzern helfen, bearbeiten und Generieren von Material aus ihrer Modelle anwenden können.  
  
 Eine der wichtigsten Anwendungen von DSLs ist, Programmcode, Konfigurationsdateien und andere Artefakte generieren. Insbesondere in großen Projekten und Produktlinien, wobei verschiedene Varianten eines Produkts erstellt werden, kann viele der Variablen Aspekte von DSLs generiert eine erheblich größere Zuverlässigkeit und eine sehr schnelle Reaktion auf anforderungsänderungen bereitstellen.  
  
 Der Rest dieser Übersicht ist eine exemplarische Vorgehensweise, die die grundlegenden Vorgänge zum Erstellen und verwenden eine domänenspezifische Sprache führt [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Zum Definieren einer DSL müssen folgende Komponenten installiert sein:  
  
|||  
|-|-|  
|[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]|[http://go.Microsoft.com/fwlink/?LinkId=185579](http://go.microsoft.com/fwlink/?LinkId=185579)|  
|[!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)]|[http://go.Microsoft.com/fwlink/?LinkId=185580](http://go.microsoft.com/fwlink/?LinkId=185580)|  
|Modeling SDK für Visual Studio||  


[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

  
## <a name="creating-a-dsl-solution"></a>Erstellen eine DSL-Projektmappe  
 Um eine neue domänenspezifische Sprache zu erstellen, erstellen Sie ein neues [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] -Lösung mithilfe der Projektvorlage domänenspezifische Sprache.  
  
#### <a name="to-create-a-dsl-solution"></a>So erstellen Sie eine DSL-Projektmappe  
  
1.  Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.  
  
2.  Klicken Sie unter **Projekttypen**, erweitern Sie die **andere Projekttypen** Knoten, und klicken Sie auf **Erweiterbarkeit**.  
  
3.  Klicken Sie auf **domänenspezifischen Sprachdesigner**.  
  
     ![Erstellen von DSL-Dialogfeld](../modeling/media/create_dsldialog.png "Create_DSLDialog")  
  
4.  In der **Namen** geben **FamilyTree**. Klicken Sie auf **OK**.  
  
     Die **Domain-Specific Language Assistenten** wird geöffnet und zeigt eine Liste der Vorlagen-DSL-Projektmappen.  
  
     Klicken Sie auf die einzelnen Vorlagen, um eine Beschreibung anzuzeigen,  
  
     Vorlagen sind hilfreich Ausgangspunkt. Diese bietet einer vollständigen funktionierendes DSL, die Sie an Ihre Bedürfnisse bearbeiten können. Normalerweise wählen Sie die Vorlage am nächsten liegt, was Sie erstellen möchten.  
  
5.  Wählen Sie in dieser exemplarischen Vorgehensweise die **minimale Sprache** Vorlage.  
  
6.  Geben Sie auf der entsprechenden Seite des Assistenten eine Dateinamenerweiterung für die DSL ein. Diese Erweiterung wird für Dateien mit Instanzen Ihrer DSL verwendet.  
  
    -   Wählen Sie eine Erweiterung, die keine Anwendung auf Ihrem Computer oder auf einem Computer, auf dem Sie die DSL installieren möchten zugeordnet ist. Beispielsweise **Docx** und **Htm** wäre akzeptablen Dateinamenerweiterungen.  
  
    -   Der Assistent warnt Sie, wenn die eingegebene Erweiterung bereits als DSL verwendet wird. Verwenden Sie nach Möglichkeit eine andere Dateinamenerweiterung. Sie können die experimentelle Instanz des Visual Studio SDK auch zurücksetzen, um alte experimentelle Designer zu löschen. Klicken Sie auf **Start**, klicken Sie auf **Programme**, **Microsoft Visual Studio 2010 SDK**, **Tools**, und klicken Sie dann **Zurücksetzen die Microsoft Visual Studio 2010 experimentellen Instanz**.  
  
7.  Überprüfen Sie die anderen Seiten, und klicken Sie dann auf **Fertig stellen**.  
  
     Eine Projektmappe wird generiert, die zwei Projekte enthält. Sie werden als Dsl und DslPackage bezeichnet. Eine Diagrammdatei öffnet, benannte "DslDefinition.DSL".  
  
    > [!NOTE]
    >  Großteil des Codes, die Sie in den Ordnern in beiden Projekten sehen können, wird aus "DslDefinition.DSL" generiert. Aus diesem Grund sind die meisten Ihrer DSL in dieser Datei geändert.  
  
 Die Benutzeroberfläche gleicht nun der folgenden Abbildung.  
  
 ![DSL-Designer](../modeling/media/dsl_designer.png "Dsl_designer")  
  
 Diese Projektmappe definiert eine domänenspezifische Sprache. Weitere Informationen finden Sie unter [Überblick über die Benutzeroberfläche von Domain-Specific Language Tools](../modeling/overview-of-the-domain-specific-language-tools-user-interface.md).  
  
## <a name="the-important-parts-of-the-dsl-solution"></a>Die wichtigen Teile der DSL-Projektmappe  
 Beachten Sie die folgenden Aspekte der neuen Projektmappe ein.  
  
-   **Dsl\DslDefinition.DSL** Dies ist die Datei, die Sie sehen, wenn Sie eine DSL-Projektmappe erstellen. Fast alle der Code in der Projektmappe wird aus dieser Datei generiert, und die meisten Änderungen, die Sie für die Definition einer DSL stellen hier vorgenommen werden. Weitere Informationen finden Sie unter Arbeiten mit dem [arbeiten mit dem DSL-Definitionsdiagramm](../modeling/working-with-the-dsl-definition-diagram.md).  
  
-   **DSL-Projekt** dieses Projekt enthält Code, die einer domänenspezifischen Sprache definiert.  
  
-   **DslPackage-Projekt** dieses Projekt enthält Code, der Instanzen der DSL geöffnet und bearbeitet werden kann [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
##  <a name="a-namedebugginga-running-the-dsl"></a><a name="Debugging"></a>Ausführen der DSL  
 Sie können die DSL-Projektmappe ausführen, sobald Sie es erstellt haben. Später können Sie die DSL-Definition nach und nach Ausführen der Projektmappe nach jeder Änderung erneut ändern.  
  
#### <a name="to-experiment-with-the-dsl"></a>Experimentieren mit der DSL  
  
1.  Klicken Sie auf **alle Vorlagen transformieren** in der Symbolleiste des Projektmappen-Explorer. Dies generiert die meisten des Quellcodes von "DslDefinition.DSL" neu.  
  
    > [!NOTE]
    >  Wenn Sie "DslDefinition.DSL" ändern, klicken Sie auf **alle Vorlagen transformieren** bevor Sie die Projektmappe neu erstellen. Dieser Schritt kann automatisiert werden. Weitere Informationen finden Sie unter [wie alle Vorlagen transformieren automatisieren](http://msdn.microsoft.com/en-us/b63cfe20-fe5e-47cc-9506-59b29bca768a).  
  
2.  Drücken Sie F5, oder klicken Sie auf die **Debuggen** im Menü klicken Sie auf **Debuggen starten**.  
  
     Die DSL erstellt und wird in der experimentellen Instanz von installiert [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
     Eine experimentelle Instanz von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wird gestartet. Die experimentelle Instanz hat die Einstellungen aus der Registrierung, der eine separate Teilstruktur, in denen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Erweiterungen für Debugzwecke registriert sind. Normale Instanzen von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] haben keinen Zugriff auf Erweiterungen, die es registriert.  
  
3.  In der experimentellen Instanz von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], öffnen Sie die Modelldatei **Test** von **Projektmappen-Explorer**.  
  
     \- oder –  
  
     Mit der rechten Maustaste des Projekts Debuggen, zeigen Sie auf **hinzufügen**, und klicken Sie dann auf **Element**. In der **hinzufügen** wählen Sie im Dialogfeld der Dateityp Ihrer DSL.  
  
     Die Datei wird als ein leeres Diagramm geöffnet.  
  
     Die Toolbox wird geöffnet und zeigt Tools, die den Diagrammtyp.  
  
4.  Verwenden Sie die Tools zum Erstellen von Formen und Konnektoren im Diagramm.  
  
    1.  Zum Erstellen von Shapes ziehen Sie aus der Beispiel-Form-Werkzeug in das Diagramm.  
  
    2.  Um zwei Formen zu verbinden, klicken Sie auf die Beispiel-Verbinder, klicken Sie auf die erste Form, und klicken Sie dann auf die zweite Form.  
  
5.  Klicken Sie auf die Bezeichnungen der Formen zu ändern.  
  
 Die experimentelle [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wird im folgende Beispiel ähneln:  
  
 ![](../modeling/media/dsl_min.png "DSL_min")  
  
### <a name="the-content-of-a-model"></a>Der Inhalt eines Modells  
 Der Inhalt der Datei, die eine Instanz einer DSL wird aufgerufen, ein *Modell*. Das Modell enthält *Modell**Elemente* und *Links* zwischen den Elementen. Die DSL-Definition gibt an, welche Arten von Modellelementen und Links können im Modell vorhanden sind. Z. B. in einer DSL aus der Vorlage minimale Sprache erstellt, ist es ein Typ des Modellelements, und ein Link.  
  
 Die DSL-Definition kann angeben, wie das Modell in einem Diagramm angezeigt wird. Sie können aus einer Vielzahl von Formaten von Formen und Konnektoren auswählen. Sie können angeben, dass einige Formen in anderen Formen angezeigt werden.  
  
 Sehen Sie ein Modell als eine Struktur in der **Explorer** anzeigen, während Sie ein Modell bearbeitet werden. Hinzufügen von Formen im Diagramm werden die Modellelemente auch im Explorer angezeigt. Der Explorer kann verwendet werden, auch wenn es kein Diagramm.  
  
 Wenn den Explorer in den debugging-Instanz nicht [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]auf der **Ansicht** , zeigen Sie im Menü auf **Weitere Fenster**, und klicken Sie dann auf * \<Ihre Sprache >* **Explorer**.  
  
### <a name="the-api-of-your-dsl"></a>Die API der DSL  
 Die DSL generiert eine API, mit dem Sie zum Lesen und Aktualisieren von Modellen, die Instanzen der DSL. Die API kann zum Generieren von Textdateien aus einem Modell. Weitere Informationen finden Sie unter [Design-Time Code Generation mithilfe von T4-Textvorlagen](../modeling/design-time-code-generation-by-using-t4-text-templates.md).  
  
 Öffnen Sie in der Projektmappe Debuggen die Vorlagendateien mit der Erweiterung "tt". Diese Beispiele veranschaulichen, wie Sie Text aus Modellen generieren und ermöglichen es Ihnen, die API Ihrer DSL testen können. Eines der Beispiele in geschrieben [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], die andere in [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].  
  
 Jede Vorlage ist Datei die Datei, die generiert werden. Erweitern Sie die Vorlagendatei im Projektmappen-Explorer, und öffnen Sie die generierte Datei.  
  
 Die Vorlagedatei enthält ein kurzes Stück Code, der alle Elemente im Modell aufgeführt.  
  
 Die generierte Datei enthält das Ergebnis.  
  
 Wenn Sie eine Modelldatei ändern, wird nach dem Generieren von Dateien entsprechende Änderungen in der generierten Dateien angezeigt.  
  
##### <a name="to-regenerate-text-files-after-you-change-the-model-file"></a>Text-Dateien neu generieren, nachdem Sie die Datei ändern  
  
1.  In der experimentellen Instanz von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], speichern Sie die Datei.  
  
2.  Stellen Sie sicher, dass der Namensparameter der Datei in den einzelnen TT-Dateien auf die Modelldatei bezieht, die Sie für Experimente verwenden. Speichern Sie die TT-Datei.  
  
3.  Klicken Sie auf **alle Vorlagen transformieren** in der Symbolleiste des **Projektmappen-Explorer**.  
  
     \- oder –  
  
     Mit der rechten Maustaste in der Vorlagen, die zu generieren, und klicken Sie dann auf **benutzerdefiniertes Tool ausführen**.  
  
 Sie können eine beliebige Anzahl von Textvorlagendateien zu einem Projekt hinzufügen. Jede Vorlage generiert eine Datei.  
  
> [!NOTE]
>  Wenn Sie die DSL-Definition ändern, funktioniert der Textvorlagencode Beispiel nicht, sofern die Aktualisierung.  
  
 Weitere Informationen finden Sie unter [Generieren von Code aus einer domänenspezifischen Sprache](../modeling/generating-code-from-a-domain-specific-language.md) und [Schreiben von Code zum Anpassen einer domänenspezifischen Sprache](../modeling/writing-code-to-customise-a-domain-specific-language.md).  
  
## <a name="customizing-the-dsl"></a>Anpassen der DSL  
 Wenn Sie die DSL-Definition ändern möchten, schließen Sie die experimentelle Instanz, und aktualisieren Sie die Klassendefinition im Hauptfenster [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Instanz.  
  
> [!NOTE]
>  Nachdem Sie die DSL-Definition geändert haben, verlieren Sie möglicherweise Informationen in den Test-Modellen, die Sie mit früheren Versionen erstellt wurden.  Beispielsweise enthält die debugging-Projektmappe eine Datei mit dem Namen Beispiel enthält einige Formen und Konnektoren. Nach dem Starten Ihrer DSL-Definition zu entwickeln, werden sie nicht angezeigt, und sie gehen verloren, wenn Sie die Datei speichern.  
  
 Sie können eine Vielzahl von Erweiterungen Ihrer DSL vornehmen. In den folgenden Beispielen erhalten Sie einen Eindruck von den Möglichkeiten.  
  
 Klicken Sie nach jeder Änderung Speichern der DSL-Definition auf **alle Vorlagen transformieren** in **Projektmappen-Explorer**, und drücken Sie dann die **F5** Experimentieren mit der geänderten DSL.  
  
### <a name="rename-the-types-and-tools"></a>Benennen Sie die Typen und Tools  
 Benennen Sie die vorhandene Domänenklassen und Beziehungen. Beispielsweise konnte beginnend mit einer Dsl-Definition aus der Vorlage minimale Sprache erstellt, der folgenden umbenennen, stellen Sie die DSL Familie Strukturen darstellen Vorgänge.  
  
##### <a name="to-rename-domain-classes-relationships-and-tools"></a>Umbenennen von Domänenklassen, Beziehungen und tools  
  
1.  Im Diagramm DslDefinition umbenennen **ExampleModel** auf **FamilyTreeModel**, **ExampleElement** zu **Person**, **Ziele** auf **Eltern**, und **Quellen** zu **Kinder**. Sie können jede Bezeichnung, um sie zu ändern klicken.  
  
     ![DSL-Definitionsdiagramm - stammbaummodell](../modeling/media/familyt_person.png "FamilyT_Person")  
  
2.  Benennen Sie die Element- und Connector-Tools.  
  
    1.  Öffnen Sie das DSL-Explorer-Fenster auf die Registerkarte Projektmappen-Explorer. Wenn Sie es nicht sehen die **Ansicht** , zeigen Sie im Menü auf **Weitere Fenster** , und klicken Sie dann auf **DSL-Explorer**. DSL-Explorer ist sichtbar, nur, wenn die DSL-Definitionsdiagramm das aktive Fenster ist.  
  
    2.  Öffnen Sie das Eigenschaftenfenster, und positionieren Sie es so, dass Sie DSL-Explorer und Eigenschaften zur gleichen Zeit sehen können.  
  
    3.  Erweitern Sie im DSL-Explorer **Editor**, **Toolboxregisterkarten**, * \<Ihre DSL >*, und klicken Sie dann **Tools**.  
  
    4.  Klicken Sie auf **ExampleElement**. Dies ist das Toolboxelement, das zum Erstellen von Elementen verwendet wird.  
  
    5.  Ändern Sie im Fenster Eigenschaften die **Namen** -Eigenschaft **Person**.  
  
         Beachten Sie, dass die **Beschriftung** -Eigenschaft ebenfalls geändert wird.  
  
    6.  Ändern Sie den Namen der auf die gleiche Weise die **ExampleConnector** -tool in **ParentLink**. Ändern der **Beschriftung** Eigenschaft, sodass diese nicht über eine Kopie der Name-Eigenschaft ist. Geben Sie beispielsweise **übergeordneter Link**.  
  
3.  Erstellen Sie die DSL neu.  
  
    1.  Speichern Sie die DSL-Definitionsdatei.  
  
    2.  Klicken Sie auf **alle Vorlagen transformieren** in der Symbolleiste des Projektmappen-Explorers  
  
    3.  Drücken Sie F5. Warten Sie, bis der experimentellen Instanz von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wird angezeigt.  
  
4.  In der Projektmappe debuggen, in der experimentellen Instanz von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], öffnen Sie eine Testdatei für das Modell. Ziehen Sie Elemente auf es aus der Toolbox. Beachten Sie, dass das Tool Beschriftungen und dem Typnamen im DSL-Explorer geändert haben.  
  
5.  Speichern Sie die Datei.  
  
6.  Öffnen Sie eine TT-Datei, und Ersetzen Sie Vorkommen von den alten Namen und die Eigenschaften mit den neuen Namen.  
  
7.  Stellen Sie sicher, dass der Dateiname, der in der TT-Datei angegeben ist Ihr Testmodell gibt.  
  
8.  Speichern Sie die TT-Datei. Öffnen Sie die generierte Datei aus, um das Ergebnis der Ausführung des Codes in die TT-Datei finden Sie unter. Stellen Sie sicher, dass er korrekt ist.  
  
### <a name="add-domain-properties-to-classes"></a>Fügen Sie Domäneneigenschaften Klassen hinzu  
 Eine Domänenklasse, z. B. zur Darstellung der Jahre Geburtsdatum und Tod einer Person Eigenschaften hinzugefügt.  
  
 Um die neuen Eigenschaften im Diagramm sichtbar zu machen, müssen Sie hinzufügen *Decorators* auf die Form, in dem das Modellelement angezeigt. Sie müssen auch die Eigenschaften der Decorator-Elementen zuordnen.  
  
##### <a name="to-add-properties-and-display-them"></a>Eigenschaften hinzufügen und anzeigen  
  
1.  Die Eigenschaften hinzufügen.  
  
    1.  In der DSL-Definitionsdiagramm mit der rechten Maustaste die **Person** Domänenklasse, zeigen Sie auf **hinzufügen**, und klicken Sie dann auf **Domäneneigenschaft**.  
  
    2.  Geben Sie eine Liste der neuen Eigenschaftennamen, wie z. B. **Geburtsdatum** und **Tod**. Drücken Sie **EINGABETASTE** nach jedem.  
  
2.  Hinzufügen von Decorator-Elementen, die die Eigenschaften in der Form angezeigt werden.  
  
    1.  Führen Sie die graue Linie, die von der Person-Domänenklasse der anderen Seite des Diagramms erweitert. Dies ist eine diagrammelementzuordnung. Die Domänenklasse verweist auf eine Shape-Klasse.  
  
    2.  Mit der rechten Maustaste dieses Shape-Klasse, zeigen Sie auf **hinzufügen**, und klicken Sie dann auf **Text-Decorator**.  
  
    3.  Fügen Sie z. B. zwei Decorator-Elemente mit Namen **BirthDecorator** und **DeathDecorator**.  
  
    4.  Wählen Sie jedes neue Decorator-Element, und legen Sie im Fenster Eigenschaften die **Position** Feld. Dies bestimmt, in dem der Eigenschaftswert für die Domäne auf der Form angezeigt wird. Legen Sie z. B. **InnerBottomLeft** und **InnerBottomRight**.  
  
         ![Depot-Form Definition](../modeling/media/familyt_compartment.png "FamilyT_Compartment")  
  
3.  Die Eigenschaften der Decorator-Elementen zugeordnet.  
  
    1.  Öffnen Sie die DSL-Details-Fenster. Es ist in der Regel auf einer Registerkarte neben im Ausgabefenster. Wenn Sie es nicht sehen die **Ansicht** auf **Weitere Fenster**, und klicken Sie dann auf **DSL-Details**.  
  
    2.  Klicken Sie auf die DSL-Definitionsdiagramm auf der Verbindungslinie der **Person** Domänenklasse, um die Shape-Klasse.  
  
    3.  In **DSL-Details**auf der **Decorator-Zuordnungen** Registerkarte, klicken Sie auf das Kontrollkästchen auf einen nicht zugeordneten Decorator-Elements. In **Anzeigeeigenschaft**, wählen Sie die Eigenschaft "Domain", er zugeordnet soll. Ordnen Sie z. B. **BirthDecorator** auf **Geburtsdatum**.  
  
4.  Speichern Sie die DSL, klicken Sie auf alle Vorlagen transformieren, und drücken Sie F5.  
  
5.  Ein Beispieldiagramm Modell Vergewissern Sie sich, dass Sie jetzt klicken Sie auf die Positionen, die Sie ausgewählt haben und Werte eingeben können. Darüber hinaus bei der Auswahl einer **Person** Form, das Fenster Eigenschaften zeigt die neuen Eigenschaften, Geburtsdatum und Tod.  
  
6.  In einer TT-Datei können Sie Code hinzufügen, die die Eigenschaften der einzelnen Personen abruft.  
  
 ![Stammbaumdiagramm, Toolbox und Explorer](../modeling/media/familyt_instance.png "FamilyT_Instance")  
  
### <a name="define-new-classes"></a>Neue Klassen definieren  
 Sie können ein Modell Domänenklassen und Beziehungen hinzufügen. Beispielsweise könnten Sie eine neue Klasse darstellt, Städte und eine neue Beziehung dargestellt, dass eine Person in einer Stadt befanden erstellen.  
  
 Um die verschiedenen Typen in einem Modelldiagramm eindeutig zu machen, können Sie verschiedene Arten von Formen oder Formen mit anderen Geometrie und Farben, die Domänenklassen zuordnen.  
  
##### <a name="to-add-and-display-a-new-domain-class"></a>Zum Hinzufügen einer neuen Domänenklasse  
  
1.  Fügen Sie eine Domänenklasse und stellen Sie es ein untergeordnetes Element des Modellstamms.  
  
    1.  Klicken Sie in der DSL-Definitionsdiagramm auf die **einbettende Beziehung** -tool, klicken Sie auf die Stammklasse **FamilyTreeModel**, und klicken Sie dann auf einen leeren Bereich des Diagramms.  
  
         Eine neue Domänenklasse wird angezeigt, die mit der FamilyTreeModel mit einer einbettenden Beziehung verbunden ist.  
  
         Legen Sie den Namen, z. B. **Stadt**.  
  
        > [!NOTE]
        >  Jede Domänenklasse mit Ausnahme der Stamm des Modells muss das Ziel mindestens einer einbettenden Beziehung sein, oder es muss eine Klasse, die das Ziel einer einbetten ist erben. Aus diesem Grund ist es häufig sinnvoll, eine Domänenklasse erstellen, mit dem Tool einbettende Beziehung.  
  
    2.  Fügen Sie eine Domäneneigenschaft auf die neue Klasse, z. B. **Namen**.  
  
2.  Fügen Sie eine verweisbeziehung zwischen Person und Stadt.  
  
    1.  Klicken Sie auf die **Verweisbeziehung** tool, klicken Sie auf Person und klicken Sie dann auf Stadt.  
  
         ![DSL-definitionsfragment: stammbaumstamm](../modeling/media/familyt_root.png "FamilyT_Root")  
  
        > [!NOTE]
        >  Verweisbeziehungen darstellen Querverweise von einem Teil der Modellstruktur in einen anderen.  
  
3.  Fügen Sie eine Form, um die Städte in den Diagrammen Modell darstellen.  
  
    1.  Ziehen Sie eine **Geometrieform** aus der Toolbox in das Diagramm, und benennen Sie es, z. B. **TownShape**.  
  
    2.  Legen Sie im Fenster Eigenschaften die Felder Darstellung der neuen Form, wie z. B. Füllfarbe und Geometry.  
  
    3.  Hinzufügen eines Decorator-Elements um den Namen der Stadt, und nennen Sie sie NameDecorator. Legen Sie seine Position-Eigenschaft.  
  
4.  Ordnen Sie die Domänenklasse Stadt der TownShape.  
  
    1.  Klicken Sie auf die **Diagrammelementzuordnung** -tool, und klicken Sie auf die Domänenklasse für Stadt und dann die TownShape Shape-Klasse.  
  
    2.  In der **Decorator-Zuordnungen** auf der Registerkarte der **DSL-Details** Fenster mit dem Connector Zuordnung ausgewählt, NameDecorator überprüfen und festlegen **Anzeigeeigenschaft** Namen.  
  
5.  Erstellen Sie einen Connector zur Darstellung der Beziehung zwischen Person und Städte.  
  
    1.  Ziehen Sie einen Connector aus der Toolbox in das Diagramm. Namen Sie, und legen Sie seine Darstellungseigenschaften.  
  
    2.  Verwenden der **Diagrammelementzuordnung** Tool, um den neuen Connector mit der Beziehung zwischen Person und Stadt zu verknüpfen.  
  
         ![Stammbaumdefinition mit formzuordnung](../modeling/media/familyt_shapemap.png "FamilyT_ShapeMap")  
  
6.  Erstellen Sie ein Elementtool umgezogen ausführen.  
  
    1.  In **DSL-Explorer**, erweitern Sie **Editor** dann **Toolboxregisterkarten**.  
  
    2.  Mit der rechten Maustaste * \<Ihre DSL >* , und klicken Sie dann auf **neues Elementtool hinzufügen**.  
  
    3.  Festlegen der **Namen** -Eigenschaft der neuen Tools, und legen seine **Klasse** -Eigenschaft Stadt.  
  
    4.  Legen Sie die **Toolboxsymbol** Eigenschaft. Click **[...] ** und in der **Dateinamen** wählen eine Symboldatei.  
  
7.  Erstellen Sie einen Connector-Tool zum Erstellen einer Verknüpfung zwischen Städte und Personen.  
  
    1.  Mit der rechten Maustaste * \<Ihre DSL >* , und klicken Sie dann auf **neue Verbinder hinzufügen**.  
  
    2.  Legen Sie die Name-Eigenschaft des neuen Tools.  
  
    3.  In der **ConnectionBuilder** -Eigenschaft, wählen Sie den Generator, der den Namen der Person-Stadt Beziehung enthält.  
  
    4.  Legen Sie die **Toolboxsymbol**.  
  
8.  Speichern Sie die DSL-Definition, klicken Sie auf **alle Vorlagen transformieren**, und drücken Sie dann die **F5**.  
  
9. In der experimentellen Instanz von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], öffnen Sie eine Testdatei für das Modell. Verwenden Sie die neuen Tools, um Städte und Links zwischen Städten und Personen zu erstellen. Beachten Sie, dass Sie nur die Links zwischen Element den korrekten Objekttypen erstellen können.  
  
10. Erstellen Sie Code, der die Stadt aufgeführt, in der jede Person befindet. Textvorlagen sind einer der Bereiche, in denen dieser Code ausgeführt werden kann. Sie könnten z. B. die vorhandene Sample.tt-Datei in der Projektmappe debuggen ändern, so, dass sie den folgenden Code enthält:  
  
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
 Sie können diese DSL weiter entwickeln, durch Hinzufügen von validierungseinschränkungen. Diese Einschränkungen sind Methoden, die Sie definieren können, und sicherstellen, dass das Modell im richtigen Zustand ist. Beispielsweise können Sie eine Einschränkung, um sicherzustellen, definieren, die das Geburtsdatum ein untergeordnetes Element des übergeordneten liegt. Das Feature zur Validierung wird eine Warnung angezeigt, wenn der DSL-Benutzer versucht, ein Modell zu speichern, die Einschränkungen berücksichtigt wird. Weitere Informationen finden Sie unter [Überprüfung in einer domänenspezifischen Sprache](../modeling/validation-in-a-domain-specific-language.md).  
  
 Sie können auch Befehle definieren, die der Benutzer aufrufen kann. Befehle können das Modell zu ändern. Sie können auch mit anderen Modellen interagieren [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und externe Ressourcen. Weitere Informationen finden Sie unter [Gewusst wie: Ändern eines Menübefehls Standard](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).  
  
## <a name="deploying-the-dsl"></a>Bereitstellen von DSL  
 Um anderen Benutzern die Verwendung einer domänenspezifischen Sprache zu ermöglichen, Sie Verteilen einer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] -Erweiterung (VSIX)-Datei. Dies wird erstellt, wenn Sie die DSL-Projektmappe zu erstellen.  
  
 Suchen Sie die VSIX-Datei im Ordner "Bin" der Projektmappe. Kopieren sie auf dem Computer, auf dem Sie installieren möchten. Doppelklicken Sie auf dem Computer auf die VSIX-Datei. Die DSL kann verwendet werden, in allen Instanzen des [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] auf diesem Computer.  
  
 Sie können das gleiche Verfahren die DSL auf Ihrem eigenen Computer installieren, sodass Sie nicht verfügen, verwenden Sie die experimentelle Instanz von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Weitere Informationen finden Sie unter [Bereitstellung Domain-Specific Language Solutions](../modeling/deploying-domain-specific-language-solutions.md).  
  
##  <a name="a-namereseta-removing-old-experimental-dsls"></a><a name="Reset"></a>Entfernen alte experimentelle DSLs  
 Wenn Sie experimentelle DSLs erstellt haben Sie nicht mehr benötigen, vom Computer durch Zurücksetzen Entfernen der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] experimentelle Instanz.  
  
 Dies wird von Ihrem Computer entfernen, alle experimentelle DSLs und andere experimentelle [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Erweiterungen. Hierbei handelt es sich um Erweiterungen, die im Debugmodus ausgeführt wurden.  
  
 Diese Prozedur entfernt keine DSLs oder andere [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Erweiterungen, die vollständig installiert wurde, indem Sie die VSIX-Datei ausführen.  
  
#### <a name="to-reset-the-visual-studio-experimental-instance"></a>Die experimentelle Instanz Visual Studio zurücksetzen  
  
1.  Klicken Sie auf **Start**, klicken Sie auf **Programme**, **Microsoft Visual Studio 2010 SDK**, **Tools**, und klicken Sie dann **Zurücksetzen die Microsoft Visual Studio 2010 experimentellen Instanz**.  
  
2.  Neu erstellen, alle experimentelle DSLs oder andere experimentelle [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Erweiterungen, die Sie weiterhin verwenden möchten.  
  
## <a name="see-also"></a>Siehe auch  
 [Grundlegendes zu Modellen, Klassen und Beziehungen](../modeling/understanding-models-classes-and-relationships.md)   
 [So definieren Sie eine domänenspezifische Sprache](../modeling/how-to-define-a-domain-specific-language.md)   

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]


