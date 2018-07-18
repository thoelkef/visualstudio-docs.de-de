---
title: Anpassen von Text- und Image-Feldern
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 01a55cbf2bf8d741594bae273389086e50dcc981
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31953130"
---
# <a name="customizing-text-and-image-fields"></a>Anpassen von Text- und Image-Feldern
Wenn Sie einen Text-Decorator-Element in einer Form definieren, wird er durch ein Textfeld dargestellt. Beispiele für die Initialisierung des TextFields und andere ShapeFields überprüfen Sie Dsl\GeneratedCode\Shapes.cs in der DSL-Projektmappe.

 Ein Textfeld ist ein Objekt, das einen Bereich innerhalb einer Form, z. B. den Speicherplatz, der eine Bezeichnung zugewiesen verwaltet. Ein Textfeld-Instanz ist für viele Formen der gleichen Klasse freigegeben. Die Textfeld-Instanz nicht den Text der Bezeichnung für jede Instanz separat gespeichert: stattdessen die `GetDisplayText(ShapeElement)` Methode nimmt die Form als Parameter und der Text abhängig von den aktuellen Status der Form und die Model-Element suchen können.

## <a name="how-the-appearance-of-a-text-field-is-determined"></a>Wie wird die Darstellung eines Text-Felds bestimmt.
 Die `DoPaint()` Methode aufgerufen wird, um zeigt das Feld auf dem Bildschirm. Sie können entweder die Standardeinstellung überschreiben `DoPaint(),` oder überschreiben Sie einige der Methoden, die ihn aufruft. Die folgende vereinfachte Version der Standardmethoden helfen bei der zu verstehen, wie das Standardverhalten außer Kraft setzen:

```
// Simplified version:
public override void DoPaint(DiagramPaintEventArgs e, ShapeElement parentShape)
{
  string text = GetDisplayText(shape);
  StringFormat format = GetStringFormat(parentShape);
  Brush brush = GetTextBrush(e.View, shape);
  using (Font font = GetFont(shape))
  {
    e.Graphics.DrawString(text, font, brush, format);
  }
}
// StringFormat determines whether the string is centered etc.
// To customize statically for all instances of this shape field,
// assign to DefaultStringFormat.
// To customize dynamically or per shape, override this:
public virtual StringFormat GetStringFormat(ShapeElement shape)
{ return DefaultStringFormat; }

// Override to customize the displayed string:
public virtual string GetDisplayText(ShapeElement shape)
{ return this.GetValue(shape).ToString(); }

// Brush determines the text color.
// To change the brush for every field, change the shape's styleset.
// To customize to a brush in the style set, override GetTextBrushId.
// To change the brush to non-standard color, override this.
// Should take account of whether selected.
public virtual Brush GetTextBrush(DiagramClientView view, ShapeElement shape)
{ return shape.StyleSet.GetBrush(this.GetTextBrushId(view, shape)); }

// Brush ID selects a brush from a StyleSet.
// Either return a member of DiagramBrushes
// or add your own brush to the shape or application's styleset.
// Override this to change dynamically or per instance.
// To change statically, just assign to default values.
public virtual StyleSetResourceId GetTextBrushId(DiagramClientView view, ShapeElement shape)
{ return IsSelected(view, shape) ? (view.Focused ? DefaultSelectedTextBrushId
: DefaultInactiveSelectedTextBrushId ) : DefaultTextBrushId ;
}

// Font determines the shape and size of the text.
// To change the font for every field, change the shape's styleset.
// To customize to a font in the style set, override GetFontId.
// To change the font to a non-standard font, override this.
public virtual Font GetFont(ShapeElement shape)
{ return shape.StyleSet.GetFont(GetFontId(shape)); }

// Selects a font from a styleset.
// Either return a member of DiagramFonts or
// add your own font to the shape or application's styleset.
// To change statically for all instances of this field,
// assign to DefaultFontId.
// To change per shape or dynamically, override this.
public virtual StyleSetResourceId GetFontId(ShapeElement parentShape)
{ return DefaultFontId; }

```

 Es gibt mehrere Paare von `Get` Methoden und `Default` Eigenschaften, z. B. `DefaultMultipleLine/GetMultipleLine()`. Sie können die Standardeigenschaft zum Ändern des Werts für alle Instanzen des Feldes Form einen Wert zuweisen. Wenn den Wert aus einer Form "-Instanz an eine andere oder abhängig von den Status der Form" oder seine Modellelement variieren soll, überschreiben die `Get` Methode.

