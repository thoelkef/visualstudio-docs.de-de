---
title: "Gewusst wie: Erweitern des DSL-Designer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fa807f1b-2780-491e-925b-abbfd31b2bfa
caps.latest.revision: 9
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 9
---
# Gewusst wie: Erweitern des DSL-Designer
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können Erweiterungen in den Designer erstellen, mit dem DSL\-Definitionen zu bearbeiten. Typen der Erweiterung, die Sie gehören das Hinzufügen von Menübefehlen vornehmen können, hinzufügen Handler für ziehen, und doppelklicken Sie auf Gesten und Regeln, die ausgelöst werden, wenn bestimmte Typen von Werten oder Beziehungen ändern. Die Erweiterungen können als eine Visual Studio Integration Extension \(VSIX\) verpackt und an andere Benutzer verteilt werden.  
  
 Beispielcode und Weitere Informationen zu dieser Funktion finden Sie in Visual Studio [Website Visualization and Modeling SDK \(VMSDK\)](http://go.microsoft.com/fwlink/?LinkID=186128).  
  
## Zum Einrichten der Lösung  
 Richten Sie ein Projekt, das den Code für die Erweiterung enthält, und ein VSIX\-Projekt, das das Projekt exportiert. Eine Projektmappe kann andere Projekte enthalten, die in der gleichen VSIX integriert sind.  
  
#### Erstellen Sie eine DSL\-Designer\-Erweiterungsprojektmappe  
  
1.  Erstellen Sie ein neues Projekt mit der Projektvorlage für Klassenbibliothek. In der **Neues Projekt** im Dialogfeld klicken Sie auf **Visual C\#\-** und dann im mittleren Fenster auf **Klassenbibliothek**.  
  
     Dieses Projekt enthält den Code der Erweiterungen.  
  
2.  Erstellen Sie ein neues Projekt mithilfe der VSIX\-Projektvorlage. In der **Neues Projekt** Dialogfeld erweitern Sie **Visual C\#\-**, klicken Sie auf **Erweiterbarkeit**, und klicken Sie dann im mittleren Fenster auf **VSIX\-Projekt**.  
  
     Wählen Sie **Hinzufügen**.  
  
     "Source.Extension.vsixmanifest", die im VSIX\-manifest\-Editor wird geöffnet.  
  
3.  Klicken Sie oberhalb der Inhaltsfeld auf **Inhalt hinzufügen**.  
  
4.  In der **Inhalt hinzufügen** \(Dialogfeld\), legen **Inhaltstyp auswählen** auf **MEF\-Komponente**, und legen Sie **Projekt** auf Ihr Klassenbibliotheksprojekt hinzu.  
  
5.  Klicken Sie auf **Editionen auswählen** und stellen Sie sicher, dass **Visual Studio Enterprise** aktiviert ist.  
  
6.  Stellen Sie sicher, dass das VSIX\-Projekt das Startprojekt der Projektmappe ist.  
  
7.  Fügen Sie im Klassenbibliotheksprojekt Verweise auf die folgenden Assemblys hinzu:  
  
     Microsoft.VisualStudio.CoreUtility  
  
     Microsoft.VisualStudio.Modeling.Sdk.11.0  
  
     Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0  
  
     Microsoft.VisualStudio.Modeling.Sdk.DslDefinition.11.0  
  
     Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0  
  
     System.ComponentModel.Composition  
  
     System.Drawing  
  
     System.Drawing.Design  
  
     System.Windows.Forms  
  
## Tests und Bereitstellung  
 Um eine Erweiterung in diesem Thema zu testen, erstellen Sie, und führen Sie die Projektmappe. Eine experimentelle Instanz von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wird geöffnet. Öffnen Sie in diesem Fall eine DSL\-Projektmappe. Bearbeiten Sie das Diagramm DslDefinition. Das Erweiterungsverhalten kann angezeigt werden.  
  
 Die Erweiterungen für den Hauptknoten bereitstellen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], und auf anderen Computern, gehen Sie folgendermaßen vor:  
  
1.  Suchen Sie die VSIX\-Installationsdatei im VSIX\-Projekt in bin\\\*\\\*.vsix  
  
2.  Kopieren Sie diese Datei auf den Zielcomputer und in Windows Explorer \(oder Datei\-Explorer\), doppelklicken Sie darauf.  
  
     Die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Extension Manager öffnet, um sicherzustellen, dass die Erweiterung installiert wurde.  
  
 Gehen Sie folgendermaßen vor, um die Erweiterung zu deinstallieren:  
  
