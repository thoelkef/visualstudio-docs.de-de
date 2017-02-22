---
title: "Integrieren von Modellen mit Visual Studio-Modelbus | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2ff722f3-21d6-44e2-9efd-f6694aee9987
caps.latest.revision: 26
caps.handback.revision: 26
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Integrieren von Modellen mit Visual Studio-Modelbus
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus stellt eine Methode zum Erstellen von Links zwischen Modellen und von anderen Tools in Modellen. Sie können z. B. domänenspezifische Sprache \(DSL\) Modelle und UML\-Modellen verknüpfen. Sie können einen integrierten Satz von DSLs erstellen.  
  
 ModelBus können Sie einen eindeutigen Verweis auf ein Modell oder für ein bestimmtes Element in einem Modell zu erstellen. Dieser Verweis kann außerhalb des Modells, z. B. in einem Element in einem anderen Modell gespeichert werden. Beim späteren Gelegenheit, ein Tool erhalten Zugriff auf das Element möchte, die Model Bus\-Infrastruktur lädt das entsprechende Modell und das Element zurück. Wenn Sie möchten, können Sie das Modell für den Benutzer anzeigen. Wenn die Datei in den vorherigen Zustand zugegriffen werden kann, fragt ModelBus den Benutzer zu finden. Wenn der Benutzer die Datei findet, repariert ModelBus alle Verweise auf die Datei.  
  
> [!NOTE]
>  In der aktuellen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] \-Implementierung von ModelBus müssen die verknüpften Modelle muss Elemente in der gleichen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Lösung.  
  
 Weitere Informationen und Beispielcode finden Sie unter:  
  
-   [Gewusst wie: Hinzufügen eines Drag & Drop\-Handlers](../modeling/how-to-add-a-drag-and-drop-handler.md)  
  
-   [Modeling SDK für Visual Studio](http://www.microsoft.com/download/details.aspx?id=40754)  
  
##  <a name="provide"></a> Gewähren des Zugriffs auf eine DSL  
 Bevor Sie ModelBus\-Verweise auf ein Modell oder dessen Elemente erstellen können, müssen Sie einen ModelBusAdapter für die DSL definieren. Die einfachste Möglichkeit hierzu ist die Verwendung der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] \-Modellbuserweiterung, die dem DSL\-Designer Befehle hinzugefügt.  
  
###  <a name="expose"></a> Eine DSL\-Definition dem Modellbus verfügbar machen.  
  
1.  Herunterladen Sie und installieren Sie die Visual Studio\-ModelBus\-Erweiterung, wenn es bereits installiert haben. Weitere Informationen finden Sie unter [Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=185579).  
  
2.  Öffnen Sie die DSL\-Definitionsdatei. Mit der rechten Maustaste in der Entwurfsoberfläche, und klicken Sie dann auf **Modelbus aktivieren**.  
  
3.  Wählen Sie im Dialogfeld **ich diese DSL für ModelBus verfügbar machen möchten**. Wenn Sie diese DSL Modelle verfügbar machen und Verweise auf andere DSLs nutzen möchten, können Sie beide Optionen auswählen.  
  
4.  Klicken Sie auf **OK**. Der DSL\-Projektmappe wird ein neues Projekt "ModelBusAdapter" hinzugefügt.  
  
