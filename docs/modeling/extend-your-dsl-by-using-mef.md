---
title: Erweitern von DSL mittels MEF
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 6e6c790677ea49ad784e7ff5d48326a1d5e216ad
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53986166"
---
# <a name="extend-your-dsl-by-using-mef"></a>Erweitern von DSL mittels MEF

Sie können Ihrer domänenspezifischen Sprache (DSL) erweitern, mithilfe des Managed Extensibility Framework (MEF). Sie oder andere Entwickler werden Erweiterungen für die DSL zu schreiben, ohne die DSL-Definition und die Programm-Codes zu ändern. Diese Erweiterungen umfassen Befehle des Menüs, Drag & Drop-Handler und Validierung. Benutzer werden zum Installieren Ihrer DSL, und klicken Sie dann optional Erweiterungen dafür.

Darüber hinaus beim Sie MEF in Ihrer DSL aktivieren, kann es einfacher für Sie einige der Features Ihrer DSL, geschrieben sein, auch wenn sie alle zusammen mit der DSL erstellt werden.

Weitere Informationen über MEF finden Sie unter [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

### <a name="to-enable-your-dsl-to-be-extended-by-mef"></a>So aktivieren Sie Ihre DSL von MEF erweitert werden

1.  Erstellen Sie einen neuen Ordner namens **MefExtension** innerhalb der **DslPackage** Projekt. Fügen Sie die folgenden Dateien hinzu:

     Dateiname: `CommandExtensionVSCT.tt`

    > [!IMPORTANT]
    > Legen Sie die GUID in diese Datei, um die GUID CommandSetId identisch sein, die in DslPackage\GeneratedCode\Constants.tt definiert ist

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#
    // CmdSet Guid must be defined before master template is included
    // This Guid must be kept synchronized with the CommandSetId Guid in Constants.tt
    Guid guidCmdSet = new Guid ("00000000-0000-0000-0000-000000000000");
    string menuidCommandsExtensionBaseId="0x4000";
    #>
    <#@ include file="DslPackage\CommandExtensionVSCT.tt" #>
    ```

    Dateiname: `CommandExtensionRegistrar.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\CommandExtensionRegistrar.tt" #>
    ```

    Dateiname: `ValidationExtensionEnablement.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\ValidationExtensionEnablement.tt" #>
    ```

    Dateiname: `ValidationExtensionRegistrar.tt`

    Wenn Sie diese Datei hinzufügen, müssen Sie Überprüfung in Ihrer DSL aktivieren, mit mindestens einer der Schalter in **EditorValidation** im DSL-Explorer.

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\ValidationExtensionRegistrar.tt" #>
    ```

    Dateiname: `PackageExtensionEnablement.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\PackageExtensionEnablement.tt" #>
    ```

2.  Erstellen Sie einen neuen Ordner namens **MefExtension** innerhalb der **Dsl** Projekt. Fügen Sie die folgenden Dateien hinzu:

     Dateiname: `DesignerExtensionMetaDataAttribute.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="Dsl\DesignerExtensionMetadataAttribute.tt" #>
    ```

    Dateiname: `GestureExtensionEnablement.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="Dsl\GestureExtensionEnablement.tt" #>
    ```

    Dateiname: `GestureExtensionController.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="Dsl\GestureExtensionController.tt" #>
    ```

3.  Fügen Sie die folgende Zeile an die vorhandene Datei mit dem Namen **Dslpackage\commands**:

    ```xml
    <Include href="MefExtension\CommandExtensionVSCT.vsct"/>
    ```

    Fügen Sie die Zeile hinter der vorhandenen `<Include>` Richtlinie.

4.  Open *"DslDefinition.DSL"*.

5.  Wählen Sie im DSL-Explorer **editor\validierung**.

6.  Stellen Sie im Eigenschaftenfenster sicher, dass mindestens eine der Eigenschaften mit dem Namen **verwendet** ist `true`.

7.  In der **Projektmappen-Explorer** -Symbolleiste klicken Sie auf **alle Vorlagen transformieren**.

     Untergeordnete Dateien, die unterhalb der einzelnen Dateien, die Sie hinzugefügt werden angezeigt.

8.  Erstellen Sie und führen Sie die Projektmappe, um sicherzustellen, dass sie weiterhin funktioniert.

Ihre DSL ist jetzt die MEF-aktiviert. Sie können Menübefehle, Gesten Handler und validierungseinschränkungen als MEF-Erweiterungen schreiben. Sie können diese Erweiterungen in der DSL-Projektmappe zusammen mit anderem benutzerdefinierten Code schreiben. Darüber hinaus können Sie oder andere Entwickler separate Visual Studio-Erweiterungen schreiben, die Ihre DSL zu erweitern.

## <a name="creating-an-extension-for-a-mef-enabled-dsl"></a>Erstellen einer Erweiterung für eine DSL mit MEF-aktiviert

Wenn Sie Zugriff auf eine MEF-fähigen DSL, die von Ihnen selbst oder eine andere Person erstellt haben, können Sie Erweiterungen dafür schreiben. Die Erweiterungen können verwendet werden, um Menübefehle, Gesten-Handler oder validierungseinschränkungen hinzuzufügen. Um diese Erweiterungen zu erstellen, verwenden Sie Visual Studio-Erweiterung (VSIX)-Projektmappe. Die Lösung besteht aus zwei Teilen: einem Klassenbibliotheksprojekt, das die Code-Assembly erstellt, und ein VSIX-Projekt, mit der die Assembly verpackt.

#### <a name="to-create-a-dsl-extension-vsix"></a>Um eine DSL-Erweiterung VSIX zu erstellen.

1. Erstellen Sie ein neues Klassenbibliotheksprojekt. Klicken Sie hierzu in der **neues Projekt** wählen Sie im Dialogfeld **Visual Basic** oder **Visual C#-** und wählen Sie dann **Klassenbibliothek**.

2. Fügen Sie einen Verweis auf die Assembly der DSL, in das neue Klassenbibliotheksprojekt.

   - Diese Assembly wurde in der Regel einen Namen mit der Endung ". DSL.dll".

   - Wenn Sie Zugriff auf das DSL-Projekt haben, finden Sie die Assemblydatei im Verzeichnis **Dsl\bin\\\\***

   - Wenn Sie Zugriff auf die DSL-VSIX-Datei haben, finden Sie die Assembly durch Ändern der Dateinamenerweiterung, der die VSIX-Datei in ".zip". Dekomprimieren Sie die ZIP-Datei.

3. Fügen Sie Verweise auf die folgenden .NET-Assemblys hinzu:

   -   Microsoft.VisualStudio.Modeling.Sdk.11.0.dll

   -   Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0.dll

   -   Microsoft.VisualStudio.Modeling.Sdk.Shell.11.0.dll

   -   System.ComponentModel.Composition.dll

   -   System.Windows.Forms.dll

4. Erstellen Sie ein VSIX-Projekt, in der gleichen Projektmappe. Klicken Sie hierzu in der **neues Projekt** Dialogfeld erweitern Sie **Visual Basic** oder **Visual C#-**, klicken Sie auf **Erweiterbarkeit**, und wählen Sie dann auf  **VSIX-Projekt**.

5. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste in des VSIX-Projekts, und klicken Sie dann auf **als Startprojekt festlegen**.

6. Öffnen Sie in das neue Projekt **"Source.Extension.vsixmanifest"**.

7. Klicken Sie auf **fügen Inhalt hinzu,**. Legen Sie im Dialogfeld **Inhaltstyp** zu **MEF-Komponente**, und **Quellprojekt** auf Ihr Klassenbibliotheksprojekt hinzu.

8. Fügen Sie ein VSIX-Verweis auf die DSL hinzu.

   1. In **"Source.Extension.vsixmanifest"**, klicken Sie auf **Verweis hinzufügen**

   2. Klicken Sie im Dialogfeld auf **Nutzlast hinzufügen** und suchen Sie dann auf die VSIX-Datei der DSL. Die VSIX-Datei wird in der DSL-Projektmappe erstellt, in ** DslPackage\bin\\\\***.

       Dadurch können Benutzer, die die DSL und die Erweiterung zur gleichen Zeit zu installieren. Wenn der Benutzer bereits die DSL installiert hat, wird nur die Erweiterung installiert.

9. Überprüfen und aktualisieren Sie die anderen Felder des **"Source.Extension.vsixmanifest"**. Klicken Sie auf **Editionen auswählen** und stellen Sie sicher, dass die richtigen Versionen von Visual Studio festgelegt werden.

10. Fügen Sie Code hinzu, um das Klassenbibliotheksprojekt hinzu. Verwenden Sie die Beispiele im nächsten Abschnitt als Leitfaden.

     Sie können eine beliebige Anzahl von Befehls-, Gesten- und Validierungsklassen hinzufügen.

11. Um die Erweiterung zu testen, indem Sie **F5**. Klicken Sie in der experimentellen Instanz von Visual Studio erstellen Sie, oder öffnen Sie eine Beispieldatei der DSL.

## <a name="writing-mef-extensions-for-dsls"></a>Schreiben von MEF-Erweiterungen für DSLs

Sie können Erweiterungen in das Codeprojekt der Assembly von einer separaten Projektmappe der DSL-Erweiterung schreiben. Sie können auch als einfache Möglichkeit zum Schreiben von Befehlen, Gesten und Validierungscode als Teil der DSL MEF im DslPackage-Projekt verwenden.

### <a name="menu-commands"></a>Menübefehle

Um einen Menübefehl schreiben zu können, definieren Sie eine Klasse, die implementiert <xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ICommandExtension> und die Klasse mit dem Attribut, das in Ihrer DSL, die mit dem Namen definiert ist-Präfix *Ihredsl*`CommandExtension`. Sie können mehrere Menübefehlsklasse schreiben.

`QueryStatus()` wird aufgerufen, wenn der Benutzer das Diagramm klickt. Er sollte die aktuelle Auswahl überprüfen und `command.Enabled` , um anzugeben, wenn der Befehl gilt.

```csharp
using System.ComponentModel.Composition;
using System.Linq;
using Company.MyDsl; // My DSL
using Company.MyDsl.ExtensionEnablement; // My DSL
using Microsoft.VisualStudio.Modeling; // Transactions
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement; // IVsSelectionContext
using Microsoft.VisualStudio.Modeling.ExtensionEnablement; // ICommandExtension

namespace MyMefExtension
{
  // Defined in Dsl\MefExtension\DesignerExtensionMetaDataAttribute.cs:
  [MyDslCommandExtension]
  public class MyCommandClass : ICommandExtension
  {
    /// <summary>
    /// Provides access to current document and selection.
    /// </summary>
    [Import]
    IVsSelectionContext SelectionContext { get; set; }

    /// <summary>
    /// Called when the user selects this command.
    /// </summary>
    /// <param name="command"></param>
    public void Execute(IMenuCommand command)
    {
      // Transaction is required if you want to update elements.
      using (Transaction t = SelectionContext.CurrentStore
              .TransactionManager.BeginTransaction("fix names"))
      {
        foreach (ExampleShape shape in SelectionContext.CurrentSelection)
        {
          ExampleElement element = shape.ModelElement as ExampleElement;
          element.Name = element.Name + " !";
        }
        t.Commit();
      }
    }

    /// <summary>
    /// Called when the user right-clicks the diagram.
    /// Determines whether the command should appear.
    /// This method should set command.Enabled and command.Visible.
    /// </summary>
    /// <param name="command"></param>
    public void QueryStatus(IMenuCommand command)
    {
      command.Enabled =
        command.Visible = (SelectionContext.CurrentSelection.OfType<ExampleShape>().Count() > 0);
    }

    /// <summary>
    /// Called when the user right-clicks the diagram.
    /// Determines the text of the command in the menu.
    /// </summary>
    public string Text
    {
      get { return "My menu command"; }
    }
  }
}
```

### <a name="gesture-handlers"></a>Gestenhandler

Ein Gestenhandler kann Verarbeiten von Objekten, die auf das Diagramm von überall innerhalb oder außerhalb von Visual Studio gezogen. Das folgende Beispiel ermöglicht den Benutzer Dateien aus dem Windows-Explorer auf das Diagramm ziehen. Es erstellt die Elemente, die die Dateinamen enthalten.

Sie können Ereignishandler zur Behandlung von zieht aus anderen DSL-Modelle und UML-Modellen schreiben. Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen eines Drag & Drop-Handlers](../modeling/how-to-add-a-drag-and-drop-handler.md).

