---
title: Anpassen von Text- und Image-Feldern
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d63354d552b04d07f0b2d0ede41d28fc33cda3a3
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55970724"
---
# <a name="customizing-text-and-image-fields"></a>Anpassen von Text- und Image-Feldern
Wenn Sie einen Text-Decorator in einer Form definieren, wird er durch einen TextField dargestellt. Beispiele für die Initialisierung von TextFields und andere ShapeFields untersuchen Sie Dsl\GeneratedCode\Shapes.cs in der DSL-Projektmappe.

 Ein Textfeld handelt es sich um ein Objekt, das einen Bereich innerhalb einer Form, wie z. B. den Speicherplatz, die eine Bezeichnung zugewiesen verwaltet. Viele Formen der gleichen Klasse wird ein Textfeld-Instanz gemeinsam genutzt. TextField-Instanz nicht den Text der Bezeichnung für jede Instanz separat gespeichert: stattdessen die `GetDisplayText(ShapeElement)` Methode nimmt die Form als Parameter und der Text abhängig von den aktuellen Status der Form sowie ihres Modellelements suchen können.

## <a name="how-the-appearance-of-a-text-field-is-determined"></a>Wie wird die Darstellung eines Textfeldes bestimmt.
 Die `DoPaint()` Methode aufgerufen wird, um zeigt das Feld auf dem Bildschirm. Sie können entweder die Standardeinstellung überschreiben `DoPaint(),` oder überschreiben einiger der Methoden, die ihn aufruft. Die folgende vereinfachte Version der standardmäßigen Methoden können Sie erfahren, wie Sie das Standardverhalten außer Kraft setzen:

```csharp
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

 Es gibt mehrere Paare von `Get` Methoden und `Default` Eigenschaften, z. B. `DefaultMultipleLine/GetMultipleLine()`. Sie können die Standardeigenschaft zum Ändern des Werts für alle Instanzen des Form-Felds einen Wert zuweisen. Wenn den Wert aus einer Shape-Instanz ein anderes Kommunikationsprotokoll oder abhängig vom Zustand der Form oder ihres Modellelements unterschiedlich sein soll, überschreiben die `Get` Methode.

## <a name="static-customizations"></a>Statische Anpassungen
 Wenn Sie jede Instanz dieses Felds Form ändern möchten, zunächst herausfinden Sie, ob Sie die Eigenschaft in der DSL-Definition festlegen können. Sie können z. B. Schriftgrad und Schriftschnitt im Eigenschaftenfenster festlegen.

 Falls nicht, und überschreiben Sie dann die `InitializeShapeFields` Ihre Shape-Klasse, und weisen Sie einen Wert an die entsprechende Methode `Default...` Eigenschaft des Textfelds.

> [!WARNING]
>  Zum Überschreiben `InitializeShapeFields()`, müssen Sie festlegen, die **generiert doppelte Ableitungen** Eigenschaft der Shape-Klasse, `true` in der DSL-Definition.

 In diesem Beispiel hat eine Form ein Textfeld, das für die Kommentare von Benutzern verwendet wird. Die standard-Kommentar-Schriftart verwendet werden soll. Da es einer Standardschriftart, aus dem Stil handelt, können wir die Standard-Schriftart-Id festlegen:

```csharp

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
 Damit wird die Darstellung variieren abhängig vom Zustand einer Form oder ihres Modellelements, leiten Sie eine eigene Unterklasse von `TextField` und überschreiben Sie mindestens eine `Get...` Methoden. Sie müssen auch der Shape InitializeShapeFields Methode überschreiben und Ersetzen Sie die Instanz von dem Textfeld mit einer Instanz Ihrer eigenen Klasse.

 Im folgenden Beispiel wird die Schriftart für ein Textfeld abhängig vom Zustand des Modellelements der Form einer booleschen Domäneneigenschaft.

 Erstellen Sie eine neue DSL-Projektmappe mithilfe der Vorlage für die minimale Sprache, zum Ausführen dieses Beispiels den Code. Fügen Sie eine booleschen Domäneneigenschaft `AlternateState` mit der Domänenklasse ExampleElement. Fügen Sie ein Symbol für Decorator-Element der ExampleShape-Klasse aus, und legen Sie das Image in eine Bitmapdatei. Klicken Sie auf **alle Vorlagen transformieren**. Fügen Sie eine neue Codedatei im DSL-Projekt, und fügen Sie den folgenden Code.

 Um den Code zu testen, drücken Sie F5, und öffnen Sie in der Projektmappe Debuggen ein Beispieldiagramm. Der Standardzustand des Symbols sollte angezeigt werden. Wählen Sie die Form, und ändern Sie im Eigenschaftenfenster den Wert des der **AlternateState** Eigenschaft. Die Schriftart des Elementnamens sollten ändern.

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