## <a name="static-customizations"></a>Statische Anpassungen
 Wenn Sie jede Instanz dieses Shape-Felds ändern möchten, zunächst herausfinden Sie, ob die Eigenschaft in der DSL-Definition festgelegt werden kann. Sie können z. B. Schriftgrad und Schriftschnitt im Eigenschaftenfenster festlegen.

 Falls nicht, und überschreiben Sie dann die `InitializeShapeFields` Ihrer Shape-Klasse, und weisen Sie einen Wert an die entsprechende Methode `Default...` Eigenschaft des Textfelds.

> [!WARNING]
>  Überschreiben `InitializeShapeFields()`, müssen Sie festlegen der **generiert doppelte abgeleitete** Eigenschaft der Form "-Klasse, um `true` in der DSL-Definition.

 In diesem Beispiel hat eine Form "ein Textfeld, das für die Benutzerkommentare verwendet wird. Wir möchten die standardmäßige Kommentar Schriftart zu verwenden. Da es sich um eine Standardschriftart aus dem Satz Stil handelt, können wir die Standard-Schriftart-Id festlegen:

```

 partial class ExampleShape
{   protected override void InitializeShapeFields(IList<ShapeField> shapeFields)
    {
      // Fields set up according to DSL Definition:
      base.InitializeShapeFields(shapeFields);
      // Find and update comment field:
      TextField commentField = ShapeElement.FindShapeField(shapeFields, "CommentDecorator") as TextField;
      // Use the standard font for comments:
      commentField.DefaultFontId = DiagramFonts.CommentText;

```

## <a name="dynamic-customizations"></a>Dynamische Anpassungen
 Um die Darstellung variieren abhängig von den Status einer Form oder seine Modellelement machen, leiten Sie eine eigene Unterklasse von `TextField` und überschreiben Sie mindestens eine `Get...` Methoden. Sie müssen auch Ihre Form InitializeShapeFields Überschreibungsmethode und Ersetzen Sie die Instanz von das Textfeld mit einer Instanz Ihrer eigenen Klasse.

 Im folgenden Beispiel wird die Schriftart des einem Textfeld den Status einer booleschen Domäneneigenschaft des Modellelements für die Form abhängig.

 Um dieses Beispielcode auszuführen, erstellen Sie eine neue DSL-Projektmappe, die mit der minimalen Language-Vorlage. Hinzufügen einer Domäneneigenschaft vom Typ Boolean `AlternateState` der ExampleElement Domäne-Klasse. Die ExampleShape-Klasse ein Symbol Decorator-Element hinzu, und legen Sie das Bild in eine Bitmapdatei. Klicken Sie auf **Transformieren aller Vorlagen**. Fügen Sie in der DSL-Projekt eine neue Codedatei hinzu, und fügen Sie den folgenden Code.

 Drücken Sie F5, um den Code zu testen, und öffnen Sie in der Projektmappe Debuggen ein Beispieldiagramm. Der Standardstatus des Symbols sollte angezeigt werden. Wählen Sie die Form, und ändern Sie im Fenster Eigenschaften den Wert von der **AlternateState** Eigenschaft. Ändern Sie die Schriftart des Elementnamens sollten.