```csharp
using System.ComponentModel.Composition;
using System.Linq;
using Company.MyDsl;
using Company.MyDsl.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling; // Transactions
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;

namespace MefExtension
{
  [MyDslGestureExtension]
  class MyGestureExtension : IGestureExtension
  {
    public void OnDoubleClick(ShapeElement targetElement, DiagramPointEventArgs diagramPointEventArgs)
    {
      System.Windows.Forms.MessageBox.Show("double click!");
    }

    /// <summary>
    /// Called when the user drags anything over the diagram.
    /// Return true if the dragged object can be dropped on the current target.
    /// </summary>
    /// <param name="targetMergeElement">The shape or diagram that the mouse is currently over</param>
    /// <param name="diagramDragEventArgs">Data about the dragged element.</param>
    /// <returns></returns>
    public bool CanDragDrop(ShapeElement targetMergeElement, DiagramDragEventArgs diagramDragEventArgs)
    {
      // This handler only allows items to be dropped onto the diagram:
      return targetMergeElement is MefDsl2Diagram &&
      // And only accepts files dragged from Windows Explorer:
        diagramDragEventArgs.Data.GetFormats().Contains("FileNameW");
    }

    /// <summary>
    /// Called when the user drops an item onto the diagram.
    /// </summary>
    /// <param name="targetDropElement"></param>
    /// <param name="diagramDragEventArgs"></param>
    public void OnDragDrop(ShapeElement targetDropElement, DiagramDragEventArgs diagramDragEventArgs)
    {
      MefDsl2Diagram diagram = targetDropElement as MefDsl2Diagram;
      if (diagram == null) return;

      // This handler only accepts files dragged from Windows Explorer:
      string[] draggedFileNames = diagramDragEventArgs.Data.GetData("FileNameW") as string[];
      if (draggedFileNames == null || draggedFileNames.Length == 0) return;

      using (Transaction t = diagram.Store.TransactionManager.BeginTransaction("file names"))
      {
        // Create an element to represent each file:
        foreach (string fileName in draggedFileNames)
        {
          ExampleElement element = new ExampleElement(diagram.ModelElement.Partition);
          element.Name = fileName;

          // This method of adding the new element allows the position
          // of the shape to be specified:
          ElementGroup group = new ElementGroup(element);
          diagram.ElementOperations.MergeElementGroupPrototype(
            diagram, group.CreatePrototype(), PointD.ToPointF(diagramDragEventArgs.MousePosition));
        }
        t.Commit();
      }
    }
  }
}
```