1.  im [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], auf die **Tools** Menü klicken Sie auf **Extension Manager**.  
  
2.  Wählen Sie die Erweiterung aus, und löschen Sie ihn.  
  
## Einen Befehl im Kontextmenü hinzufügen  
 Damit der Befehl im Kontextmenü auf die DSL\-Designer\-Oberfläche oder im DSL\-Explorer\-Fenster angezeigt wird, können schreiben Sie eine Klasse, die der folgenden.  
  
 Implementieren Sie die Klasse muss `ICommandExtension` und muss das Attribut `DslDefinitionModelCommandExtension`.  
  
```  
using System.Collections.Generic;  
using System.ComponentModel.Composition;  
using System.Linq;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;  
using Microsoft.VisualStudio.Modeling.DslDefinition;  
using Microsoft.VisualStudio.Modeling.DslDefinition.ExtensionEnablement;  
using Microsoft.VisualStudio.Modeling.DslDesigner;  
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
  
namespace Fabrikam.SimpleDslDesignerExtension  
{  
  /// <summary>  
  /// Command extending the DslDesigner.  
  /// </summary>  
  [DslDefinitionModelCommandExtension]   
  public class MyDslDesignerCommand : ICommandExtension  
  {  
    /// <summary>  
    /// Selection Context for this command  
    /// </summary>  
    [Import]  
    IVsSelectionContext SelectionContext { get; set; }  
  
    /// <summary>  
    /// Is the command visible and active?  
    /// This is called when the user right-clicks.  
    /// </summary>  
    public void QueryStatus(IMenuCommand command)  
    {  
      command.Visible = true;  
      // Is there any selected DomainClasses in the Dsl explorer?  
      command.Enabled =   
        SelectionContext.AtLeastOneSelected<DomainClass>();  
  
      // Is there any selected ClassShape on the design surface?  
      command.Enabled |=   
        (SelectionContext.GetCurrentSelection<ClassShape>()  
                .Count() > 0);  
    }  
    /// <summary>  
    /// Executes the command   
    /// </summary>  
    /// <param name="command">Command initiating this action</param>  
    public void Execute(IMenuCommand command)  
    {  
      ...  
    }  
    /// <summary>  
    /// Label for the command  
    /// </summary>  
    public string Text  
    {  
      get { return "My Command"; }  
    }  
  }  
}  
```  
  
## Behandlung von Mausgesten  
 Der Code ist ähnlich wie der Code des Menübefehls.  
  
```  
[DslDefinitionModelGestureExtension]  
 class MouseGesturesExtensions : IGestureExtension  
 {  
  /// <summary>  
  /// Double-clicking on a shape representing a Domain model element displays this model element in a dialog box  
  /// </summary>  
  /// <param name="targetElement">Shape element on which the user has clicked</param>  
  /// <param name="diagramPointEventArgs">event args for this double-click</param>  
  public void OnDoubleClick(ShapeElement targetElement,  
       DiagramPointEventArgs diagramPointEventArgs)  
  {  
   ModelElement modelElement = PresentationElementHelper.  
        GetDslDefinitionModelElement(targetElement);  
   if (modelElement != null)  
   {  
    MessageBox.Show(string.Format(  
      "Double clicked on {0}", modelElement.ToString()),   
      "Model element double-clicked");  
   }  
  }  
  
  /// <summary>  
  /// Tells if the DslDesigner can consume the to-be-dropped information  
  /// </summary>  
  /// <param name="targetMergeElement">Shape on which we try to drop</param>  
  /// <param name="diagramDragEventArgs">Drop event</param>  
  /// <returns><c>true</c> if we can consume the to be dropped data, and <c>false</c> otherwise</returns>  
  public bool CanDragDrop(ShapeElement targetMergeElement,  
        DiagramDragEventArgs diagramDragEventArgs)  
  {  
   if (diagramDragEventArgs.Data.GetDataPresent(DataFormats.FileDrop))  
   {  
    diagramDragEventArgs.Effect = DragDropEffects.Copy;  
    return true;  
   }  
   return false;  
  }  
  
  /// <summary>  
  /// Processes the drop by displaying the dropped text  
  /// </summary>  
  /// <param name="targetMergeElement">Shape on which we dropped</param>  
  /// <param name="diagramDragEventArgs">Drop event</param>  
  public void OnDragDrop(ShapeElement targetDropElement, DiagramDragEventArgs diagramDragEventArgs)  
  {  
   if (diagramDragEventArgs.Data.GetDataPresent(DataFormats.FileDrop))  
   {  
    string[] droppedFiles =   
      diagramDragEventArgs.Data.  
               GetData(DataFormats.FileDrop) as string[];  
    MessageBox.Show(string.Format("Dropped text {0}",  
        string.Join("\r\n", droppedFiles)), "Dropped Text");  
   }  
  }  
 }  
```  
  
