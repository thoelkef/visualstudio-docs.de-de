---
title: Hinzufügen von Befehlen und Gesten zu Abhängigkeitsdiagrammen
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, adding custom commands
- dependency diagrams, adding custom gestures
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ea106d98dbd18f224e7f2a9d95734eff591dfc2b
ms.sourcegitcommit: 6a19c5ece38a70731496a38f2ef20676ff18f8a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/09/2019
ms.locfileid: "65476658"
---
# <a name="add-commands-and-gestures-to-dependency-diagrams"></a>Hinzufügen von Befehlen und Gesten zu Abhängigkeitsdiagrammen

Sie können definieren mit der rechten Maustaste Menübefehle und Gestenhandler in Abhängigkeitsdiagrammen in Visual Studio. Sie können diese Erweiterungen in einer Visual Studio-Integrationserweiterung (VSIX) verpacken, die Sie an andere Visual Studio-Benutzer verteilen können.

Sie können bei Bedarf mehrere Befehls- und Gestenhandler im gleichen Visual Studio-Projekt definieren. Sie können auch mehrere Projekte dieser Art in einer VSIX kombinieren. Beispielsweise können Sie eine einzelne VSIX definieren, die Ebenenbefehle, und eine domänenspezifische Sprache enthält.

> [!NOTE]
> Sie können architekturvalidierung auch anpassen, in der Quellcode der der Benutzer Code mit Abhängigkeitsdiagrammen verglichen wird. Sie sollten die Architekturvalidierung in einem separaten Visual Studio-Projekt definieren. Sie können sie der gleichen VSIX hinzufügen wie anderen Erweiterungen. Weitere Informationen finden Sie unter [Hinzufügen einer benutzerdefinierten architekturvalidierung zu Abhängigkeitsdiagrammen](../modeling/add-custom-architecture-validation-to-layer-diagrams.md).

## <a name="requirements"></a>Anforderungen