### <a name="validation-constraints"></a>Validierungseinschränkungen

Validierungsmethoden werden markiert, die `ValidationExtension` -Attribut, das generiert wird, durch die DSL, und auch durch <xref:Microsoft.VisualStudio.Modeling.Validation.ValidationMethodAttribute>. Die Methode kann in jeder Klasse, die nicht von einem Attribut markiert ist, angezeigt werden.

Weitere Informationen finden Sie unter [Validierung in einer domänenspezifischen Sprache](../modeling/validation-in-a-domain-specific-language.md).

```csharp
using Company.MyDsl;
using Company.MyDsl.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.Validation;

namespace MefExtension
{
  class MyValidationExtension // Can be any class.
  {
    // SAMPLE VALIDATION METHOD.
    // All validation methods have the following attributes.

    // Specific to the extended DSL:
    [MyDslValidationExtension]

    // Determines when validation is applied:
    [ValidationMethod(
       ValidationCategories.Save
     | ValidationCategories.Open
     | ValidationCategories.Menu)]

    /// <summary>
    /// When validation is executed, this method is invoked
    /// for every element in the model that is an instance
    /// of the second parameter type.
    /// </summary>
    /// <param name="context">For reporting errors</param>
    /// <param name="elementToValidate"></param>
    private void ValidateClassNames
      (ValidationContext context,
       // Type determines to what elements this will be applied:
       ExampleElement elementToValidate)
    {
      // Write code here to test values and links.
      if (elementToValidate.Name.IndexOf(' ') >= 0)
      {
        // Log any unacceptable values:
        context.LogError(
          // Description:
          "Name must not contain spaces"
          // Error code unique to this type of error:
          , "MyDsl001"
          // Element to highlight when user double-clicks error:
          , elementToValidate);
} } } }
```

## <a name="see-also"></a>Siehe auch

- [Bereitstellen von Visual Studio-Erweiterungen](../extensibility/shipping-visual-studio-extensions.md)
- [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)
- [Vorgehensweise: Hinzufügen eines Drag & Drop-Handlers](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [Validierung in einer domänenspezifischen Sprache](../modeling/validation-in-a-domain-specific-language.md)
