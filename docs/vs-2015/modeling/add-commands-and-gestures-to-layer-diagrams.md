---
title: Hinzufügen von Befehlen und Bewegungen zu Ebenendiagrammen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- layer diagrams, adding custom commands
- layer diagrams, adding custom gestures
ms.assetid: ac9c417b-0b40-4a90-86f5-ee3cbdce030b
caps.latest.revision: 40
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: f70bcea2599ac318d59255a274629b5c53cea730
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49889788"
---
# <a name="add-commands-and-gestures-to-layer-diagrams"></a>Hinzufügen von Befehlen und Bewegungen zu Ebenendiagrammen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können Kontextmenübefehle und Gestenhandler in Ebenendiagrammen in Visual Studio definieren. Sie können diese Erweiterungen in einer Visual Studio-Integrationserweiterung (VSIX) verpacken, die Sie an andere Visual Studio-Benutzer verteilen können.  
  
 Sie können bei Bedarf mehrere Befehls- und Gestenhandler im gleichen Visual Studio-Projekt definieren. Sie können auch mehrere Projekte dieser Art in einer VSIX kombinieren. Sie könnten z. B. eine einzelne VSIX definieren, die Ebenenbefehle, eine domänenspezifische Sprache und Befehle für UML-Diagramme einschließt.  
  
> [!NOTE]
>  Sie können die Architekturvalidierung auch anpassen, in der der Quellcode der Benutzer mit Ebenendiagrammen verglichen wird. Sie sollten die Architekturvalidierung in einem separaten Visual Studio-Projekt definieren. Sie können sie der gleichen VSIX hinzufügen wie anderen Erweiterungen. Weitere Informationen finden Sie unter [Hinzufügen einer benutzerdefinierten architekturvalidierung zu Ebenendiagrammen](../modeling/add-custom-architecture-validation-to-layer-diagrams.md).  
  
## <a name="requirements"></a>Anforderungen  
 Siehe [Anforderungen](../modeling/extend-layer-diagrams.md#prereqs).  
  
## <a name="defining-a-command-or-gesture-in-a-new-vsix"></a>Definieren eines Befehls oder einer Geste in einer neuen VSIX  
 Projektvorlagen stellen die schnellste Methode dar, eine Erweiterung zu erstellen. Dabei werden der Code und die VSIX im selben Projekt platziert.  
  
#### <a name="to-define-an-extension-by-using-a-project-template"></a>So definieren Sie mithilfe einer Projektvorlage eine Erweiterung  
  
1. Erstellen Sie in einer neuen Projektmappe ein Projekt. Verwenden Sie dazu den Befehl **Neues Projekt** im Menü **Datei** .  
  
2. Wählen Sie im Dialogfeld **Neues Projekt** unter **Modellierungsprojekte**entweder **Layer Designer Command Extension** (Ebenen-Designer - Befehlserweiterung) oder **Layer Designer Command Extension**(Ebenen-Designer - Gestenerweiterung) aus.  
  
    Mit dieser Vorlage wird ein Projekt mit einem kleinen Arbeitsbeispiel erstellt.  
  
3. Drücken Sie **STRG+F5** oder **F5**, um die Erweiterung zu testen.  
  
    Eine experimentelle Instanz von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] wird gestartet. Erstellen Sie in dieser Instanz ein Ebenendiagramm. Der Befehl oder die Gestenerweiterung sollte in diesem Diagramm funktionieren.  
  
4. Schließen Sie die experimentelle Instanz, und ändern Sie den Beispielcode. Weitere Informationen finden Sie unter [Navigieren zu und Update layer-Modellen im Programmcode](../modeling/navigate-and-update-layer-models-in-program-code.md).  
  
