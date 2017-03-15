---
title: "Erstellen einer Windows Forms-basierten dom&#228;nenspezifischen Sprache | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 452318ff-8ecf-46d0-8ca0-4013d0cdafaf
caps.latest.revision: 17
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 17
---
# Erstellen einer Windows Forms-basierten dom&#228;nenspezifischen Sprache
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können Windows Forms verwenden, um den Zustand eines DSL\-Modells \(domänenspezifische Sprache\) anzuzeigen, anstatt ein DSL\-Diagramm zu verwenden.  Dieses Thema führt Sie durch das Binden eines Windows Form an eine DSL mithilfe des Visualisierungs\- und Modellierungs\-SDK von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 ![DSL&#45;Wpf&#45;2](../modeling/media/dsl-wpf-2.png "DSL\-Wpf\-2")  
Eine DSL\-Instanz, die eine Windows Form\-Benutzeroberfläche und den Modell\-Explorer anzeigt.  
  
## Erstellen einer Windows Forms\-DSL  
 Die DSL\-Vorlage **Minimaler WinForm\-Designer** erstellt ein minimales DSL, das entsprechend den Benutzeranforderungen geändert werden kann.  
  
#### So erstellen Sie eine minimale WinForms\-DSL  
  
1.  Erstellen Sie ein DSL aus der **Minimalen WinForm\-Designer** Vorlage.  
  
     In dieser exemplarischen Vorgehensweise wird von den folgenden Namen ausgegangen:  
  
    |||  
    |-|-|  
    |Projektmappe und DSL\-Name|FarmApp|  
    |Namespace|Company.FarmApp|  
  
2.  Experimentieren Sie mit dem ursprünglichen Beispiel, das die Vorlage bereitgestellt:  
  
    1.  Transformieren Sie alle Vorlagen.  
  
    2.  Erstellen Sie das Beispiel, und führen Sie es aus. \(**CTRL\+F5**\).  
  
    3.  Öffnen Sie in der experimentellen Instanz von Visual Studio die `Sample`\-Datei im Debugprojekt.  
  
         Beachten Sie, dass sie in einem Windows Forms\-Steuerelement angezeigt wird.  
  
         Sie können auch die Elemente des Modells im Explorer anzeigen.  
  
         Fügen Sie mehrere Elemente entweder im Projektmappen\-Explorer oder im Formular hinzu, und beachten Sie, dass diese in der anderen Anzeige angezeigt werden.  
  
 In der Hauptinstanz von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], sollten Sie die folgenden Punkte bezüglich der DSL\-Projektmappe beachten:  
  
-   `DslDefinition.dsl` Die Gruppe enthält keine Diagrammelemente.  Dies liegt daran, dass Sie keine DSL\-Diagramme verwenden, um Instanzmodelle für dieses DSL anzuzeigen.  Stattdessen binden Sie eine Windows Form an das Modell, und die Elemente in der Form zeigen das Modell an.  
  
-   Zusätzlich zu den `Dsl` und `DslPackage`\-Projekten enthält die Projektmappe ein drittes Projekt mit dem Namen `UI.` **UI**\-Projekt enthält die Definition eines Windows Forms\-Steuerelements.  `DslPackage` hängt von `UI` ab und `UI` hängt von `Dsl` ab.  
  
-   Im `DslPackage`\-Projekt enthält `UI\DocView.cs` den Code, der das Windows Forms\-Steuerelement anzeigt, das im `UI`\-Projekt definiert ist.  
  
-   Das `UI`\-Projekt enthält ein funktionstüchtiges Beispiel eines Formsteuerelements, das an die DSL gebunden ist.  Es funktioniert jedoch nicht, wenn Sie die DSL\-Definition geändert haben.  Das `UI`\-Projekt enthält:  
  
    -   Eine Windows\-Formular\-Klasse mit dem Namen `ModelViewControl`.  
  
    -   Eine Datei mit dem Namen `DataBinding.cs`, die eine weitere partielle Definition von `ModelViewControl` enthält.  Um den Inhalt anzuzeigen, öffnen Sie im **Projektmappen\-Explorer** das Kontextmenü für die Datei, und wählen Sie **Code anzeigen** aus.  
  
### Über das Benutzeroberflächen\-Projekt  
 Wenn Sie die Datei "DSL\-Definitionen" aktualisieren, um ein eigenes DSL zu definieren, müssen Sie das Steuerelement im `UI`\-Projekt aktualisieren, um die DSL anzuzeigen.  Im Gegensatz zum `Dsl`\- und `DslPackage`\-Projekte wird das `UI`\-Beispielprojekt nicht aus `DslDefinitionl.dsl` generiert.  Sie können .tt\-Dateien hinzufügen, um den Code zu generieren, wenn Sie diese möchten, obwohl das in dieser exemplarischen Vorgehensweise nicht abgedeckt wird.  
  
