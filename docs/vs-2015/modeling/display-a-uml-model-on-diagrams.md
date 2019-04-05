---
title: Anzeigen ein UML-Modells in Diagrammen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API
ms.assetid: adf1f1f2-2ad9-4ade-82de-c6a5194ab471
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2c68089615fd38276e428df6ffaa906d0b3f6742
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58957379"
---
# <a name="display-a-uml-model-on-diagrams"></a>Anzeigen eines UML-Modells in Diagrammen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Im Programmcode zu einer Erweiterung von Visual Studio können Sie steuern, wie Modellelemente in Diagrammen angezeigt werden. Welche Versionen von Visual Studio UML-Modelle unterstützen, erfahren Sie unter [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 In diesem Thema:  
 -   [Um ein Element in einem Diagramm angezeigt werden.](#Display)  
  
-   [Zugreifen auf die Formen, die ein Element darstellen.](#GetShapes)  
  
-   [Verschieben und Ändern der Größe von Formen](#Moving)  
  
-   [So entfernen Sie eine Form aus einem Diagramm](#Removing)  
  
-   [Öffnen und Erstellen von Diagrammen](#Opening)  
  
-   [Anpassen von mit VSTU Befehl zum Ausrichten von Formen](#AlignCommand)  
  
##  <a name="Display"></a> Um ein Element in einem Diagramm angezeigt werden.  
 Wenn Sie ein Element erstellen, z. B. einen Anwendungsfall oder eine Aktion, können Benutzer das Element im UML-Modell-Explorer sehen, aber es wird nicht immer automatisch in einem Diagramm angezeigt. In einigen Fällen müssen Sie Code schreiben, um es anzuzeigen. In der folgenden Tabelle sind die Alternativen zusammengefasst.  
  
|Elementtyp|Beispiel:|Code zum Anzeigen muss wie folgt lauten|  
|---------------------|-----------------|-------------------------------------|  
|Klassifizierer|`Class`<br /><br /> `Component`<br /><br /> `Actor`<br /><br /> `Use Case`|Erstellen Sie zugeordnete Formen in angegebenen Diagrammen. Sie können für jeden Klassifizierer eine beliebige Anzahl von Formen erstellen.<br /><br /> `diagram.Display<modelElementType>`<br /><br /> `(modelElement, parentShape,`<br /><br /> `xPosition , yPosition);`<br /><br /> Legen Sie `parentShape` für eine Form auf der obersten Ebene des Diagramms auf `null` fest.<br /><br /> So zeigen Sie eine Form in einer anderen Form an:<br /><br /> `IShape<IUseCase> usecaseShape =`<br /><br /> `useCaseDiagram.Display`<br /><br /> `(useCase,`<br /><br /> `subsystemShape,`<br /><br /> `subsystemShape.XPosition + 5,`<br /><br /> `subsystemShape.YPosition + 5);` **Hinweis:**  Wenn Sie die Anzeige innerhalb Ausführen einer **ILinkedUndo** Transaktion gibt die Methode manchmal keine `IShape`. Die Form wird jedoch ordnungsgemäß erstellt, und mit `IElement.Shapes().` kann darauf zugegriffen werden.|  
|Untergeordnetes Element des Klassifizierers|Attribut, Vorgang,<br /><br /> Teil, Port|Automatisch – Kein Code erforderlich. <br /><br /> Wird als Teil des übergeordneten Elements angezeigt.|  
|Verhalten|Interaktion (Sequenz),<br /><br /> Aktivität|Binden Sie das Verhalten an ein entsprechendes Diagramm.<br /><br /> Jedes Verhalten kann nur jeweils an ein Diagramm gebunden werden.<br /><br /> Zum Beispiel:<br /><br /> `sequenceDiagram.Bind(interaction);`<br /><br /> `activityDiagram.Bind(activity);`|  
|Untergeordnetes Element des Verhaltens|Lebenslinien, Meldungen, Aktionen, Objektknoten|Automatisch – Kein Code erforderlich. <br /><br /> Wird angezeigt, wenn das übergeordnete Element an ein Diagramm gebunden ist.|  
|Beziehung|Zuordnung, Generalisierung, Fluss, Abhängigkeit|Automatisch – Kein Code erforderlich. <br /><br /> Wird in jedem Diagramm angezeigt, in dem beide Enden angezeigt werden.|  
  
##  <a name="GetShapes"></a> Zugreifen auf die Formen, die ein Element darstellen.  
 Die Form, die ein Element darstellt, gehört zu den folgenden Typen:  
  
 `IShape`  
  
 `IShape<` *ElementType* `>`  
  
 wo *ElementType* ist ein Typ des Modellelements wie `IClass` oder `IUseCase`.  
  
|||  
|-|-|  
|`anElement.Shapes ()`|Alle `IShapes`, die dieses Element in geöffneten Diagrammen darstellen.|  
|`anElement.Shapes(aDiagram)`|Alle `IShapes`-Elemente, die dieses Element in einem bestimmten Diagramm darstellen.|  
|`anIShape.GetElement()`|Das `IElement`-Element, das von der Form dargestellt wird. Normalerweise würden Sie dieses Element in eine Unterklasse von IElement umwandeln.|  
|`anIShape.Diagram`|Das `IDiagram`-Element, das die Form enthält.|  
|`anIShape.ParentShape`|Die Form, die `anIShape` enthält. Eine Anschluss-Form ist z. B. in einer Komponentenform enthalten.|  
|`anIShape.ChildShapes`|Formen, die in einem `IShape`-Element oder `IDiagram`-Element enthalten sind.|  
|`anIShape.GetChildShapes<IUseCase>()`|Die Formen, die in einem `IShape`-Element oder einem `IDiagram`-Element enthalten sind und Elemente des angegebenen Typs darstellen, z. B. `IUseCase`.|  
|`IShape iShape = ...;`<br /><br /> `IShape<IClass> classShape = iShape.ToIShape<IClass>();`<br /><br /> `IClass aClass = classShape.Element;`|Wandeln Sie eine generische `IShape` in ein stark typisiertes `IShape<IElement>`.|  
|`IShape<IClassifier> classifierShape;`<br /><br /> `IShape<IUseCase> usecaseShape =`<br /><br /> `classifierShape.ToIShape<IUseCase>();`|Wandeln Sie eine Form von einem parametrisierten Formtyp in einen anderen um.|  
  
##  <a name="Moving"></a> Verschieben und Ändern der Größe von Formen  
  
|||  
|-|-|  
|`anIShape.Move(x, y, [width], [height])`|Verschieben Sie eine Form, oder ändern Sie ihre Größe.|  
|`IDiagram.EnsureVisible( IEnumerable<IShape> shapes, bool zoomToFit = false)`|Aktivieren Sie das Fenster, und führen Sie einen Bildlauf durch das Diagramm durch, sodass alle Formen sichtbar sind. Die Formen müssen alle im Diagramm angezeigt werden. Wenn `zoomToFit` auf „true“ festgelegt ist, wird das Diagramm ggf. skaliert, damit alle Formen sichtbar sind.|  
  
 Ein Beispiel finden Sie unter [Definieren eines Ausrichtungsbefehls](#AlignCommand).  
  
##  <a name="Removing"></a> So entfernen Sie eine Form aus einem Diagramm  
 Sie können Formen einiger Elementtypen löschen, ohne das Element zu löschen.  
  
|Modellelement|So entfernen Sie die Form|  
|-------------------|-------------------------|  
|Ein Klassifizierer: Klasse, Schnittstelle, Enumeration, Akteur, Anwendungsfall oder Komponente|`shape.Delete();`|  
|Ein Verhalten: Interaktion oder Aktivität|Sie können das Diagramm aus dem Projekt löschen. Verwenden Sie `IDiagram.FileName`, um den Pfad abzurufen.<br /><br /> Dabei wird nicht das Verhalten aus dem Modell gelöscht.|  
|Eine beliebige andere Form|Sie können andere Formen nicht explizit aus einem Diagramm löschen. Die Form wird automatisch entfernt, wenn das Element aus dem Modell gelöscht oder wenn die übergeordnete Form aus dem Diagramm entfernt wird.|  
  
##  <a name="Opening"></a> Öffnen und Erstellen von Diagrammen  
  
### <a name="to-access-the-users-current-diagram-from-a-command-or-gesture-extension"></a>So greifen Sie über einen Befehl oder eine Gestenerweiterung auf das aktuelle Diagramm des Benutzers zu  
 Deklarieren Sie diese importierte Eigenschaft in der Klasse:  
  
 `[Import]`  
  
 `IDiagramContext Context { get; set; }`  
  
 Greifen Sie in einer Methode auf das Diagramm zu:  
  
 `IClassDiagram classDiagram =`  
  
 `Context.CurrentDiagram as IClassDiagram;`  
  
> [!NOTE]
>  Eine Instanz von `IDiagram` (und der Untertypen wie `IClassDiagram`) ist nur innerhalb der verarbeiteten Befehls gültig. Es wird nicht empfohlen, ein `IDiagram`-Objekt in einer Variablen zu speichern, die beim Zurückgeben der Steuerung beibehalten wird.  
  
 Weitere Informationen finden Sie unter [Definieren eines Menübefehls in einem Modellierungsdiagramm](../modeling/define-a-menu-command-on-a-modeling-diagram.md).  
  
### <a name="to-obtain-a-list-of-open-diagrams"></a>So rufen Sie eine Liste geöffneter Diagramme ab  
 Eine Liste von Diagrammen, die zurzeit im Projekt geöffnet sind:  
  
```  
Context.CurrentDiagram.ModelStore.Diagrams()  
```  
  
## <a name="to-access-the-diagrams-in-a-project"></a>So greifen Sie auf die Diagramme in einem Projekt zu  
 Die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -API kann verwendet werden, um Modellierungsprojekte und Diagramme zu öffnen und zu erstellen.  
  
 Beachten Sie die Umwandlung von `EnvDTE.ProjectItem` in `IDiagramContext`.  
  
```  
  
      using EnvDTE; // Visual Studio API  
...  
[Import]  
public IServiceProvider ServiceProvider { get; set; }  
...  
// Get Visual Studio API  
DTE dte = ServiceProvider.GetService(typeof(DTE)) as DTE;  
// Get current Visual Studio project  
Project project = dte.ActiveDocument.ProjectItem.ContainingProject;  
// Open and process every diagram in the project.  
foreach (ProjectItem item in project.ProjectItems)  
{  
  // Cast ProjectItem to IDiagramContext  
  IDiagramContext context = item as IDiagramContext;  
  if (context == null)  
  {  
     // This is not a diagram file.  
     continue;  
  }  
  // Open the file and give the window the focus.  
  if (!item.IsOpen)  
  {  
      item.Open().Activate();  
  }  
  // Get the diagram.  
  IDiagram diagram = context.CurrentDiagram;  
  // Deal with specific diagram types.  
  ISequenceDiagram seqDiagram = diagram as ISequenceDiagram;  
  if (seqDiagram != null)  
  { ... } } }  
```  
  
 Instanzen von `IDiagram` und den zugehörigen Untertypen sind nicht gültig, nachdem die Steuerung wieder an [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] übergeben wurde.  
  
 Sie können auch den Modellspeicher eines [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Projekts abrufen:  
  
```  
  
      Project project = ...;  
IModelStore modelStore = (project as IModelingProject).Store;  
```  
  
##  <a name="AlignCommand"></a> Beispiel: Befehl zum Ausrichten von Formen  
 Im folgenden Code wird ein Menübefehl implementiert, mit dem Formen ordentlich ausgerichtet werden. Der Benutzer muss zuerst mindestens zwei Formen einfügen, die in etwa vertikal oder horizontal aneinander ausgerichtet sind. Dann können ihre Mittelpunkte mit dem Befehl „Align“ aneinander ausgerichtet werden.  
  
 Um den Befehl verfügbar zu machen, fügen Sie diesen Code einem Menübefehlsprojekt hinzu, und stellen Sie den Benutzern dann die resultierende Erweiterung bereit. Weitere Informationen finden Sie unter [Definieren eines Menübefehls in einem Modellierungsdiagramm](../modeling/define-a-menu-command-on-a-modeling-diagram.md).  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.ComponentModel.Composition;  
using System.Linq;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
  
namespace AlignCommand  
{  
  // Implements a command to align shapes in a UML class diagram.  
  // The user first selects shapes that are roughly aligned either vertically or horizontally.  
  // This command will straighten them up.  
  
  // Place this file in a menu command extension project.  
  // See http://msdn.microsoft.com/library/ee329481.aspx  
  
  [Export(typeof(ICommandExtension))]  
  [ClassDesignerExtension] // TODO: Add other diagram types if needed  
  class CommandExtension : ICommandExtension  
  {  
    /// <summary>  
    /// See http://msdn.microsoft.com/library/ee329481.aspx  
    /// </summary>  
    [Import]  
    IDiagramContext context { get; set; }  
  
    /// <summary>  
    /// Transaction context.  
    /// See http://msdn.microsoft.com/library/ee330926.aspx  
    /// </summary>  
    [Import]  
    ILinkedUndoContext linkedUndo { get; set; }  
  
    /// <summary>  
    /// Called when the user selects the command.  
    /// </summary>  
    /// <param name="command"></param>  
    public void Execute(IMenuCommand command)  
    {  
      Align(context.CurrentDiagram.SelectedShapes);  
    }  
  
    /// <summary>  
    /// Called when the user right-clicks on the diagram.  
    /// Determines whether the command is enabled.  
    /// </summary>  
    /// <param name="command"></param>  
    public void QueryStatus(IMenuCommand command)  
    {  
      IEnumerable<IShape> currentSelection = context.CurrentDiagram.SelectedShapes;  
      // Make it visible if there are shapes selected:  
      command.Visible = currentSelection.Count() > 0 && !(currentSelection.FirstOrDefault() is IDiagram);  
  
      // Make it enabled if there are two or more shapes that are roughly in line:  
      command.Enabled = currentSelection.Count() > 1  
        && (HorizontalAlignCenter(currentSelection) > 0.0  
        || VerticalAlignCenter(currentSelection) > 0.0);  
  
    }  
  
    /// <summary>  
    /// Title of the menu command.  
    /// </summary>  
    public string Text  
    {  
      get { return "Align Shapes"; }  
    }  
  
    /// <summary>  
    /// Find a horizontal line that goes through a list of shapes.  
    /// </summary>  
    /// <param name="shapes"></param>  
    /// <returns></returns>  
    private static double HorizontalAlignCenter(IEnumerable<IShape> shapes)  
    {  
      double Y = -1.0;  
      double top = 0.0, bottom = shapes.First().Bottom();  
      foreach (IShape shape in shapes)  
      {  
        top = Math.Max(top, shape.Top());  
        bottom = Math.Min(bottom, shape.Bottom());  
      }  
      if (bottom > top) Y = (bottom + top) / 2.0;  
      return Y;  
    }  
  
    /// <summary>  
    /// Find a vertical line that goes through a list of shapes.  
    /// </summary>  
    /// <param name="shapes"></param>  
    /// <returns></returns>  
    private static double VerticalAlignCenter(IEnumerable<IShape> shapes)  
    {  
      double X = -1.0;  
      double left = 0.0, right = shapes.First().Right();  
      foreach (IShape shape in shapes)  
      {  
        left = Math.Max(left, shape.Left());  
        right = Math.Min(right, shape.Right());  
      }  
      if (right > left) X = (right + left) / 2.0;  
      return X;  
    }  
  
    /// <summary>  
    /// Line up those shapes that are roughly aligned.  
    /// </summary>  
    /// <param name="shapes"></param>  
    private void Align(IEnumerable<IShape> shapes)  
    {  
      if (shapes.Count() > 1)  
      {  
        // The shapes must all overlap either horizontally or vertically.  
        // Find a horizontal line that is covered by all the shapes:  
        double Y = HorizontalAlignCenter(shapes);  
        if (Y > 0.0) // Negative if they don't overlap.  
        {  
          // Adjust all the shape positions in one transaction:  
          using (ILinkedUndoTransaction t = linkedUndo.BeginTransaction("align"))  
          {  
            foreach (IShape shape in shapes)  
            {  
              shape.AlignYCenter(Y);  
            }  
            t.Commit();  
          }  
        }  
        else  
        {  
          // Find a vertical line that is covered by all the shapes:  
          double X = VerticalAlignCenter(shapes);  
          if (X > 0.0) // Negative if they don't overlap.  
          {  
            // Adjust all the shape positions in one transaction:  
            using (ILinkedUndoTransaction t = linkedUndo.BeginTransaction("align"))  
            {  
              foreach (IShape shape in shapes)  
              {  
                shape.AlignXCenter(X);  
              }  
              t.Commit();  
            }  
          }  
        }  
      }  
    }  
  }  
  
  /// <summary>  
  /// Convenience extensions for IShape.  
  /// </summary>  
  public static class IShapeExtension  
  {  
    public static double Bottom(this IShape shape)  
    {  
      return shape.YPosition + shape.Height;  
    }  
  
    public static double Top(this IShape shape)  
    {  
      return shape.YPosition;  
    }  
  
    public static double Left(this IShape shape)  
    {  
      return shape.XPosition;  
    }  
  
    public static double Right(this IShape shape)  
    {  
      return shape.XPosition + shape.Width;  
    }  
  
    public static void AlignYCenter(this IShape shape, double Y)  
    {  
      shape.Move(shape.XPosition, Y - shape.YCenter());  
    }  
  
    public static void AlignXCenter(this IShape shape, double X)  
    {  
      shape.Move(X - shape.XCenter(), shape.YPosition);  
    }  
  
    /// <summary>  
    /// We can adjust what bit of the shape we want to be aligned.  
    /// The default is the center of the shape.  
    /// </summary>  
    /// <param name="shape"></param>  
    /// <returns></returns>  
    public static double YCenter(this IShape shape)  
    {  
        return shape.Height / 2.0;  
    }   
  
    /// <summary>  
    /// We can adjust what bit of the shape we want to be aligned.  
    /// The default is the center of the shape.  
    /// </summary>  
    /// <param name="shape"></param>  
    /// <returns></returns>  
    public static double XCenter(this IShape shape)  
    {  
        return shape.Width / 2.0;  
    }  
  }  
}  
  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Erweitern von UML-Modellen und-Diagrammen](../modeling/extend-uml-models-and-diagrams.md)   
 [Navigieren Sie im UML-Modell](../modeling/navigate-the-uml-model.md)   
 [Beispiel: Ausrichten von Formen auf einem Diagrammmenübefehl](http://go.microsoft.com/fwlink/?LinkId=213809)   
 [Beispiel: Erstellen von Elementen, Formen und Stereotypen](http://go.microsoft.com/fwlink/?LinkId=213811)