5. Sie können dem gleichen Projekt mehrere Befehls- oder Gestenhandler hinzufügen. Weitere Informationen finden Sie in einem der folgenden Abschnitte:  
  
    [Definieren eines Menübefehls](#command)  
  
    [Definieren eines Gestenhandlers](#gesture)  
  
6. Um die Erweiterung in der Hauptinstanz von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]oder auf einem anderen Computer zu installieren, suchen Sie die **.vsix** -Datei im Ordner *bin\\*. Kopieren Sie die Datei auf den Computer, auf dem Sie sie installieren möchten, und doppelklicken Sie dann darauf. Verwenden Sie zum Deinstallieren der Datei die Option **Erweiterungen und Updates** im Menü **Extras** .  
  
## <a name="adding-a-command-or-gesture-to-a-separate-vsix"></a>Hinzufügen eines Befehls oder einer Geste zu einem separaten VSIX  
 Wenn Sie eine VSIX erstellen möchten, die Befehle, Ebenenvalidierungssteuerelemente und andere Erweiterungen enthält, empfiehlt es sich, ein Projekt zum Definieren der VSIX und getrennte Projekte für die Handler zu erstellen. Weitere Informationen zu anderen Modellerweiterungstypen finden Sie unter [Erweitern von UML-Modellen und Diagrammen](../modeling/extend-uml-models-and-diagrams.md).  
  
#### <a name="to-add-layer-extensions-to-a-separate-vsix"></a>So fügen Sie einer separaten VSIX Ebenenerweiterungen hinzu  
  
1.  Erstellen Sie in einer neuen oder vorhandenen Visual Studio-Projektmappe ein Klassenbibliotheksprojekt. Klicken Sie im Dialogfeld **Neues Projekt** auf **Visual C#** , und klicken Sie dann auf **Klassenbibliothek**. Dieses Projekt enthält Befehls- oder Gestenhandlerklassen.  
  
    > [!NOTE]
    >  Sie können mehrere Befehls- oder Gestenhandlerklassen in einer Klassenbibliothek definieren, jedoch sollten Sie Ebenenvalidierungsklassen in einer separaten Klassenbibliothek definieren.  
  
2.  Identifizieren oder erstellen Sie ein VSIX-Projekt in der Projektmappe. Ein VSIX-Projekt enthält eine Datei mit dem Namen **source.extension.vsixmanifest**. So fügen Sie ein VSIX-Projekt:  
  
    1.  Erweitern Sie im Dialogfeld **Neues Projekt** den Knoten **Visual C#**, und klicken Sie auf **Erweiterungen**und anschließend auf **VSIX Project**.  
  
    2.  Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das VSIX-Projekt, und klicken Sie anschließend auf **Als Startprojekt festlegen**.  
  
    3.  Klicken Sie auf **Editionen auswählen** , und stellen Sie sicher, dass **Visual Studio** aktiviert ist.  
  
3.  Fügen Sie in **source.extension.vsixmanifest**unter **Objekte**das Befehls- oder Gestenhandlerprojekt als MEF-Komponente hinzu.  
  
    1.  Wählen Sie auf der Registerkarte **Objekte**die Option **Neu**aus.  
  
    2.  Wählen Sie bei **Typ**die Option **Microsoft.VisualStudio.MefComponent**aus.  
  
    3.  Wählen Sie bei **Quelle**die Option **Projekt in der aktuellen Projektmappe** und den Namen des Befehls- oder Gestenhandlerprojekts aus.  
  
    4.  Speichern Sie die Datei.  
  
4.  Kehren Sie zum Befehls- oder Gestenhandlerprojekt zurück, und fügen Sie die folgenden Projektverweise hinzu.  
  
|**Verweis**|**Optionen**|  
|-------------------|------------------------------------|  
|Programme\Microsoft Visual Studio [Version]\Common7\IDE\Extensions\Microsoft\Architecture Tools\ExtensibilityRuntime\Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.dll|Erstellen und Bearbeiten von Ebenen|  
|Microsoft.VisualStudio.Uml.Interfaces|Erstellen und Bearbeiten von Ebenen|  
|Microsoft.VisualStudio.ArchitectureTools.Extensibility|Ändern von Formen in Diagrammen|  
|System.ComponentModel.Composition|Definieren von Komponenten mit Managed Extensibility Framework (MEF)|  
|Microsoft.VisualStudio.Modeling.Sdk.[Version]|Definieren von Modellierungserweiterungen|  
|Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[Version]|Aktualisieren von Formen und Diagrammen|  
  
1.  Bearbeiten Sie die Klassendatei im C#-Klassenbibliotheksprojekt so, dass sie den Code für die Erweiterung enthält. Weitere Informationen finden Sie in einem der folgenden Abschnitte:  
  
     [Definieren eines Menübefehls](#command)  
  
     [Definieren eines Gestenhandlers](#gesture)  
  
     Siehe auch [Navigieren zu und Update layer-Modellen im Programmcode](../modeling/navigate-and-update-layer-models-in-program-code.md).  
  
2.  Drücken Sie STRG+F5 oder F5, um die Anwendung zu testen. Eine experimentelle Instanz von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] wird geöffnet. Erstellen oder öffnen Sie ein Ebenendiagramm in dieser Instanz.  
  
3.  Um die Erweiterung in der Hauptinstanz von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]oder auf einem anderen Computer zu installieren, suchen Sie die Datei **.vsix** im Verzeichnis **bin** des VSIX-Projekts. Kopieren Sie die Datei auf den Computer, auf dem Sie die VSIX installieren möchten. Doppelklicken Sie auf die VSIX-Datei in Windows-Explorer (Datei-Explorer in Windows 8).  
  
     Verwenden Sie zum Deinstallieren der Datei die Option **Erweiterungen und Updates** im Menü **Extras** .  
  
##  <a name="command"></a> Definieren eines Menübefehls  
 Sie können einer vorhandenen Geste oder einem Befehlsprojekt mehrere Menübefehlsdefinitionen hinzufügen. Jeder Befehl wird von einer Klasse definiert, die über die folgenden Eigenschaften verfügt:  
  
- Die Klasse wird folgendermaßen deklariert:  
  
   `[LayerDesignerExtension]`  
  
   `[Export(typeof(ICommandExtension))]`  
  
   `public class`  *MyLayerCommand*  `: ICommandExtension { ... }`  
  
- Der Namespace und der Name der Klasse sind unwichtig.  
  
- `ICommandExtension` wird mit den folgenden Methoden implementiert:  
  
  -   `string Text {get;}` - Die Bezeichnung, die im Menü angezeigt wird.  
  
  -   `void QueryStatus(IMenuCommand command)` - Wird aufgerufen, wenn der Benutzer mit der rechten Maustaste auf das Diagramm klickt, und bestimmt, ob der Befehl für die aktuelle Auswahl des Benutzers sichtbar und aktiviert ist.  
  
  -   `void Execute(IMenuCommand command)` - Wird aufgerufen, wenn der Benutzer den Befehl auswählt.  
  
- Sie können `IDiagramContext`importieren, um die aktuelle Auswahl zu bestimmen:  
  
   `[Import]`  
  
   `public IDiagramContext DiagramContext { get; set; }`  
  
   `...`  
  
   `DiagramContext.CurrentDiagram.SelectedShapes.Count()...`  
  
  Weitere Informationen finden Sie unter [Navigieren zu und Update layer-Modellen im Programmcode](../modeling/navigate-and-update-layer-models-in-program-code.md).  
  
  Erstellen Sie zum Hinzufügen eines neuen Befehls eine neue Codedatei, die das folgende Beispiel enthält. Testen und bearbeiten Sie das Beispiel dann.  
  
```  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;  
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
using System.ComponentModel.Composition;  
using System.Linq;  
  
namespace MyLayerExtension // Change to your preference.  
{  
  // This is a feature for Layer diagrams:  
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
  
##  <a name="gesture"></a> Definieren eines Gestenhandlers  
 Ein Gestenhandler reagiert, wenn der Benutzer Elemente auf das Ebenendiagramm zieht und wenn der Benutzer auf eine beliebige Stelle im Diagramm doppelklickt.  
  
 Sie können dem vorhandenen Befehls- oder Gestenhandler-VSIX-Projekt eine Codedatei hinzufügen, die einen Gestenhandler definiert:  
  
```  
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
  
  ```  
  public void OnDragDrop(IShape target, IDataObject data)  
  {  
      ILayerElement element = target.GetLayerElement();  
      if (element is ILayer)  
      {  
          // ...  
      }  
  }  
  ```  
  
- Handler für einige Typen von gezogenen Elementen sind bereits definiert. Der Benutzer kann z. B. Elemente aus dem Projektmappen-Explorer in ein Ebenendiagramm ziehen. Sie können keinen Ziehhandler für diese Elementtypen definieren. In diesen Fällen werden die `DragDrop` -Methoden nicht aufgerufen.  
  
  Weitere Informationen zum Decodieren anderer Elemente, wenn sie in das Diagramm gezogen werden, finden Sie unter [Definieren eines gestenhandlers in einem Modellierungsdiagramm](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Navigieren in und Aktualisieren von Ebenenmodellen im Programmcode](../modeling/navigate-and-update-layer-models-in-program-code.md)   
 [Hinzufügen einer benutzerdefinierten architekturvalidierung zu Ebenendiagrammen](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)   
 [Definieren und Installieren einer Modellierungserweiterung](../modeling/define-and-install-a-modeling-extension.md)