## Reagieren auf Änderungen Wert  
 Dieser Handler benötigt ein Domänenmodell ordnungsgemäß funktioniert. Wir bieten eine einfache Domänenmodell.  
  
```  
using System.Diagnostics;  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.DslDefinition;  
namespace Fabrikam.SimpleDslDesignerExtension  
{  
  /// <summary>  
  /// Rule firing when the type of a domain model property is changed. The change is displayed  
  /// in the debugger (Output window of the Visual Studio instance debugging this extension)  
  /// </summary>  
  [RuleOn(typeof(PropertyHasType))]  
  public class DomainPropertyTypeChangedRule : RolePlayerChangeRule  
  {  
    /// <summary>  
    /// Method called when the Type of a Domain Property   
    /// is changed by the user in a DslDefinition  
    /// </summary>  
    /// <param name="e"></param>  
    public override void RolePlayerChanged(RolePlayerChangedEventArgs e)  
    {  
      // We are only interested in the type  
      if (e.DomainRole.Id == PropertyHasType.TypeDomainRoleId)  
      {  
        PropertyHasType relationship =   
           e.ElementLink as PropertyHasType;  
        DomainType newType = e.NewRolePlayer as DomainType;  
        DomainType oldType = e.OldRolePlayer as DomainType;  
        DomainProperty property = relationship.Property;  
  
         // We write about the Type change in the debugguer  
        Debug.WriteLine(string.Format("The type of the Domain property '{0}' of domain class '{1}' changed from '{2}' to '{3}'",  
          property.Name,  
          property.Class.Name,  
          oldType.GetFullName(false),  
          newType.GetFullName(false))  
} }  }  );  
```  
  
 Im folgende Code wird ein einfaches Modell implementiert. Erstellen Sie eine neue GUID, um den Platzhalter zu ersetzen.  
  
```  
using System;  
using System.ComponentModel.Composition;  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.DslDefinition;  
namespace Fabrikam.SimpleDslDesignerExtension  
{  
    /// <summary>  
    /// Simplest possible domain model   
    /// needed only for extension rules.   
    /// </summary>  
    [DomainObjectId(SimpleDomainModelExtension.DomainModelId)]  
    public class SimpleDomainModelExtension : DomainModel  
    {  
        // Id of this domain model extension   
        // Please replace this with a new GUID:  
        public const string DomainModelId =   
                  "00000000-0000-0000-0000-000000000000";  
  
        /// <summary>  
        /// Constructor for the domain model extension  
        /// </summary>  
        /// <param name="store">Store in which the domain model will be loaded</param>  
        public SimpleDomainModelExtension(Store store)  
            : base(store, new Guid(SimpleDomainModelExtension.DomainModelId))  
        {  
  
        }  
  
        /// <summary>  
        /// Rules brought by this domain model extension  
        /// </summary>  
        /// <returns></returns>  
        protected override System.Type[] GetCustomDomainModelTypes()  
        {  
            return new Type[] {  
                     typeof(DomainPropertyTypeChangedRule)  
                              };  
        }  
    }  
  
    /// <summary>  
    /// Provider for the DomainModelExtension  
    /// </summary>  
    [Export(typeof(DomainModelExtensionProvider))]    [ProvidesExtensionToDomainModel(typeof(DslDefinitionModelDomainModel))]  
    public class SimpleDomainModelExtensionProvider   
          : DomainModelExtensionProvider  
    {  
        /// <summary>  
        /// Extension model type  
        /// </summary>  
        public override Type DomainModelType  
        {  
            get  
            {  
                return typeof(SimpleDomainModelExtension);  
            }  
        }  
  
    }  
}  
```