5.  Wenn Sie die DSL in einer Textvorlage zugreifen möchten, müssen Sie "adaptermanager.tt" im neuen Projekt ändern. Überspringen Sie diesen Schritt, wenn Sie die DSL von anderem Code wie Befehlen und Ereignishandler zugreifen möchten. Weitere Informationen finden Sie unter [Verwenden von Visual Studio\-ModelBus in einer Textvorlage](../modeling/using-visual-studio-modelbus-in-a-text-template.md).  
  
    1.  Ändern Sie die Basisklasse von AdapterManagerBase in <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager>.  
  
    2.  Fügen Sie am Ende der Datei dieses zusätzliche Attribut vor der AdapterManager\-Klasse:  
  
         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`  
  
    3.  Fügen Sie in den Verweisen des ModelBusAdapter\-Projekt **Microsoft.VisualStudio.TextTemplating.Modeling.11.0**.  
  
     Wenn Sie die DSL über Textvorlagen sowohl von anderem Code zugreifen möchten, benötigen Sie zwei Adapter, geändert und unverändert.  
  
6.  Klicken Sie auf **Alle Vorlagen transformieren**.  
  
7.  Generieren Sie die Projektmappe neu.  
  
 Es ist jetzt kann ModelBus Instanzen dieser DSL öffnen.  
  
 Der Ordner `ModelBusAdapters\bin\*` enthält die Assemblys erstellt, indem die `Dsl` Projekt und die `ModelBusAdapters` Projekt. Um diese DSL von einer anderen DSL zu verweisen, sollten Sie diese Assemblys importieren.  
  
### Sicherstellen, dass Elemente verwiesen werden kann  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus\-Adapter verwenden Sie die Guid eines Elements, in der Standardeinstellung identifiziert. Diese Bezeichner müssen daher in der Modelldatei beibehalten werden.  
  
##### Um sicherzustellen, dass dieses Element\-IDs erhalten bleiben  
  
1.  Öffnen Sie "DslDefinition.DSL".  
  
2.  Erweitern Sie im DSL\-Explorer **XML\-Serialisierungsverhalten**, dann **Klassendaten**.  
  
3.  Für jede Klasse, die Sie Modellbusverweise erstellen möchten verweist:  
  
     Klicken Sie auf den Klassenknoten, und stellen Sie im Fenster Eigenschaften sicher, dass **Id Serialisieren** Wert `true`.  
  
 Wenn Sie die Elementnamen zum Identifizieren von Elementen statt Guids verwenden möchten, können Sie Teile der generierten Adapter überschreiben. Überschreiben Sie die folgenden Methoden in der Klasse für den Adapter:  
  
-   Überschreiben Sie `GetElementId` die ID zurückgeben soll. Diese Methode wird aufgerufen, wenn Verweise erstellt werden.  
  
-   Überschreiben Sie `ResolveElementReference` das richtige Element aus einem Modellbusverweis zu finden.  
  
##  <a name="editRef"></a> Zugreifen auf eine DSL von einer anderen DSL  
 Sie können modellbusverweise in einer Domäneneigenschaft in einer DSL speichern, und Sie benutzerdefinierten Code schreiben, der sie verwendet. Sie können auch den Benutzer einen modellbusverweis zu erstellen, indem Sie eine Modelldatei und ein Element darin auswählen lassen.  
  
 Um eine DSL Verweise auf eine andere DSL verwenden aktivieren, sollte zunächst sollten Sie einen *Consumer* von modellbusverweisen.  
  
#### So aktivieren Sie eine DSL Verweise auf eine verfügbar gemachte DSL nutzen  
  
1.  In der DSL\-Definitionsdiagramm mit der rechten Maustaste in den Hauptteil des Diagramms, und klicken Sie dann auf **Modelbus aktivieren**.  
  
2.  Wählen Sie im Dialogfeld **dieses Modells modellbusverweise aktivieren**.  
  
3.  Fügen Sie im Dsl\-Projekt der Consumer\-DSL den Projektverweisen die folgenden Assemblys hinzu. Sie finden diese Assemblys \(DLL\-Dateien\) in das Verzeichnis ModelBusAdapter\\bin\\ \* des verfügbar gemachten DSL.  
  
    -   Die verfügbar gemachten DSL\-Assembly, z. B. **Fabrikam.FamilyTree.Dsl.dll**  
  
    -   Der verfügbar gemachten Model bus Adapterassembly, z. B. **Fabrikam.FamilyTree.ModelBusAdapter.dll**  
  
4.  Die folgenden .NET Assemblys den Projektverweisen des Consumer\-DSL\-Projekt hinzufügen.  
  
    1.  **Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0.dll**  
  
    2.  **Microsoft.VisualStudio.Modeling.Sdk.Integration.Shell.11.0.dll**  
  
#### Um einen Modellbusverweis in einer Domäneneigenschaft speichern  
  
1.  Klicken Sie in der DSL\-Definition der Consumer\-DSL eine Domänenklasse eine Domäneneigenschaft hinzu, und legen Sie dessen Namen.  
  
2.  Fenster mit der Eigenschaft "Domain" ausgewählt haben, legen Sie im Eigenschaftenfenster **Typ** auf `ModelBusReference`.  
  
 In dieser Phase Programmcode kann den Wert der Eigenschaft festgelegt, aber es im Eigenschaftenfenster schreibgeschützt ist.  
  
 Sie können Benutzer die Eigenschaft mit einem speziellen ModelBus\-Verweis\-Editor festlegen können. Es gibt zwei Versionen dieses Editors oder *Datumsauswahl:* ermöglicht Benutzern, eine Modelldatei auszuwählen, und der andere Benutzer eine Modelldatei und ein Element innerhalb des Modells auswählen kann.  
  
#### Ermöglicht den Benutzer, einen Modellbusverweis in einer Domäneneigenschaft festzulegen  
  
1.  Die Eigenschaft "Domain" und dann auf **Bearbeiten ModelBusReference\-spezifische Eigenschaften**. Ein Dialogfeld wird geöffnet. Dies ist die *Modellbusauswahl*.  
  
2.  Wählen Sie die entsprechenden **Art von ModelBusReference**: ein Modell oder ein Element in einem Modell.  
  
3.  Geben Sie in der Datei die Filterzeichenfolge eine Zeichenfolge ein, z. B. `Family Tree files |*.ftree`. Ersetzen Sie durch die Erweiterung der verfügbar gemachten DSL.  
  
4.  Wenn Sie ein Element in einem Modell verweisen möchten, können Sie eine Liste von Typen, die der Benutzer auswählen kann, beispielsweise "Company.FamilyTree.Person" hinzufügen.  
  
5.  Klicken Sie auf **OK**, und klicken Sie dann auf **Alle Vorlagen transformieren** in der Symbolleiste des Projektmappen\-Explorers.  
  
    > [!WARNING]
    >  Wenn Sie ein gültiges Modell oder eine Entität nicht ausgewählt haben, wird die Schaltfläche "OK", wirkungslos, obwohl er möglicherweise als aktiviert angezeigt.  
  
6.  Wenn Sie eine Liste von Zieltypen wie "Company.FamilyTree.Person" angegeben haben, müssen Sie dann Sie einen Assemblyverweis auf das DSL\-Projekt hinzufügen verweisen auf die DLL der Ziel\-DSL, beispielsweise "Company.FamilyTree.DSL.dll"  
  
#### So testen Sie einen Modellbusverweis  
  
1.  Erstellen Sie die verfügbar gemachten und Nutzung DSLs.  
  
2.  Führen Sie eine der DSLs im experimentellen Modus durch Drücken von F5 oder STRG \+ F5.  
  
3.  In den Debugging\-Projekt in der experimentellen Instanz von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], Hinzufügen von Dateien, die Instanzen der beiden DSLS sind.  
  
    > [!NOTE]
    >  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus kann nur Verweise auf Modelle, die Elemente in der gleichen auflösen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Lösung. Sie können nicht zum Beispiel einen Verweis auf eine Modelldatei in einem anderen Teil des Dateisystems erstellen.  
  
4.  Erstellen Sie einige Elemente und Links in der Instanz von verfügbar gemachten DSL, und speichern Sie es.  
  
5.  Öffnen Sie eine Instanz der Consumer\-DSL, und wählen Sie ein Modellelement, das eine Eigenschaft für einen modellbusverweis verfügt.  
  
6.  Doppelklicken Sie im Eigenschaftenfenster auf die Eigenschaft für einen modellbusverweis. Das Auswahldialogfeld wird geöffnet.  
  
7.  Klicken Sie auf **Durchsuchen** und wählen Sie die Instanz des verfügbar gemachten DSL.  
  
     Die Auswahl auch können ein Element im Modell auswählen, wenn Sie die elementspezifischen modellbusverweis angegeben.  
  
## Erstellen von Verweisen im Programmcode  
 Wenn Sie einen Verweis auf ein Modell oder ein Element in einem Modell speichern möchten, erstellen Sie eine `ModelBusReference`. Es gibt zwei Arten von `ModelBusReference`: Modellverweise und Elementverweise.  
  
 Um einen Modellverweis zu erstellen, benötigen Sie den AdapterManager der DSL, von denen das Modell eine Instanz und den Dateinamen ist, oder [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Projektelement des Modells.  
  
 Zum Erstellen eines Elementverweises benötigen Sie einen Adapter für die Modelldatei und das Element, dem Sie verweisen möchten.  
  
> [!NOTE]
>  Mit der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus, können nur Verweise auf Elemente in der gleichen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Lösung.  
  
### Importieren Sie die verfügbar gemachten DSL\-Assemblys  
 Fügen Sie in das betreffende Projekt Projektverweise auf die DSL und die ModelBusAdapter\-Assemblys der verfügbar gemachten DSL.  
  
 Nehmen wir beispielsweise an, dass Sie ModelBus\-Verweise in Elementen einer MusicLibrary\-DSL speichern möchten. Die ModelBus\-Verweise verweisen auf Elemente der FamilyTree\-DSL. In der `Dsl` MusicLibrary\-Projektmappe im Knoten "Verweise", Projekt fügen Sie Verweise auf die folgenden Assemblys:  
  
-   Fabrikam.FamilyTree.Dsl.dll – die verfügbar gemachten DSL.  
  
-   Fabrikam.FamilyTree.ModelBusAdapters.dll – der ModelBus\-Adapter der verfügbar gemachten DSL.  
  
-   Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0  
  
-   Microsoft.VisualStudio.Modeling.Sdk.Integration.Shell.11.0  
  
 Diese Assemblys befinden sich die `ModelBusAdapters` \-Projekt mit der verfügbar gemachten DSL unter `bin\*`.  
  
 In der Codedatei, in denen Sie Verweise erstellen, müssen Sie in der Regel die Namespaces zu importieren:  
  
```  
// The namespace of the DSL you want to reference:  
using Fabrikam.FamilyTree;  // Exposed DSL  
using Fabrikam.FamilyTree.ModelBusAdapters;  
using Microsoft.VisualStudio.Modeling.Integration;  
using System.Linq;  
...  
```  
  
### Um einen Verweis auf ein Modell zu erstellen.  
 Um einen Modellverweis zu erstellen, Zugriff auf den AdapterManager der verfügbar gemachten DSL, und verwenden, um einen Verweis auf das Modell zu erstellen. Sie können entweder einen Dateipfad angeben oder ein `EnvDTE.ProjectItem`.  
  
 Vom AdapterManager erhalten Sie einen Adapter bietet Zugriff auf einzelne Elemente im Modell.  
  
> [!NOTE]
>  Sie müssen einen Adapter löschen, wenn Sie damit fertig sind. Die einfachste Möglichkeit, dies zu erreichen, bietet eine `using` Anweisung. Dies wird anhand des folgenden Beispiels veranschaulicht.  
  
```  
// The file path of a model instance of the FamilyTree DSL:  
string targetModelFile = "TudorFamilyTree.ftree";  
// Get the ModelBus service:  
IModelBus modelBus =   
    this.Store.GetService(typeof(SModelBus)) as IModelBus;  
