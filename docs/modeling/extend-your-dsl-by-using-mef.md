---
title: Erweitern der DSL mithilfe des MEF erstellte | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3e7be79a-53ab-4d79-863a-bef8d27839bd
caps.latest.revision: "14"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: 1f64368c90f6d77be24271eeaac96cc6b5624f67
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="extend-your-dsl-by-using-mef"></a>Erweitern von DSL mittels MEF
Sie können Ihre domänenspezifische Sprache (DSL) mit Managed Extensibility Framework (MEF) erweitern. Sie oder andere Entwickler werden können zum Schreiben von Erweiterungen für die DSL ohne Änderung der DSL-Definition und Programmcode. Diese Erweiterungen umfassen Menübefehle, Drag & Drop-Handler und Überprüfung. Benutzer werden zum Installieren der DSL, und klicken Sie dann optional Erweiterungen dafür können.  
  
 Darüber hinaus beim Sie MEF in der DSL aktivieren, kann es einige der Funktionen von der DSL Schreiben einfacher sein, auch wenn sie alle zusammen mit der DSL erstellt werden.  
  
 Weitere Informationen über MEF finden Sie unter [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).  
  
### <a name="to-enable-your-dsl-to-be-extended-by-mef"></a>Zum Aktivieren der DSL von MEF erweitert werden  
  
1.  Erstellen Sie einen neuen Ordner namens **MefExtension** innerhalb der **DslPackage** Projekt. Die folgenden Dateien hinzufügen:  
  
     Dateiname:`CommandExtensionVSCT.tt`  
  
    > [!IMPORTANT]
    >  Legen Sie die GUID in dieser Datei mit der der GUID-CommandSetId identisch sein, die in DslPackage\GeneratedCode\Constants.tt definiert ist  
  
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
  
     Dateiname:`CommandExtensionRegistrar.tt`  
  
    ```  
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>  
    <#@ include file="DslPackage\CommandExtensionRegistrar.tt" #>  
    ```  
  
     Dateiname:`ValidationExtensionEnablement.tt`  
  
    ```  
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>  
    <#@ include file="DslPackage\ValidationExtensionEnablement.tt" #>  
    ```  
  
     Dateiname:`ValidationExtensionRegistrar.tt`  
  
     Wenn Sie diese Datei hinzufügen, müssen Sie Überprüfung in der DSL aktivieren, mit mindestens einer der Schalter in **EditorValidation** im Explorer für DSL.  
  
    ```  
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>  
    <#@ include file="DslPackage\ValidationExtensionRegistrar.tt" #>  
    ```  
  
     Dateiname:`PackageExtensionEnablement.tt`  
  
    ```  
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>  
    <#@ include file="DslPackage\PackageExtensionEnablement.tt" #>  
    ```  
  
2.  Erstellen Sie einen neuen Ordner namens **MefExtension** innerhalb der **Dsl** Projekt. Die folgenden Dateien hinzufügen:  
  
     Dateiname:`DesignerExtensionMetaDataAttribute.tt`  
  
    ```  
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>  
    <#@ include file="Dsl\DesignerExtensionMetadataAttribute.tt" #>  
    ```  
  
     Dateiname:`GestureExtensionEnablement.tt`  
  
    ```  
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>  
    <#@ include file="Dsl\GestureExtensionEnablement.tt" #>  
    ```  
  
     Dateiname:`GestureExtensionController.tt`  
  
    ```  
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>  
    <#@ include file="Dsl\GestureExtensionController.tt" #>  
    ```  
  
3.  Fügen Sie die folgende Zeile an die vorhandene Datei mit dem Namen **DslPackage\Commands.vsct**:  
  
    ```  
    <Include href="MefExtension\CommandExtensionVSCT.vsct"/>  
    ```  
  
     Fügen Sie die Zeile nach den vorhandenen `<Include>` Richtlinie.  
  
4.  `Open DslDefinition.dsl.`  
  
5.  Wählen Sie im Explorer für DSL **Editor\Validation**.  
  
