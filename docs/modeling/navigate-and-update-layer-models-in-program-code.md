---
title: Navigieren in und Aktualisieren von Ebenenmodellen im Programmcode | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- layer models, navigating in program code
- layer models, updating in program code
ms.assetid: c60edc87-33ee-4964-a954-40069f9febf3
caps.latest.revision: 20
author: alexhomer1
ms.author: ahomer
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: cfe4f389516a3421bdc0d8643790dbb9c7cc2733
ms.contentlocale: de-de
ms.lasthandoff: 09/06/2017

---
# <a name="navigate-and-update-layer-models-in-program-code"></a>Navigieren in und Aktualisieren von Ebenenmodellen im Programmcode
In diesem Thema werden die Elemente und Beziehungen in Ebenenmodellen beschrieben, die Sie mithilfe von Programmcode durchsuchen und aktualisieren können. Weitere Informationen zur Abhängigkeit Diagramme aus der Sicht des Benutzers finden Sie unter [Abhängigkeit Diagrammen: Verweis](../modeling/layer-diagrams-reference.md) und [Abhängigkeit Diagrammen: Richtlinien](../modeling/layer-diagrams-guidelines.md).  
  
 Die <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer> in diesem Thema beschriebene Modell ist eine Fassade eines allgemeineren <xref:Microsoft.VisualStudio.GraphModel> Modell. Wenn Sie schreiben eine [Menübefehl-oder gestenerweiterung](../modeling/add-commands-and-gestures-to-layer-diagrams.md), verwenden Sie die `Layer` Modell. Wenn Sie schreiben eine [layer validierungserweiterung](../modeling/add-custom-architecture-validation-to-layer-diagrams.md), es ist einfacher zu verwenden die `GraphModel`.  
  
## <a name="transactions"></a>Transaktionen  
 Erwägen Sie beim Aktualisieren eines Modells die Änderungen in eine `ILinkedUndoTransaction` einzuschließen. Auf diese Weise werden die Änderungen zu einer Transaktion gruppiert. Wenn eine der Änderungen fehlschlägt, wird die gesamte Transaktion zurückgesetzt. Wenn der Benutzer eine Änderung rückgängig macht, werden alle Änderungen zusammen rückgängig gemacht.  
  
```  
using (ILinkedUndoTransaction t =  
        LinkedUndoContext.BeginTransaction("a name"))  
{   
    // Make changes here ....  
    t.Commit(); // Don't forget this!  
}  
```  
  
## <a name="containment"></a>Kapselung  
 ![ILayer und ILayerModel können beide ILAYER enthalten. ] (../modeling/media/layerapi_containment.png "LayerApi_Containment")  
  
 Ebenen (<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayer>) und das Ebenenmodell (<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerModel>) können Kommentare und Ebenen enthalten.  
  
 Eine Ebene (`ILayer`) kann in einem Ebenenmodell (`ILayerModel`) enthalten sein oder in einer anderen `ILayer` geschachtelt werden.  
  
 Verwenden Sie die Erstellungsmethoden für den entsprechenden Container, um einen Kommentar oder eine Ebene zu erstellen.  
  
## <a name="dependency-links"></a>Abhängigkeitslinks  
 Ein Abhängigkeitslink wird durch ein Objekt dargestellt. Er kann in beide Richtungen navigiert werden:  
  
 ![Ein ILayerDependencyLink verbindet zwei ILAYER. ] (../modeling/media/layerapi_dependency.png "LayerApi_Dependency")  
  
 Rufen Sie `source.CreateDependencyLink(target)` auf, um einen Abhängigkeitslink zu erstellen.  
  
## <a name="comments"></a>Kommentare  
 Kommentare können auf Ebenen oder im Ebenenmodell enthalten sein. Zudem können sie mit beliebigen anderen Ebenenelementen verknüpft werden:  
  
 ![Kommentare können jedem Ebenenelement hinzugefügt werden. ] (../modeling/media/layerapi_comments.png "LayerApi_Comments")  
  
 Ein Kommentar kann mit einer beliebigen Anzahl von Elementen sowie auch mit keinem Element verknüpft werden.  
  
 Verwenden Sie Folgendes, um die Kommentare abzurufen, die einem Ebenenelement zugeordnet sind:  
  
```csharp  
ILayerModel model = diagram.GetLayerModel();   
IEnumerable<ILayerComment> comments =   
   model.Comments.Where(comment =>   
      comment.Links.Any(link => link.Target == layerElement));  
  
```  
  
> [!CAUTION]
>  Die `Comments`-Eigenschaft einer `ILayer` ruft die Kommentare ab, die in `ILayer` enthalten sind. Es werden nicht die mit ihr verknüpften Kommentare abgerufen.  
  
 Erstellen Sie einen Kommentar, indem Sie `CreateComment()` im entsprechenden Container aufrufen.  
  
 Erstellen Sie einen Link, indem Sie `CreateLink()` auf den Kommentar anwenden.  
  
