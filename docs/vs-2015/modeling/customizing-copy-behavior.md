---
title: Customizing Copy Behavior | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 87fff01c-60ba-440a-b8a0-185edcef83ac
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e17e29e36be5636662e6105a05446a9cbe0aa724
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301191"
---
# <a name="customizing-copy-behavior"></a>Anpassen des Kopierverhaltens
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In einer domänenspezifischen Sprache (Domain-Specific Language, DSL), die mit dem [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-SDK für Visualisierung und Modellierung erstellt wurde, können Sie ändern, was beim Kopieren und Einfügen von Elementen passiert.

## <a name="standard-copy-and-paste-behavior"></a>Standardmäßiges Verhalten beim Kopieren und Einfügen
 To enable copying, set the **Enable Copy Paste** property of the **Editor** node in DSL Explorer.

 Wenn der Benutzer Elemente in die Zwischenablage kopiert, werden standardmäßig auch die folgenden Elemente kopiert:

- Eingebettete Nachfolger der ausgewählten Elemente. (Also Elemente, die Ziele von Einbettungsbeziehungen sind, deren Quelle kopierte Elemente sind.)

- Beziehungslinks zwischen kopierten Elementen.

  Diese Regel gilt rekursiv für die kopierten Elemente und Links.

  ![Copied and pasted elements](../modeling/media/dslcopypastedefault.png "DslCopyPasteDefault")

  Die kopierten Elemente und Links werden serialisiert und in einem <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> (EGP) gespeichert, der in der Zwischenablage platziert wird.

  Ein Bild der kopierten Elemente wird ebenfalls in die Zwischenablage aufgenommen. Dies ermöglicht das Einfügen in andere Anwendungen wie Word.

  Der Benutzer kann kopierte Elemente in ein Ziel einfügen, das gemäß DSL-Definition die Elemente akzeptiert. In einer DSL, die aus der Projektmappenvorlage "Komponenten" generiert wurde, kann der Benutzer beispielsweise Ports in Komponenten einfügen, nicht aber in das Diagramm. Und er kann Komponenten in das Diagramm einfügen, nicht aber in andere Komponenten.

## <a name="customizing-copy-and-paste-behavior"></a>Anpassen des Verhaltens beim Kopieren und Einfügen
 For more information about customizing the model by using program code, see [Navigating and Updating a Model in Program Code](../modeling/navigating-and-updating-a-model-in-program-code.md).

 **Enable or disable copy, cut, and paste.**
In DSL Explorer, set the **Enable Copy Paste** property of the **Editor** node.

 **Copy links to the same target.** For example, to have a copied comment box linked to the same subject element.
Set the **Propagates Copy** property of the role to **Propagate copy to link only**. For more information, see [Customizing Link Copy Behavior](#customizeLinks).

 Kopieren Sie verknüpfte Elemente. Wenn Sie ein neues Element kopieren, werden beispielsweise auch Kopien verknüpfter Kommentarfelder erstellt.
Set the **Propagates Copy** property of the role to **Propagate copy to link and opposite role player**. For more information, see [Customizing Link Copy Behavior](#customizeLinks).

 **Rapidly duplicate elements by copying and pasting.** Normally, the item you just copied is still selected, and you cannot paste the same type of element onto it.
Fügen Sie der Domänenklasse eine Direktive für Elementzusammenführungen hinzu, und legen Sie sie für vorwärts gerichtete Zusammenführungen in der übergeordneten Klasse fest. Dies hat die gleichen Auswirkungen auf Ziehvorgänge. For more information, see [Customizing Element Creation and Movement](../modeling/customizing-element-creation-and-movement.md).

 \- oder -

 Wählen Sie vor dem Einfügen der Elemente das Diagramm aus, indem Sie `ClipboardCommandSet.ProcessOnPasteCommand()` überschreiben. Fügen Sie diesen Code in einer benutzerdefinierten Datei im DslPackage-Projekt hinzu:

```csharp
namespace Company.MyDsl {
using System.Linq;
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Shell;
partial class MyDslClipboardCommandSet
{
  protected override void ProcessOnMenuPasteCommand()
  {
 // Deselect the current selection after copying:
 Diagram diagram = (this.CurrentModelingDocView as SingleDiagramDocView).Diagram;
    this.CurrentModelingDocView
     .SelectObjects(1, new object[] { diagram }, 0);
  }
} }

```

 **Create additional links when the user pastes onto a selected target.** For example, when a comment box is pasted onto an element, a link is made between them.
Fügen Sie der Zieldomänenklasse eine Direktive für Elementzusammenführungen hinzu, und legen Sie für sie fest, dass die Zusammenführung durch Hinzufügen von Links verarbeitet wird. Dies hat die gleichen Auswirkungen auf Ziehvorgänge. For more information, see [Customizing Element Creation and Movement](../modeling/customizing-element-creation-and-movement.md).

 \- oder -

 Überschreiben Sie `ClipboardCommandSet.ProcessOnPasteCommand()`, um nach dem Aufruf der Basismethode weitere Links zu erstellen.

 **Customize the formats in which elements can be copied** to external applications – for example, to add a border to the bitmap form.
Override *MyDsl*`ClipboardCommandSet.ProcessOnMenuCopyCommand()` in the DslPackage project.

 **Customize how elements are copied to the clipboard by the copy command, but not in a drag operation.**
Override *MyDsl*`ClipboardCommandSet.CopyModelElementsIntoElementGroupPrototype()` in the DslPackage project.

 **Preserve shape layout through copy and paste.**
Wenn der Benutzer mehrere Formen kopiert, können Sie deren relative Positionen beim Einfügen erhalten. This technique is demonstrated by the example at [VMSDK: Circuit Diagrams sample](https://go.microsoft.com/fwlink/?LinkId=213879).

 Sie können diesen Effekt erreichen, indem Sie dem kopierten ElementGroupPrototype Formen und Konnektoren hinzufügen. Für das Überschreiben empfiehlt sich ElementOperations.CreateElementGroupPrototype(). Fügen Sie dem Dsl-Projekt zu diesem Zweck den folgenden Code hinzu:

```csharp

public class MyElementOperations : DesignSurfaceElementOperations
{
  // Create an EGP to add to the clipboard.
  // Called when the elements to be copied have been
  // collected into an ElementGroup.
 protected override ElementGroupPrototype CreateElementGroupPrototype(ElementGroup elementGroup, ICollection<ModelElement> elements, ClosureType closureType)
  {
 // Add the shapes and connectors:
 // Get the elements already in the group:
    ModelElement[] mels = elementGroup.ModelElements
        .Concat(elementGroup.ElementLinks) // Omit if the paste target is not the diagram.
        .ToArray();
 // Get their shapes:
    IEnumerable<PresentationElement> shapes =
       mels.SelectMany(mel =>
            PresentationViewsSubject.GetPresentation(mel));
    elementGroup.AddRange(shapes);

 return base.CreateElementGroupPrototype
           (elementGroup, elements, closureType);
  }

 public MyElementOperations(IServiceProvider serviceProvider, ElementOps1Diagram diagram)
      : base(serviceProvider, diagram)
  { }
}

// Replace the standard ElementOperations
// singleton with your own:
partial class MyDslDiagram // EDIT NAME
{
 /// <summary>
 /// Singleton ElementOperations attached to this diagram.
 /// </summary>
 public override DesignSurfaceElementOperations ElementOperations
  {
 get
    {
 if (singleton == null)
      {
        singleton = new MyElementOperations(this.Store as IServiceProvider, this);
      }
 return singleton;
    }
  }
 private MyElementOperations singleton = null;
}

```

 **Paste shapes in a chosen location, such as the current cursor position.**
Wenn der Benutzer mehrere Formen kopiert, können Sie deren relative Positionen beim Einfügen erhalten. This technique is demonstrated by the example at [VMSDK: Circuit Diagrams sample](https://go.microsoft.com/fwlink/?LinkId=213879).

 Diesen Effekt erreichen Sie, indem Sie `ClipboardCommandSet.ProcessOnMenuPasteCommand()` überschreiben, sodass die positionsspezifische Version von `ElementOperations.Merge()` verwendet wird. Fügen Sie dem DslPackage-Projekt zu diesem Zweck den folgenden Code hinzu:

```csharp

partial class MyDslClipboardCommandSet // EDIT NAME
{
   /// <summary>
    /// This method assumes we only want to paste things onto the diagram
    /// - not onto anything contained in the diagram.
    /// The base method pastes in a free space on the diagram.
    /// But if the menu was used to invoke paste, we want to paste in the cursor position.
    /// </summary>
    protected override void ProcessOnMenuPasteCommand()
    {

  NestedShapesSampleDocView docView = this.CurrentModelingDocView as NestedShapesSampleDocView;

      // Retrieve data from clipboard:
      System.Windows.Forms.IDataObject data = System.Windows.Forms.Clipboard.GetDataObject();

      Diagram diagram = docView.CurrentDiagram;
      if (diagram == null) return;

      if (!docView.IsContextMenuShowing)
      {
        // User hit CTRL+V - just use base method.

        // Deselect anything that's selected, otherwise
        // pasted item will be incompatible:
        if (!this.IsDiagramSelected())
        {
          docView.SelectObjects(1, new object[] { diagram }, 0);
        }

        // Paste into a convenient spare space on diagram:
    base.ProcessOnMenuPasteCommand();
      }
      else
      {
        // User right-clicked - paste at mouse position.

        // Utility class:
        DesignSurfaceElementOperations op = diagram.ElementOperations;

        ShapeElement pasteTarget = diagram;

        // Check whether what's in the paste buffer is acceptable on the target.
        if (pasteTarget != null && op.CanMerge(pasteTarget, data))
        {

        // Although op.Merge would be a no-op if CanMerge failed, we check CanMerge first
          // so that we don't create an empty transaction (after which Undo would be no-op).
          using (Transaction t = diagram.Store.TransactionManager.BeginTransaction("paste"))
          {
            PointD place = docView.ContextMenuMousePosition;
            op.Merge(pasteTarget, data, PointD.ToPointF(place));
            t.Commit();
          }
        }
      }
    }
  }
```

 **Let the user drag and drop elements.**
See [How to: Add a Drag-and-Drop Handler](../modeling/how-to-add-a-drag-and-drop-handler.md).

## <a name="customizeLinks"></a> Customizing Link Copy Behavior
 Wenn der Benutzer ein Element kopiert, ist das Standardverhalten, dass etwaige eingebettete Elemente ebenfalls kopiert werden. Sie können das standardmäßige Kopierverhalten ändern. In the DSL Definition, select a role at one side of a relationship and in the Properties window set the **Propagates Copy** value.

 ![Propagates Copy property of domain role](../modeling/media/dslpropagatescopy.png "DslPropagatesCopy")

 Es gibt drei Werte:

- Kopie nicht übertragen

- Kopie nur an Link übertragen – Wenn die Gruppe eingefügt wird, verweist die neue Kopie dieses Links auf das vorhandene Element am anderen Ende des Links.

- Kopie an Link und Inhaber der Gegenrolle übertragen – Die kopierte Gruppe enthält eine Kopie des Elements am anderen Ende des Links.

  ![Effect of copying with PropagateCopyToLinkOnly](../modeling/media/dslpropagatecopy.png "DslPropagateCopy")

  Die Änderungen, die Sie vornehmen, haben Auswirkungen auf die Elemente und das kopierte Bild.

## <a name="programming-copy-and-paste-behavior"></a>Programmieren des Verhaltens beim Kopieren und Einfügen
 Viele Aspekte des DSL-Verhaltens beim Kopieren, Einfügen, Erstellen und Löschen von Objekten werden von einer Instanz von <xref:Microsoft.VisualStudio.Modeling.ElementOperations> gesteuert, die mit dem Diagramm verknüpft ist. Sie können das DSL-Verhalten ändern, indem Sie eine eigene Klasse von <xref:Microsoft.VisualStudio.Modeling.ElementOperations> ableiten und die Eigenschaft <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.ElementOperations%2A> Ihrer Diagrammklasse überschreiben.

> [!TIP]
> For more information about customizing the model by using program code, see [Navigating and Updating a Model in Program Code](../modeling/navigating-and-updating-a-model-in-program-code.md).

 ![Sequence diagram for the Copy operation](../modeling/media/dslcopyseqdiagram.png "dslCopySeqDiagram")

 ![Sequence diagram of Paste operation](../modeling/media/dslpasteseqdiagram.png "dslPasteSeqDiagram")

#### <a name="to-define-your-own-elementoperations"></a>So definieren Sie eine eigene ElementOperations-Klasse

1. Erstellen Sie in einer neuen Datei in Ihrem DSL-Projekt eine Klasse, die von <xref:Microsoft.VisualStudio.Modeling.Diagrams.DesignSurfaceElementOperations> abgeleitet ist.

2. Fügen Sie eine partielle Klassendefinition für Ihre Diagrammklasse hinzu. The name of this class can be found in **Dsl\GeneratedCode\Diagrams.cs**.

    In the diagram class, override  <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.ElementOperations%2A> to return an instance of your ElementOperations subclass. Sie sollten bei jedem Aufruf die gleiche Instanz zurückgeben.

   Fügen Sie diesen Code in einer benutzerdefinierten Codedatei im DslPackage-Projekt hinzu:

```csharp

using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;

  public partial class MyDslDiagram
  {
    public override DesignSurfaceElementOperations ElementOperations
    {
      get
      {
        if (this.elementOperations == null)
        {
          this.elementOperations = new MyElementOperations(this.Store as IServiceProvider, this);
        }
        return this.elementOperations;
      }
    }
    private MyElementOperations elementOperations = null;
  }

  public class MyElementOperations : DesignSurfaceElementOperations
  {
    public MyElementOperations(IServiceProvider serviceProvider, MyDslDiagram diagram)
      : base(serviceProvider, diagram)
    { }
    // Overridden methods follow
  }

```

## <a name="receiving-items-dragged-from-other-models"></a>Empfangen von Elementen, die aus anderen Modellen gezogen wurden
 Mit ElementOperations kann auch das Verhalten von Kopier-, Verschiebe-, Lösch- und Drag &amp; Drop-Vorgängen definiert werden. Zur Veranschaulichung der Verwendung von ElementOperations wird im hier angegebenen Beispiel ein benutzerdefiniertes Drag &amp; Drop-Verhalten konfiguriert. However, for that purpose you might consider the alternative approach described in [How to: Add a Drag-and-Drop Handler](../modeling/how-to-add-a-drag-and-drop-handler.md), which is more extensible.

 Definieren Sie zwei Methoden in Ihrer ElementOperations-Klasse:

- `CanMerge(ModelElement targetElement, System.Windows.Forms.IDataObject data)` bestimmt, ob das Quellelement auf die Zielform, den Zielkonnektor oder das Zieldiagramm gezogen werden kann.

- `MergeElementGroupPrototype(ModelElement targetElement, ElementGroupPrototype sourcePrototype)` kombiniert das Quellelement im Ziel.

### <a name="canmerge"></a>CanMerge()
 `CanMerge()` wird aufgerufen, um Feedback für den Benutzer festzulegen, wenn er die Maus über das Diagramm bewegt. Die Parameter der Methode sind die Elemente, über die die Maus bewegt wird, sowie die Daten zur Quelle, aus der der Ziehvorgang durchgeführt wurde. Der Benutzer kann von überall auf dem Bildschirm ziehen. Daher kann das Quellobjekt viele verschiedene Typen aufweisen und in unterschiedlichen Formaten serialisiert werden. Wenn die Quelle ein DSL- oder UML-Modell ist, ist der Datenparameter die Serialisierung von <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype>. Zieh-, Kopier- und Toolboxvorgänge verwenden ElementGroupPrototypes zur Darstellung von Fragmenten von Modellen.

 Ein Elementgruppenprototyp kann eine beliebige Anzahl von Elementen und Links enthalten. Elementtypen können anhand ihrer GUIDs identifiziert werden. Die GUID ist die Form, die gezogen wurde, und nicht das zugrunde liegende Modellelement. Im folgenden Beispiel gibt `CanMerge()` "true" zurück, wenn eine Klassenform aus einem UML-Diagramm in dieses Diagramm gezogen wird.

```csharp
public override bool CanMerge(ModelElement targetShape, System.Windows.Forms.IDataObject data)
 {
  // Extract the element prototype from the data.
  ElementGroupPrototype prototype = ElementOperations.GetElementGroupPrototype(this.ServiceProvider, data);
  if (targetShape is MyTargetShape && prototype != null &&
        prototype.RootProtoElements.Any(rootElement =>
          rootElement.DomainClassId.ToString()
          ==  "3866d10c-cc4e-438b-b46f-bb24380e1678")) // Guid of UML Class shapes
          // or SourceClass.DomainClassId
        return true;
   return base.CanMerge(targetShape, data);
 }

```

## <a name="mergeelementgroupprototype"></a>MergeElementGroupPrototype()
 Diese Methode wird aufgerufen, wenn der Benutzer ein Element auf einem Diagramm, einer Form oder einem Konnektor ablegt. Sie sollte den gezogenen Inhalt im Zielelement zusammenführen. In diesem Beispiel bestimmt der Code, ob die Kombination der Typen des Ziels und des Prototyps erkannt wird. Falls ja, konvertiert die Methode die gezogenen Elemente in einen Prototyp der Elemente, die dem Modell hinzugefügt werden sollen. Die Basismethode wird aufgerufen, um die Zusammenführung der konvertieren oder nicht konvertieren Elemente vorzunehmen.

```csharp
public override void MergeElementGroupPrototype(ModelElement targetShape, ElementGroupPrototype sourcePrototype)
{
  ElementGroupPrototype prototypeToMerge = sourcePrototype;
  MyTargetShape pel = targetShape as MyTargetShape;
  if (pel != null)
  {
    prototypeToMerge = ConvertDraggedTypeToLocal(pel, sourcePrototype);
  }
  if (prototypeToMerge != null)
    base.MergeElementGroupPrototype(targetShape, prototypeToMerge);
}

```

 In diesem Beispiel werden UML-Klassenelemente verarbeitet, die aus einem UML-Klassendiagramm gezogen werden. Die DSL ist nicht dafür vorgesehen, UML-Klassen direkt zu speichern. Stattdessen wird für jede gezogene UML-Klasse ein DSL-Element erstellt. Dies ist z. B. dann nützlich, wenn die DSL ein Instanzendiagramm ist. Der Benutzer könnte Klassen auf das Diagramm ziehen, um Instanzen dieser Klassen zu erstellen.

```csharp

private ElementGroupPrototype ConvertDraggedTypeToLocal (MyTargetShape snapshot, ElementGroupPrototype prototype)
{
  // Find the UML project:
  EnvDTE.DTE dte = snapshot.Store.GetService(typeof(EnvDTE.DTE)) as EnvDTE.DTE;
  foreach (EnvDTE.Project project in dte.Solution.Projects)
  {
    IModelingProject modelingProject = project as IModelingProject;
    if (modelingProject == null) continue; // not a modeling project
    IModelStore store = modelingProject.Store;
    if (store == null) continue;
    // Look for the shape that was dragged:
    foreach (IDiagram umlDiagram in store.Diagrams())
    {
      // Get modeling diagram that implements UML diagram:
      Diagram diagram = umlDiagram.GetObject<Diagram>();
      Guid elementId = prototype.SourceRootElementIds.FirstOrDefault();
      ShapeElement shape = diagram.Partition.ElementDirectory.FindElement(elementId) as ShapeElement;
      if (shape == null) continue;
      IClass classElement = shape.ModelElement as IClass;
      if (classElement == null) continue;

      // Create a prototype of elements in my DSL, based on the UML element:
      Instance instance = new Instance(snapshot.Store);
      instance.Type = classElement.Name;
      // Pack them into a prototype:
      ElementGroup group = new ElementGroup(instance);
      return group.CreatePrototype();
    }
  }
  return null;
}

```

## <a name="standard-copy-behavior"></a>Standardmäßiges Kopierverhalten
 Der Code in diesem Abschnitt veranschaulicht Methoden, die Sie überschreiben können, um das Kopierverhalten zu ändern. Um Ihnen zu zeigen, wie Sie eigene Anpassungen erreichen, wird in diesem Abschnitt Code dargestellt, mit dem die an Kopiervorgängen beteiligten Methoden überschrieben werden. Das Standardverhalten wird jedoch nicht geändert.

 Wenn der Benutzer STRG+C drückt oder den Menübefehl "Kopieren" verwendet, wird die Methode <xref:Microsoft.VisualStudio.Modeling.Shell.ClipboardCommandSet.ProcessOnMenuCopyCommand%2A> aufgerufen. You can see how this is set up in **DslPackage\Generated Code\CommandSet.cs**. For more information about how commands are set up, see [How to: Add a Command to the Shortcut Menu](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).

 You can override ProcessOnMenuCopyCommand by adding a partial class definition of *MyDsl*`ClipboardCommandSet` in the DslPackage project.

```csharp
using System.Collections.Generic;
using System.Drawing;
using System.Windows.Forms;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;

partial class MyDslClipboardCommandSet
{
  /// <summary>
  /// Override ProcessOnMenuCopyCommand() to copy elements to the
  /// clipboard in different formats, or to perform additional tasks
  /// before or after copying – for example deselect the copied elements.
  /// </summary>
  protected override void ProcessOnMenuCopyCommand()
  {
    IList<ModelElement> selectedModelElements = this.SelectedElements;
    if (selectedModelElements.Count == 0) return;

    // System container for clipboard data.
    // The IDataObject can contain data in several formats.
    IDataObject dataObject = new DataObject();

    Bitmap bitmap = null; // For export to other programs.
    try
    {
      #region Create EGP for copying to a DSL.
      this.CopyModelElementsIntoElementGroupPrototype
                     (dataObject, selectedModelElements);
      #endregion

      #region Create bitmap for copying to another application.
      // Find all the shapes associated with this selection:
      List<ShapeElement> shapes = new List<ShapeElement>(
        this.ResolveExportedShapesForClipboardImages
              (dataObject, selectedModelElements));

      bitmap = this.CreateBitmapForClipboard(shapes);
      if (bitmap != null)
      {
        dataObject.SetData(DataFormats.Bitmap, bitmap);
      }
      #endregion

      // Add the data to the clipboard:
      Clipboard.SetDataObject(dataObject, true, 5, 100);
    }
    finally
    {
      // Dispose bitmap after SetDataObject:
      if (bitmap != null) bitmap.Dispose();
    }
  }
/// <summary>
/// Override this to customize the element group that is copied to the clipboard.
/// </summary>
protected override void CopyModelElementsIntoElementGroupPrototype(IDataObject dataObject, IList<ModelElement> selectedModelElements)
{
  return this.ElementOperations.Copy(dataObject, selectedModelElements);
}
}
```

 Jedes Diagramm weist eine Singleton-Instanz von ElementOperations auf. Sie können eigene Ableitungen bereitstellen. Diese Datei, die in das DSL-Projekt aufgenommen werden kann, verhält sich wie der Code, den sie überschreibt:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;

namespace Company.MyDsl
{
  partial class MyDslDiagram
  {
    /// <summary>
    /// Singleton ElementOperations attached to this diagram.
    /// </summary>
    public override DesignSurfaceElementOperations ElementOperations
    {
      get
      {
        if (this.elementOperations == null)
        {
          this.elementOperations = new MyElementOperations(this.Store as IServiceProvider, this);
        }
        return this.elementOperations;
      }
    }
    private MyElementOperations elementOperations = null;
  }

  // Our own version of ElementOperations so that we can override:
  public class MyElementOperations : DesignSurfaceElementOperations
  {
    public MyElementOperations(IServiceProvider serviceProvider, ElementOps1Diagram diagram)
      : base(serviceProvider, diagram)
    { }

    /// <summary>
    /// Copy elements to the clipboard data.
    /// Provides a hook for adding custom data.
    /// </summary>
    public override void Copy(System.Windows.Forms.IDataObject data,
      ICollection<ModelElement> elements,
      ClosureType closureType,
      System.Drawing.PointF sourcePosition)
    {
      if (CanAddElementGroupFormat(elements, closureType))
      {
        AddElementGroupFormat(data, elements, closureType);
      }

      // Override these to store additional data:
      if (CanAddCustomFormat(elements, closureType))
      {
        AddCustomFormat(data, elements, closureType, sourcePosition);
      }
    }

    protected override void AddElementGroupFormat(System.Windows.Forms.IDataObject data, ICollection<ModelElement> elements, ClosureType closureType)
    {
      // Add the selected elements and those implied by the propagate copy rules:
      ElementGroup elementGroup = this.CreateElementGroup(elements, closureType);

      // Mark all the elements that are not embedded under other elements:
      this.MarkRootElements(elementGroup, elements, closureType);

      // Store in the clipboard data:
      ElementGroupPrototype elementGroupPrototype = this.CreateElementGroupPrototype(elementGroup, elements, closureType);
      data.SetData(ElementGroupPrototype.DefaultDataFormatName, elementGroupPrototype);
    }

    /// <summary>
    /// Override this to store additional elements in the element group:
    /// </summary>
    protected override ElementGroupPrototype CreateElementGroupPrototype(ElementGroup elementGroup, ICollection<ModelElement> elements, ClosureType closureType)
    {
      ElementGroupPrototype prototype = new ElementGroupPrototype(this.Partition, elementGroup.RootElements, elementGroup);
      return prototype;
    }

    /// <summary>
    /// Create an element group from the given starting elements, using the
    /// copy propagation rules specified in the DSL Definition.
    /// By default, this includes all the embedded descendants of the starting elements,
    /// and also includes reference links where both ends are already included.
    /// </summary>
    /// <param name="startElements">model elements to copy</param>
    /// <param name="closureType"></param>
    /// <returns></returns>
    protected override ElementGroup CreateElementGroup(ICollection<ModelElement> startElements, ClosureType closureType)
    {
      // ElementClosureWalker finds all the connected elements,
      // according to the propagate copy rules specified in the DSL Definition:
      ElementClosureWalker walker = new ElementClosureWalker(this.Partition,
        closureType, // Normally ClosureType.CopyClosure
        startElements,
        true, // Do not load other models.
        null, // Optional list of domain roles not to traverse.
        true); // Include relationship links where both ends are already included.

      walker.Traverse(startElements);
      IList<ModelElement> closureList = walker.ClosureList;
      Dictionary<object, object> closureContext = walker.Context;

      // create a group for this closure
      ElementGroup group = new ElementGroup(this.Partition);
      group.AddRange(closureList, false);

      // create the element group prototype for the group
      foreach (object key in closureContext.Keys)
      {
        group.SourceContext.ContextInfo[key] = closureContext[key];
      }

      return group;
    }
  }
}

```

## <a name="see-also"></a>Siehe auch
 [Customizing Element Creation and Movement](../modeling/customizing-element-creation-and-movement.md) [How to: Add a Drag-and-Drop Handler](../modeling/how-to-add-a-drag-and-drop-handler.md) [Customizing Deletion Behavior](../modeling/customizing-deletion-behavior.md) [Sample: VMSDK Circuit Diagrams sample](https://go.microsoft.com/fwlink/?LinkId=213879)
