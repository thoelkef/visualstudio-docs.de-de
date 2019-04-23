---
title: 'Vorgehensweise: Abfangen eines Klicks auf eine Form oder einen Decorator'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 531e723bbc7c1b288a73f1ea036cb24efcf8ce4a
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60056110"
---
# <a name="how-to-intercept-a-click-on-a-shape-or-decorator"></a>Vorgehensweise: Abfangen eines Klicks auf eine Form oder einen Decorator
Die folgenden Prozeduren veranschaulichen Gewusst wie: Abfangen ein Klicks auf eine Form oder ein Symbol für Decorator-Element. Sie können abfangen, Klicks, Doppelklicks, zieht, und andere anwendungsstiftbewegungen, und stellen Sie das Element reagieren.

## <a name="to-intercept-clicks-on-shapes"></a>Abfangen von Klicks auf Formen
 Schreiben Sie eine partielle Klassendefinition für die Shape-Klasse im Dsl-Projekt, in einer Codedatei, die aus den generierten Code getrennt ist. Außer Kraft setzen `OnDoubleClick()` oder eine der anderen Methoden, die mit einem Namen enthält `On...`. Zum Beispiel:

```csharp
public partial class MyShape // change
  {
    public override void OnDoubleClick(DiagramPointEventArgs e)
    {
      base.OnDoubleClick(e);
      System.Windows.Forms.MessageBox.Show("Click");
      e.Handled = true;
  }  }
```

> [!NOTE]
>  Legen Sie `e.Handled` zu `true`, es sei denn, der das Ereignis, die dem Shape / Diagramm übergeben werden soll.

## <a name="to-intercept-clicks-on-decorators"></a>Abfangen von Klicks auf Decorator-Elemente
 Image-Decorator-Elemente werden auf einer Instanz von ImageField-Klasse, übertragen die eine OnDoubleClick-Methode verfügt. Sie können die Klicks abfangen, wenn Sie eine Unterklasse ImageField schreiben. Die Felder werden in der Methode InitializeShapeFields eingerichtet. Aus diesem Grund müssen Sie diese Methode zum Instanziieren Ihrer Unterklasse anstelle der regulären ImageField ändern. Die InitializeShapeFields-Methode wird in den generierten Code der Shape-Klasse. Sie können die Shape-Klasse überschreiben, wenn Sie festlegen, die `Generates Double Derived` Eigenschaft wie im folgenden Verfahren beschrieben.

 Obwohl InitializeShapeFields eine Instanzmethode ist, wird es nur einmal für jede Klasse aufgerufen. Aus diesem Grund ist Sie nur eine Instanz des ClickableImageField für jedes Feld in jeder Klasse, die nicht eine Instanz für jede Form im Diagramm vorhanden. Wenn der Benutzer eine Instanz doppelklickt, müssen Sie ermitteln, welche Instanz erreicht wurde, wie der Code im Beispiel veranschaulicht.

#### <a name="to-intercept-a-click-on-an-icon-decorator"></a>Zum Abfangen eines Klicks auf ein Symbol für Decorator-Element

1. Öffnen Sie oder erstellen Sie eine DSL-Projektmappe.

2. Wählen Sie oder erstellen Sie eine Form, die über ein Symbol für Decorator-Element verfügt, und ordnen sie Sie einer Domänenklasse.

3. In einer Codedatei, die aus den Dateien auf getrennt ist die `GeneratedCode` Ordner, die neue Unterklasse von ImageField erstellen:

    ```csharp
    using Microsoft.VisualStudio.Modeling;
    using Microsoft.VisualStudio.Modeling.Design;
    using Microsoft.VisualStudio.Modeling.Diagrams;
    using System.Collections.Generic;
    using System.Linq;

    namespace Fabrikam.MyDsl { // Change to your namespace
    internal class ClickableImageField : ImageField
    {
      // You can also override OnClick and so on.
      public override void OnDoubleClick(DiagramPointEventArgs e)
      {
        base.OnDoubleClick(e);
        // Work out which instance was hit.
        MyShape shapeHit = e.HitDiagramItem.Shape as MyShape;
        if (shapeHit != null)
        {
          MyDomainClass element =
              shapeHit.ModelElement as MyDomainClass;
          System.Windows.Forms.MessageBox.Show(
             "Double click on shape for " + element.Name);
          // If we do not set Handled, the event will
          // be passed to the containing shape:
          e.Handled = true;
        }
      }

       public ClickableImageField(string fieldName)
         : base(fieldName)
       { }
    }
    ```

     Sie sollten festlegen, behandelt, die auf "true", wenn Sie nicht möchten, dass das Ereignis Containerform übergeben werden soll.

