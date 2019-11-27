---
title: Definieren eines Gesten Handlers in einem Modellierungs Diagramm | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending, double-click
- UML - extending, drag and drop
ms.assetid: e5e1d70a-3539-4321-a3b1-89e86e4d6430
caps.latest.revision: 36
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bf749d1073faf4cf22febafce716af36b47c6484
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299307"
---
# <a name="define-a-gesture-handler-on-a-modeling-diagram"></a>Definieren eines Gestenhandlers in einem Modellierungsdiagramm
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio können Sie Befehle definieren, die ausgeführt werden, wenn Benutzer auf Elemente doppelklicken oder Elemente in ein UML-Diagramm ziehen. Sie können diese Erweiterungen in eine Visual Studio-Integrationserweiterung ([VSIX](https://go.microsoft.com/fwlink/?LinkId=160780)) packen, die Sie an andere Visual Studio-Benutzer verteilen können.

 Wenn bereits ein integriertes Verhalten für den Diagrammtyp und den Elementtyp vorhanden ist, das gezogen werden soll, können Sie dieses Verhalten möglicherweise nicht hinzufügen oder überschreiben.

## <a name="requirements"></a>Voraussetzungen
 Siehe [Anforderungen](../modeling/extend-uml-models-and-diagrams.md#Requirements).

 Welche Versionen von Visual Studio dieses Feature unterstützen, erfahren Sie unter [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="creating-a-gesture-handler"></a>Erstellen eines Gestenhandlers
 Um für einen UML-Designer einen Gestenhandler zu definieren, müssen Sie eine Klasse erstellen, die das Verhalten des Gestenhandlers definiert, und diese Klasse in eine Visual Studio-Integrationserweiterung (VSIX) einbetten. Die VSIX fungiert als Container, der den Handler installieren kann. Es gibt zwei alternative Methoden, um einen Gestenhandler zu definieren:

- **Erstellen Sie einen Gesten Handler in seiner eigenen VSIX mithilfe einer Projektvorlage.** Dies ist die schnellere Methode. Verwenden Sie diese, wenn Sie den Handler nicht mit anderen Erweiterungstypen, z. B. Validierungserweiterungen, benutzerdefinierten Toolboxelementen oder Menübefehlen, kombinieren möchten.

- **Erstellen Sie separate Gesten Handler und VSIX-Projekte.** Verwenden Sie diese Methode, wenn Sie mehrere Erweiterungstypen in dieselbe VSIX kombinieren möchten. Wenn beispielsweise der Gestenhandler erwartet, dass das Modell bestimmte Einschränkungen berücksichtigt, können Sie es in dieselbe VSIX wie eine Validierungsmethode einbetten.

#### <a name="to-create-a-gesture-handler-in-its-own-vsix"></a>So erstellen Sie einen Gestenhandler in seiner eigenen VSIX

1. Klicken Sie im Dialogfeld **Neues Projekt** unter **Modellierungsprojekte**auf **Gestenerweiterung**.

2. Öffnen Sie die **.cs** -Datei im neuen Projekt, und ändern Sie die `GestureExtension` -Klasse, um den Gestenhandler zu implementieren.

    Weitere Informationen finden Sie unter [Implementieren des Gestenhandlers](#Implementing).

3. Testen Sie den Gestenhandler durch Drücken von F5. Weitere Informationen finden Sie unter [Ausführen des Gestenhandlers](#Executing).

4. Installieren Sie den Gesten Handler auf einem anderen Computer, indem Sie den Datei- **bin\\\*\\\*. vsix** kopieren, die vom Projekt erstellt wurde. Weitere Informationen finden Sie unter [Installieren und Deinstallieren einer Erweiterung](#Installing).

   Es gibt ein alternatives Verfahren:

#### <a name="to-create-a-separate-class-library-dll-project-for-the-gesture-handler"></a>So erstellen Sie ein separates Klassenbibliotheksprojekt (DLL) für den Gestenhandler

1. Erstellen Sie in einer neuen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Projektmappe oder in einer vorhandenen Projektmappe ein Klassenbibliotheksprojekt.

   1. Wählen Sie im Menü **Datei** die Befehle **Neu** und **Projekt** aus.

   2. Erweitern Sie unter **Installierte Vorlagen**entweder **Visual C#** oder **Visual Basic**, und wählen Sie anschließend in der mittleren Spalte **Klassenbibliothek**aus.

2. Fügen Sie dem Projekt die folgenden Verweise hinzu.

    `Microsoft.VisualStudio.Modeling.Sdk.[version]`

    `Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[version]`

    `Microsoft.VisualStudio.ArchitectureTools.Extensibility`

    `Microsoft.VisualStudio.Uml.Interfaces`

    `System.ComponentModel.Composition`

    `System.Windows.Forms`

    `Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer` – Dies ist nur erforderlich, wenn Sie Ebenendiagramme erweitern. Weitere Informationen finden Sie unter [Erweitern von ebenendiagrammen](../modeling/extend-layer-diagrams.md).

3. Fügen Sie dem Projekt eine Klassendatei hinzu, und legen Sie deren Inhalt auf den folgenden Code fest.

   > [!NOTE]
   > Ändern Sie die Namespace- und Klassennamen entsprechend den jeweiligen Anforderungen.

   ```
   using System.ComponentModel.Composition;
   using System.Linq;
   using System.Collections.Generic;
   using Microsoft.VisualStudio.Modeling.Diagrams;
   using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
   using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
   using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
   using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
   using Microsoft.VisualStudio.Uml.AuxiliaryConstructs;
   using Microsoft.VisualStudio.Modeling;
   using Microsoft.VisualStudio.Uml.Classes;
   // ADD other UML namespaces if required

   namespace MyGestureHandler // CHANGE
   {
     // DELETE any of these attributes if the handler
     // should not work with some types of diagram.
     [ClassDesignerExtension]
     [ActivityDesignerExtension]
     [ComponentDesignerExtension]
     [SequenceDesignerExtension]
     [UseCaseDesignerExtension]
     // [LayerDesignerExtension]

     // Gesture handlers must export IGestureExtension:
     [Export(typeof(IGestureExtension))]
     // CHANGE class name
     public class MyGesture1 : IGestureExtension
     {
       [Import]
       public IDiagramContext DiagramContext { get; set; }

       /// <summary>
       /// Called when the user double-clicks on the diagram
       /// </summary>
       /// <param name="targetElement"></param>
       /// <param name="diagramPointEventArgs"></param>
       public void OnDoubleClick(ShapeElement targetElement, DiagramPointEventArgs diagramPointEventArgs)
       {
         // CHANGE THIS CODE FOR YOUR APPLICATION.

         // Get the target shape, if any. Null if the target is the diagram.
         IShape targetIShape = targetElement.CreateIShape();

         // Do something...
       }

       /// <summary>
       /// Called repeatedly when the user drags from anywhere on the screen.
       /// Return value should indicate whether a drop here is allowed.
       /// </summary>
       /// <param name="targetMergeElement">References the element to be dropped on.</param>
       /// <param name="diagramDragEventArgs">References the element to be dropped.</param>
       /// <returns></returns>
       public bool CanDragDrop(ShapeElement targetMergeElement, DiagramDragEventArgs diagramDragEventArgs)
       {
         // CHANGE THIS CODE FOR YOUR APPLICATION.

         // Get the target element, if any. Null if the target is the diagram.
         IShape targetIShape = targetMergeElement.CreateIShape();

         // This example allows drag of any UML elements.
         return GetModelElementsFromDragEvent(diagramDragEventArgs).Count() > 0;
       }

       /// <summary>
       /// Execute the action to be performed on the drop.
       /// </summary>
       /// <param name="targetDropElement"></param>
       /// <param name="diagramDragEventArgs"></param>
       public void OnDragDrop(ShapeElement targetDropElement, DiagramDragEventArgs diagramDragEventArgs)
       {
         // CHANGE THIS CODE FOR YOUR APPLICATION.
       }

       /// <summary>
       /// Retrieves UML IElements from drag arguments.
       /// Works for drags from UML diagrams.
       /// </summary>
       private IEnumerable<IElement> GetModelElementsFromDragEvent
               (DiagramDragEventArgs dragEvent)
       {
         //ElementGroupPrototype is the container for
         //dragged and copied elements and toolbox items.
         ElementGroupPrototype prototype =
            dragEvent.Data.
            GetData(typeof(ElementGroupPrototype))
                 as ElementGroupPrototype;
         // Locate the originals in the implementation store.
         IElementDirectory implementationDirectory =
            dragEvent.DiagramClientView.Diagram.Store.ElementDirectory;

         return prototype.ProtoElements.Select(
           prototypeElement =>
           {
             ModelElement element = implementationDirectory
               .FindElement(prototypeElement.ElementId);
             ShapeElement shapeElement = element as ShapeElement;
             if (shapeElement != null)
             {
               // Dragged from a diagram.
               return shapeElement.ModelElement as IElement;
             }
             else
             {
               // Dragged from UML Model Explorer.
               return element as IElement;
             }
           });
       }

     }
   }

   ```

    Weitere Informationen zum Füllen der Methoden finden Sie unter [Implementieren des Gestenhandlers](#Implementing).

   Sie müssen den Menübefehl einem VSIX-Projekt hinzufügen, das als Container für die Installation des Befehls fungiert. Gegebenenfalls können Sie in dasselbe VSIX auch weitere Komponenten einschließen.

#### <a name="to-add-a-separate-gesture-handler-to-a-vsix-project"></a>So fügen Sie einem VSIX-Projekt einen separaten Gestenhandler hinzu

1. Diese Prozedur ist nicht erforderlich, wenn Sie den Gestenhandler mit einer eigenen VSIX erstellt haben.

2. Erstellen Sie ein VSIX-Projekt, sofern die Projektmappe noch kein VSIX-Projekt enthält.

    1. Wählen Sie im **Projektmappen-Explorer**im Kontextmenü der Projektmappe die Option **Hinzufügen**und dann **Neues Projekt**aus.

    2. Erweitern Sie unter **Installierte Vorlagen**den Knoten **Visual C#** oder **Visual Basic**, und wählen Sie anschließend **Erweiterungen**aus. Wählen Sie in der mittleren Spalte **VSIX Project**.

3. Legen Sie das VSIX-Projekt als Startprojekt der Projektmappe fest.

    - Wählen Sie im Projektmappen-Explorer im Kontextmenü des VSIX-Projekts die Option **Als Startprojekt festlegen**aus.

4. Fügen Sie das Gestenhandler-Klassenbibliotheksprojekt als MEF-Komponente im **source.extension.vsixmanifest**hinzu:

    1. Legen Sie auf der Registerkarte **MetaData** einen Namen für VSIX fest.

    2. Legen Sie auf der Registerkarte **Ziele installieren** die Visual Studio-Versionen als Ziele fest.

    3. Wählen Sie auf der Registerkarte **Objekte** die Option **Neu**und wählen Sie im Dialogfeld:

         **Typ** = **MEF-Komponente**

         **Quelle** = **Ein Projekt in der aktuellen Projektmappe**

         **Projekt** = *Ihr Klassenbibliotheksprojekt*

## <a name="Executing"></a>Ausführen des Gesten Handlers
 Führen Sie den Gestenhandler zu Testzwecken im Debugmodus aus.

#### <a name="to-test-the-gesture-handler"></a>So testen Sie den Gestenhandler

1. Drücken Sie **F5**, oder klicken Sie im Menü **Debuggen** auf **Debuggen starten**.

    Eine experimentelle Instanz von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] wird gestartet.

    **Problembehandlung**: Wenn ein neuer [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nicht startet:

   - Wenn Sie mehr als ein Projekt haben, stellen Sie sicher, dass das VSIX-Projekt als Startprojekt der Projektmappe festgelegt wird.

   - Öffnen Sie im Projektmappen-Explorer das Kontextmenü für das Start- oder einzelne Projekt und wählen Sie Eigenschaften aus. Wählen Sie im Projekteigenschaften-Editor die Registerkarte **Debuggen** aus. Stellen Sie sicher, dass die Zeichenfolge im Feld **externes Programm starten** der vollständige Pfadname [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]ist, in der Regel:

        `C:\Program Files\Microsoft Visual Studio [version]\Common7\IDE\devenv.exe`

2. Öffnen oder erstellen Sie in der experimentellen Instanz von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]ein Modellierungsprojekt, und öffnen oder erstellen Sie ein Modellierungsdiagramm. Verwenden Sie ein Diagramm, das zu einem der Typen gehört, die in den Attributen der Gestenhandlerklasse aufgeführt sind.

3. Doppelklicken Sie auf eine beliebige Stelle im Diagramm. Der Doppelklickhandler sollte aufgerufen werden.

4. Ziehen Sie ein Element aus dem UML-Explorer auf das Diagramm. Der Ziehhandler sollte aufgerufen werden.

   **Problembehandlung:** Wenn der Gestenhandler nicht ordnungsgemäß funktioniert, stellen Sie Folgendes sicher:

- Das Gestenhandlerprojekt ist im VSIX-Projekt als MEF-Komponente auf der Registerkarte **Objekte** im **source.extensions.manifest** aufgeführt.

- Die Parameter aller `Import` -Attribute und `Export` -Attribute sind gültig.

- Die `CanDragDrop` -Methode gibt nicht `false`zurück.

- Der verwendete Modelldiagrammtyp (UML-Klasse, Sequenz usw.) ist als eines der Gestenhandler-Klassenattribute [ClassDesignerExtension], [SequenceDesignerExtension] usw. aufgeführt.

- Für diesen Typ des Zielelements und des abgelegten Elements ist noch keine integrierte Funktionalität definiert.

## <a name="Implementing"></a>Implementieren des Gesten Handlers

### <a name="the-gesture-handler-methods"></a>Die Gestenhandlermethoden
 Die Gestenhandlerklasse implementiert und exportiert <xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement.IGestureExtension>. Sie müssen die folgenden Methoden definieren:

|||
|-|-|
|`bool CanDragDrop (ShapeElement target, DiagramDragEventArgs dragEvent)`|Geben Sie `true` zurück, um für das Quellelement, auf das in `dragEvent` verwiesen wird, das Ablegen auf diesem Ziel zu ermöglichen.<br /><br /> Diese Methode darf keine Änderungen am Modell vornehmen. Sie muss schnell ausgeführt werden, da damit der Pfeilzustand bestimmt wird, während der Benutzer die Maus bewegt.|
|`void OnDragDrop (ShapeElement target, DiagramDragEventArgs dragEvent)`|Aktualisieren Sie das Modell basierend auf dem Zielobjekt und auf dem Quellobjekt, auf das in `dragEvent`verwiesen wird.<br /><br /> Wird aufgerufen, wenn der Benutzer die Maus nach dem Ziehvorgang loslässt.|
|`void OnDoubleClick (ShapeElement target, DiagramPointEventArgs pointEvent)`|`target` ist die Form, auf die der Benutzer doppelt geklickt hat.|

 Sie können Handler schreiben, die nicht nur UML akzeptieren, sondern auch eine Vielzahl anderer Elemente, z. B. Dateien, Knoten in einer .NET-Klassenansicht usw. Benutzer können diese Elemente in ein UML-Diagramm ziehen, wenn Sie eine `OnDragDrop` -Methode schreiben, die die serialisierte Form der Elemente decodieren kann. Die Decodierungsmethoden variieren von Elementtyp zu Elementtyp.

 Die Parameter dieser Methoden lauten wie folgt:

- `ShapeElement target`. Die Form oder das Diagramm, auf die bzw. das der Benutzer ein Element gezogen hat.

    `ShapeElement` ist eine Klasse in der Implementierung, die den UML-Modellierungstools zugrunde liegt. Um das Risiko von Inkonsistenzen im UML-Modell und in den Diagrammen zu reduzieren, sollten die Methoden dieser Klasse nicht direkt verwendet werden. Schließen Sie stattdessen das-Element in einem-`IShape`ein, und verwenden Sie dann die unter [Anzeigen eines UML-Modells in Diagrammen](../modeling/display-a-uml-model-on-diagrams.md)beschriebenen Methoden.

  - Abrufen einer `IShape`:

      ```
      IShape targetIShape = target.CreateIShape(target);
      ```

  - Abrufen des Modellelements, das das Ziel des Drag & Drop-Vorgangs ist:

      ```
      IElement target = targetIShape.Element;
      ```

      Sie können das Element in einen spezifischeren Typ von Element umwandeln.

  - Abrufen des UML-Modellspeichers, der das UML-Modell enthält:

      ```
      IModelStore modelStore =
        targetIShape.Element.GetModelStore(); 
      ```

  - So erhalten Sie Zugriff auf den Host und Dienstanbieter

      ```
      target.Store.GetService(typeof(EnvDTE.DTE)) as EnvDTE.DTE
      ```

- `DiagramDragEventArgs eventArgs`. Dieser Parameter enthält die serialisierte Form des Quellobjekts eines Ziehvorgangs:

    ```
    System.Windows.Forms.IDataObject data = eventArgs.Data;
    ```

     Sie können viele unterschiedliche Elemente aus verschiedenen Teilen von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]oder vom Windows-Desktop in ein Diagramm ziehen. Unterschiedliche Elementtypen werden in `IDataObject`unterschiedlich codiert. Informationen zum Extrahieren der Elemente finden Sie in der Dokumentation für den jeweiligen Objekttyp.

     Wenn das Quell Objekt ein UML-Element ist, das aus dem UML-Modell-Explorer oder einem anderen UML-Diagramm gezogen wird, finden Sie weitere Informationen unter [Get UML modelelements from IDataObject](../modeling/get-uml-model-elements-from-idataobject.md)

### <a name="writing-the-code-of-the-methods"></a>Schreiben des Methodencodes
 Weitere Informationen über das Schreiben des Codes zum Lesen und Aktualisieren des Modells finden Sie unter [Programming with the UML API](../modeling/programming-with-the-uml-api.md).

 Informationen zum Zugreifen auf Modellinformationen in einem Zieh Vorgang finden Sie unter Abrufen [von UML-Modellelementen aus IDataObject](../modeling/get-uml-model-elements-from-idataobject.md).

 Wenn Sie mit einem Sequenzdiagramm arbeiten, finden Sie weitere Informationen unter [Bearbeiten von UML-Sequenzdiagrammen mithilfe der UML-API](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md).

 Zusätzlich zu den Parametern der Methoden können Sie auch eine importierte Eigenschaft in der Klasse deklarieren, die Zugriff auf das aktuelle Diagramm und Modell bietet.

```
[Import] public IDiagramContext DiagramContext { get; set; }
```

 Die `IDiagramContext` -Deklaration ermöglicht es Ihnen, in den Methoden Code zu schreiben, der auf das Diagramm, die aktuelle Auswahl und das Modell zugreift:

```
IDiagram diagram = this.DiagramContext.CurrentDiagram;
foreach (IShape<IElement> shape in diagram.GetSelectedShapes<IElement>)
{ IElement element = shape.Element; ... }
IModelStore modelStore = diagram.ModelStore;
IModel model = modelStore.Root;
foreach (IDiagram diagram in modelStore.Diagrams) {...}
foreach (IElement element in modelStore.AllInstances<IUseCase>) {...}
```

 Weitere Informationen finden Sie unter [Navigieren im UML-Modell](../modeling/navigate-the-uml-model.md).

## <a name="Installing"></a>Installieren und Deinstallieren einer Erweiterung
 Sie können eine [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] -Erweiterung sowohl auf Ihrem eigenen Computer als auch auf anderen Computern installieren.

#### <a name="to-install-an-extension"></a>So installieren Sie eine Erweiterung

1. Suchen Sie auf dem Computer nach der **.vsix** -Datei, die vom VSIX-Projekt erstellt wurde.

    1. Wählen Sie im **Projektmappen-Explorer**im Kontextmenü des VSIX-Projekts **Ordner in Windows Explorer öffnen**aus.

    2. Suchen Sie den Datei- **bin\\\*\\** _yourproject_ **. VSIX.**

2. Kopieren Sie die **.vsix** -Datei auf den Zielcomputer, auf dem Sie die Erweiterung installieren möchten. Dies kann Ihr eigener Computer oder ein anderer Computer sein.

     Der Zielcomputer muss über eine der Editionen von [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] verfügen, die Sie in **source.extension.vsixmanifest**.

3. Öffnen Sie auf dem Zielcomputer die **.vsix** -Datei.

     **Installer für Visual Studio-Erweiterungen** wird geöffnet, und die Erweiterung wird installiert.

4. Starten Sie [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], bzw. starten Sie die Anwendung neu.

#### <a name="to-uninstall-an-extension"></a>So deinstallieren Sie eine Erweiterung

1. Wählen Sie im Menü **Tools** **Erweiterungen und Updates**aus.

2. Erweitern Sie **Installierte Erweiterungen**.

3. Wählen Sie die Erweiterung aus, und wählen Sie anschließend **Deinstallieren**.

   In seltenen Fällen kann es vorkommen, dass eine fehlerhafte Erweiterung nicht geladen und ein Bericht im Fehlerfenster erstellt wird, aber im Erweiterungs-Manager keine Informationen angezeigt werden. Sie haben die Möglichkeit, die Erweiterung zu entfernen, indem Sie die Datei aus dem folgenden Ordner löschen:

   *% LocalAppData%* **\local\microsoft\visualstudio\\[Version] \extensions**

## <a name="DragExample"></a> Beispiel
 Im folgenden Beispiel wird gezeigt, wie basierend auf den Teilen und Anschlüssen einer aus einem Komponentendiagramm gezogenen Komponente Lebenslinien in einem Sequenzdiagramm erstellt werden.

 Drücken Sie zum Testen F5. Eine experimentelle Instanz von Visual Studio wird geöffnet. Öffnen Sie in dieser Instanz ein UML-Modell, und erstellen Sie in einem Komponentendiagramm eine Komponente. Fügen Sie dieser Komponente einige Schnittstellen und interne Komponententeile hinzu. Wählen Sie die Schnittstellen und die Teile aus. Ziehen Sie anschließend die Schnittstellen und die Teile auf ein Sequenzdiagramm. (Ziehen Sie aus dem Komponenten Diagramm nach oben auf die Registerkarte für das Sequenzdiagramm und anschließend in das Sequenzdiagramm.) Für jede Schnittstelle und jeden Teil wird eine Lebenslinie angezeigt.

 Weitere Informationen zum Binden von Interaktionen an Sequenzdiagramme finden [Sie unter Bearbeiten von UML-Sequenzdiagrammen mithilfe der UML-API](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md).

```
using System.Collections.Generic;
using System.ComponentModel.Composition;
using System.Linq;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
using Microsoft.VisualStudio.Uml.AuxiliaryConstructs;
using Microsoft.VisualStudio.Uml.Classes;
using Microsoft.VisualStudio.Uml.Interactions;
using Microsoft.VisualStudio.Uml.CompositeStructures;
using Microsoft.VisualStudio.Uml.Components;

/// <summary>
/// Creates lifelines from component ports and parts.
/// </summary>
[Export(typeof(IGestureExtension))]
[SequenceDesignerExtension]
public class CreateLifelinesFromComponentParts : IGestureExtension
{
  [Import]
  public IDiagramContext Context { get; set; }

  /// <summary>
  /// Called by the modeling framework when
  /// the user drops something on a target.
  /// </summary>
  /// <param name="target">The target shape or diagram </param>
  /// <param name="dragEvent">The item being dragged</param>
  public void OnDragDrop(ShapeElement target,
           DiagramDragEventArgs dragEvent)
  {
    ISequenceDiagram diagram = Context.CurrentDiagram
            as ISequenceDiagram;
    IInteraction interaction = diagram.Interaction;
    if (interaction == null)
    {
      // Sequence diagram is empty: create an interaction.
      interaction = diagram.ModelStore.Root.CreateInteraction();
      interaction.Name = Context.CurrentDiagram.Name;
      diagram.Bind(interaction);
    }
    foreach (IConnectableElement connectable in
       GetConnectablesFromDrag(dragEvent))
    {
      ILifeline lifeline = interaction.CreateLifeline();
      lifeline.Represents = connectable;
      lifeline.Name = connectable.Name;
    }
  }

  /// <summary>
  /// Called by the modeling framework to determine whether
  /// the user can drop something on a target.
  /// Must not change anything.
  /// </summary>
  /// <param name="target">The target shape or diagram</param>
  /// <param name="dragEvent">The item being dragged</param>
  /// <returns>true if this item can be dropped on this target</returns>
  public bool CanDragDrop(ShapeElement target,
           DiagramDragEventArgs dragEvent)
  {
    IEnumerable<IConnectableElement> connectables = GetConnectablesFromDrag(dragEvent);
    return connectables.Count() > 0;
  }

  ///<summary>
  /// Get dragged parts and ports of an IComponent.
  ///</summary>
  private IEnumerable<IConnectableElement>
    GetConnectablesFromDrag(DiagramDragEventArgs dragEvent)
  {
    foreach (IElement element in
      GetModelElementsFromDragEvent(dragEvent))
    {
      IConnectableElement part = element as IConnectableElement;
      if (part != null)
      {
        yield return part;
      }
    }
  }

  /// <summary>
  /// Retrieves UML IElements from drag arguments.
  /// Works for drags from UML diagrams.
  /// </summary>
  private IEnumerable<IElement> GetModelElementsFromDragEvent
          (DiagramDragEventArgs dragEvent)
  {
    //ElementGroupPrototype is the container for
    //dragged and copied elements and toolbox items.
    ElementGroupPrototype prototype =
       dragEvent.Data.
       GetData(typeof(ElementGroupPrototype))
            as ElementGroupPrototype;
    // Locate the originals in the implementation store.
    IElementDirectory implementationDirectory =
       dragEvent.DiagramClientView.Diagram.Store.ElementDirectory;

    return prototype.ProtoElements.Select(
      prototypeElement =>
      {
        ModelElement element = implementationDirectory
          .FindElement(prototypeElement.ElementId);
        ShapeElement shapeElement = element as ShapeElement;
        if (shapeElement != null)
        {
          // Dragged from a diagram.
          return shapeElement.ModelElement as IElement;
        }
        else
        {
          // Dragged from UML Model Explorer.
          return element as IElement;
        }
      });
  }

  public void OnDoubleClick(ShapeElement targetElement, DiagramPointEventArgs diagramPointEventArgs)
  {
  }
}

```

 Der Code von `GetModelElementsFromDragEvent()` wird in [Get UML-Modellelementen aus IDataObject](../modeling/get-uml-model-elements-from-idataobject.md)beschrieben.

## <a name="see-also"></a>Siehe auch
 [Definieren und Installieren einer Modellierungs Erweiterung](../modeling/define-and-install-a-modeling-extension.md) [Erweitern von UML-Modellen und Diagrammen](../modeling/extend-uml-models-and-diagrams.md) [Definieren eines Menübefehls in einem Modellierungs Diagramm](../modeling/define-a-menu-command-on-a-modeling-diagram.md) [Definieren von Validierungs Einschränkungen für UML-Modelle](../modeling/define-validation-constraints-for-uml-models.md) [Programmieren mit der UML-API](../modeling/programming-with-the-uml-api.md)