## <a name="layer-elements"></a>Ebenenelemente  
 Alle Elementtypen, die in einem Modell enthalten sein können, sind Ebenenelemente:  
  
 ![Abhängigkeit enthalten Diagramm ILayerElements. ] (../modeling/media/layerapi_layerelements.png "LayerApi_LayerElements")  
  
## <a name="properties"></a>Eigenschaften  
 Jedes `ILayerElement` verfügt über ein Zeichenfolgenwörterbuch namens `Properties`. Über dieses Wörterbuch können Sie willkürliche Informationen an ein beliebiges Ebenenelement anfügen.  
  
## <a name="artifact-references"></a>Artefaktverweise  
 Ein Artefaktverweis (<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerArtifactReference>) stellt den Link zwischen einer Ebene und einem Projektelement dar, z. B. eine Datei, eine Klasse oder ein Ordner. Der Benutzer erstellt Elemente, beim Erstellen einer Ebene oder durch Ziehen von Elementen aus dem Projektmappen-Explorer, Klassenansicht und Objektkatalog in ein Diagramm Abhängigkeit hinzufügen. Mit einer Ebene kann eine beliebige Anzahl von Artefaktverweisen verknüpft werden.  
  
 Jede Zeile im Ebenen-Explorer zeigt einen Artefaktverweis an. Weitere Informationen finden Sie unter [Abhängigkeit Diagramme erstellen, aus dem Code](../modeling/create-layer-diagrams-from-your-code.md).  
  
 Folgende hauptsächliche Typen und Methoden sind von Artefaktverweisen betroffen:  
  
 <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerArtifactReference>. Die Eigenschaft "Kategorien" gibt an, welche Art von Artefakt referenziert wird, z. B. Klasse, ausführbare Datei oder Assembly. Die Kategorien bestimmen, wie der Bezeichner das Zielartefakt identifiziert.  
  
 <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ArtifactReferenceExtensions.CreateArtifactReferenceAsync%2A> erstellt einen Artefaktverweis über ein <xref:EnvDTE.Project> oder <xref:EnvDTE.ProjectItem>. Das ist ein asynchroner Vorgang. Daher stellen Sie normalerweise einen Rückruf bereit, der nach Abschluss der Erstellung aufgerufen wird.  
  
 Ebenenartefaktverweise dürfen nicht mit Artefakten in Anwendungsfalldiagrammen verwechselt werden.  
  
## <a name="shapes-and-diagrams"></a>Formen und Diagramme  
 Es werden zwei Objekte verwendet, um die einzelnen Elemente in einem Ebenenmodell darzustellen: <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerElement> und <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IShape>. `IShape` stellt Position und Größe der Form auf dem Diagramm dar. In Ebenenmodellen jeder `ILayerElement` verfügt über einen `IShape`, und jeder `IShape` auf eine Abhängigkeit besitzt ein `ILayerElement`. `IShape` wird auch für UML-Modelle verwendet. Daher verfügt nicht jedes `IShape` über ein Ebenenelement.  
  
 Auf dieselbe Weise wird <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerModel> für ein <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IDiagram> angezeigt.  
  
 Im Code eines benutzerdefinierten Befehl- oder Gestenhandlers können Sie das aktuelle Diagramm und die aktuelle Formenauswahl aus dem `DiagramContext`-Import abrufen:  
  
```  
public class ... {  
[Import]  
    public IDiagramContext DiagramContext { get; set; }  
...  
public void ... (...)   
{ IDiagram diagram = this.DiagramContext.CurrentDiagram;  
  ILayerModel model = diagram.GetLayerModel();  
  if (model != null)  
  { foreach (ILayer layer in model.Layers) { ... }}  
  foreach (IShape selected in diagram.SelectedShapes)  
  { ILayerElement element = selected.GetLayerElement();  
    if (element != null) ... }}  
```  
  
 ![Jedes ILayerElement wird durch eine IShape angegeben. ] (../modeling/media/layerapi_shapes.png "LayerApi_Shapes")  
  
 <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IShape> und <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IDiagram> werden auch zum Anzeigen von UML-Modellen verwendet. Weitere Informationen finden Sie unter [anzeigen ein UML-Modells in Diagrammen](../modeling/display-a-uml-model-on-diagrams.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Hinzufügen von Befehlen und Bewegungen zu Abhängigkeit Diagrammen](../modeling/add-commands-and-gestures-to-layer-diagrams.md)   
 [Hinzufügen von benutzerdefinierten architekturüberprüfung zu Abhängigkeit-Diagrammen](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)   
 [Fügen Sie benutzerdefinierter Eigenschaften zu Abhängigkeit-Diagramme hinzu](../modeling/add-custom-properties-to-layer-diagrams.md)   
 [Abhängigkeit Diagrammen: Referenz](../modeling/layer-diagrams-reference.md)   
 [Abhängigkeitsdiagramme: Richtlinien](../modeling/layer-diagrams-guidelines.md)   