// Get an adapterManager for the target DSL:  
FamilyTreeAdapterManager manager =   
    (modelbus.GetAdapterManager(FamilyTreeAdapter.AdapterId)   
     as FamilyTreeAdapterManager;  
// or: (modelBus.FindAdapterManagers(targetModelFile).First())  
// or could provide an EnvDTE.ProjectItem  
  
// Create a reference to the target model:  
// NOTE: the target model must be a file in this project.  
ModelBusReference modelReference =  
     manager.CreateReference(targetModelFile);  
// or can use an EnvDTE.ProjectItem instead of the filename  
  
// Get the root element of this model:  
using (FamilyTreeAdapter adapter =   
     modelBus.CreateAdapter(modelReference) as FamilyTreeAdapter)  
{  
  FamilyTree modelRoot = adapter.ModelRoot;  
  // Access elements under the root in the usual way:  
  foreach (Person p in modelRoot.Persons) {...}  
  // You can create adapters for individual elements:  
  ModelBusReference elementReference =  
     adapter.GetElementReference(person);  
  ...  
} // Dispose adapter  
  
```  
  
 Wenn Sie verwenden möchten `modelReference` später können Sie sie speichern in einer Domäneneigenschaft mit dem externen Datentyp `ModelBusReference`:  
  
```  
using Transaction t = this.Store.TransactionManager  
    .BeginTransaction("keep reference"))  
{  
  artist.FamilyTreeReference = modelReference;  
  t.Commit();  
}  
```  
  
 Damit Benutzer diese Domäneneigenschaft bearbeiten können, verwenden Sie `ModelReferenceEditor` als Parameter im Editor\-Attribut. Weitere Informationen finden Sie unter [kann der Benutzer die Bearbeitung eines Verweises](#editRef).  
  
### Um einen Verweis auf ein Element erstellen  
 Der Adapter, den Sie für das Modell erstellt kann verwendet werden, erstellen und Auflösen von verweisen.  
  
```  
// person is an element in the FamilyTree model:  
ModelBusReference personReference =   
  adapter.GetElementReference(person);  