```
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
...

  partial class ExampleShape
  {
    /// <summary>
    /// Compose a list of the fields in this shape.
    /// Called once for each shape class.
    /// </summary>
    protected override void InitializeShapeFields(IList<ShapeField> shapeFields)
    {
      // Fields set up according to DSL Definition:
      base.InitializeShapeFields(shapeFields);
      // Replace the text field for NameDecorator:
      TextField oldField = ShapeElement.FindShapeField(shapeFields, "NameDecorator") as TextField;
      shapeFields.Remove(oldField);
      // Replace with my text field based on DSL Definition values:
      MyTextField newField = new MyTextField(oldField);
      shapeFields.Add(newField);
    }
  }
  /// <summary>
  /// Dynamic font depends on state of model element.
  /// </summary>
  public class MyTextField : TextField
  {
    public MyTextField(TextField prototype)
      : base(prototype.Name)
    {
      DefaultText = prototype.DefaultText;
      DefaultFocusable = prototype.DefaultFocusable;
      DefaultAutoSize = prototype.DefaultAutoSize;
      AnchoringBehavior.MinimumHeightInLines = prototype.AnchoringBehavior.MinimumHeightInLines;
      AnchoringBehavior.MinimumWidthInCharacters = prototype.AnchoringBehavior.MinimumWidthInCharacters;
      DefaultAccessibleState = prototype.DefaultAccessibleState;
    }

    public override System.Drawing.Font GetFont(ShapeElement parentShape)
    {
      // Access the Boolean domain property of the model element:
      if ((parentShape.ModelElement as ExampleElement).AlternateState)
        return new System.Drawing.Font("Callisto", 14.0f,
               System.Drawing.FontStyle.Italic |
               System.Drawing.FontStyle.Bold);
      else
        return base.GetFont(parentShape);
    }

  }

```

## <a name="style-sets"></a>Stil-sets
 Das vorhergehende Beispiel zeigt, wie Sie das Textfeld "Schriftart ändern können, die verfügbar ist. Allerdings ist die bevorzugte Methode zum Ändern, zu einem Satz von Formaten, die mit der Form "oder der Anwendung zugeordnet ist. Überschreiben Sie zu diesem Zweck <xref:Microsoft.VisualStudio.Modeling.Diagrams.TextField.GetFontId%2A> oder GetTextBrushId().

 Alternativ können Sie erwägen Sie, welche Stil der Form durch Außerkraftsetzen von <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.InitializeResources%2A>. Dies hat die Auswirkungen der Änderung der Schriftarten und Pinsel für alle formfelder.

## <a name="customizing-image-fields"></a>Anpassen von Bildfelder
 Wenn Sie ein Decorator-Bildelement in eine Form vom Typ definieren und eine Form "Bild" zu definieren, wird der Bereich, in dem die Form angezeigt wird, durch eine ImageField verwaltet. Beispiele für die Initialisierung des ImageFields und andere ShapeFields überprüfen Sie Dsl\GeneratedCode\Shapes.cs in der DSL-Projektmappe.

 Ein ImageField ist ein Objekt, das einen Bereich innerhalb einer Form, z. B. den Speicherplatz zugewiesen werden, um einen Decorator-Element verwaltet. Viele Formen der gleichen formenklasse ist eine ImageField Instanz freigegeben. Die ImageField-Instanz für jede Form "ein separates Abbild nicht gespeichert: stattdessen die `GetDisplayImage(ShapeElement)` Methode der Form" als Parameter akzeptiert und können abhängig von den aktuellen Status der Form "und dessen Modellelement Bilds nachschlagen.

 Wenn besonderes Verhalten, z. B. eine Variable Bild soll, können Sie eine eigene Klasse von ImageField abgeleitet erstellen.

#### <a name="to-create-a-subclass-of-imagefield"></a>So erstellen eine Unterklasse von ImageField

1.  Legen Sie die **generiert doppelte abgeleitet** Eigenschaft der Form "übergeordneten Klasse in der DSL-Definition.

2.  Überschreiben Sie die `InitializeShapeFields` Methode der Form "-Klasse.

    -   Erstellen Sie eine neue Codedatei im Projekt DSL und Schreiben einer partiellen Klassendefinition für die Form "-Klasse. Überschreiben der Methodendefinition vorhanden.

3.  Überprüfen Sie den Code der `InitializeShapeFields` in DSL\GeneratedCode\Shapes.cs.

     In der Überschreibungsmethode Aufrufen der Basismethode, und erstellen Sie eine Instanz Ihrer eigenen Image-Feld-Klasse. Hiermit können Sie das reguläre Bildfeld in ersetzen die `shapeFields` Liste.