## <a name="style-sets"></a>Formatvorlagen
 Das vorhergehende Beispiel zeigt, wie Sie das Textfeld ein, alle Schriftarten ändern können, die verfügbar ist. Allerdings ist die bevorzugte Methode zum Ändern eines Formatvorlagen, die die Form oder mit der Anwendung zugeordnet ist. Zu diesem Zweck Sie außer Kraft setzen <xref:Microsoft.VisualStudio.Modeling.Diagrams.TextField.GetFontId%2A> oder GetTextBrushId().

 Alternativ sollten Sie Änderungen der Formatvorlage die Form durch Überschreiben <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.InitializeResources%2A>. Dies hat es sich um die Auswirkungen der Änderung die Schriftarten und Pinsel für alle formfelder.

## <a name="customizing-image-fields"></a>Anpassen von Image-Feldern
 Wenn Sie ein Decorator-Bildelement in einer Form definieren, und wenn Sie eine Bild-Form definieren, wird der Bereich, in dem die Form angezeigt wird, von einem ImageField verwaltet. Beispiele für die Initialisierung von ImageFields und andere ShapeFields untersuchen Sie Dsl\GeneratedCode\Shapes.cs in der DSL-Projektmappe.

 Ein ImageField handelt es sich um ein Objekt, das einen Bereich innerhalb einer Form, wie z. B. den Speicherplatz zugewiesen werden, um ein Decorator-Element verwaltet. Viele Formen der gleiche Shape-Klasse wird eine Instanz von ImageField gemeinsam genutzt. Die ImageField-Instanz ein separates Abbild für jede Form nicht gespeichert: stattdessen die `GetDisplayImage(ShapeElement)` Methode nimmt die Form als Parameter und das Image abhängig von den aktuellen Status der Form sowie ihres Modellelements suchen können.

 Wenn besonderes Verhalten wie eine Image-Variablen werden sollen, können Sie eine eigene Klasse von ImageField erstellen.

#### <a name="to-create-a-subclass-of-imagefield"></a>Erstellen Sie eine Unterklasse von ImageField

1.  Legen Sie die **generiert doppelte Ableitungen** Eigenschaft der übergeordneten Form-Klasse in Ihrer DSL-Definition.

2.  Überschreiben der `InitializeShapeFields` Methode der Shape-Klasse.

    -   Erstellen Sie eine neue Codedatei im DSL-Projekt, und Schreiben Sie eine partielle Klassendefinition für die Shape-Klasse. Überschreiben Sie die Definition der Methode vorhanden.

3.  Überprüfen Sie den Code der `InitializeShapeFields` in DSL\GeneratedCode\Shapes.cs.

     Rufen Sie in der Überschreibungsmethode die Basismethode auf, und klicken Sie dann erstellen Sie eine Instanz Ihrer eigenen Images-Feld-Klasse. Verwenden Sie diese ersetzen die regulären Bildfeld in der `shapeFields` Liste.

## <a name="dynamic-icons"></a>Dynamische Symbole
 In diesem Beispiel wird ein Symbol zu ändern, die abhängig vom Zustand des Modellelements der Form.

> [!WARNING]
>  In diesem Beispiel wird veranschaulicht, wie Sie ein dynamisches Bild-Decorator-Element. Aber wenn Sie nur ein oder zwei Abbilder abhängig vom Status einer Variablen des Modells wechseln möchten, es ist einfacher, mehrere Image-Decorator-Elemente erstellen, suchen sie in der gleichen Position auf der Form und legen Sie den Filter Sichtbarkeit, hängt von bestimmten Werten des Modells Variable. Zum Festlegen dieser Filter wählen Sie das flächenkartogramm, in der DSL-Definition, öffnen Sie das DSL-Details-Fenster, und klicken Sie auf der Registerkarte "Decorator-Elemente".

 Erstellen Sie eine neue DSL-Projektmappe mithilfe der Vorlage für die minimale Sprache, zum Ausführen dieses Beispiels den Code. Fügen Sie eine booleschen Domäneneigenschaft `AlternateState` mit der Domänenklasse ExampleElement. Fügen Sie ein Symbol für Decorator-Element der ExampleShape-Klasse aus, und legen Sie das Image in eine Bitmapdatei. Klicken Sie auf **alle Vorlagen transformieren**. Fügen Sie eine neue Codedatei im DSL-Projekt, und fügen Sie den folgenden Code.

 Um den Code zu testen, drücken Sie F5, und öffnen Sie in der Projektmappe Debuggen ein Beispieldiagramm. Der Standardzustand des Symbols sollte angezeigt werden. Wählen Sie die Form, und ändern Sie im Eigenschaftenfenster den Wert des der **AlternateState** Eigenschaft. Das Symbol sollte dann über dieser Form um 90 Grad gedreht angezeigt.

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