```  
  
 Wenn Sie verwenden möchten `elementReference` später können Sie sie speichern in einer Domäneneigenschaft mit dem externen Datentyp `ModelBusReference`. Damit Benutzer ihn bearbeiten können, verwenden `ModelElementReferenceEditor` als Parameter im Editor\-Attribut. Weitere Informationen finden Sie unter [kann der Benutzer die Bearbeitung eines Verweises](#editRef).  
  
### Auflösen von verweisen  
 Wenn Sie haben eine `ModelBusReference` \(MBR\) erhalten Sie das Modell oder das Modellelement aus, auf die sie verweist. Wenn das Element im Diagramm oder einer anderen Ansicht angezeigt wird, können Sie die Ansicht öffnen und wählen Sie das Element.  
  
 Sie können einen Adapter mit einem MBR erstellen. Vom Adapter können Sie den Stamm des Modells abrufen. Sie können auch MBR beheben, die auf bestimmte Elemente innerhalb des Modells verweisen.  
  
```  
using Microsoft.VisualStudio.Modeling.Integration; ...  
ModelBusReference elementReference = ...;  
  
// Get the ModelBus service:  
IModelBus modelBus =   
    this.Store.GetService(typeof(SModelBus)) as IModelBus;  
// Use a model reference or an element reference  
// to obtain an adapter for the target model:  
using (FamilyTreeAdapter adapter =   
   modelBus.CreateAdapter(elementReference) as FamilyTreeAdapter)  
   // or CreateAdapter(modelReference)  
{  
  // Get the root of the model:  
  FamilyTree tree = adapter.ModelRoot;  
  
  // Get a model element:  
  MyDomainClass mel =  
    adapter.ResolveElementReference<MyDomainClass>(elementReference);  
  if (mel != null) {...}  
  
  // Get the diagram or other view, if there is one:  
  ModelBusView view = adapter.GetDefaultView();  
  if (view != null)   
  {  
   view.Open();  
   // Display the diagram:  
   view.Show();   
   // Attempt to select the shape that presents the element:  
   view.SetSelection(elementReference);  
  }  
} // Dispose the adapter.  
```  
  
##### Zum Auflösen von ModelBus\-Verweise in einer Textvorlage  
  
1.  Die DSL, die Sie zugreifen möchten, benötigen einen ModelBus\-Adapter, die für den Zugriff durch Textvorlagen konfiguriert wurde. Weitere Informationen finden Sie unter [Gewähren des Zugriffs auf eine DSL](#provide).  
  
2.  In der Regel wird ein Ziel der Zugriff auf die DSL mit \(Model Bus Reference, MBR\) in einer Quell\-DSL gespeichert. Die Vorlage enthält deshalb die Direktive der Quell\-DSL sowie Code zur MBR\-Auflösung. Weitere Informationen zu Textvorlagen finden Sie unter [Generieren von Code für eine domänenspezifische Sprache](../modeling/generating-code-from-a-domain-specific-language.md).  
  
    ```  
    <#@ template debug="true" hostspecific="true"   
    inherits="Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation" #>   
    <#@ SourceDsl processor="SourceDslDirectiveProcessor" requires="fileName='Sample.source'" #>  
    <#@ output extension=".txt" #>  
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0" #>  
    <#@ assembly name = "System.Core" #>  
    <#@ assembly name = "Company.CompartmentDragDrop.Dsl.dll" #>  
    <#@ assembly name = "Company.CompartmentDragDrop.ModelBusAdapter.dll" #>  
    <#@ import namespace="Microsoft.VisualStudio.Modeling.Integration" #>  
    <#@ import namespace="System.Linq" #>  
    <#@ import namespace="Company.CompartmentDragDrop" #>  
    <#@ import namespace="Company.CompartmentDragDrop.ModelBusAdapters" #>  
    <# // Get source root from directive processor:  
      ExampleModel source = this.ExampleModel;   
      // This DSL has a MBR in its root:  
    using (ModelBusAdapter adapter = this.ModelBus.CreateAdapter(source.ModelReference) as ModelBusAdapter)   
      {  
      ModelBusAdapterManager manager = this.ModelBus.FindAdapterManagers(this.Host.ResolvePath("Sample.compDD1")).FirstOrDefault();  
      ModelBusReference modelReference =  
        manager.CreateReference(this.Host.ResolvePath("Sample.compDD1"));  
  
      // Get the root element of this model:  
      using (CompartmentDragDropAdapter adapter =   
         this.ModelBus.CreateAdapter(modelReference) as CompartmentDragDropAdapter)  
      {  
        ModelRoot root = adapter.ModelRoot;  
    #>  
    [[<#= root.Name #>]]  
    <#  
      }  
    #>  
  
    ```  
  
 Weitere Informationen und eine exemplarische Vorgehensweise finden Sie unter [Verwenden von Visual Studio\-ModelBus in einer Textvorlage](../modeling/using-visual-studio-modelbus-in-a-text-template.md)  
  
## Serialisieren eines ModelBusReference  
 Wenn Sie speichern möchten eine `ModelBusReference` \(MBR\) in Form einer Zeichenfolge, können Sie ihn serialisieren:  
  
```  
string serialized = modelBus.SerializeReference(elementReference);  
// Store it anywhere, then get it back again:  
ModelBusReference elementReferenceRestored =  
    modelBus.DeserializeReference(serialized, null);  
```  
  
 Ein MBR, die auf diese Weise serialisiert werden ist unabhängig vom Kontext. Wenn Sie den einfachen dateibasierten Modellbusadapter verwenden, enthält der MBR einen absoluten Dateipfad. Dies ist ausreichend, wenn die Instanz instanzmodelldateien nicht verschoben werden. Die Model\-Dateien werden jedoch in der Regel Elemente in einem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Projekt. Die Benutzer werden erwarten, dass das gesamte Projekt in verschiedene Teile des Dateisystems verschieben können. Sie werden auch erwarten, dass in der Lage, behalten Sie das Projekt unter Versionskontrolle und auf verschiedenen Computern zu öffnen. Pfadnamen sollten daher relativ zum Speicherort des Projekts serialisiert werden, die die Dateien enthält.  
  
### Serialisieren relativ zum angegebenen Dateipfad  
 Ein `ModelBusReference` enthält eine `ReferenceContext`, ein Wörterbuch, in dem Sie Informationen wie der Dateipfad relativ zu dem er serialisiert werden speichern können.  
  
 Serialisieren Sie relativ zu einem Pfad:  
  
```  
elementReference.ReferenceContext.Add(  
   ModelBusReferencePropertySerializer.FilePathSaveContextKey,   
   currentProjectFilePath);  
string serialized = modelBus.SerializeReference(elementReference);  
```  
  
 Um den Verweis aus der Zeichenfolge abzurufen:  
  
```  
ReferenceContext context = new ReferenceContext();  
context.Add(ModelBusReferencePropertySerializer.FilePathLoadContextKey,  
    currentProjectFilePath);  
ModelBusReference elementReferenceRestored =  
    modelBus.DeserializeReference(serialized, context);  
```  
  
### Von anderen Adaptern erstellte ModelBusReferences  
 Die folgenden Informationen sind hilfreich, wenn Sie einen eigenen Adapter erstellen möchten.  
  
 Ein `ModelBusReference` \(MBR\) besteht aus zwei Teilen: dem MBR\-Header vom Modellbus deserialisiert wird, und eine adapterspezifische, die vom spezifischen Adapter\-Manager verarbeitet wird. Dadurch können Sie Ihre eigenen Serialisierungsformat für Adapter bereitstellen. Beispielsweise können Sie Datei, sondern eine Datenbank verweisen, oder Sie zusätzliche Informationen in den Adapterverweis speichern würden. Ihr eigener Adapter könnte Weitere Informationen in der `ReferenceContext`.  
  
 Wenn Sie einen MBR deserialisieren, müssen Sie einen ReferenceContext angeben, die dann im MBR\-Objekt gespeichert ist. Wenn Sie einen MBR serialisieren, wird der gespeicherte ReferenceContext vom Adapter verwendet, um die Generierung die Zeichenfolge. Die deserialisierte Zeichenfolge enthält nicht alle Informationen im ReferenceContext. Im einfachen dateibasierten Adapter enthält beispielsweise ReferenceContext einen stammdateipfad, der nicht in der serialisierten MBR\-Zeichenfolge gespeichert wird.  
  
 Der MBR wird in zwei Stufen deserialisiert:  
  
-   `ModelBusReferencePropertySerializer` ist ein standardmäßiges Serialisierungsprogramm, das den MBR\-Header verarbeitet. Es verwendet die standardmäßige DSL `SerializationContext` Eigenschaftensammlung, die in gespeichert ist die `ReferenceContext` mithilfe des Schlüssels `ModelBusReferencePropertySerializer.ModelBusLoadContextKey`. Insbesondere die `SerializationContext` sollte eine Instanz von enthalten `ModelBus`.  
  
-   Ihr ModelBus\-Adapter befasst sich mit den adapterspezifischen Teil des MBR. Sie können zusätzliche Informationen im ReferenceContext des MBR gespeichert. Der einfache dateibasierte Adapter behält die stammdateipfade mit den Schlüsseln `FilePathLoadContextKey` und `FilePathSaveContextKey`.  
  
     Ein Adapterverweis in eine Modelldatei deserialisiert wird, wenn es verwendet wird.  
  
## Zum Erstellen eines Modells  
  
### Erstellen, öffnen und Bearbeiten eines Modells  
 Das folgende Fragment stammt aus dem Beispiel auf der VMSDK\-Website. Es veranschaulicht die Verwendung von ModelBusReferences zum Erstellen und öffnen Sie ein Modell, und beziehen Sie das Diagramm, das dem Modell zugeordnet.  
  
 In diesem Beispiel ist der Name der Ziel\-DSL StateMachine. Mehrere Namen werden, z. B. der Name der Modellklasse und den Namen der ModelBusAdapter abgeleitet.  
  
```  
using Fabrikam.StateMachine.ModelBusAdapters;   
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
using Microsoft.VisualStudio.Modeling.Integration;  
using Microsoft.VisualStudio.Modeling.Integration.Shell;  
using Microsoft.VisualStudio.Modeling.Shell;  
...  
// Create a new model.  
ModelBusReference modelReference =   
   StateMachineAdapterManager    .CreateStateMachineModel(modelName, fileName);  
//Keep reference of new model in this model.  
using (Transaction t = ...)  
{  
  myModelElement.ReferenceProperty = modelReference;  
  t.Commit();  
}  
// Get the ModelBus service from Visual Studio.  
IModelBus modelBus = Microsoft.VisualStudio.Shell.Package.  
    GetGlobalService(typeof(SModelBus)) as IModelBus;  
// Get a modelbus adapter on the new model.  
ModelBusAdapter modelBusAdapter;  
modelBus.TryCreateAdapter(modelReference,   
    this.ServiceProvider, out modelBusAdapter);  
using (StateMachineAdapter adapter =   
      modelBusAdapter as StateMachineAdapter)  
{  
    if (adapter != null)  
    {  
        // Obtain a Diagram from the adapter.  
        Diagram targetDiagram =   
           ((StandardVsModelingDiagramView)  
                 adapter.GetDefaultView()  
            ).Diagram;  
  
        using (Transaction t =   
             targetDiagram.Store.TransactionManager  
                .BeginTransaction("Update diagram"))  
        {  
            DoUpdates(targetDiagram);  
            t.Commit();  
        }  
  
        // Display the new diagram.  
        adapter.GetDefaultView().Show();  
    }  
}  
```  
  
## Überprüfen von verweisen  
 Mit brokenreferencedetector werden alle Domäneneigenschaften in einem Speicher, der ModelBusReferences enthalten kann. Ruft die Aktion, die angeben, in dem eine Aktion gefunden wird. Dies ist besonders nützlich für Validierungsmethoden. Die folgenden Validierungsmethode testet den Speicher bei dem Versuch, das Modell zu speichern und beschädigte Verweise im Fehlerfenster angezeigt:  
  
```  
[ValidationMethod(ValidationCategories.Save)]  
public void ValidateModelBusReferences(ValidationContext context)  
{  
  BrokenReferenceDetector.DetectBrokenReferences(this.Store,  
    delegate(ModelElement element, // parent of property  
             DomainPropertyInfo property, // identifies property  
             ModelBusReference reference) // invalid reference  
    {   
      context.LogError(string.Format(INVALID_REF_FORMAT,   
             property.Name,   
             referenceState.Name,   
             new ModelBusReferenceTypeConverter().  
                 ConvertToInvariantString(reference)),   
         "Reference",   
         element);  
      });  
}}  
private const string INVALID_REF_FORMAT =   
    "The '{0}' domain property of ths ReferenceState instance "  
  + "named '{1}' contains reference value '{2}' which is invalid";  
```  
  
## Von der ModelBus\-Erweiterung ausgeführte Aktionen  
 Die folgende Informationen ist nicht unbedingt erforderlich, aber nützlich sein, wenn Sie ModelBus einsetzen.  
  
 ModelBus\-Erweiterung werden die folgenden Änderungen in der DSL\-Projektmappe.  
  
 Wenn Sie die DSL\-Definitionsdiagramm mit der rechten Maustaste, klicken Sie auf **Modelbus aktivieren**, und wählen Sie dann **aktivieren diese DSL als ModelBus**:  
  
-   In der DSL\-Projekt ein Verweis hinzugefügt wird **Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0.dll**  
  
-   In der DSL\-Definition wird ein externer Verweis hinzugefügt: `Microsoft.VisualStudio.Modeling.Integration.ModelBusReference`.  
  
     Sehen Sie den Verweis im **DSL\-Explorer**, unter **Domänentypen**. Um Verweise auf externe Typen manuell hinzuzufügen, klicken Sie auf den Stammknoten.  
  
-   Eine neue Vorlagendatei wird hinzugefügt, **Dsl\\GeneratedCode\\ModelBusReferencesSerialization.tt**.  
  
 Wenn Sie legen den Typ einer Domäneneigenschaft auf ModelBusReference, und klicken Sie dann mit der rechten Maustaste in der Eigenschaft und klicken Sie auf **Aktivieren ModelBusReference\-spezifische Eigenschaften**:  
  
-   Die Eigenschaft "Domain" werden mehrere CLR\-Attribute hinzugefügt. Sie sehen sie im Feld "benutzerdefinierte Attribute" im Eigenschaftenfenster angezeigt. In **Dsl\\GeneratedCode\\DomainClasses.cs**, sehen Sie die Attribute der Eigenschaftendeklaration:  
  
    ```  
    [System.ComponentModel.TypeConverter(typeof(  
    Microsoft.VisualStudio.Modeling.Integration.ModelBusReferenceTypeConverter))]  
    [System.ComponentModel.Editor(typeof(  
      Microsoft.VisualStudio.Modeling.Integration.Picker  
      .ModelReferenceEditor // or ModelElementReferenceEditor  
      ), typeof(System.Drawing.Design.UITypeEditor))]  
    [Microsoft.VisualStudio.Modeling.Integration.Picker  
      .SupplyFileBasedBrowserConfiguration  
      ("Choose a model file", "Target model|*.target")]  
    ```  
  
 Wenn Sie mit der rechten Maustaste auf die DSL\-Definitionsdiagramm klicken, klicken Sie auf **ModelBus aktivieren**, und wählen Sie **verfügbar machen diese DSL für ModelBus**:  
  
-   Ein neues Projekt `ModelBusAdapter` wird der Projektmappe hinzugefügt.  
  
-   Ein Verweis auf `ModelBusAdapter` wird hinzugefügt, das `DslPackage` Projekt.`ModelBusAdapter` enthält einen Verweis auf die `Dsl` Projekt.  
  
-   In **DslPackage\\source.extention.tt**, `|ModelBusAdapter|` als MEF\-Komponente hinzugefügt wird.  
  
## Siehe auch  
 [Gewusst wie: Öffnen eines Modells aus einer Datei im Programmcode](../modeling/how-to-open-a-model-from-file-in-program-code.md)   
 [Integrate UML models with other models and tools](../modeling/integrate-uml-models-with-other-models-and-tools.md)   
 [Gewusst wie: Hinzufügen eines Drag & Drop\-Handlers](../modeling/how-to-add-a-drag-and-drop-handler.md)   
 [Verwenden von Visual Studio\-ModelBus in einer Textvorlage](../modeling/using-visual-studio-modelbus-in-a-text-template.md)