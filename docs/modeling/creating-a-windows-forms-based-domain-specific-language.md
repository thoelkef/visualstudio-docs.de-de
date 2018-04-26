---
title: Erstellen einer Windows Forms-basierten domänenspezifischen Sprache
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: ce2fa2f067b72d051aa21eba0db2b8f0eda8b43f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="creating-a-windows-forms-based-domain-specific-language"></a>Erstellen einer Windows Forms-basierten domänenspezifischen Sprache
Sie können Windows Forms verwenden, um den Status eines Modells domänenspezifische Sprache (DSL), anstatt einen DSL-Diagramm anzuzeigen. Dieses Thema führt Sie durch ein, Binden von Windows Forms an eine DSL, indem Sie die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Visualization and Modeling SDK.

 ![DSL&#45;Wpf&#45;2](../modeling/media/dsl-wpf-2.png "DSL-Wpf-2") ein DSL-Instanz, die eine Windows-Formular-Benutzeroberfläche und den Modell-Explorer anzeigt.

## <a name="creating-a-windows-forms-dsl"></a>Erstellen einer Windows Forms DSL
 Die **minimale WinForm-Designer** DSL-Vorlage erstellt eine minimale DSL, die Sie ändern können, um Ihren eigenen Anforderungen anzupassen.

#### <a name="to-create-a-minimal-winforms-dsl"></a>So erstellen eine minimale WinForms DSL

1.  Erstellen Sie eine DSL aus der **minimale WinForm-Designer** Vorlage.

     In dieser exemplarischen Vorgehensweise werden die folgenden Namen angenommen:

    |||
    |-|-|
    |Projektmappen und DSL-name|FarmApp|
    |Namespace|Company.FarmApp|

2.  Experimentieren Sie mit dem ersten Beispiel, das die Vorlage bereitstellt:

    1.  Transformieren Sie aller Vorlagen an.

    2.  Erstellen und Ausführen des Beispiels (**STRG + F5**).

    3.  Öffnen Sie in der experimentellen Instanz von Visual Studio die `Sample` Datei im Projekt debuggen.

         Beachten Sie, dass er in einem Windows Forms-Steuerelement angezeigt wird.

         Sie können auch die Elemente des Modells angezeigt, die im Explorer anzeigen.

         Fügen Sie einige Elemente, die entweder im Format oder im Explorer, und beachten Sie, dass sie in der anderen Anzeige angezeigt werden.

 In der Hauptinstanz von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], beachten Sie die folgenden Punkte bezüglich der DSL-Lösung:

-   `DslDefinition.dsl` enthält keine Diagrammelemente. Dies ist, da nicht DSL Diagramme mit der Instanz Modelle für diese DSL anzuzeigen. Stattdessen binden Sie ein Windows Form für das Modell und die Elemente auf dem Formular werden das Modell angezeigt.

-   Zusätzlich zu den `Dsl` und `DslPackage` Projekte, die Projektmappe enthält eine dritte Projekt mit dem Namen `UI.` **UI** Projekt enthält die Definition eines Windows Forms-Steuerelements. `DslPackage` richtet sich nach `UI`, und `UI` richtet sich nach `Dsl`.

-   In der `DslPackage` Projekt `UI\DocView.cs` enthält den Code, in dem Windows Forms-Steuerelement angezeigt, die in definiert ist die `UI` Projekt.

-   Die `UI` Projekt enthält ein funktionstüchtiges Beispiel ein Formularsteuerelement gebunden, der DSL. Allerdings können sie nicht verwendet, wenn Sie die DSL-Definition geändert haben. Die `UI` Projekt enthält:

    -   Eine Windows Forms-Klasse, die mit dem Namen `ModelViewControl`.

    -   Eine Datei namens `DataBinding.cs` , enthält eine zusätzliche partielle Definition der `ModelViewControl`. Um seinen Inhalt anzuzeigen **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die Datei, und wählen Sie **Code anzeigen**.

### <a name="about-the-ui-project"></a>Über das UI-Projekt
 Bei der Aktualisierung der DSL-Definitionsdatei Definieren eigener DSL müssen Sie das Steuerelement im Aktualisieren der `UI` Projekt zum Anzeigen der DSL. Im Gegensatz zu den `Dsl` und `DslPackage` projiziert das Beispiel `UI` Projekt wird nicht generiert `DslDefinitionl.dsl`. Sie können hinzufügen TT-Dateien, um den Code zu generieren, wenn Sie möchten, obwohl, die in dieser exemplarischen Vorgehensweise nicht behandelt wird.

