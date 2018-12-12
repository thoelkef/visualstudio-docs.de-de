---
title: Integrieren von Modellen mithilfe von Modelbus
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: e72814b34790dd133f09e0fb16c594e12ea8147c
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2018
ms.locfileid: "53064596"
---
# <a name="integrating-models-by-using-visual-studio-modelbus"></a>Integrieren von Modellen mit Visual Studio-ModelBus

Visual Studio-ModelBus stellt eine Methode zum Erstellen von Links zwischen Modellen und von anderen Tools in Modelle bereit. Sie können z. B. einer domänenspezifischen Sprache (DSL) Modelle und UML-Modelle verknüpfen. Sie können einen integrierten Satz von DSLs erstellen.

Mit ModelBus können Sie einen eindeutigen Verweis auf ein Modell oder ein bestimmtes Element in einem Modell erstellen. Dieser Verweis kann außerhalb des Modells gespeichert werden, beispielweise in einem Element eines anderen Modells. Wenn zu einem späteren Zeitpunkt ein Tool Zugriff auf das Element benötigt, wird das entsprechende Modell in der Modellbusinfrastruktur geladen und das Element zurückgegeben. Bei Bedarf können Sie das Modell dem Benutzer zeigen. Wenn am vorherigen Speicherort kein Zugriff auf die Datei möglich ist, wird der Benutzer von ModelBus aufgefordert, nach der Datei zu suchen. Findet der Benutzer die Datei, korrigiert ModelBus alle Verweise auf die Datei.

> [!NOTE]
> In der aktuellen Implementierung von Visual Studio ModelBus muss die verknüpften Modelle Elemente in der gleichen Visual Studio-Projektmappe.

Weitere Informationen und Beispielcode finden Sie unter:

-   [Gewusst wie: Hinzufügen eines Drag & Drop-Handlers](../modeling/how-to-add-a-drag-and-drop-handler.md)