6.  Stellen Sie sicher, dass mindestens eine der Eigenschaften mit dem Namen im Fenster Eigenschaften **verwendet...**  ist `true`.  
  
7.  Klicken Sie auf der Symbolleiste Projektmappen-Explorer auf **alle Vorlagen transformieren**.  
  
     Untergeordnete Dateien werden unterhalb der einzelnen Dateien, die Sie hinzugefügt.  
  
8.  Erstellen Sie und führen Sie die Projektmappe, um sicherzustellen, dass es weiterhin ausgeführt wird.  
  
 Der DSL ist jetzt mit dem MEF-aktiviert. Sie können Menübefehle, Gesten Handler und validierungseinschränkungen als MEF-Erweiterungen schreiben. Sie können diese Erweiterungen in der Projektmappe DSL zusammen mit anderen benutzerdefinierten Code schreiben. Darüber hinaus Sie oder andere Entwickler können schreiben separate [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Erweiterungen, die der DSL zu erweitern.  
  
## <a name="creating-an-extension-for-a-mef-enabled-dsl"></a>Erstellen eine Erweiterung für eine MEF-fähigen DSL  
 Wenn Sie Zugriff auf eine MEF-fähigen DSL von sich selbst oder eine andere Person erstellt haben, können Sie Erweiterungen dafür schreiben. Die Erweiterungen können verwendet werden, um Menübefehle, Gesten-Handler oder validierungseinschränkungen hinzuzufügen. Um diese Erweiterungen zu erstellen, verwenden Sie eine [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Extension (VSIX)-Lösung. Die Lösung besteht aus zwei Teilen: einem Klassenbibliotheksprojekt, in dem die Codeassembly erstellt und ein VSIX-Projekt, die die Assembly verpackt.  
  
#### <a name="to-create-a-dsl-extension-vsix"></a>So erstellen eine DSL-Erweiterung VSIX  
  
1.  Erstellen Sie ein neues Klassenbibliotheksprojekt. Klicken Sie hierzu in der **neues Projekt** wählen Sie im Dialogfeld **Visual Basic** oder **Visual C#-** und wählen Sie dann **-Klassenbibliothek**.  
  
2.  Fügen Sie in das neue Klassenbibliotheksprojekt einen Verweis auf die Assembly der DSL.  
  
    -   Diese Assembly wurde in der Regel einen Namen mit der Endung ". DSL.dll".  
  
    -   Wenn Sie das Projekt DSL können zugreifen, finden Sie die Assemblydatei unter dem Verzeichnis **Dsl\bin\\\***  
  
    -   Wenn Sie Zugriff auf die DSL VSIX-Datei haben, finden Sie die Assembly, durch die Dateinamenerweiterung der VSIX-Datei in ".zip" ändern. Dekomprimieren Sie die ZIP-Datei.  
  
3.  Fügen Sie Verweise auf die folgenden .NET Assemblys hinzu:  
  
    -   Microsoft.VisualStudio.Modeling.Sdk.11.0.dll  
  
    -   Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0.dll  
  
    -   Microsoft.VisualStudio.Modeling.Sdk.Shell.11.0.dll  
  
    -   System.ComponentModel.Composition.dll  
  
    -   System.Windows.Forms.dll  
  
4.  Erstellen Sie ein VSIX-Projekt, in der gleichen Projektmappe. Klicken Sie hierzu in der **neues Projekt** Dialogfeld erweitern Sie **Visual Basic** oder **Visual C#-**, klicken Sie auf **Erweiterbarkeit**, und wählen Sie dann  **VSIX-Projekt**.  
  
5.  Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste des VSIX-Projekts, und klicken Sie dann auf **als Startprojekt festlegen**.  
  
6.  Öffnen Sie in das neue Projekt **"Source.Extension.vsixmanifest"**.  
  
7.  Klicken Sie auf **Inhalte hinzufügen**. Klicken Sie im Dialogfeld festlegen **Inhaltstyp** auf **MEF-Komponente**, und **Quellprojekt** auf Ihr Klassenbibliotheksprojekt.  
  
8.  Fügen Sie ein VSIX-Verweis auf die DSL hinzu.  
  
    1.  In **"Source.Extension.vsixmanifest"**, klicken Sie auf **Verweis hinzufügen**  
  
    2.  Klicken Sie im Dialogfeld auf **hinzufügen Nutzlast** und suchen Sie die VSIX-Datei der DSL. Die VSIX-Datei wird in der DSL-Lösung erstellt, in **DslPackage\bin\\\***.  
  
         Dadurch können Benutzer, die zur gleichen Zeit der DSL und die Erweiterung zu installieren. Wenn der Benutzer bereits mit der DSL installiert hat, wird nur die Erweiterung installiert.  
  
9. Überprüfen und aktualisieren Sie die anderen Felder der **"Source.Extension.vsixmanifest"**. Klicken Sie auf **Editionen auswählen** und überprüfen Sie, ob die richtige [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Editionen festgelegt sind.  
  
10. Fügen Sie Code, auf das Klassenbibliotheksprojekt. Im Beispiel im nächsten Abschnitt als Leitfaden verwendet.  
  
     Sie können eine beliebige Anzahl von Befehlen, Gesten und Validierungsklassen hinzufügen.  
  
11. Um die Erweiterung zu testen, drücken Sie die **F5**. In der experimentellen Instanz von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]erstellen oder öffnen Sie eine Beispieldatei der DSL.  
  
## <a name="writing-mef-extensions-for-dsls"></a>Schreiben von MEF-Erweiterungen für konzentriert  
 Sie können Erweiterungen in das Projekt von einer separaten DSL-Erweiterungsprojektmappe Assembly-Code schreiben. Sie können auch als eine einfache Möglichkeit zum Schreiben von Befehlen, Gesten und Validierungscode als Teil der DSL MEF in Ihrem Projekt DslPackage verwenden.  
  
### <a name="menu-commands"></a>Menübefehle  
 Um einen Menübefehl zu schreiben, definieren Sie eine Klasse, die implementiert <xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ICommandExtension> und die Klasse mit dem Attribut, das in der DSL, die mit dem Namen definiert Präfixlänge *YourDsl*`CommandExtension`. Sie können mehrere Menübefehlsklasse schreiben.  
  
 `QueryStatus()`wird aufgerufen, wenn der Benutzer auf das Diagramm klickt. Er sollte die aktuelle Auswahl überprüfen und `command.Enabled` , um anzugeben, wenn der Befehl anwendbar ist.  
  
```  
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
 Objekte, die von jedem beliebigen Standort, auf das Diagramm gezogen innerhalb oder außerhalb ein gestenhandlers behandeln kann [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Das folgende Beispiel ermöglicht den Benutzer Dateien aus Windows-Explorer auf das Diagramm zu ziehen. Elemente, die Dateinamen enthalten, erstellt.  
  
 Sie können Handler für den Umgang mit zieht aus anderen DSL und UML-Modelle erstellen. Weitere Informationen finden Sie unter [wie: Hinzufügen eines Drag-and-Drop-Ereignishandlers](../modeling/how-to-add-a-drag-and-drop-handler.md).  
  
```  
  
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
 Validierungsmethoden werden markiert, die `ValidationExtension` -Attribut, das generiert wird, von der DSL, und auch <xref:Microsoft.VisualStudio.Modeling.Validation.ValidationMethodAttribute>. Die Methode kann in einer Klasse, die nicht von einem Attribut markiert ist, angezeigt werden.  
  
 Weitere Informationen finden Sie unter [Überprüfung in einer domänenspezifischen Sprache](../modeling/validation-in-a-domain-specific-language.md).  
  
```  
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
 [Versand von Visual Studio-Erweiterungen](../extensibility/shipping-visual-studio-extensions.md)   
 [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)   
 [Vorgehensweise: Hinzufügen eines Drag-and-Drop-Ereignishandlers](../modeling/how-to-add-a-drag-and-drop-handler.md)   
 [Validierung in einer domänenspezifischen Sprache](../modeling/validation-in-a-domain-specific-language.md)