## <a name="updating-the-dsl-definition"></a>Aktualisieren der DSL-Definition
 Die folgenden DSL-Definition in dieser exemplarischen Vorgehensweise verwendet wird.

 ![DSL&#45;Wpf&#45;1](../modeling/media/dsl-wpf-1.png "DSL-Wpf-1")

#### <a name="to-update-the-dsl-definition"></a>Zum Aktualisieren der DSL-definition

1.  DslDefinition.dsl in der DSL-Designer zu öffnen.

2.  Löschen Sie **ExampleElement**

3.  Benennen Sie die **ExampleModel** Domänenklasse zu `Farm`.

     Geben Sie ihm Weitere Domäneneigenschaften mit dem Namen `Size` des Typs **Int32**, und `IsOrganic` des Typs **booleschen**.

    > [!NOTE]
    >  Wenn Sie die Stammklasse der Domäne zu löschen und dann eine neue Stamm erstellen, müssen Sie der Stammklasse-Editor-Eigenschaft zurückgesetzt. In **Explorer für DSL**Option **Editor**. Legen Sie dann im Fenster Eigenschaften **Stammklasse** auf `Farm`.

4.  Verwenden der **Domänenklasse namens** mit dem Tool die folgenden Domänenklassen zu erstellen:

    -   `Field` -Geben Sie dieser eine weitere Domäneneigenschaft, die mit dem Namen `Size`.

    -   `Animal` -Im Eigenschaftenfenster festgelegt **Inheritance Modifier** auf **abstrakte**.

5.  Verwenden der **Domänenklasse** mit dem Tool die folgenden Klassen zu erstellen:

    -   `Sheep`

    -   `Goat`

6.  Verwenden der **Vererbung** Tool vornehmen `Goat` und `Sheep` Vererben `Animal`.

7.  Verwenden der **Embedding** Tool So betten Sie ein `Field` und `Animal` unter `Farm`.

8.  Möglicherweise möchten das Diagramm zu leeren. Verwenden Sie zum Verringern der Anzahl von doppelten Elementen der **Teilstruktur hier schalten** Befehl im Kontextmenü der Elemente der Blattebene.

9. **Transformieren aller Vorlagen** auf der Symbolleiste des Projektmappen-Explorer.

10. Erstellen der **Dsl** Projekt.

    > [!NOTE]
    >  In dieser Phase werden die anderen Projekte nicht fehlerfrei erstellt. Wir möchten jedoch das Dsl-Projekt erstellen, sodass die Assembly des Datenquellen-Assistenten zur Verfügung steht.

## <a name="updating-the-ui-project"></a>Aktualisieren des UI-Projekts
 Jetzt können Sie ein neues benutzerdefiniertes Steuerelement erstellen, das die Informationen anzeigt, die in der DSL-Modell gespeichert ist. Die einfachste Möglichkeit, das Benutzersteuerelement mit dem Modell herzustellen, erfolgt über datenbindungen. Die Datenbindung mit dem Namen Adaptertyp **ModelingBindingSource** ist speziell zur Verbindung mit nicht VMSDK Schnittstellen konzentriert.

#### <a name="to-define-your-dsl-model-as-a-data-source"></a>DSL-Modell als Datenquelle zu definieren

1.  Auf der **Daten** Menü wählen **Datenquellen anzeigen**.

     Die **Datenquellen** Fenster wird geöffnet.

     Wählen Sie **neue Datenquelle hinzufügen**. Die **Data Source Configuration Wizard** wird geöffnet.

2.  Wählen Sie **Objekt**, **Weiter**.

     Erweitern Sie **Dsl**, **Company.FarmApp**, und wählen Sie **Farm**, also in der Stammklasse des Modells. Klicken Sie auf **Fertig stellen**.

     Im Projektmappen-Explorer die **UI** Projekt enthält jetzt **Properties\DataSources\Farm.datasource**

     Die Eigenschaften und Beziehungen der Modellklasse werden im Fenster "Datenquellen" angezeigt.

     ![DslWpf&#45;3](../modeling/media/dslwpf-3.png "DslWpf-3")

#### <a name="to-connect-your-model-to-a-form"></a>Verbindung von Ihrem Modell zu einem Formular

1.  In der **UI** Projekt, löschen Sie alle vorhandenen .cs-Dateien.

2.  Fügen Sie einen neuen **Benutzersteuerelement** Datei mit dem Namen `FarmControl` auf die **UI** Projekt.

3.  In der **Datenquellen** Fenster auf das Dropdown-Menü auf **Farm**, wählen Sie **Details**.

     Übernehmen Sie die Standardeinstellungen für die anderen Eigenschaften aus.

4.  Öffnen Sie in der Entwurfsansicht FarmControl.cs.

     Ziehen Sie **Farm** aus dem Datenquellenfenster auf FarmControl.

     Ein Satz von Steuerelementen angezeigt wird, eine für jede Eigenschaft. Die Beziehungseigenschaften generieren keine Steuerelemente.

5.  Löschen Sie **FarmBindingNavigator**. Dies wird auch automatisch generiert, der `FarmControl` -Designer, aber es ist nicht für diese Anwendung nützlich.

6.  Verwenden der Toolbox, erstellen Sie zwei Instanzen des **DataGridView**, und nennen Sie diese `AnimalGridView` und `FieldGridView`.

    > [!NOTE]
    >  Ein alternativer Schritt ist, ziehen die Elemente von Tieren und Felder aus dem Fenster "Datenquellen", auf das Steuerelement. Diese Aktion wird automatisch erstellt, Datenblätter und Bindungen zwischen der Rasteransicht und der Datenquelle. Allerdings funktioniert diese Bindung nicht für konzentriert ordnungsgemäß. Daher ist es besser, erstellen Sie die Datenblätter und Bindungen manuell.

7.  Wenn keine die Toolbox enthält die **ModelingBindingSource** -tool, fügen Sie es hinzu. Im Kontextmenü von der **Daten** Registerkarte **Elemente auswählen**. In der **Toolboxelemente** wählen Sie im Dialogfeld **ModelingBindingSource** aus der **Registerkarte ".NET Framework"**.

8.  Verwenden der Toolbox, erstellen Sie zwei Instanzen des **ModelingBindingSource**, und nennen Sie diese `AnimalBinding` und `FieldBinding`.

9. Legen Sie die **DataSource** -Eigenschaft jedes **ModelingBindingSource** auf **FarmBindingSource**.

     Legen Sie die **DataMember** Eigenschaft **Tieren** oder **Felder**.

10. Festlegen der **DataSource** Eigenschaften des `AnimalGridView` auf `AnimalBinding`, und der `FieldGridView` auf `FieldBinding`.

11. Passen Sie das Layout des Steuerelements Ihre Farm ein.

 Die **ModelingBindingSource** ist ein Adapter, die mehrere Funktionen ausführt, die für konzentriert spezifisch sind:

-   Es umschließt eine Speichertransaktion VMSDK Updates.

     Wenn der Benutzer das Datenraster für die Sicht eine Zeile gelöscht, würde z. B. eine reguläre Bindung eine Transaktion Ausnahme führen.

-   Dadurch wird sichergestellt, dass, wenn der Benutzer eine Zeile auswählt, werden im Eigenschaftenfenster die Eigenschaften des entsprechenden Modellelements, statt die Rasterzeile Daten angezeigt.

 ![DslWpf4](../modeling/media/dslwpf4.png "DslWpf4") Schema von Links zwischen Datenquellen und Ansichten.

#### <a name="to-complete-the-bindings-to-the-dsl"></a>Die Bindungen für die DSL abgeschlossen

1.  Fügen Sie den folgenden Code in einer separaten Codedatei in der **UI** Projekt:

    ```csharp
    using System.ComponentModel;
    using Microsoft.VisualStudio.Modeling;
    using Microsoft.VisualStudio.Modeling.Design;

    namespace Company.FarmApp
    {
      partial class FarmControl
      {
        public IContainer Components { get { return components; } }

        /// <summary>Binds the WinForms data source to the DSL model.
        /// </summary>
        /// <param name="nodelRoot">The root element of the model.</param>
        public void DataBind(ModelElement modelRoot)
        {
          WinFormsDataBindingHelper.PreInitializeDataSources(this);
          this.farmBindingSource.DataSource = modelRoot;
          WinFormsDataBindingHelper.InitializeDataSources(this);
        }
      }
    }
    ```

2.  In der **DslPackage** Projekt, bearbeiten **DslPackage\DocView.tt** zum Aktualisieren der Definition der folgenden Variablen:

    ```csharp
    string viewControlTypeName = "FarmControl";
    ```

## <a name="testing-the-dsl"></a>Testen der DSL
 DSL-Lösung kann jetzt erstellen und ausführen, obwohl Sie möglicherweise weitere Verbesserungen später hinzufügen möchten.

#### <a name="to-test-the-dsl"></a>So testen Sie die DSL

1.  Erstellen Sie die Projektmappe, und führen Sie sie aus.

2.  Öffnen Sie in der experimentellen Instanz von Visual Studio, die **Beispiel** Datei.

3.  In der **FarmApp Explorer**, öffnen Sie das Kontextmenü für die **Farm** Stammknoten, und wählen Sie **neue Ziege hinzufügen**.

     `Goat1` wird angezeigt, der **Tieren** anzeigen.

    > [!WARNING]
    >  Verwenden Sie das Kontextmenü, auf die **Farm** Knoten nicht der **Tieren** Knoten.

4.  Wählen Sie die **Farm** Stammknoten und Anzeigen seiner Eigenschaften.

     Ändern Sie in der Formularansicht die **Namen** oder **Größe** der Farm.

     Wenn Sie jedes Feld im Formular die entsprechenden eigenschaftenänderungen im Eigenschaftenfenster verlassen.

## <a name="enhancing-the-dsl"></a>Verbessern der DSL

#### <a name="to-make-the-properties-update-immediately"></a>Zu den Eigenschaften, die sofort zu aktualisieren

1.  Wählen Sie in der Entwurfsansicht von FarmControl.cs einen einfachen Feldverweis z. B. Name, Größe oder IsOrganic.

2.  Erweitern Sie im Fenster Eigenschaften **DataBindings** , und öffnen Sie **(Erweitert)**.

     In der **Formatierung und erweiterte Bindung** Dialogfeld unter **Datenquellen-Aktualisierungsmodus**, wählen Sie **OnPropertyChanged**.

3.  Erstellen Sie die Projektmappe, und führen Sie sie aus.

     Überprüfen Sie, wenn Sie den Inhalt des Felds, der entsprechenden Eigenschaft des der Farm modelländerungen sofort ändern.

#### <a name="to-provide-add-buttons"></a>Zum Hinzufügen von Schaltflächen zur Verfügung stellen

1.  In der Entwurfsansicht von FarmControl.cs mithilfe der Toolbox um eine Schaltfläche im Formular zu erstellen.

     Bearbeiten Sie den Namen und den Text der Schaltfläche, z. B. `New Sheep`.

2.  Öffnen Sie den Code hinter der Schaltfläche (z. B. durch Doppelklick).

     Bearbeiten Sie es wie folgt:

    ```csharp
    private void NewSheepButton_Click(object sender, EventArgs e)
    {
      using (Transaction t = farm.Store.TransactionManager.BeginTransaction("Add sheep"))
      {
        elementOperations.MergeElementGroup(farm,
          new ElementGroup(new Sheep(farm.Partition)));
        t.Commit();
      }
    }

    // The following code is shared with other add buttons:
    private ElementOperations operationsCache = null;
    private ElementOperations elementOperations
    {
      get
      {
        if (operationsCache == null)
        {
          operationsCache = new ElementOperations(farm.Store, farm.Partition);
        }
        return operationsCache;
      }
    }
    private Farm farm
    {
      get { return this.farmBindingSource.DataSource as Farm; }
    }

    ```

     Sie müssen auch die folgende Anweisung einfügen:

    ```csharp

    using Microsoft.VisualStudio.Modeling;

    ```

3.  Fügen Sie ähnliche Ziegen und Felder hinzu.

4.  Erstellen Sie die Projektmappe, und führen Sie sie aus.

5.  Stellen Sie sicher, dass die Schaltfläche "Neu" ein Element hinzufügt. Das neue Element sollte in den FarmApp-Explorer und in der Rasteransicht der Daten angezeigt werden.

     Sie sollten den Namen des Elements in der Rasteransicht der Daten bearbeiten können. Sie können auch dort löschen.

 ![DSL&#45;Wpf&#45;2](../modeling/media/dsl-wpf-2.png "DSL-Wpf-2")

### <a name="about-the-code-to-add-an-element"></a>Über den Code zum Hinzufügen eines Elements
 Für das neue Element Schaltflächen ist der folgende alternative Code etwas einfacher.

```csharp
private void NewSheepButton_Click(object sender, EventArgs e)
{
  using (Transaction t = farm.Store.TransactionManager.BeginTransaction("Add sheep"))
  {
    farm.Animals.Add(new Sheep(farm.Partition)); ;
    t.Commit();
  }
}

```

 Dieser Code ist jedoch kein Standardname für das neue Element festlegen. Er wird nicht ausgeführt, benutzerdefinierten zusammenführen, die Sie möglicherweise im definiert haben die **Element Merge Direktiven** der DSL und er wird nicht ausgeführt, benutzerdefinierten Code, der möglicherweise definiert wurden.

 Daher empfehlen wir die Verwendung von <xref:Microsoft.VisualStudio.Modeling.ElementOperations> Erstellen neuer Elemente. Weitere Informationen finden Sie unter [Element erstellen anpassen und Bewegung](../modeling/customizing-element-creation-and-movement.md).

## <a name="see-also"></a>Siehe auch

- [So definieren Sie eine domänenspezifische Sprache](../modeling/how-to-define-a-domain-specific-language.md)
- [Schreiben von Code zum Anpassen einer domänenspezifischen Sprache](../modeling/writing-code-to-customise-a-domain-specific-language.md)
- [Modellierungs-SDK für Visual Studio - Domänenspezifische Sprachen](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)