4. Überschreiben Sie die InitializeShapeFields-Methode in Ihrer Form Classs, indem Sie die folgende Definition der partiellen Klasse hinzufügen.

    ```csharp
    public partial class MyShape // change
    {
     protected override void InitializeShapeFields
          (IList<ShapeField> shapeFields)
     {
      base.InitializeShapeFields(shapeFields);
      // You can see the above method in MyShapeBase
      // in the generated Shapes.cs
      // It has already added fields for the Icons.
      // So you will have to retrieve them and replace with your own.
      ShapeField unwantedField = shapeFields.First
          (field => field.Name == "IconDecorator1");
      shapeFields.Remove(unwantedField);

      // Now replicate the generated code from the base class
      // in Shape.cs, but with your own image constructor.
      ImageField field2 = new ClickableImageField("IconDecorator1");
      field2.DefaultImage = ImageHelper.GetImage(
        MyDslDomainModel.SingletonResourceManager
        .GetObject("MyShapeIconDecorator1DefaultImage"));
          shapeFields.Add(field2);
    }
    ```

1. Erstellen Sie die Projektmappe, und führen Sie sie aus.

2. Doppelklicken Sie auf das Symbol auf einer Instanz von der Form. Testnachricht sollte angezeigt werden.

## <a name="intercepting-clicks-and-drags-on-compartmentshape-lists"></a>Abfangen von klickt und zieht in CompartmentShape-Listen
 Im folgende Beispiel kann Benutzer Elemente in einem Depot-Form neu anordnen, indem Sie sie ziehen. So führen Sie diesen Code aus:

1. Erstellen Sie eine neue DSL-Projektmappe mithilfe der **Klassendiagramme** Projektmappe (Vorlage).

    Sie können auch mit einer Lösung für Ihre eigenen arbeiten, die Depot-Formen enthält. Dieser Code wird vorausgesetzt, dass eine einbettende Beziehung zwischen den Modellelementen, dargestellt durch die Form und die Elemente in der Depot-Listenelementen dargestellt.

2. Legen Sie die **generiert doppelte Ableitungen** -Eigenschaft der depotform.

3. Fügen Sie diesen Code in einer Datei in die **Dsl** Projekt.

4. Passen Sie die Domänennamen-Klasse und-Form in diesem Code entsprechend Ihrer eigenen DSL.

   Zusammenfassend lässt sich sagen funktioniert wie folgt der Code auf. In diesem Beispiel `ClassShape` ist der Name des der Depot-Form.

- Eine Reihe von Mausereignishandler wird an jede Compartment-Instanz angefügt werden, bei der Erstellung.

- Die `ClassShape.MouseDown` Ereignis speichert das aktuelle Element.

- Wenn die Maus bewegt aus das aktuelle Element eine Instanz von MouseAction erstellt wurde, die legt den Cursor fest, und die Maus erfasst, bis Sie wieder freigegeben wird.

     Um zu vermeiden, behindert mit anderen Aktionen, z. B. durch Festlegen der Text eines Elements wird die MouseAction nicht erstellt, bis die Maus auf das ursprüngliche Element verlassen hat.

     Eine Alternative zum Erstellen einer MouseAction wäre einfach MouseUp lauschen. Allerdings würde dies nicht funktioniert ordnungsgemäß, wenn der Benutzer die Maustaste loslässt, nach außen ziehen. Die MouseAction ist unabhängig davon, in dem die Maustaste wieder loslassen, wird die entsprechende Aktion durchführen können.

- Wenn die Maus veröffentlicht wird, ordnet MouseAction.MouseUp die Reihenfolge der Links zwischen den Modellelementen neu an.

- Die Änderung der Reihenfolge einer Rolle wird ausgelöst, eine Regel, die die Anzeige aktualisiert wird. Dieses Verhalten ist bereits definiert, und es ist kein zusätzlicher Code erforderlich.

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Design;
using Microsoft.VisualStudio.Modeling.Diagrams;
using System.Collections.Generic;
using System.Linq;

// This sample allows users to re-order items in a compartment shape by dragging.