## Die DSL\-Definition aktualisieren  
 Die folgende DSL\-Definition wird in dieser Komplettlösung verwendet.  
  
 ![DSL&#45;Wpf&#45;1](../modeling/media/dsl-wpf-1.png "DSL\-Wpf\-1")  
  
#### So aktualisieren Sie die DSL\-Definition  
  
1.  Öffnen Sie DslDefinition.dsl im DSL\-Designer.  
  
2.  **ExampleElement** löschen  
  
3.  Benennen Sie die **ExampleModel** Domänenklasse zu `Farm` um.  
  
     Geben Sie ihm die zusätzlichen Domäneneigenschaften mit Namen `Size` des Typs **Int32**und `IsOrganic` des Typs **Boolean**.  
  
    > [!NOTE]
    >  Wenn Sie die Stammdomänen\-Klasse löschen und dann einen neuen Stamm erstellen, müssen Sie die Editor Root Class\-Eigenschaft zurücksetzen.  In **DSL\-Explorer** wählen Sie **Editor** aus.  Anschließend legen Sie die **Stammklasse** im Eigenschaftenfenster auf `Farm` fest.  
  
4.  Verwenden Sie das Tool **Benannte Domänenklasse**, um die folgenden Domänenklassen zu erstellen:  
  
    -   `Feld` – Geben Sie diesem eine zusätzliche Domäneneigenschaft, die als `Größe` benannt ist.  
  
    -   `Animal` – Legen Sie im Eigenschaftenfenster **Inheritance Modifier** auf **Abstract** fest.  
  
5.  Verwenden Sie das Tool **Domain Class**, um die folgenden Klassen zu erstellen:  
  
    -   `Schafe`  
  
    -   `Ziege`  
  
6.  Verwenden Sie das Tool **Vererbung**, um `Goat` und `Sheep` von `Tier` zu erben.  
  
7.  Verwenden Sie das Tool **Einbetten**, um `Field` und `Animal` unter `Farm` einzubetten.  
  
8.  Sie sollten das Diagramm aufräumen.  Um die Anzahl von doppelten Elemente zu reduzieren, verwenden Sie den Befehl **Teilstruktur hierher** im Kontextmenü von Endelementen.  
  
9. **Alle Vorlagen transformieren** in der Werkzeugleiste des Projektmappen\-Explorer.  
  
10. Erstellen Sie das **Dsl** Projekt  
  
    > [!NOTE]
    >  In dieser Phase werden die anderen Projekte nicht ohne Fehler erstellt.  Allerdings soll das DSL\-Projekt so erstellt werden, dass die Assembly für den Datenquellenassistenten verfügbar ist.  
  
## UI\-Projektupdate  
 Jetzt können Sie ein neues Benutzersteuerelement erstellen, das die Informationen, die im DSL\-Modell gespeichert sind, anzeigt.  Die einfachste Vorgehensweise, die Benutzersteuerung mit dem Modell zu verbinden, ist durch Datenbindungen.  Der Datenbindungs\-Adaptertyp mit dem Namen **ModelingBindingSource** wurde speziell konzipiert, um DSLs mit Nicht\-VMSDK\-Schnittstellen zu verbinden.  
  
#### So definieren Sie das DSL\-Modell als Datenquelle  
  
1.  Wählen Sie im Menü **Daten** die Option **Datenquellen anzeigen** aus.  
  
     Das Fenster **Datenquellen** wird geöffnet.  
  
     Wählen Sie **Neue Datenquelle hinzufügen** aus  Der **Assistent zum Konfigurieren von Datenquellen** wird geöffnet.  
  
2.  Wählen Sie **Objekt**, **Weiter** aus.  
  
     Erweitern Sie **Dsl**, **Company.FarmApp** und wählen Sie **Farm** aus. Das ist die Stammklasse des Modells.  Wählen Sie **Fertig stellen** aus.  
  
     Im Projektmappen\-Explorer enthält das **UI**\-Projekt jetzt **Properties\\DataSources\\Farm.datasource**  
  
     Die Eigenschaften und Beziehungen Ihrer Modellklasse werden im Datenquellenfenster angezeigt.  
  
     ![DslWpf&#45;3](../modeling/media/dslwpf-3.png "DslWpf\-3")  
  
#### So verbinden Sie das Modell mit einem Formular  
  
1.  Löschen Sie im **UI**\-Projekt alle vorhandenen .cs\-Dateien.  
  
2.  Fügen Sie dem **UI**\-Projekt eine neue **Benutzersteuerelement** Datei mit Namen `FarmControl` hinzu.  
  
3.  Klicken Sie im Fenster **Datenquellen** im Dropdownmenü auf **Farm** und wählen Sie **Details** aus.  
  
     Standardeinstellungen für die anderen Eigenschaften beibehalten.  
  
4.  Öffnen Sie FarmControl.cs in der Entwurfsansicht.  
  
     Ziehen Sie **Farm** aus dem Tabelle aus dem Datenquellenfenster auf FarmControl.  
  
     Ein Satz von Steuerelementen wird angezeigt, einer für jede Eigenschaft.  Die Beziehungseigenschaften generieren keine Steuerelemente.  
  
5.  **farmBindingNavigator** löschen.  Dies wird ebenfalls automatisch im `FarmControl`\-Designer generiert, ist jedoch für diese Anwendung nicht hilfreich.  
  
6.  Unter Verwenden der Toolbox erstellen Sie zwei Instanzen von **DataGridView**, und benennen Sie sie `AnimalGridView` und `FieldGridView`.  
  
    > [!NOTE]
    >  Ein alternativer Schritt besteht darin, die Tier\-Feldelemente aus dem Datenquellenfenster auf das Steuerelement zu ziehen.  Diese Aktion stellt automatisch Datenraster und Bindungen zwischen dem Raster und der Datenquelle her.  Diese Bindung funktioniert jedoch nicht ordnungsgemäß für DSLs.  Daher empfiehlt es sich, die Datenraster und Bindungen manuell zu erstellen.  
  
7.  Wenn die Toolbox das **ModelingBindingSource** Tool nicht enthält, fügen Sie es hinzu.  Wählen Sie im Kontextmenü auf der Registerkarte **Daten Elemente auswählen** aus.  Wählen Sie im Dialogfeld **Toolboxelemente auswählen** die Option **ModelingBindingSource** auf der Registerkarte **.NET Framework** aus.  
  
8.  Unter Verwenden der Toolbox erstellen Sie zwei Instanzen von **ModelingBindingSource**, und benennen Sie sie `AnimalBinding` und `FieldBinding`.  
  
9. Legen Sie die **DataSource**\-Eigenschaft der einzelnen **ModelingBindingSource**\-Elemente auf **farmBindingSource** fest.  
  
     Legen Sie die **DataMember**\-Eigenschaft auf **Tiere** oder **Felder** fest.  
  
10. Legen Sie die **DataSource**\-Eigenschaften unter `AnimalGridView` auf `AnimalBinding` und unter `FieldGridView` auf `FieldBinding` fest.  
  
11. Passen Sie das Layout des Steuerelements der Farm nach Ihrem Geschmack an.  
  
 **ModelingBindingSource** ist ein Adapter, der mehrere DSL\-spezifische Aufgaben ausführt:  
  
-   Er umschließt Updates in einer VMSDK\-Speicher\-Transaktion.  
  
     Wenn der Benutzer beispielsweise eine Zeile im Datenansichtsraster löscht, würde eine reguläre Bindung zu einer Transaktiosausnahme führen.  
  
-   Es stellt sicher, dass, wenn der Benutzer eine Zeile auswählt, das Eigenschaftenfenster die Eigenschaften des entsprechenden Modellelements anstelle der Datenrasterzeile anzeigt.  
  
 ![DslWpf4](../modeling/media/dslwpf4.png "DslWpf4")  
Schema von Links zwischen Datenquellen und Ansichten.  
  
#### So stellen Sie die DSL\-Bindungen her  
  
1.  Fügen Sie den folgenden Code in einer separaten Codedatei im **UI** Projekt hinzu:  
  
    ```c#  
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
  
2.  Im **DslPackage**\-Projekt bearbeiten Sie **DslPackage\\DocView.tt**, um die folgende Variablendefinition zu aktualisieren:  
  
    ```c#  
    string viewControlTypeName = "FarmControl";  
    ```  
  
## Testen von DSL  
 Die DSL\-Projektmappe kann jetzt entstehen und laufen, obwohl Sie später vielleicht weitere Verbesserungen hinzufügen möchten.  
  
#### So testen Sie die DSL  
  
1.  Erstellen Sie die Projektmappe, und führen Sie sie aus  
  
2.  Öffnen Sie in der experimentellen Instanz von Visual Studio Sie die Datei **Beispiel**.  
  
3.  In **FarmApp\-Explorer** öffnen Sie das Kontextmenü im **Farm**\-Stammknoten, und wählen Sie **Neue Ziege hinzufügen** aus.  
  
     `Goat1` wird in der **Tiere** Ansicht angezeigt.  
  
    > [!WARNING]
    >  Sie müssen das Kontextmenü im **Farm**\-Knoten verwenden, nicht im **Animals**\-Knoten verwenden.  
  
4.  Wählen Sie den Stammknoten **Farm** aus, und zeigen Sie seine Eigenschaften an.  
  
     Ändern Sie in der Formularansicht **Name** oder **Größe** der Farm.  
  
     Wenn Sie von den einzelnen Feldern im Formular navigieren, wird die entsprechende Eigenschaft im Eigenschaftenfenster geändert.  
  
## Verbessern des DSL  
  
#### So legen Sie ein sofortiges Update der Eigenschaften fest  
  
1.  Wählen Sie in der Entwurfsansicht von FarmControl.cs ein einfaches Feld wie Name, Größe oder IsOrganic aus.  
  
2.  Erweitern Sie im Eigenschaftenfenster **DataBindings**, und öffnen Sie **\(Erweitert\)**.  
  
     Im Dialogfeld **Formatierung und erweiterte Bindung** unter **Datenquellen\-Aktualisierungsmodus** wählen Sie **OnPropertyChanged** aus.  
  
3.  Erstellen Sie die Projektmappe, und führen Sie sie aus  
  
     Stellen Sie sicher, dass, wenn Sie den Inhalt des Felds geändert haben, die zugehörige Eigenschaft des Farmmodells ebenfalls sofort geändert wird.  
  
#### So stellen Sie Schaltflächen zum Hinzufügen bereit  
  
1.  Verwenden Sie in der Entwurfsansicht von FarmControl.cs die Toolbox, um eine Schaltfläche auf dem Formular zu erstellen.  
  
     Bearbeiten Sie den Namen und den Text der Schaltfläche z.B. zu `Neue Schafe`.  
  
2.  Öffnen Sie den Code hinter der Schaltfläche \(z. B. durch Doppelklicken auf diese\).  
  
     Bearbeiten Sie sie wie folgt:  
  
    ```c#  
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
  
     Außerdem müssen Sie die folgenden Direktiven einfügen:  
  
    ```c#  
  
    using Microsoft.VisualStudio.Modeling;  
  
    ```  
  
3.  Fügen Sie ähnliche Schaltflächen für Ziegen und Felder hinzu.  
  
4.  Erstellen Sie die Projektmappe, und führen Sie sie aus  
  
5.  Überprüfen Sie, ob die neue Schaltfläche ein Element hinzufügt.  Das neue Element wird sowohl im FarmApp\-Explorer als auch in der Datenrasteransicht angezeigt.  
  
     Sie sollten in der Lage sein, den Namen des Elements in der Ansicht Datenraster zu bearbeiten.  Sie können es auch hier löschen.  
  
 ![DSL&#45;Wpf&#45;2](../modeling/media/dsl-wpf-2.png "DSL\-Wpf\-2")  
  
### Über den Code zum Hinzufügen eines Elements  
 Für die neuen Element\-Schaltflächen ist der folgenden alternative Code etwas einfacher.  
  
```c#  
private void NewSheepButton_Click(object sender, EventArgs e)  
{  
  using (Transaction t = farm.Store.TransactionManager.BeginTransaction("Add sheep"))  
  {  
    farm.Animals.Add(new Sheep(farm.Partition)); ;  
    t.Commit();  
  }  
}  
  
```  
  
 Allerdings legt dieser Code keinen Standardnamen für das neue Element fest.  Es führt keine benutzerdefinierte Zusammenführung aus, die Sie möglicherweise in den **Elementzusammenführungsdirektiven** der DSL definiert haben, und auch keinen benutzerdefinierten Zusammenführungscode, der möglicherweise definiert wurde.  
  
 Daher wird empfohlen, <xref:Microsoft.VisualStudio.Modeling.ElementOperations> zu verwenden, um neue Elemente zu erstellen.  Weitere Informationen finden Sie unter [Anpassen der Elementerstellung und \-verschiebung](../modeling/customizing-element-creation-and-movement.md).  
  
## Siehe auch  
 [So definieren Sie eine domänenspezifische Sprache](../modeling/how-to-define-a-domain-specific-language.md)   
 [Schreiben von Code zum Anpassen einer domänenspezifischen Sprache](../modeling/writing-code-to-customise-a-domain-specific-language.md)   
 [Modeling SDK für Visual Studio \- domänenspezifische Sprachen](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)