Siehe [Anforderungen](../modeling/extend-layer-diagrams.md#requirements).

## <a name="define-a-command-or-gesture-in-a-new-vsix"></a>Definieren eines Befehls oder einer Geste in einer neuen VSIX

Projektvorlagen stellen die schnellste Methode dar, eine Erweiterung zu erstellen. Dabei werden der Code und die VSIX im selben Projekt platziert.

1. Erstellen Sie ein neues **Layer Designer Command Extension** oder **Layer Designer-Gestenerweiterung** Projekt.

   Mit dieser Vorlage wird ein Projekt mit einem kleinen Arbeitsbeispiel erstellt.

2. Um die Erweiterung zu testen, indem Sie **STRG**+**F5** oder **F5**.

    Eine experimentelle Instanz von Visual Studio wird gestartet. Erstellen Sie in diesem Fall ein Abhängigkeitsdiagramm. Der Befehl oder die Gestenerweiterung sollte in diesem Diagramm funktionieren.

3. Schließen Sie die experimentelle Instanz, und ändern Sie den Beispielcode.

4. Sie können dem gleichen Projekt mehrere Befehls- oder Gestenhandler hinzufügen. Weitere Informationen finden Sie in einem der folgenden Abschnitte:

    [Definieren eines Menübefehls](#command)

    [Definieren eines Gestenhandlers](#gesture)

::: moniker range="vs-2017"

5. Um die Erweiterung in der Hauptinstanz von Visual Studio oder auf einem anderen Computer installieren, suchen die *VSIX* Datei die *Bin* Verzeichnis. Kopieren Sie die Datei auf den Computer, auf dem Sie sie installieren möchten, und doppelklicken Sie dann darauf. Wählen Sie zum Deinstallieren der Datei **Erweiterungen und Updates** auf die **Tools** Menü.

::: moniker-end

::: moniker range=">=vs-2019"

5. Um die Erweiterung in der Hauptinstanz von Visual Studio oder auf einem anderen Computer installieren, suchen die *VSIX* Datei die *Bin* Verzeichnis. Kopieren Sie die Datei auf den Computer, auf dem Sie sie installieren möchten, und doppelklicken Sie dann darauf. Wählen Sie zum Deinstallieren der Datei **Verwalten von Erweiterungen** auf die **Erweiterungen** Menü.

::: moniker-end

## <a name="add-a-command-or-gesture-to-a-separate-vsix"></a>Hinzufügen eines Befehls oder einer Geste zu einer separaten VSIX

Wenn Sie eine VSIX erstellen möchten, die Befehle, Ebenenvalidierungssteuerelemente und andere Erweiterungen enthält, empfiehlt es sich, ein Projekt zum Definieren der VSIX und getrennte Projekte für die Handler zu erstellen.

1. Erstellen Sie ein neues **Klassenbibliotheksprojekt**. Dieses Projekt enthält Befehls- oder Gestenhandlerklassen.

   > [!NOTE]
   > Sie können mehrere Befehls- oder Gestenhandlerklassen in einer Klassenbibliothek definieren, jedoch sollten Sie Ebenenvalidierungsklassen in einer separaten Klassenbibliothek definieren.

2. Hinzufügen oder ein VSIX-Projekt in der Projektmappe zu erstellen. Ein VSIX-Projekt enthält eine Datei mit dem Namen **"Source.Extension.vsixmanifest"** .

3. In **Projektmappen-Explorer**mit der rechten Maustaste auf das VSIX-Projekt, und wählen Sie **als Startprojekt festlegen**.

4. Fügen Sie in **source.extension.vsixmanifest**unter **Objekte**das Befehls- oder Gestenhandlerprojekt als MEF-Komponente hinzu.

    1. Wählen Sie auf der Registerkarte **Objekte**die Option **Neu**aus.

    2. Wählen Sie bei **Typ**die Option **Microsoft.VisualStudio.MefComponent**aus.

    3. Wählen Sie bei **Quelle**die Option **Projekt in der aktuellen Projektmappe** und den Namen des Befehls- oder Gestenhandlerprojekts aus.

    4. Speichern Sie die Datei.

5. Zum Befehls- oder Gestenhandlerprojekts Handlerprojekt zurück, und fügen Sie die folgenden Projektverweise hinzu:

   |**Verweis**|**Optionen**|
   |-|-|
   |Programme\Microsoft Visual Studio [Version]\Common7\IDE\Extensions\Microsoft\Architecture Tools\ExtensibilityRuntime\Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.dll|Erstellen und Bearbeiten von Ebenen|
   |Microsoft.VisualStudio.Uml.Interfaces|Erstellen und Bearbeiten von Ebenen|
   |Microsoft.VisualStudio.ArchitectureTools.Extensibility|Ändern von Formen in Diagrammen|
   |System.ComponentModel.Composition|Definieren von Komponenten mit Managed Extensibility Framework (MEF)|
   |Microsoft.VisualStudio.Modeling.Sdk.[Version]|Definieren von Modellierungserweiterungen|
   |Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[Version]|Aktualisieren von Formen und Diagrammen|

6. Bearbeiten Sie die Klassendatei im C#-Klassenbibliotheksprojekt so, dass sie den Code für die Erweiterung enthält. Weitere Informationen finden Sie in einem der folgenden Abschnitte:

     [Definieren eines Menübefehls](#command)

     [Definieren eines Gestenhandlers](#gesture)

7. Um das Feature zu testen, drücken Sie die **STRG**+**F5** oder **F5**.

   Eine experimentelle Instanz von Visual Studio wird geöffnet. Erstellen Sie in diesem Fall oder öffnen Sie ein Abhängigkeitsdiagramm aus.

8. Um die VSIX-Datei in der Hauptinstanz von Visual Studio oder auf einem anderen Computer zu installieren, suchen die **VSIX** Datei die **Bin** Verzeichnis des VSIX-Projekts. Kopieren Sie die Datei auf den Computer, auf dem Sie die VSIX installieren möchten. Doppelklicken Sie auf die VSIX-Datei im Datei-Explorer.

## <a name="command"></a> Definieren eines Menübefehls

Sie können einer vorhandenen Geste oder einem Befehlsprojekt mehrere Menübefehlsdefinitionen hinzufügen. Jeder Befehl wird von einer Klasse definiert, die über die folgenden Eigenschaften verfügt:

- Die Klasse wird folgendermaßen deklariert:

   `[LayerDesignerExtension]`

   `[Export(typeof(ICommandExtension))]`

   `public class`  *MyLayerCommand*  `: ICommandExtension { ... }`

- Der Namespace und der Name der Klasse sind unwichtig.

- `ICommandExtension` wird mit den folgenden Methoden implementiert:

  - `string Text {get;}` - Die Bezeichnung, die im Menü angezeigt wird.

  - `void QueryStatus(IMenuCommand command)` - Wird aufgerufen, wenn der Benutzer mit der rechten Maustaste auf das Diagramm klickt, und bestimmt, ob der Befehl für die aktuelle Auswahl des Benutzers sichtbar und aktiviert ist.

  - `void Execute(IMenuCommand command)` - Wird aufgerufen, wenn der Benutzer den Befehl auswählt.

- Sie können `IDiagramContext`importieren, um die aktuelle Auswahl zu bestimmen:

   `[Import]`

   `public IDiagramContext DiagramContext { get; set; }`

   `...`

   `DiagramContext.CurrentDiagram.SelectedShapes.Count()...`

Erstellen Sie zum Hinzufügen eines neuen Befehls eine neue Codedatei, die das folgende Beispiel enthält. Testen und bearbeiten Sie das Beispiel dann.

```csharp
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
using System.ComponentModel.Composition;
using System.Linq;

namespace MyLayerExtension // Change to your preference.
{
  // This is a feature for dependency diagrams:
  [LayerDesignerExtension]
  // This feature is a menu command:
  [Export(typeof(ICommandExtension))]
  // Change the class name to your preference:
  public class MyLayerCommand : ICommandExtension
  {
    [Import]
    public IDiagramContext DiagramContext { get; set; }

    [Import]
    public ILinkedUndoContext LinkedUndoContext { get; set; }

    // Menu command label:
    public string Text
    {
      get { return "Duplicate layers"; }
    }

    // Called when the user right-clicks the diagram.
    // Defines whether the command is visible and enabled.
    public void QueryStatus(IMenuCommand command)
    {
      command.Visible =
      command.Enabled = DiagramContext.CurrentDiagram
        .SelectedShapes.Count() > 0;
    }

    // Called when the user selects the command.
    public void Execute(IMenuCommand command)
    {
      // A selection of starting points:
      IDiagram diagram = this.DiagramContext.CurrentDiagram;
      ILayerModel lmodel = diagram.GetLayerModel();
      foreach (ILayer layer in lmodel.Layers)
      { // All layers in model.
      }
      // Updates should be performed in a transaction:
      using (ILinkedUndoTransaction t =
        LinkedUndoContext.BeginTransaction("copy selection"))
      {
        foreach (ILayer layer in
          diagram.SelectedShapes
            .Select(shape=>shape.GetLayerElement())
            .Where(element => element is ILayer))
        {
          ILayer copy = lmodel.CreateLayer(layer.Name + "+");
          // Position the shapes:
          IShape originalShape = layer.GetShape();
          copy.GetShape().Move(
            originalShape.XPosition + originalShape.Width * 1.2,
            originalShape.YPosition);
        }
        t.Commit();
      }
    }
  }
}
```

## <a name="gesture"></a> Definieren eines Gestenhandlers

Ein Gestenhandler reagiert, wenn der Benutzer Elemente auf dem Abhängigkeitsdiagramm zieht und der Benutzer eine beliebige Stelle im Diagramm doppelklickt.

Sie können dem vorhandenen Befehls- oder Gestenhandler-VSIX-Projekt eine Codedatei hinzufügen, die einen Gestenhandler definiert:

```csharp
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
using System.ComponentModel.Composition;
using System.Linq;

namespace MyLayerExtensions // change to your preference
{
  [LayerDesignerExtension]
  [Export(typeof(IGestureExtension))]
  public class MyLayerGestureHandler : IGestureExtension
  {
  }
}
```

Beachten Sie die folgenden Punkte zu Gestenhandlern:

- `IGestureExtension` umfasst folgende Member:

     **OnDoubleClick** - Wird aufgerufen, wenn der Benutzer auf eine beliebige Stelle im Diagramm doppelklickt.

     **CanDragDrop** - Wird wiederholt aufgerufen, wenn der Benutzer beim Ziehen eines Elements in das Diagramm die Maus bewegt. Das muss schnell funktionieren.

     **OnDragDrop** - Wird aufgerufen, wenn der Benutzer ein Element im Diagramm ablegt.

- Das erste Argument für jede Methode ist `IShape`, aus der Sie das Ebenenelement abrufen können. Zum Beispiel:

    ```csharp
    public void OnDragDrop(IShape target, IDataObject data)
    {
        ILayerElement element = target.GetLayerElement();
        if (element is ILayer)
        {
            // ...
        }
    }
    ```

- Handler für einige Typen von gezogenen Elementen sind bereits definiert. Beispielsweise kann der Benutzer Elemente im Projektmappen-Explorer in ein Abhängigkeitsdiagramm ziehen. Sie können keinen Ziehhandler für diese Elementtypen definieren. In diesen Fällen werden die `DragDrop` -Methoden nicht aufgerufen.

## <a name="see-also"></a>Siehe auch

- [Hinzufügen einer benutzerdefinierten Architekturvalidierung zu Abhängigkeitsdiagrammen](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)