// This example is built on the "Class Diagrams" solution template of VMSDK (DSL Tools).
// You will need to change the following domain class names to your own:
// ClassShape = a compartment shape
// ClassModelElement = the domain class displayed using a ClassShape
// This code assumes that the embedding relationships
// displayed in the compartments don't use inheritance
// (don't have base or derived domain relationships).

namespace Company.CompartmentDrag
{
 /// <summary>
 /// Manage the mouse while dragging a compartment item.
 /// </summary>
 public class CompartmentDragMouseAction : MouseAction
 {
  private ModelElement sourceChild;
  private ClassShape sourceShape;
  private RectangleD sourceCompartmentBounds;

  public CompartmentDragMouseAction(ModelElement sourceChildElement, ClassShape sourceParentShape, RectangleD bounds)
   : base (sourceParentShape.Diagram)
  {
   sourceChild = sourceChildElement;
   sourceShape = sourceParentShape;
   sourceCompartmentBounds = bounds; // For cursor.
  }

  /// <summary>
  /// Call back to the source shape to drop the dragged item.
  /// </summary>
  /// <param name="e"></param>
  protected override void OnMouseUp(DiagramMouseEventArgs e)
  {
   base.OnMouseUp(e);
   sourceShape.DoMouseUp(sourceChild, e);
   this.Cancel(e.DiagramClientView);
   e.Handled = true;
  }

  /// <summary>
  /// Ideally, this shouldn't happen. This action should only be active
  /// while the mouse is still pressed. However, it can happen if you
  /// move the mouse rapidly out of the source shape, let go, and then
  /// click somewhere else in the source shape.
  /// </summary>
  /// <param name="e"></param>
  protected override void OnMouseDown(DiagramMouseEventArgs e)
  {
   base.OnMouseDown(e);
   this.Cancel(e.DiagramClientView);
   e.Handled = false;
  }

  /// <summary>
  /// Display an appropriate cursor while the drag is in progress:
  /// Up-down arrow if we are inside the original compartment.
  /// No entry if we are elsewhere.
  /// </summary>
  /// <param name="currentCursor"></param>
  /// <param name="diagramClientView"></param>
  /// <param name="mousePosition"></param>
  /// <returns></returns>
  public override System.Windows.Forms.Cursor GetCursor(System.Windows.Forms.Cursor currentCursor, DiagramClientView diagramClientView, PointD mousePosition)
  {
   // If the cursor is inside the original compartment, show up-down cursor.
   return sourceCompartmentBounds.Contains(mousePosition)
    ? System.Windows.Forms.Cursors.SizeNS // Up-down arrow.
    : System.Windows.Forms.Cursors.No;
  }
 }

 /// <summary>
 /// Override some methods of the compartment shape.
 /// *** GenerateDoubleDerived must be set for this shape in DslDefinition.dsl. ****
 /// </summary>
 public partial class ClassShape
 {
  /// <summary>
  /// Model element that is being dragged.
  /// </summary>
  private static ClassModelElement dragStartElement = null;
  /// <summary>
  /// Absolute bounds of the compartment, used to set the cursor.
  /// </summary>
  private static RectangleD compartmentBounds;

  /// <summary>
  /// Attach mouse listeners to the compartments for the shape.
  /// This is called once per compartment shape.
  /// The base method creates the compartments for this shape.
  /// </summary>
  public override void EnsureCompartments()
  {
   base.EnsureCompartments();
   foreach (Compartment compartment in this.NestedChildShapes.OfType<Compartment>())
   {
    compartment.MouseDown += new DiagramMouseEventHandler(compartment_MouseDown);
    compartment.MouseUp += new DiagramMouseEventHandler(compartment_MouseUp);
    compartment.MouseMove += new DiagramMouseEventHandler(compartment_MouseMove);
   }
  }

  /// <summary>
  /// Remember which item the mouse was dragged from.
  /// We don't create an Action immediately, as this would inhibit the
  /// inline text editing feature. Instead, we just remember the details
  /// and will create an Action when/if the mouse moves off this list item.
  /// </summary>
  /// <param name="sender"></param>
  /// <param name="e"></param>
  void compartment_MouseDown(object sender, DiagramMouseEventArgs e)
  {
   dragStartElement = e.HitDiagramItem.RepresentedElements
     .OfType<ClassModelElement>().FirstOrDefault();
   compartmentBounds = e.HitDiagramItem.Shape.AbsoluteBoundingBox;
  }