-   [Modellierungs-SDK für Visual Studio](http://www.microsoft.com/download/details.aspx?id=40754)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="provide"></a> Bereitstellen von Zugriff auf eine DSL
 Bevor Sie ModelBus-Verweise auf ein Modell oder dessen Elemente erstellen können, müssen Sie einen ModelBusAdapter für die DSL erstellen. Die einfachste Möglichkeit hierzu ist die Verwendung der Visual Studio-Modellbuserweiterung, wodurch der DSL-Designer Befehle hinzugefügt.

### <a name="expose"></a> Um eine DSL-Definition dem Modellbus verfügbar zu machen

1. Laden Sie die Visual Studio-Modellbuserweiterung herunter, und installieren Sie sie, sofern noch nicht geschehen. Weitere Informationen finden Sie unter [Visualisierungs- und Modellierungs-SDK](http://go.microsoft.com/fwlink/?LinkID=185579).

2. Öffnen Sie die DSL-Definitionsdatei. Mit der rechten Maustaste in der Entwurfsoberfläche, und klicken Sie dann auf **Modelbus aktivieren**.

3. Wählen Sie in das Dialogfeld **ich möchte diese DSL für ModelBus verfügbar machen**. Sie können beide Optionen auswählen, wenn diese DSL Modelle verfügbar machen soll und Verweise auf andere DSLs nutzen soll.

4. Klicken Sie auf **OK**. Der DSL-Projektmappe wird ein neues ModelBusAdapter-Projekt hinzugefügt.

5. Wenn Sie auf die DSL über eine Textvorlage zugreifen möchten, müssen Sie "AdapterManager.tt" im neuen Projekt ändern. Überspringen Sie diesen Schritt, wenn Sie mit anderem Code wie Befehlen oder Ereignishandlern auf die DSL zugreifen möchten. Weitere Informationen finden Sie unter [mithilfe von Visual Studio-ModelBus in einer Textvorlage](../modeling/using-visual-studio-modelbus-in-a-text-template.md).

   1. Ändern Sie die Basisklasse von AdapterManagerBase in <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager>.

   2. Fügen Sie am Ende der Datei dieses zusätzliche Attribut vor der AdapterManager-Klasse ein:

       `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`

   3. Fügen Sie in den Verweisen des ModelBusAdapter-Projekts **Microsoft.VisualStudio.TextTemplating.Modeling.11.0**.

      Wenn Sie auf die DSL über Textvorlagen und anderen Code zugreifen möchten, benötigen Sie einen geänderten und einen nicht geänderten Adapter.

6. Klicken Sie auf **alle Vorlagen transformieren**.

7. Generieren Sie die Projektmappe neu.

   Jetzt kann ModelBus Instanzen dieser DSL öffnen.

   Der Ordner `ModelBusAdapters\bin\*` enthält die Assemblys, die vom `Dsl`-Projekt und vom `ModelBusAdapters`-Projekt erstellt wurden. Um mit einer anderen DSL auf diese DSL zu verweisen, sollten Sie diese Assemblys importieren.

### <a name="ensure-that-elements-can-be-referenced"></a>Stellen Sie sicher, dass Elemente verwiesen werden kann

Visual Studio-ModelBus-Adapter verwenden Sie die Guid eines Elements, in der Standardeinstellung identifiziert. Diese IDs müssen deshalb in der Modelldatei erhalten bleiben.

Um sicherzustellen, dass dieses Element sind IDs beibehalten:

1. Öffnen Sie "DslDefinition.dsl".

2. Erweitern Sie im DSL-Explorer **XML-Serialisierungsverhalten**, klicken Sie dann **Klassendaten**.

3. Für jede Klasse, für die Sie Modellbusverweise erstellen möchten:

    Klicken Sie auf den Klassenknoten, und stellen Sie im Eigenschaftenfenster sicher, dass **Id Serialisieren** nastaven NA hodnotu `true`.

   Wenn Sie statt GUIDs Elementnamen für die Identifikation von Elementen verwenden möchten, können Sie alternativ Teile der generierten Adapter überschreiben. Überschreiben Sie in der Adapterklasse die folgende Methoden:

-   Überschreiben Sie `GetElementId`, damit die gewünschte ID zurückgegeben wird. Diese Methode wird aufgerufen, wenn Verweise erstellt werden.

-   Überschreiben Sie `ResolveElementReference`, um das richtige Element in einem Modellbusverweis zu finden.

## <a name="editRef"></a> Zugreifen auf eine DSL von einer anderen DSL

Sie können Modellbusverweise in einer Domäneneigenschaft in einer DSL speichern und dann benutzerdefinierten Code schreiben, der sie nutzt. Sie können es auch dem Benutzer ermöglichen, einen Modellbusverweis zu erstellen, indem er eine Modelldatei und ein darin enthaltenes Element auswählt.

Um eine DSL Verweise auf eine andere DSL verwenden zu können, Sie sollten machen Sie es zunächst eine *Consumer* von modellbusverweisen.

### <a name="to-enable-a-dsl-to-consume-references-to-an-exposed-dsl"></a>So aktivieren Sie eine DSL als Consumer von Verweisen auf eine verfügbar gemachte DSL

1.  Klicken Sie in der DSL-Definitionsdiagramm mit der rechten Maustaste in den Hauptteil des Diagramms, und klicken Sie dann auf **Modelbus aktivieren**.

2.  Wählen Sie im Dialogfeld **ich möchte dieses Modell zur modellbusverweise aktivieren**.

3.  Fügen Sie im Dsl-Projekt der Consumer-DSL den Projektverweisen die folgenden Assemblys hinzu. Sie finden diese Assemblys (DLL-Dateien) in der ModelBusAdapter\bin\\* Verzeichnis verfügbar gemachten DSL.

    -   Die verfügbar gemachten DSL-Assembly, beispielsweise **Fabrikam.FamilyTree.Dsl.dll**

    -   Der verfügbar gemachten Model bus Modellbusadapter-Assembly, z. B. **Fabrikam.FamilyTree.ModelBusAdapter.dll**

4.  Fügen Sie die folgenden .NET-Assemblys den Projektverweisen des Consumer-DSL-Projekts hinzu.

    1.  **Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0.dll**

    2.  **Microsoft.VisualStudio.Modeling.Sdk.Integration.Shell.11.0.dll**

### <a name="to-store-a-model-bus-reference-in-a-domain-property"></a>So speichern Sie einen Modellbusverweis in einer Domäneneigenschaft

1. Fügen Sie in der DSL-Definition der Consumer-DSL einer Domänenklasse eine Domäneneigenschaft hinzu, und legen Sie ihren Namen fest.

2. Fenster mit der Eigenschaft "Domain" ausgewählt haben, legen Sie im Eigenschaftenfenster **Typ** zu `ModelBusReference`.

   In dieser Phase kann mit Programmcode der Eigenschaftenwert festgelegt werden, er ist aber im Eigenschaftenfenster schreibgeschützt.

   Sie können es den Benutzern ermöglichen, die Eigenschaft mit einem speziellen ModelBus-Verweis-Editor festzulegen. Es gibt zwei Versionen dieses Editors oder *Auswahl:* eine kann Benutzer eine Modelldatei auszuwählen, und die andere Benutzer eine Modelldatei und ein Element innerhalb des Modells auswählen kann.

### <a name="to-allow-the-user-to-set-a-model-bus-reference-in-a-domain-property"></a>So ermöglichen Sie es dem Benutzer, einen Modellbusverweis in einer Domäneneigenschaft festzulegen

1.  Mit der rechten Maustaste in die Eigenschaft "Domain", und klicken Sie dann auf **bearbeiten ModelBusReference-spezifische Eigenschaften**. Ein Dialogfeld wird geöffnet. Dies ist die *Modellbusauswahl*.

2.  Wählen Sie das entsprechende **Art von ModelBusReference**: auf ein Modell oder ein Element in einem Modell.

3.  Geben Sie im Dateidialogfeld für die Filterzeichenfolge eine Zeichenfolge wie `Family Tree files |*.ftree` ein. Ersetzen Sie die Dateierweiterung der verfügbar gemachten DSL.

4.  Wenn Sie auf ein Element in einem Modell verweisen möchten, können Sie eine Liste der Typen hinzufügen, aus denen der Benutzer auswählen kann, beispielsweise "Company.FamilyTree.Person".

5.  Klicken Sie auf **OK**, und klicken Sie dann auf **alle Vorlagen transformieren** in die **Projektmappen-Explorer** Symbolleiste.

    > [!WARNING]
    > Wenn Sie kein gültiges Modell bzw. keine gültige Entität ausgewählt haben, hat die Schaltfläche "OK" keine Wirkung, auch wenn sie so aussieht, als wäre sie aktiviert.

6.  Wenn Sie eine Liste von Zieltypen wie "Company.FamilyTree.Person" angegeben haben, müssen Sie einen Assemblyverweis auf das DSL-Projekt hinzufügen, indem Sie auf die DLL der Ziel-DSL verweisen, beispielsweise "Company.FamilyTree.Dsl.dll".

### <a name="to-test-a-model-bus-reference"></a>So testen Sie einen Modellbusverweis

1.  Erstellen Sie die verfügbar gemachte DSL und die Consumer-DSL.

2.  Führen Sie eine der DSLs im experimentellen Modus aus, indem Sie F5 oder STRG+F5 drücken.

3.  Fügen Sie im debuggingprojekt in der experimentellen Instanz von Visual Studio Dateien, die Instanzen der beiden DSLS sind hinzu.

    > [!NOTE]
    > Visual Studio-ModelBus kann nur Verweise auf Modelle auflösen, die Elemente in der gleichen Visual Studio-Projektmappe sind. Sie können beispielsweise keinen Verweis auf eine Modelldatei in einem anderen Teil Ihres Dateisystems erstellen.

4.  Erstellen Sie einige Elemente und Links in der Instanz der verfügbar gemachten DSL, und speichern Sie sie.

5.  Öffnen Sie eine Instanz der Consumer-DSL, und wählen Sie ein Modellelement aus, dass eine Eigenschaft für einen Modellbusverweis enthält.

6.  Doppelklicken Sie im Eigenschaftenfenster auf die Eigenschaft für einen Modellbusverweis. Das Auswahldialogfeld wird geöffnet.

7.  Klicken Sie auf **Durchsuchen** , und wählen Sie die Instanz der verfügbar gemachten DSL.

     Über die Auswahl können Sie ein Element im Modell auswählen, wenn Sie einen elementspezifischen Modellbusverweis angegeben haben.

## <a name="creating-references-in-program-code"></a>Erstellen von Verweisen im Programmcode

Wenn Sie einen Verweis auf ein Modell oder ein Element in einem Modell speichern möchten, erstellen Sie einen `ModelBusReference`. Es gibt zwei Arten von `ModelBusReference`: Modellverweise und Elementverweise.

Um einen Modellverweis zu erstellen, benötigen Sie den AdapterManager der DSL, von denen das Modell eine Instanz, und der Dateiname oder die Visual Studio-Projektelement des Modells ist.

Zum Erstellen eines Elementverweises benötigen Sie einen Adapter für die Modelldatei und ein Element, auf das Sie verweisen möchten.

> [!NOTE]
> Mit der Visual Studio-ModelBus können Sie nur Verweise auf Elemente in der gleichen Visual Studio-Projektmappe erstellen.

### <a name="import-the-exposed-dsl-assemblies"></a>Importieren der verfügbar gemachten DSL-Assemblys

Fügen Sie im Consumerprojekt Projektverweise auf die DSL und die ModelBusAdapter-Assemblys der verfügbar gemachten DSL hinzu.

Nehmen Sie beispielsweise an, Sie möchten ModelBus-Verweise in Elementen einer MusicLibrary-DSL speichern. Die ModelBus-Verweise verweisen auf Elemente der FamilyTree-DSL. Fügen Sie im `Dsl`-Projekt der MusicLibrary-Projektmappe im Knoten "Verweise" Verweise auf die folgenden Assemblys hinzu:

- Fabrikam.FamilyTree.Dsl.dll – die verfügbar gemachte DSL.

- Fabrikam.FamilyTree.ModelBusAdapters.dll – der ModelBus-Adapter der verfügbar gemachten DSL.

- Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0

- Microsoft.VisualStudio.Modeling.Sdk.Integration.Shell.11.0

  Sie finden diese Assemblys im `ModelBusAdapters`-Projekt der verfügbar gemachten DSL unter `bin\*`.

  In der Regel müssen Sie die folgenden Namespaces in die Codedatei importieren, in der Sie Verweise erstellen:

```csharp
// The namespace of the DSL you want to reference:
using Fabrikam.FamilyTree;  // Exposed DSL
using Fabrikam.FamilyTree.ModelBusAdapters;
using Microsoft.VisualStudio.Modeling.Integration;
using System.Linq;
...
```

### <a name="to-create-a-reference-to-a-model"></a>So erstellen Sie einen Verweis auf ein Modell

Zum Erstellen eines Modellverweises greifen Sie auf den AdapterManager der verfügbar gemachten DSL zu und erstellen damit einen Verweis auf das Modell. Sie können einen Dateipfad oder ein `EnvDTE.ProjectItem` angeben.

Vom AdapterManager können Sie einen Adapter abrufen, der Zugriff auf einzelne Elemente im Modell bietet.

> [!NOTE]
> Sie müssen einen Adapter löschen, wenn Sie damit fertig sind. Sie erreichen dies am einfachsten mit einer `using`-Anweisung. Dies wird anhand des folgenden Beispiels veranschaulicht.

```csharp
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

Für eine spätere Nutzung können Sie `modelReference` in einer Domäneneigenschaft speichern, die `ModelBusReference` mit einem externen Typ aufweist:

```csharp
using Transaction t = this.Store.TransactionManager
    .BeginTransaction("keep reference"))
{
  artist.FamilyTreeReference = modelReference;
  t.Commit();
}
```

Damit die Benutzer diese Domäneneigenschaft bearbeiten können, verwenden Sie `ModelReferenceEditor` als Parameter im Editor-Attribut. Weitere Informationen finden Sie unter [ermöglicht dem Benutzer, die Bearbeitung eines Verweises](#editRef).

### <a name="to-create-a-reference-to-an-element"></a>So erstellen Sie einen Verweis auf ein Element

Der Adapter, den Sie für das Modell erstellt haben, kann zum Erstellen und Auflösen von Verweisen verwendet werden.

```csharp
// person is an element in the FamilyTree model:
ModelBusReference personReference =
  adapter.GetElementReference(person);
```

Für eine spätere Nutzung können Sie `elementReference` in einer Domäneneigenschaft speichern, die `ModelBusReference` mit einem externen Typ aufweist. Damit die Benutzer ihn bearbeiten können, verwenden Sie `ModelElementReferenceEditor` als Parameter im Editor-Attribut. Weitere Informationen finden Sie unter [ermöglicht dem Benutzer, die Bearbeitung eines Verweises](#editRef).

### <a name="resolving-references"></a>Auflösen von Verweisen

Wenn Sie über einen `ModelBusReference` (MBR) verfügen, können Sie das Modell oder das Modellelement abrufen, auf das verwiesen wird. Wenn das Element im Diagramm oder einer anderen Ansicht vorhanden ist, können Sie die Ansicht öffnen und das Element auswählen.

Sie können einen Adapter mit einem MBR erstellen. Vom Adapter können Sie den Stamm des Modells abrufen. Darüber hinaus können Sie MBRs auflösen, die auf bestimmte Elemente im Modell verweisen.

```csharp
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

#### <a name="to-resolve-modelbus-references-in-a-text-template"></a>So lösen Sie ModelBus-Verweise in einer Textvorlage auf

1. Die DSL, auf die Sie zugreifen möchten, muss einen ModelBus-Adapter aufweisen, der für Zugriff durch Textvorlagen konfiguriert ist. Weitere Informationen finden Sie unter [Gewähren von Zugriff auf eine DSL](#provide).

2. Normalerweise greifen Sie auf eine Ziel-DSL mit einem Modellbusverweis (Model Bus Reference, MBR) zu, der in einer Quell-DSL gespeichert ist. Ihre Vorlage enthält deshalb die Direktive der Quell-DSL sowie Code zur MBR-Auflösung. Weitere Informationen zu Textvorlagen finden Sie unter [Generieren von Code aus einer domänenspezifischen Sprache](../modeling/generating-code-from-a-domain-specific-language.md).

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

   Weitere Informationen und eine exemplarische Vorgehensweise finden Sie [mithilfe von Visual Studio-ModelBus in einer Textvorlage](../modeling/using-visual-studio-modelbus-in-a-text-template.md)

## <a name="serializing-a-modelbusreference"></a>Serialisieren eines ModelBusReference

Wenn Sie einen `ModelBusReference` (MBR) als Zeichenfolge speichern möchten, können Sie ihn serialisieren:

```csharp
string serialized = modelBus.SerializeReference(elementReference);
// Store it anywhere, then get it back again:
ModelBusReference elementReferenceRestored =
    modelBus.DeserializeReference(serialized, null);
```

Ein auf diese Weise serialisierter MBR ist kontextunabhängig. Wenn Sie den einfachen dateibasierten Modellbusadapter verwenden, enthält der MBR einen absoluten Dateipfad. Dies ist ausreichend, wenn die Instanzmodelldateien nicht verschoben werden. Allerdings werden die Modelldateien in der Regel Elemente in einem Visual Studio-Projekt. Ihre Benutzer werden erwarten, dass sie das gesamte Projekt in andere Teile des Dateisystems verschieben können. Sie werden außerdem erwarten, dass sie für das Projekt Quellcodeverwaltung nutzen und es auf verschiedenen Computern öffnen können. Pfadnamen sollten daher relativ zum Speicherort des Projekts serialisiert werden, das die Dateien enthält.

### <a name="serializing-relative-to-a-specified-file-path"></a>Serialisieren relativ zum angegebenen Dateipfad

Ein `ModelBusReference` enthält einen `ReferenceContext`, ein Wörterbuch, in dem Sie Informationen wie den Dateipfad speichern können, relativ zu dem die Serialisierung erfolgen soll.

So serialisieren Sie relativ zu einem Pfad

```csharp
elementReference.ReferenceContext.Add(
   ModelBusReferencePropertySerializer.FilePathSaveContextKey,
   currentProjectFilePath);
string serialized = modelBus.SerializeReference(elementReference);
```

So rufen Sie den Verweis aus der Zeichenfolge ab

```csharp
ReferenceContext context = new ReferenceContext();
context.Add(ModelBusReferencePropertySerializer.FilePathLoadContextKey,
    currentProjectFilePath);
ModelBusReference elementReferenceRestored =
    modelBus.DeserializeReference(serialized, context);
```

### <a name="modelbusreferences-created-by-other-adapters"></a>Von anderen Adaptern erstellte ModelBusReferences
 Die folgenden Informationen sind nützlich, wenn Sie einen eigenen Adapter erstellen möchten.

 Ein `ModelBusReference` (MBR) besteht aus zwei Teilen: dem MBR-Header, der vom Modellbus deserialisiert wird, und einer adapterspezifischen Angabe, die vom spezifischen Adapter-Manager verarbeitet wird. Auf diese Weise können Sie ein eigenes Serialisierungsformat für Adapter angeben. Sie könnten beispielsweise auf eine Datenbank statt auf eine Datei verweisen. Sie könnten auch weitere Informationen im Adapterverweis speichern. Ihr eigener Adapter könnte weitere Informationen zum `ReferenceContext` hinzufügen.

 Wenn Sie einen MBR deserialisieren, müssen Sie einen ReferenceContext angeben, der dann im MBR-Objekt gespeichert wird. Wenn Sie einen MBR serialisieren, wird der gespeicherte ReferenceContext vom Adapter zur Generierung der Zeichenfolge verwendet. Die deserialisierte Zeichenfolge enthält nicht die gesamten Informationen im ReferenceContext. Beim einfachen dateibasierten Adapter enthält der ReferenceContext einen Stammdateipfad, der nicht in der serialisierten MBR-Zeichenfolge gespeichert wird.

 Der MBR wird in zwei Stufen deserialisiert:

-   `ModelBusReferencePropertySerializer` ist ein standardmäßiges Serialisierungsprogramm, das den MBR-Header verarbeitet. Es verwendet die standardmäßige DSL-Eigenschaftensammlung `SerializationContext`, die mit dem Schlüssel `ReferenceContext` im `ModelBusReferencePropertySerializer.ModelBusLoadContextKey` gespeichert wird. Insbesondere der `SerializationContext` sollte eine Instanz von `ModelBus` enthalten.

-   Ihr ModelBus-Adapter verarbeitet den adapterspezifischen Teil des MBR. Er kann weitere Informationen verwenden, die im ReferenceContext des MBR gespeichert sind. Der einfache dateibasierte Adapter behält die stammdateipfade mit den Schlüsseln `FilePathLoadContextKey` und `FilePathSaveContextKey`.

     Ein Adapterverweis in einer Modelldatei wird nur deserialisiert, wenn er verwendet wird.

## <a name="to-create-a-model"></a>So erstellen Sie ein Modell

### <a name="creating-opening-and-editing-a-model"></a>Erstellen, Öffnen und Bearbeiten eines Modells
 Das folgende Fragment stammt aus dem Beispiel auf der VMSDK-Website. Es veranschaulicht die Verwendung von ModelBusReferences zum Erstellen und Öffnen eines Modells und zum Abrufen des mit dem Modell verbundenen Diagramms.

 In diesem Beispiel lautet der Name der Ziel-DSL "StateMachine". Davon werden verschiedene Namen abgeleitet, beispielsweise der Name der Modellklasse und der ModelBusAdapter-Name.

```csharp
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

## <a name="validating-references"></a>Überprüfen von Verweisen
 Mit BrokenReferenceDetector werden alle Domäneneigenschaften in einem Speicher getestet, der ModelBusReferences enthalten kann. Er ruft die angegebene Aktion auf, wenn eine Aktion gefunden wird. Dies ist für Überprüfungsmethoden besonders nützlich. Mit der folgenden Überprüfungsmethode wird der Speicher bei dem Versuch getestet, das Modell zu speichern, dabei werden beschädigte Verweise im Fehlerfenster angegeben:

```csharp
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

## <a name="actions-performed-by-the-modelbus-extension"></a>Von der ModelBus-Erweiterung ausgeführte Aktionen

Die folgenden Informationen sind nicht entscheidend, können aber nützlich sein, wenn Sie ModelBus intensiv nutzen.

Mit der ModelBus-Erweiterung werden die folgenden Änderungen an Ihrer DSL-Projektmappe vorgenommen.

Wenn Sie die DSL-Definitionsdiagramm mit der rechten Maustaste, klicken Sie auf **Modelbus aktivieren**, und wählen Sie dann **aktivieren diese DSL für ModelBus-Consumer**:

- In der DSL-Projekt ein Verweis hinzugefügt ist **Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0.dll**

- In der DSL-Definition wird ein Verweis auf einen externen Typ hinzugefügt: `Microsoft.VisualStudio.Modeling.Integration.ModelBusReference`.

   Sehen Sie den Verweis im **DSL-Explorer**unter **Domänentypen**. Klicken Sie auf den Stammknoten, um Verweise auf externe Typen hinzuzufügen.

- Eine neue Vorlagendatei wird hinzugefügt, **Dsl\GeneratedCode\ModelBusReferencesSerialization.tt**.

Wenn Sie legen Sie den Typ einer Domäneneigenschaft auf ModelBusReference, und klicken Sie mit der rechten Maustaste in der Eigenschaft **aktivieren ModelBusReference-spezifische Eigenschaften**:

- Der Domäneneigenschaft werden mehrere CLR-Attribute hinzugefügt. Sie werden im Eigenschaftenfenster im Feld "Benutzerdefinierte Attribute" angezeigt. In **Dsl\GeneratedCode\DomainClasses.cs**, sehen Sie die Attribute der Eigenschaftendeklaration:

  ```csharp
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

Wenn Sie rechts im DSL-Definitionsdiagramm klicken, klicken Sie auf **ModelBus aktivieren**, und wählen Sie **verfügbar zu machen diese DSL für ModelBus**:

- Der Projektmappe wird ein neues `ModelBusAdapter`-Projekt hinzugefügt.

- Dem `ModelBusAdapter`-Projekt wird ein Verweis auf `DslPackage` hinzugefügt. `ModelBusAdapter` weist einen Verweis auf das `Dsl`-Projekt auf.

- In **DslPackage\source.extention.tt**, `|ModelBusAdapter|` als MEF-Komponente hinzugefügt wird.

## <a name="see-also"></a>Siehe auch

- [Gewusst wie: Öffnen eines Modells aus einer Datei im Programmcode](../modeling/how-to-open-a-model-from-file-in-program-code.md)
- [Gewusst wie: Hinzufügen eines Drag & Drop-Handlers](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [Verwenden von Visual Studio-ModelBus in einer Textvorlage](../modeling/using-visual-studio-modelbus-in-a-text-template.md)