## <a name="dynamic-icons"></a>Dynamische Symbole
 In diesem Beispiel wird ein Symbol, ändern Sie den Zustand des Modellelements für die Form abhängig.

> [!WARNING]
>  Dieses Beispiel zeigt, wie Sie einen dynamischen Abbilds Decorator-Element. Wenn Sie nur ein oder zwei Abbilder abhängig vom Status einer Variablen Modell wechseln möchten, ist es einfacher, mehrere Image Decorator-Elementen zu erstellen, suchen sie in der gleichen Position auf der Form und legen Sie dann den Filter Sichtbarkeit, hängen von bestimmten Werten des Modells Variable. Zum Festlegen dieser Filter wählen Sie die Form Zuordnung in der DSL-Definition, öffnen Sie das Fenster DSL-Detailfenster, und klicken Sie auf der Registerkarte "Decorator-Elemente".

 Um dieses Beispielcode auszuführen, erstellen Sie eine neue DSL-Projektmappe, die mit der minimalen Language-Vorlage. Hinzufügen einer Domäneneigenschaft vom Typ Boolean `AlternateState` der ExampleElement Domäne-Klasse. Die ExampleShape-Klasse ein Symbol Decorator-Element hinzu, und legen Sie das Bild in eine Bitmapdatei. Klicken Sie auf **Transformieren aller Vorlagen**. Fügen Sie in der DSL-Projekt eine neue Codedatei hinzu, und fügen Sie den folgenden Code.

 Drücken Sie F5, um den Code zu testen, und öffnen Sie in der Projektmappe Debuggen ein Beispieldiagramm. Der Standardstatus des Symbols sollte angezeigt werden. Wählen Sie die Form, und ändern Sie im Fenster Eigenschaften den Wert von der **AlternateState** Eigenschaft. Das Symbol "sollte dann über die auf dieser Form um 90 Grad gedreht angezeigt werden.

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
...
partial class ExampleShape
{
    /// <summary>
    /// Compose a list of the fields in this shape.
    /// Called once for each shape class.
    /// </summary>
    /// <param name="shapeFields"></param>
    protected override void InitializeShapeFields(IList<ShapeField> shapeFields)
    {
      // Fields set up according to DSL Definition:
      base.InitializeShapeFields(shapeFields);

      // Replace the image field:
      ShapeField oldField = ShapeElement.FindShapeField(shapeFields, "IconDecorator");
      shapeFields.Remove(oldField);
      // Must keep the same name:
      MyImageField newField = new MyImageField(oldField.Name);
      shapeFields.Add(newField);
      newField.DefaultImage = (oldField as ImageField).DefaultImage.Clone() as System.Drawing.Image;
    }
  }

  public class MyImageField : ImageField
  {
    public MyImageField(string tag) : base(tag) { }

    /// <summary>
    /// Get the image for this field in the given shape.
    /// </summary>
    public override System.Drawing.Image GetDisplayImage(ShapeElement parentShape)
    {
      ExampleElement element = parentShape.ModelElement as ExampleElement;
      if (element.AlternateState == true)
        return AlternateImage;
      else
        return base.GetDisplayImage(parentShape);
    }

    private System.Drawing.Image alternateImage;
    public System.Drawing.Image AlternateImage
    {
      get
      {
        if (alternateImage == null)
        {
          // Alternate image is a copy of the default, rotated by 90 degrees:
          alternateImage = this.DefaultImage.Clone() as System.Drawing.Image;
          alternateImage.RotateFlip(System.Drawing.RotateFlipType.Rotate90FlipNone);
        }
        return alternateImage;
      }
    }
  }
}

```

## <a name="see-also"></a>Siehe auch

- [Definieren von Formen und Konnektoren](../modeling/defining-shapes-and-connectors.md)
- [Festlegen eines Hintergrundbilds für ein Diagramm](../modeling/setting-a-background-image-on-a-diagram.md)
- [Navigieren in und Aktualisieren von Modellen im Programmcode](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Schreiben von Code zum Anpassen einer domänenspezifischen Sprache](../modeling/writing-code-to-customise-a-domain-specific-language.md)