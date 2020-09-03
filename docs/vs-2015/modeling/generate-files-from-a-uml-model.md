---
title: Generieren von Dateien aus einem UML-Modell | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML model, generating files
ms.assetid: 4e28b0e6-ce8f-45ee-9e3a-e4d600a0ad81
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 832dc3f7fea959ff4d2834aba921cd16f1117b5c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72666150"
---
# <a name="generate-files-from-a-uml-model"></a>Generieren von Dateien von einem UML-Modell
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aus einem UML-Modell können Sie Programmcode, Schemas, Dokumente, Ressourcen und andere Artefakte aller Art generieren. Eine bequeme Methode zum Erstellen von Textdateien aus einem UML-Modell ist die Verwendung von [Textvorlagen](../modeling/code-generation-and-t4-text-templates.md). Durch diese können Sie Programmcode in den Text einbetten, den Sie generieren möchten.

 Es gibt drei grundlegende Szenarien:

- [Dateien werden über einen Menübefehl oder eine Geste erzeugt](#Command) . Sie definieren einen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Befehl, der in UML-Modellen verfügbar ist.

- [Erstellen von Dateien aus einer Anwendung](#Application). Sie schreiben eine Anwendung, die UML-Modelle liest und Dateien generiert.

- Wird [zur Entwurfszeit erzeugt](#Design). Sie verwenden ein Modell, um die Funktionalität Ihrer Anwendung zu definieren und Code, Ressourcen usw. innerhalb Ihrer [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Lösung zu generieren.

  In diesem Thema wird erläutert [, wie die Textgenerierung verwendet](#What)wird. Weitere Informationen finden Sie unter [Code Generierung und T4-Text Vorlagen](../modeling/code-generation-and-t4-text-templates.md).

## <a name="generating-files-from-a-menu-command"></a><a name="Command"></a> Erstellen von Dateien aus einem Menübefehl
 Sie können vorverarbeitete Textvorlagen innerhalb eines UML-Menübefehls verwenden. Im Code der Textvorlage oder in einer separaten partiellen Klasse können Sie das Modell lesen, das vom Diagramm angezeigt wird.

 Weitere Informationen zu diesen Funktionen finden Sie in den folgenden Themen:

- [Definieren eines Menübefehls in einem Modellierungsdiagramm](../modeling/define-a-menu-command-on-a-modeling-diagram.md)

- [Laufzeittextgenerierung mithilfe von T4-Textvorlagen](../modeling/run-time-text-generation-with-t4-text-templates.md)

- [Navigieren im UML-Modell](../modeling/navigate-the-uml-model.md)

  Die im folgenden Beispiel beschriebene Methode eignet sich zum Generieren von Text aus einem einzelnen Modell, wenn Sie den Vorgang aus einem der Modelldiagramme initiieren. Wenn Sie ein Modell in einem separaten Kontext verarbeiten möchten, können Sie den Zugriff auf das Modell und seine Elemente mithilfe von [Visual Studio ModelBus](../modeling/integrate-uml-models-with-other-models-and-tools.md) in Erwägung gezogen.

### <a name="example"></a>Beispiel
 Um dieses Beispiel auszuführen, erstellen Sie ein Projekt mit einer [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Erweiterung (VSIX). Der in diesem Beispiel verwendete Projektname ist `VdmGenerator` . Klicken Sie in der Datei " **Source. Extension. vsixmanifest** " auf **Inhalt hinzufügen** , und legen Sie das Feld Typ auf **MEF-Komponente** und Quellpfad fest, der auf das aktuelle Projekt verweist. Weitere Informationen zum Einrichten dieser Art von Projekt finden Sie unter [Definieren eines Menübefehls in einem Modellierungs Diagramm](../modeling/define-a-menu-command-on-a-modeling-diagram.md).

 Fügen Sie dem Projekt eine C#-Datei hinzu, die den folgenden Code enthält. Diese Klasse definiert einen Menübefehl, der in einem UML-Klassendiagramm angezeigt wird.

```
using System;
using System.ComponentModel.Composition;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;

namespace VdmGenerator
{
  [Export(typeof(ICommandExtension))]
  [ClassDesignerExtension]
  public class GenerateVdmFromClasses : ICommandExtension
  {
    [Import] public IDiagramContext DiagramContext { get; set; }
    public void Execute(IMenuCommand command)
    {
      // Initialize the template with the Model Store.
      VdmGen generator = new VdmGen(
             DiagramContext.CurrentDiagram.ModelStore);
      // Generate the text and write it.
      System.IO.File.WriteAllText
        (System.IO.Path.Combine(
            Environment.GetFolderPath(
                Environment.SpecialFolder.Desktop),
            "Generated.txt")
         , generator.TransformText());
    }
    public void QueryStatus(IMenuCommand command)
    {
      command.Enabled = command.Visible = true;
    }
    public string Text
    { get { return "Generate VDM"; } }
  }
}
```

 Die folgende Datei ist die Textvorlage. Sie generiert eine Textzeile für jede UML-Klasse im Modell und eine Zeile für jedes Attribut in jeder Klasse. Der Code zum Lesen des Modells ist in den Text eingebettet, wobei `<# ... #>` als Trennzeichen dient.

 Um diese Datei zu erstellen, klicken Sie in Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, zeigen Sie auf **Hinzufügen**, und klicken Sie dann auf **Neues Element**. Wählen Sie **vorverarbeitete Text Vorlage**aus. Der Dateiname für dieses Beispiel muss **VdmGen.tt**lauten. Die Eigenschaft **benutzerdefiniertes Tool** der Datei sollte **texttemplatingfilepreprocessor**lauten. Weitere Informationen zu vorverarbeiteten Textvorlagen finden Sie unter [Lauf Zeit Generierung von Text mit T4-Textvorlagen](../modeling/run-time-text-generation-with-t4-text-templates.md).

```
<#@ import namespace="Microsoft.VisualStudio.Uml.Classes" #>
<#
   foreach (IClass classElement in store.AllInstances<IClass>())   {
#>
Type <#= classElement.Name #> ::
<#
     foreach (IProperty attribute in classElement.OwnedAttributes)     {
#>
       <#= attribute.Name #> : <#=
           attribute.Type == null ? ""
                                  : attribute.Type.Name #>
<#
     }   }
#>
```

 Die Textvorlage generiert eine partielle C#-Klasse, die Teil Ihres [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Projekts wird. Fügen Sie in einer separaten Datei eine weitere partielle Deklaration derselben Klasse hinzu. Durch diesen Code erhält die Vorlage Zugriff auf den UML-Modellspeicher:

```
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
namespace VdmGenerator
{
    public partial class VdmGen
    {
        private IModelStore store;
        public VdmGen(IModelStore s)
        { store = s; }
    }
}
```

 Drücken Sie **F5**, um das Projekt zu testen. Eine neue Instanz von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] wird gestartet. Öffnen oder erstellen Sie in dieser Instanz ein UML-Modell, das ein Klassendiagramm enthält. Fügen Sie dem Diagramm einige Klassen und jeder Klasse einige Attribute hinzu. Klicken Sie mit der rechten Maustaste auf das Diagramm, und klicken Sie dann auf den Beispiel Befehl `Generate VDM` . Der Befehl erstellt die Datei `C:\Generated.txt` . Untersuchen Sie diese Datei. Ihr Inhalt sollte dem folgenden Text ähneln, jedoch werden Ihre eigenen Klassen und Attribute aufgeführt:

```
Type Class1 ::
          Attribute1 : int
          Attribute2 : string
Type Class2 ::
          Attribute3 : string
```

## <a name="generating-files-from-an-application"></a><a name="Application"></a> Erstellen von Dateien aus einer Anwendung
 Sie können Dateien aus einer Anwendung generieren, die ein UML-Modell liest. Zu diesem Zweck ist [Visual Studio ModelBus](../modeling/integrate-uml-models-with-other-models-and-tools.md)die flexibelste und stabilere Methode für den Zugriff auf das Modell und seine Elemente.

 Sie können auch die grundlegende API zum Laden des Modells verwenden und das Modell mit den gleichen Verfahren wie im vorherigen Abschnitt an Textvorlagen übergeben. Weitere Informationen zum Laden eines Modells finden Sie unter [Lesen eines UML-Modells im Programmcode](../modeling/read-a-uml-model-in-program-code.md).

## <a name="generating-files-at-design-time"></a><a name="Design"></a> Erstellen von Dateien zur Entwurfszeit
 Wenn das Projekt über eine Standardmethode für die Interpretation von UML als Code verfügt, können Sie Textvorlagen erstellen, mit denen Sie innerhalb des Projekts Code aus einem UML-Modell generieren können. Normalerweise haben Sie eine Lösung, die das UML-Modellprojekt und ein oder mehrere Projekte für den Anwendungscode enthält. Jedes Codeprojekt kann mehrere Vorlagen enthalten, die basierend auf dem Inhalt des Modells Programmcode, Ressourcen und Konfigurationsdateien generieren. Der Entwickler kann alle Vorlagen ausführen, indem er auf der Projektmappen-Explorer Symbolleiste auf die Schaltfläche **alle Vorlagen transformieren** klickt. Programmcode wird normalerweise in Form von partiellen Klassen generiert, damit manuell geschriebene Teile einfach integriert werden können.

 Ein [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Projekt dieser Art kann in Form einer Vorlage verteilt werden, sodass jedes Mitglied eines Teams Projekte erstellen kann, die Code aus einem Modell auf die gleiche Weise generieren. In der Regel ist die Vorlage Teil eines Erweiterungspakets, das Validierungseinschränkungen für das Modell aufweist, um sicherzustellen, dass die Vorbedingungen des Generierungscodes erfüllt werden.

### <a name="outline-procedure-for-generating-files"></a>Verfahren zum Generieren von Dateien

- Wenn Sie einem Projekt eine Vorlage hinzufügen möchten, wählen Sie im Dialogfeld neue Datei hinzufügen die Option **Text Vorlage** aus. Sie können den meisten Arten von Projekten eine Vorlage hinzufügen, aber nicht zu Modellierungsprojekten.

- Die Eigenschaft benutzerdefinierte Tools der Vorlagen Datei sollte **TextTemplatingFileGenerator**und die Dateinamenerweiterung. tt lauten.

- Die Vorlage sollte mindestens eine Ausgabedirektive enthalten:

     `<#@ output extension=".cs" #>`

     Legen Sie das Erweiterungsfeld entsprechend der Sprache des Projekts fest.

- Damit der Generierungscode in der Vorlage auf das Modell zugreifen kann, schreiben Sie `<#@ assembly #>`-Direktiven für die zum Lesen eines UML-Modells benötigten Assemblys. Öffnen Sie das Modell mit `ModelingProject.LoadReadOnly()`. Weitere Informationen finden Sie unter [Lesen eines UML-Modells im Programmcode](../modeling/read-a-uml-model-in-program-code.md).

- Die Vorlage wird ausgeführt, wenn Sie Sie speichern, und wenn Sie auf der Symbolleiste Projektmappen-Explorer auf **alle Vorlagen transformieren** klicken.

- Weitere Informationen zu dieser Art von Vorlage finden Sie unter [Entwurfszeit Code Generierung mithilfe von T4-Text Vorlagen](../modeling/design-time-code-generation-by-using-t4-text-templates.md).

- In einem typischen Projekt gibt es mehrere Vorlagen, die unterschiedliche Dateien aus demselben Modell generieren. Der erste Teil jeder Vorlage ist identisch. Um diese Duplizierung zu reduzieren, verschieben Sie die gemeinsamen Teile in eine separate Textdatei, und rufen Sie sie dann mithilfe der `<#@include file="common.txt"#>`-Direktive in den einzelnen Vorlagen auf.

- Sie können auch einen spezialisierten Direktivenprozessor definieren, mit dem Sie Parameter für den Textgenerierungsprozess bereitstellen können. Weitere Informationen finden Sie unter [Anpassen der T4-Text Transformation](../modeling/customizing-t4-text-transformation.md).

### <a name="example"></a>Beispiel
 In diesem Beispiel wird eine C#-Klasse für jede UML-Klasse im Quellmodell generiert.

##### <a name="to-set-up-a-visual-studio-solution-for-this-example"></a>So richten Sie eine Visual Studio-Projektmappe für dieses Beispiel ein

1. Erstellen Sie in einem Modellierungsprojekt in einer neuen Projektmappe ein UML-Klassendiagramm.

   1. Klicken Sie im Menü **Architektur** auf **Neues Diagramm**.

   2. Wählen Sie **UML-Klassendiagramm**aus.

   3. Befolgen Sie die Anweisungen zur Erstellung einer neuen Projektmappe und eines neuen Modellierungsprojekts.

   4. Fügen Sie dem Diagramm einige Klassen hinzu, indem Sie das UML-Klassen-Tool aus der Toolbox ziehen.

   5. Speichern Sie die Datei.

2. Erstellen Sie ein C#- oder Visual Basic-Projekt in derselben Projektmappe.

   - Klicken Sie in Projektmappen-Explorer mit der rechten Maustaste auf die Projekt Mappe, zeigen Sie auf **Hinzufügen**, und klicken Sie dann auf **Neues Projekt**. Klicken Sie unter **installierte Vorlagen**auf **Visual Basic** oder **Visual c#,** und wählen Sie dann einen Projekttyp aus, z. b. **Konsolenanwendung**.

3. Fügen Sie eine Nur-Text-Datei zum C#- oder Visual Basic-Projekt hinzu. Diese Datei enthält Code, der freigegeben wird, wenn Sie mehrere Textvorlagen schreiben möchten.

   - Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, zeigen Sie auf **Hinzufügen**, und klicken Sie dann auf **Neues Element**. Wählen Sie **Textdatei**aus.

     Fügen Sie den Text ein, der im folgenden Abschnitt angezeigt wird.

4. Fügen Sie eine Textvorlagendatei zum C#- oder Visual Basic-Projekt hinzu.

   - Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, zeigen Sie auf **Hinzufügen**, und klicken Sie dann auf **Neues Element**. Wählen Sie **Text Vorlage**aus.

     Fügen Sie den folgenden Code in die Textvorlagendatei ein.

5. Speichern Sie die Textvorlagendatei.

6. Überprüfen Sie den Code in der untergeordneten Datei. Er sollte eine Klasse für jede UML-Klasse im Modell enthalten.

   1. Klicken Sie in einem Visual Basic Projekt auf der Symbolleiste Projektmappen-Explorer auf **alle Dateien anzeigen** .

   2. Erweitern Sie den Vorlagendateiknoten im Projektmappen-Explorer.

#### <a name="content-of-the-shared-text-file"></a>Inhalt der freigegebenen Textdatei
 In diesem Beispiel heißt die Datei „SharedTemplateCode.txt“ und befindet sich in demselben Ordner wie die Textvorlagen.

```
<# /* Common material for inclusion in my model templates */ #>
<# /* hostspecific allows access to the Visual Studio API */ #>
<#@ template debug="false" hostspecific="true" language="C#" #>
<#@ assembly name="Microsoft.VisualStudio.Uml.Interfaces.dll"#>
<#@ assembly name="Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll"#>
<#@ assembly name="EnvDTE" #>
<#@ import namespace="Microsoft.VisualStudio.Uml.Classes" #>
<#@ import namespace="Microsoft.VisualStudio.ArchitectureTools.Extensibility" #>
<#@ import namespace="Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml" #>
<#+  // Note this is a Class Feature Block
///<summary>
/// Text templates are run in a common AppDomain, so
/// we can cache the model store that we find.
///</summary>
private IModelStore StoreCache
{
  get { return AppDomain.CurrentDomain.GetData("ModelStore") as IModelStore; }
  set { AppDomain.CurrentDomain.SetData("ModelStore", value); }
}
private bool CacheIsOld()
{
    DateTime? dt = AppDomain.CurrentDomain
           .GetData("latestAccessTime") as DateTime?;
    DateTime t = dt.HasValue ? dt.Value : new DateTime();
    DateTime now = DateTime.Now;
    AppDomain.CurrentDomain.SetData("latestAccessTime", now);
    return now.Subtract(t).Seconds > 3;
}

///<summary>
/// Find the UML modeling project in this solution,
/// and load the model.
///</summary>
private IModelStore ModelStore
{
  get
  {
    // Avoid loading the model for every template:
    if (StoreCache == null || CacheIsOld())
    {
      // Use Visual Studio API to find modeling project:
      EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)
                       .GetService(typeof(EnvDTE.DTE));
      EnvDTE.Project project = null;
      foreach (EnvDTE.Project p in dte.Solution.Projects)
      {
        if (p.FullName.EndsWith(".modelproj"))
        {
          project = p;
          break;
        }
      }
      if (project == null) return null;

      // Load UML model into this AppDomain
      // and access model store:
      IModelingProjectReader reader =
           ModelingProject.LoadReadOnly(project.FullName);
      StoreCache = reader.Store;
    }
    return StoreCache;
  }
}
#>
```

#### <a name="content-of-the-text-template-file"></a>Inhalt der Textvorlagendatei
 Der folgende Text wird in der **TT** -Datei abgelegt. In diesem Beispiel werden Klassen in einer C#-Datei aus den UML-Klassen im Modell generiert. Sie können jedoch Dateien eines beliebigen Typs generieren. Die Sprache der generierten Datei hat nichts mit der Sprache zu tun, in der der Textvorlagencode geschrieben ist.

```
<#@include file="SharedTemplateCode.txt"#>
<#@ output extension=".cs" #>
namespace Test{
<#
      foreach (IClass c in ModelStore.AllInstances<IClass>())
      {
#>
   public partial class <#=c.Name#>
   {   }
<#
      }
#>
}
```

## <a name="how-to-use-text-generation"></a><a name="What"></a> Verwenden der Text Generierung
 Die wirkliche Stärke der Modellierung nutzen Sie, wenn Sie Modelle verwenden, um auf Ebene der Anforderungen oder der Architektur zu entwerfen. Sie können Textvorlagen verwenden, um dazu beizutragen, allgemeine Ideen in Code umzuwandeln. In vielen Fällen führt dies nicht zu einer 1: 1-Entsprechung zwischen den Elementen in den UML-Modellen und -Klassen oder anderen Teilen des Programmcodes.

 Darüber hinaus hängt die Transformation vom Problembereich ab. Es gibt keine universelle Zuordnung zwischen Modellen und Code.

 Nachfolgend finden Sie einige Beispiele für das Generieren von Code aus Modellen:

- **Produktlinien**. Fabrikam, Inc. erstellt und installiert Flughafen-Gepäck Behandlungssysteme. Ein Großteil der Software ähnelt sich bei den verschiedenen Installationen stark, die Softwarekonfiguration hängt jedoch davon ab, welche Gepäckabfertigungsmaschine installiert wird und wie die Teile durch Gepäckbänder miteinander verbunden sind. Zu Beginn eines Vertrags besprechen die Analytiker von Fabrikam die Anforderungen mit der Flughafenverwaltung und erfassen den Hardwareplan mithilfe eines UML-Aktivitätsdiagramms. Aus diesem Modell generiert das Entwicklungsteam Konfigurationsdateien, Programmcode, Pläne und Benutzerdokumente. Abgeschlossen wird die Arbeit durch manuelle Ergänzungen und Anpassungen des Codes. Entsprechend der von Auftrag zu Auftrag wachsenden Erfahrung wird der Umfang des generierten Materials erweitert.

- **Muster**: Die Entwickler bei Contoso, Ltd erstellen häufig Websites und entwerfen das Navigationsschema mit UML-Klassendiagrammen. Jede Webseite wird durch eine Klasse dargestellt, und Zuordnungen stellen Navigationsverknüpfungen dar. Die Entwickler generieren einen Großteil des Codes einer Website aus dem Modell. Jede Webseite entspricht mehreren Klassen und Ressourcendateieinträgen.  Diese Methode hat den Vorteil, dass die Konstruktion jeder Seite einem einzelnen Muster entspricht, wodurch sich eine größere Zuverlässigkeit und Flexibilität als bei handgeschriebenem Code ergibt. Das Muster wird beim Generieren der Vorlagen eingesetzt, während das Modell zum Erfassen der variablen Aspekte verwendet wird.

- **Schemas**: Humongous Insurance arbeitet mit Tausenden von Systemen weltweit. Diese Systeme verwenden unterschiedliche Datenbanken, Sprachen und Schnittstellen. Das zentrale Architekturteam veröffentlicht intern Modelle von Geschäftskonzepten und Prozessen. Aus diesen Modellen generieren lokale Teams Teile ihrer Datenbank und tauschen Schemas, Deklarationen in Programmcode usw. aus. Die grafische Darstellung der Modelle hilft Teams bei der Besprechung von Vorschlägen. Die Teams erstellen mehrere Diagramme, die Teilmengen des Modells zeigen, die für unterschiedliche Geschäftsbereiche gelten. Bereiche, die Änderungen unterliegen, werden farblich hervorgehoben.

## <a name="important-techniques-for-generating-artifacts"></a>Wichtige Techniken für das Generieren von Artefakten
 In den vorherigen Beispielen werden Modelle für verschiedene geschäftsabhängige Zwecke verwendet, und die Interpretation der Modellierungselemente wie Klassen und Aktivitäten variiert von einer Anwendung zur anderen. Die folgenden Techniken sind beim Generieren von Artefakten aus Modellen nützlich.

- **Profile**. Selbst innerhalb eines Geschäftsbereichs kann die Interpretation eines Elementtyps variieren. In einem Website-Diagramm beispielsweise stellen einige Klassen möglicherweise Webseiten dar, und andere Inhaltsblöcke. Um den Benutzern die Aufzeichnung dieser Unterscheidungen zu erleichtern, können Sie Stereotypen definieren. Stereotypen ermöglichen es auch, zusätzliche Eigenschaften anzufügen, die für Elemente dieser Art gelten. Stereotypen werden in Profilen verpackt. Weitere Informationen finden Sie unter [Definieren eines Profils zum Erweitern von UML](../modeling/define-a-profile-to-extend-uml.md).

     In Vorlagencode ist es einfach, auf die für ein Objekt definierten Stereotypen zugreifen. Beispiel:

    ```
    public bool HasStereotype(IClass c, string profile, string stereo)
    { return c.AppliedStereotypes.Any
       (s => s.Profile == profile && s.Name == stereo ); }
    ```

- **Eingeschränkte Modelle**. Nicht alle Modelle, die Sie erstellen können, gelten für jeden Zweck. Bei den Flughafengepäckmodellen von Fabrikam beispielsweise wäre es falsch, einen Check-in-Schalter ohne ein ausgehendes Gepäckband zu haben. Sie können Validierungsfunktionen definieren, mit denen Benutzer diese Einschränkungen berücksichtigen können. Weitere Informationen finden Sie unter [Definieren von Validierungs Einschränkungen für UML-Modelle](../modeling/define-validation-constraints-for-uml-models.md).

- **Manuelle Änderungen beibehalten**. Nur einige der Projektmappendateien können aus einem Modell generiert werden. In den meisten Fällen muss es möglich sein, den generierten Inhalt manuell hinzuzufügen oder anzupassen. Allerdings ist es wichtig, dass diese manuellen Änderungen beibehalten werden, wenn die Vorlagentransformation erneut ausgeführt wird.

     Wenn Ihre Vorlagen Code in [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)] Sprachen generieren, sollten Sie partielle Klassen generieren, damit Entwickler Methoden und Code hinzufügen können. Es ist auch hilfreich, jede Klasse als Paar zu generieren: eine abstrakte Basisklasse, die die Methoden enthält, und eine erbende Klasse, die nur den Konstruktor enthält. Auf diese Weise können Entwickler die Methoden überschreiben. Damit die Initialisierung überschrieben werden kann, erfolgt dies in einer separaten Methode und nicht in den Konstruktoren.

     Wenn eine Vorlage XML und andere Arten von Ausgabe generiert, kann es schwieriger sein, den manuellen Inhalt vom generierten Inhalt zu trennen. Eine Methode besteht darin, eine Aufgabe im Buildprozess zu erstellen, die zwei Dateien kombiniert. Eine andere Methode ist die Anpassung einer lokalen Kopie der Generierungsvorlage durch die Entwickler.

- **Verschieben Sie Code in separate**Assemblys. Wir empfehlen nicht, umfangreiche Codetexte in Vorlagen zu schreiben. Es wird empfohlen, generierten Inhalt von der Berechnung zu trennen, und Textvorlagen werden für das Bearbeiten von Code nicht gut unterstützt.

     Wenn Sie umfangreiche Berechnungen zum Generieren von Text ausführen müssen, erstellen Sie diese Funktionen stattdessen in einer separaten Assembly, und rufen Sie die zugehörigen Methoden aus der Vorlage auf.
