---
title: Define a menu command on a modeling diagram | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending, menu commands
ms.assetid: 79c277de-5871-4fc7-9701-55eec5c3cd46
caps.latest.revision: 63
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 23ba1a6900559d7ee13639bb1da696127e47e536
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299270"
---
# <a name="define-a-menu-command-on-a-modeling-diagram"></a>Definieren eines Menübefehls in einem Modellierungsdiagramm
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio können Sie zusätzliche Menüelemente in den Kontextmenüs eines UML-Diagramms definieren. Sie können steuern, ob der Menübefehl angezeigt wird und im Kontextmenü für alle Elemente des Diagramms verfügbar ist, und Sie können Code schreiben, der bei Auswahl des Menüelements ausgeführt wird. Sie können diese Erweiterungen in einer Visual Studio-Integrationserweiterung ([VSIX](https://go.microsoft.com/fwlink/?LinkId=160780)) verpacken, die Sie an andere Visual Studio-Benutzer verteilen können.

## <a name="requirements"></a>Anforderungen
 Siehe [Anforderungen](../modeling/extend-uml-models-and-diagrams.md#Requirements).

 Welche Versionen von Visual Studio dieses Features unterstützen, erfahren Sie unter [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="defining-the-menu-command"></a>Definieren des Menübefehls
 Um für einen UML-Designer einen Menübefehl zu erstellen, müssen Sie eine Klasse erstellen, die das Verhalten des Befehls definiert, und die Klasse in eine Visual Studio-Integrationserweiterung (VSIX) einbetten. Die VSIX fungiert als Container, der den Befehl installieren kann. Es gibt zwei alternative Methoden, einen Menübefehl zu definieren:

- **Create a menu command in its own VSIX using a project template.** Dies ist die schnellere Methode. Verwenden Sie diese Methode, wenn Sie die Menübefehle nicht mit anderen Erweiterungstypen, z. B. Validierungserweiterungen, benutzerdefinierten Toolboxelementen oder Gestenhandlern, kombinieren möchten.

- **Create separate menu command and VSIX projects.** Verwenden Sie diese Methode, wenn Sie mehrere Erweiterungstypen in dieselbe VSIX kombinieren möchten. Wenn beispielsweise der Menübefehl erwartet, dass das Modell bestimmte Einschränkungen berücksichtigt, können Sie es in dieselbe VSIX wie eine Validierungsmethode einbetten.

#### <a name="to-create-a-menu-command-in-its-own-vsix"></a>So erstellen Sie einen Menübefehl in einem eigenen VSIX

1. Klicken Sie im Dialogfeld **Neues Projekt** unter **Modellierungsprojekte**auf **Befehlserweiterung**.

2. Öffnen Sie die **.cs** -Datei im neuen Projekt, und ändern Sie die `CommandExtension` -Klasse, um den Befehl zu implementieren.

    Weitere Informationen finden Sie unter [Implementieren des Menübefehls](#Implementing).

3. Sie können diesem Projekt zusätzliche Befehle hinzufügen, indem Sie neue Klassen definieren.

4. Testen Sie den Menübefehl, indem Sie F5 drücken. Weitere Informationen finden Sie unter [Ausführen des Menübefehls](#Executing).

5. Install the menu command on another computer by copying the file **bin\\\*\\\*.vsix** that is built by your project. Weitere Informationen finden Sie unter [Installieren und Deinstallieren einer Erweiterung](#Installing).

   Es gibt ein alternatives Verfahren:

#### <a name="to-create-a-menu-command-in-a-separate-class-library-dll-project"></a>So erstellen Sie einen Menübefehl in einem separaten Klassenbibliothekprojekt (DLL)

1. Erstellen Sie ein neues Klassenbibliotheksprojekt, entweder in einer neuen Visual Studio-Projektmappe oder in einer vorhandenen Projektmappe.

   1. Wählen Sie im Menü **Datei** die Optionsfolge **Neu**, **Projekt**aus.

   2. Wählen Sie unter **Installierte Vorlagen**die Option **Visual C#** oder **Visual Basic**aus. Wählen Sie in der mittleren Spalte **Klassenbibliothek**aus.

   3. Legen Sie **Projektmappe** fest, um anzugeben, ob eine neue Projektmappe erstellt oder einer bereits geöffneten VSIX-Projektmappe eine Komponente hinzugefügt werden soll.

   4. Legen Sie Name und Speicherort für das Projekt fest, und klicken Sie auf OK.

2. Fügen Sie dem Projekt die folgenden Verweise hinzu.

   |                                                                                                    Referenz                                                                                                    |                                                                                                  Optionen                                                                                                  |
   |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |                                                                                        System.ComponentModel.Composition                                                                                        |                                         Definieren Sie Komponenten mithilfe von [Managed Extensibility Framework (MEF)](https://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde).                                          |
   |                                                                                      Microsoft.VisualStudio.Uml.Interfaces                                                                                      |                                                                                        Lesen und Ändern der Eigenschaften von Modellelementen                                                                                         |
   |                                                                             Microsoft.VisualStudio.ArchitectureTools.Extensibility                                                                              |                                                                                      Erstellen von Modellelementen, Ändern von Formen in Diagrammen                                                                                       |
   |                                                                                  Microsoft.VisualStudio.Modeling.Sdk.[Version]                                                                                  | Definieren von Modellereignishandlern<br /><br /> Kapseln einer Reihe von Änderungen im Modell. For more information, see [Link UML model updates by using transactions](../modeling/link-uml-model-updates-by-using-transactions.md). |
   |                                                            Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[Version]<br /><br /> (nicht immer erforderlich)                                                             |                                                                                   Zugreifen auf zusätzliche Diagrammelemente für Gestenhandler                                                                                   |
   | Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer<br /><br /> Nur für Befehle in Ebenendiagrammen erforderlich. For more information, see [Extend layer diagrams](../modeling/extend-layer-diagrams.md). |                                                                                             Definieren Sie Befehle in einem Ebenendiagramm.                                                                                              |

3. Fügen Sie dem Projekt eine Klassendatei hinzu, und legen Sie deren Inhalt auf den folgenden Code fest.

   > [!NOTE]
   > Ändern Sie den Namespace, den Klassennamen und den Rückgabewert von `Text` entsprechend den jeweiligen Anforderungen.
   >
   >  Wenn Sie mehrere Befehle definieren, werden diese im Menü in alphabetischer Reihenfolge der Klassennamen dargestellt.

   ```
   using System.ComponentModel.Composition;
   using System.Linq;
   using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
   using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
   using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
   using Microsoft.VisualStudio.Uml.AuxiliaryConstructs;
   using Microsoft.VisualStudio.Uml.Classes;
       // ADD other UML namespaces if required

   namespace UMLmenu1 // CHANGE
   {
     // DELETE any of these attributes if the command
     // should not appear in some types of diagram.
     [ClassDesignerExtension]
     [ActivityDesignerExtension]
     [ComponentDesignerExtension]
     [SequenceDesignerExtension]
     [UseCaseDesignerExtension]
     // [LayerDesignerExtension]

     // All menu commands must export ICommandExtension:
     [Export (typeof(ICommandExtension))]
     // CHANGE class name – determines order of appearance on menu:
     public class Menu1 : ICommandExtension
     {
       [Import]
       public IDiagramContext DiagramContext { get; set; }

       public void QueryStatus(IMenuCommand command)
       { // Set command.Visible or command.Enabled to false
         // to disable the menu command.
         command.Visible = command.Enabled = true;
       }

       public string Text
       {
         get { return "MENU COMMAND LABEL"; }
       }

       public void Execute(IMenuCommand command)
       {
         // A selection of starting points:
         IDiagram diagram = this.DiagramContext.CurrentDiagram;
         foreach (IShape<IElement> shape in diagram.GetSelectedShapes<IElement>())
         { IElement element = shape.Element; }
         IModelStore modelStore = diagram.ModelStore;
         IModel model = modelStore.Root;
         foreach (IElement element in modelStore.AllInstances<IClass>())
         { }
       }
     }
   }
   ```

    Weitere Informationen zum Füllen der Methoden finden Sie unter [Implementieren des Menübefehls](#Implementing).

   Sie müssen den Menübefehl einem VSIX-Projekt hinzufügen, das als Container für die Installation des Befehls fungiert. Gegebenenfalls können Sie in dasselbe VSIX auch weitere Komponenten einschließen.

#### <a name="to-add-a-menu-command-to-a-vsix-project"></a>So fügen Sie einem VSIX-Projekt einen Menübefehl hinzu

1. Diese Prozedur ist nicht erforderlich, wenn Sie den Menübefehl mit seiner eigenen VSIX erstellt haben.

2. Erstellen Sie ein VSIX-Projekt, sofern die Projektmappe noch kein VSIX-Projekt enthält.

    1. Wählen Sie im **Projektmappen-Explorer**im Kontextmenü der Projektmappe die Option **Hinzufügen**und dann **Neues Projekt**aus.

    2. Erweitern Sie unter **Installierte Vorlagen**den Knoten **Visual C#** oder **Visual Basic**, und wählen Sie anschließend **Erweiterungen**aus. Wählen Sie in der mittleren Spalte **VSIX Project**.

3. Wählen Sie im Projektmappen-Explorer im Kontextmenü des VSIX-Projekts die Option **Als Startprojekt festlegen**aus.

4. Öffnen Sie **source.extension.vsixmanifest**.

    1. Legen Sie auf der Registerkarte **MetaData** einen Namen für VSIX fest.

    2. Legen Sie auf der Registerkarte **Ziele installieren** die Visual Studio-Versionen als Ziele fest.

    3. Wählen Sie auf der Registerkarte **Objekte** die Option **Neu**und wählen Sie im Dialogfeld:

         **Typ** = **MEF-Komponente**

         **Quelle** = **Ein Projekt in der aktuellen Projektmappe**

         **Projekt** = *Ihr Klassenbibliotheksprojekt*

## <a name="Implementing"></a> Implementing the Menu Command
 Durch die Menübefehlsklasse werden die erforderlichen Methoden für <xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ICommandExtension> implementiert.

|||
|-|-|
|`string Text { get; }`|Geben Sie die Bezeichnung des Menüelements zurück.|
|`void QueryStatus(IMenuCommand command);`|Wird aufgerufen, wenn der Benutzer im Diagramm mit der rechten Maustaste klickt.<br /><br /> Diese Methode sollte das Modell nicht ändern.<br /><br /> Verwenden Sie `DiagramContext.CurrentDiagram.SelectedShapes` , um festzulegen, ob der Befehl angezeigt werden soll und aktiviert sein soll.<br /><br /> Legen Sie Folgendes fest:<br /><br /> -   `command.Visible` to `true` if the command must appear in the menu when the user right-clicks in the diagram<br />-   `command.Enabled` to `true` if the user can click the command in the menu<br />-   `command.Text` to set the menu label dynamically|
|`void Execute (IMenuCommand command);`|Wird aufgerufen, wenn Benutzer auf das Menüelement klicken, während es sichtbar und aktiviert ist.|

### <a name="accessing-the-model-in-code"></a>Zugriff auf das Modell im Code
 Schließen Sie die folgende Deklaration in die Menübefehlsklasse ein:

```
[Import] public IDiagramContext DiagramContext { get; set; }
```

 ...

 Die `IDiagramContext` -Deklaration ermöglicht es Ihnen, in den Methoden Code zu schreiben, der auf das Diagramm, die aktuelle Auswahl und das Modell zugreift:

```
IDiagram diagram = this.DiagramContext.CurrentDiagram;
foreach (IShape<IElement> shape in diagram.GetSelectedShapes<IElement>())
{ IElement element = shape.Element; ... }
IModelStore modelStore = diagram.ModelStore;
IModel model = modelStore.Root;
foreach (IElement element in modelStore.AllInstances<IUseCase>()) {...}
```

### <a name="navigating-and-updating-the-model"></a>Navigieren im Modell und Aktualisieren des Modells
 Alle Elemente des UML-Modells sind über die API verfügbar. In der aktuellen Auswahl oder im Stamm des Modells können Sie auf alle anderen Elemente zugreifen. For more information, see [Navigate the UML model](../modeling/navigate-the-uml-model.md) and [Programming with the UML API](../modeling/programming-with-the-uml-api.md).

 If you are dealing with a sequence diagram, see also [Edit UML sequence diagrams by using the UML API](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md).

 Die API ermöglicht Ihnen auch das Ändern von Elementeigenschaften, Löschen von Elementen und Beziehungen und Erstellen neuer Elemente und Beziehungen.

 Standardmäßig wird jede Änderung, die Sie in der Execute-Methode vornehmen, in einer separaten Transaktion ausgeführt. Der Benutzer kann jede Änderung einzeln rückgängig machen. If you want to group the changes into a single transaction, use a <xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ILinkedUndoTransaction> as described in [Link UML model updates by using transactions](../modeling/link-uml-model-updates-by-using-transactions.md).

### <a name="use-the-ui-thread-for-updates"></a>Verwenden des UI-Threads für Updates
 In einigen Fällen kann es nützlich sein, Updates am Modell mit einem Hintergrundthread auszuführen. Wenn der Befehl z. B. Daten aus einer langsamen Ressource lädt, können Sie den Ladevorgang in einem Hintergrundthread ausführen, damit der Benutzer die Änderungen in Echtzeit verfolgen und ggf. abbrechen kann.

 Dabei ist jedoch zu beachten, dass der Modellspeicher nicht threadsicher ist. Sie sollten Updates immer mit dem UI-Thread (Benutzeroberflächenthread) ausführen und nach Möglichkeit verhindern, dass der Benutzer während der Ausführung des Hintergrundprozesses Änderungen vornimmt. For an example, see [Update a UML model from a background thread](../modeling/update-a-uml-model-from-a-background-thread.md).

## <a name="Executing"></a> Executing the Menu Command
 Führen Sie den Befehl zu Testzwecken im Debugmodus aus.

#### <a name="to-test-the-menu-command"></a>So testen Sie den Menübefehl

1. Drücken Sie **F5**oder wählen Sie im Menü **Debug** die Option **Debugging starten**.

     Eine experimentelle Instanz von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] wird gestartet.

     **Problembehandlung**: Wenn ein neuer [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nicht startet:

    - Wenn Sie mehr als ein Projekt haben, stellen Sie sicher, dass das VSIX-Projekt als Startprojekt der Projektmappe festgelegt wird.

    - Öffnen Sie im Projektmappen-Explorer das Kontextmenü für das Start- oder einzelne Projekt und wählen Sie **Eigenschaften**aus. In the project properties editor, select the **Debug** tab. Make sure that the string in the **Start external program** field is the full pathname of [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], typically:

         `C:\Program Files\Microsoft Visual Studio [version]\Common7\IDE\devenv.exe`

2. Öffnen oder erstellen Sie in der experimentellen Instanz von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]ein Modellierungsprojekt, und öffnen oder erstellen Sie ein Modellierungsdiagramm. Verwenden Sie ein Diagramm, das zu einem der Typen gehört, die in den Attributen der Menübefehlsklasse aufgeführt sind.

3. Öffnen Sie das Kontextmenü an einer beliebigen Stelle im Diagramm. Der Befehl muss im Menü angezeigt werden.

     **Problembehandlung**: Wenn der Befehl nicht im Menü angezeigt wird, stellen Sie Folgendes sicher:

    - Das Menübefehlsprojekt ist im VSIX-Projekt als MEF-Komponente auf der Registerkarte **Objekte** in **source.extensions.manifest** aufgeführt.

    - Die Parameter des `Import` -Attributs und des `Export` -Attributs sind gültig.

    - The `QueryStatus` method is not setting the `command`.`Enabled` oder `Visible` -Feld nicht auf `false`.

    - Der verwendete Modelldiagrammtyp (UML-Klasse, Sequenz usw.) ist als eines der Menübefehlsklassen-Attribute `[ClassDesignerExtension]`, `[SequenceDesignerExtension]` usw. aufgeführt.

## <a name="Installing"></a> Installing and uninstalling an extension
 Sie können eine [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] -Erweiterung sowohl auf Ihrem eigenen Computer als auch auf anderen Computern installieren.

#### <a name="to-install-an-extension"></a>So installieren Sie eine Erweiterung

1. Suchen Sie auf dem Computer nach der **.vsix** -Datei, die vom VSIX-Projekt erstellt wurde.

    1. Wählen Sie im **Projektmappen-Explorer**im Kontextmenü des VSIX-Projekts **Ordner in Windows Explorer öffnen**aus.

    2. Locate the file **bin\\\*\\** _YourProject_ **.vsix**

2. Kopieren Sie die **.vsix** -Datei auf den Zielcomputer, auf dem Sie die Erweiterung installieren möchten. Dies kann Ihr eigener Computer oder ein anderer Computer sein.

     Der Zielcomputer muss über eine der Editionen von [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] verfügen, die Sie in **source.extension.vsixmanifest**.

3. Öffnen Sie auf dem Zielcomputer die Datei **.vsix** , indem Sie beispielsweise darauf doppelklicken.

     **Installer für Visual Studio-Erweiterungen** wird geöffnet, und die Erweiterung wird installiert.

4. Starten Sie [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], bzw. starten Sie die Anwendung neu.

#### <a name="to-uninstall-an-extension"></a>So deinstallieren Sie eine Erweiterung

1. Wählen Sie im Menü **Tools** **Erweiterungen und Updates**aus.

2. Erweitern Sie **Installierte Erweiterungen**.

3. Wählen Sie die Erweiterung aus, und wählen Sie anschließend **Deinstallieren**.

   In seltenen Fällen kann es vorkommen, dass eine fehlerhafte Erweiterung nicht geladen und ein Bericht im Fehlerfenster erstellt wird, aber im Erweiterungs-Manager keine Informationen angezeigt werden. Sie haben die Möglichkeit, die Erweiterung zu entfernen, indem Sie die Datei aus dem folgenden Ordner löschen:

   *%LocalAppData%* **\Local\Microsoft\VisualStudio\\[version]\Extensions**

## <a name="MenuExample"></a> Beispiel
 Das folgende Beispiel zeigt den Code für einen Menübefehl, der die Namen von zwei Elementen eines Klassendiagramms austauscht. Dieser Code muss in einem [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Erweiterungsprojekt erstellt und wie in den vorherigen Abschnitten beschrieben installiert werden.

```
using System.Collections.Generic; // for IEnumerable
using System.ComponentModel.Composition;
  // for [Import], [Export]
using System.Linq; // for IEnumerable extensions
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
  // for IDiagramContext
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
  // for designer extension attributes
using Microsoft.VisualStudio.Modeling.Diagrams;
  // for ShapeElement
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
  // for IGestureExtension, ICommandExtension, ILinkedUndoContext
using Microsoft.VisualStudio.Uml.Classes;
  // for class diagrams, packages

/// <summary>
/// Extension to swap names of classes in a class diagram.
/// </summary>
namespace SwapClassNames
{
  // Declare the class as an MEF component:
  [Export(typeof(ICommandExtension))]
  [ClassDesignerExtension]
  // Add more ExportMetadata attributes to make
  // the command appear on diagrams of other types.
  public class NameSwapper : ICommandExtension
  {
  // MEF required interfaces:
  [Import]
  public IDiagramContext Context { get; set; }
  [Import]
  public ILinkedUndoContext LinkedUndoContext { get; set; }

  /// <summary>
  /// Swap the names of the currently selected elements.
  /// </summary>
  /// <param name="command"></param>
  public void Execute(IMenuCommand command)
  {
    // Get selected shapes that are IClassifiers -
    // IClasses, IInterfaces, IEnumerators.
    var selectedShapes = Context.CurrentDiagram
     .GetSelectedShapes<IClassifier>();
    if (selectedShapes.Count() < 2) return;

    // Get model elements displayed by shapes.
    IClassifier firstElement = selectedShapes.First().Element;
    IClassifier lastElement = selectedShapes.Last().Element;

    // Do the swap in a transaction so that user
    // cannot undo one change without the other.
    using (ILinkedUndoTransaction transaction =
    LinkedUndoContext.BeginTransaction("Swap names"))
    {
    string firstName = firstElement.Name;
    firstElement.Name = lastElement.Name;
    lastElement.Name = firstName;
    transaction.Commit();
    }
  }

  /// <summary>
  /// Called by Visual Studio to determine whether
  /// menu item should be visible and enabled.
  /// </summary>
  public void QueryStatus(IMenuCommand command)
  {
    int selectedClassifiers = Context.CurrentDiagram
     .GetSelectedShapes<IClassifier>().Count();
    command.Visible = selectedClassifiers > 0;
    command.Enabled = selectedClassifiers == 2;
  }

  /// <summary>
  /// Name of the menu command.
  /// </summary>
  public string Text
  {
    get { return "Swap Names"; }
  }
  }

}
```

## <a name="see-also"></a>Siehe auch
 [Define and install a modeling extension](../modeling/define-and-install-a-modeling-extension.md) [Extend UML models and diagrams](../modeling/extend-uml-models-and-diagrams.md) [Define a gesture handler on a modeling diagram](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md) [Define a custom modeling toolbox item](../modeling/define-a-custom-modeling-toolbox-item.md) [Define validation constraints for UML models](../modeling/define-validation-constraints-for-uml-models.md) [Edit UML sequence diagrams by using the UML API](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md) [Programming with the UML API](../modeling/programming-with-the-uml-api.md) [Sample: Command to Align Shapes on a UML Diagram](https://go.microsoft.com/fwlink/?LinkID=213809)