  /// <summary>
  /// When the mouse moves away from the initial list item,
  /// but still inside the compartment, create an Action
  /// to supervise the cursor and handle subsequent mouse events.
  /// Transfer the details of the initial mouse position to the Action.
  /// </summary>
  /// <param name="sender"></param>
  /// <param name="e"></param>
  void compartment_MouseMove(object sender, DiagramMouseEventArgs e)
  {
   if (dragStartElement != null)
   {
    if (dragStartElement != e.HitDiagramItem.RepresentedElements.OfType<ClassModelElement>().FirstOrDefault())
    {
     e.DiagramClientView.ActiveMouseAction = new CompartmentDragMouseAction(dragStartElement, this, compartmentBounds);
     dragStartElement = null;
    }
   }
  }

  /// <summary>
  /// User has released the mouse button.
  /// </summary>
  /// <param name="sender"></param>
  /// <param name="e"></param>
  void compartment_MouseUp(object sender, DiagramMouseEventArgs e)
  {
    dragStartElement = null;
  }

  /// <summary>
  /// Forget the source item if mouse up occurs outside the
  /// compartment.
  /// </summary>
  /// <param name="e"></param>
  public override void OnMouseUp(DiagramMouseEventArgs e)
  {
   base.OnMouseUp(e);
   dragStartElement = null;
  }

  /// <summary>
  /// Called by the Action when the user releases the mouse.
  /// If we are still on the same compartment but in a different list item,
  /// move the starting item to the position of the current one.
  /// </summary>
  /// <param name="dragFrom"></param>
  /// <param name="e"></param>
  public void DoMouseUp(ModelElement dragFrom, DiagramMouseEventArgs e)
  {
   // Original or "from" item:
   ClassModelElement dragFromElement = dragFrom as ClassModelElement;
   // Current or "to" item:
   ClassModelElement dragToElement = e.HitDiagramItem.RepresentedElements.OfType<ClassModelElement>().FirstOrDefault();
   if (dragFromElement != null && dragToElement != null)
   {
    // Find the common parent model element, and the relationship links:
    ElementLink parentToLink = GetEmbeddingLink(dragToElement);
    ElementLink parentFromLink = GetEmbeddingLink(dragFromElement);
    if (parentToLink != parentFromLink && parentFromLink != null && parentToLink != null)
    {
     // Get the static relationship and role (= end of relationship):
     DomainRelationshipInfo relationshipFrom = parentFromLink.GetDomainRelationship();
     DomainRoleInfo parentFromRole = relationshipFrom.DomainRoles[0];
     // Get the node in which the element is embedded, usually the element displayed in the shape:
     ModelElement parentFrom = parentFromLink.LinkedElements[0];

     // Same again for the target:
     DomainRelationshipInfo relationshipTo = parentToLink.GetDomainRelationship();
     DomainRoleInfo parentToRole = relationshipTo.DomainRoles[0];
     ModelElement parentTo = parentToLink.LinkedElements[0];

     // Mouse went down and up in same parent and same compartment:
     if (parentTo == parentFrom && relationshipTo == relationshipFrom)
     {
      // Find index of target position:
      int newIndex = 0;
      var elementLinks = parentToRole.GetElementLinks(parentTo);
      foreach (ElementLink link in elementLinks)
      {
       if (link == parentToLink) { break; }
       newIndex++;
      }

      if (newIndex < elementLinks.Count)
      {
       using (Transaction t = parentFrom.Store.TransactionManager.BeginTransaction("Move list item"))
       {
        parentFromLink.MoveToIndex(parentFromRole, newIndex);
        t.Commit();
       }
      }
     }
    }
   }
  }

  /// <summary>
  /// Get the embedding link to this element.
  /// Assumes there is no inheritance between embedding relationships.
  /// (If there is, you need to make sure you've got the relationship
  /// that is represented in the shape compartment.)
  /// </summary>
  /// <param name="child"></param>
  /// <returns></returns>
  ElementLink GetEmbeddingLink(ClassModelElement child)
  {
   foreach (DomainRoleInfo role in child.GetDomainClass().AllEmbeddedByDomainRoles)
   {
    foreach (ElementLink link in role.OppositeDomainRole.GetElementLinks(child))
    {
     // Just the assume the first embedding link is the only one.
     // Not a valid assumption if one relationship is derived from another.
     return link;
    }
   }
   return null;
  }
 }
}
```

## <a name="see-also"></a>Siehe auch

- [Reagieren auf und Propagieren von Änderungen](../modeling/responding-to-and-propagating-changes.md)
- [Eigenschaften von Decorators](../modeling/properties-of-decorators.md)