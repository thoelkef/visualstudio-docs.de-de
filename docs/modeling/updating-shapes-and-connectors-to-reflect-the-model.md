---
title: Aktualisieren von Formen und Konnektoren zur Darstellung des Modells
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 5fa9861d081fba318805170163d9287ac113fbd0
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54997584"
---
# <a name="update-shapes-and-connectors-to-reflect-the-model"></a>Aktualisieren von Formen und Connectors zur Darstellung des Modells

In einer domänenspezifischen Sprache in Visual Studio können Sie die Darstellung einer Form, die den Zustand der zugrunde liegenden Modell widerspiegeln vornehmen.

Die Codebeispiele in diesem Thema hinzugefügt werden sollen eine `.cs` Datei Ihre `Dsl` Projekt. Sie benötigen diese Anweisungen in jeder Datei:

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
```

## <a name="set-shape-map-properties-to-control-the-visibility-of-a-decorator"></a>Formzuordnung Eigenschaften zum Steuern der Sichtbarkeit eines Decorator-Elements

Sie können die Sichtbarkeit eines Decorator-Elements steuern, ohne das Schreiben von Programmcode, indem Sie die Zuordnung zwischen der Form und die Domänenklasse in der DSL-Definition konfigurieren. Weitere Informationen finden Sie unter [Gewusst wie: Definieren Sie eine domänenspezifische Sprache](../modeling/how-to-define-a-domain-specific-language.md).

## <a name="expose-the-color-and-style-of-a-shape-as-properties"></a>Machen Sie die Farbe und den Stil einer Form als Eigenschaften verfügbar.

In der DSL-Definition mit der Maustaste der formklasse, zeigen Sie auf **verfügbare hinzufügen**, und klicken Sie dann auf eines der Elemente wie z. B. **Füllfarbe**.

Die Form verfügt jetzt über eine Eigenschaft "Domain", die Sie im Programmcode oder als Benutzer festlegen können. Beispielsweise könnten um sie in den Programmcode, der einen Befehl oder eine Regel festgelegt, Sie schreiben:

`shape.FillColor = System.Drawing.Color.Red;`

Wenn Sie die Eigenschaft Variable nur in der Programmsteuerung und nicht vom Benutzer stellen möchten, wählen Sie die neue Domäneneigenschaft z. B. **Füllfarbe** im DSL-Definitionsdiagramm. Legen Sie dann im Fenster Eigenschaften **kann durchsucht werden** zu `false` oder **UI-schreibgeschützt ist** zu `true`.

## <a name="define-change-rules-to-make-color-style-or-location-depend-on-model-element-properties"></a>Definieren Sie Regeln ändern, um Farbe, Format oder Speicherort, die Eigenschaften des Modells Element abhängig zu machen
 Sie können Regeln definieren, die die Darstellung der Form, die abhängig von anderen Teilen des Modells zu aktualisieren. Beispielsweise können Sie eine Regel für die Änderung auf ein Element des Modells definieren, die die Farbe der Form, die abhängig von den Eigenschaften des Modellelements aktualisiert. Weitere Informationen zum Ändern der Regeln finden Sie unter [Regeln weitergegeben werden Änderungen in das Modell](../modeling/rules-propagate-changes-within-the-model.md).

 Sie sollten die Regeln verwenden, nur für die Updateeigenschaften, die in den Store verwaltet werden, da Regeln nicht aufgerufen werden, wenn der Befehl "Rückgängig" ausgeführt wird. Dies schließt nicht einige grafische Features wie z. B. die Größe und die Sichtbarkeit einer Form. Um die Funktionen einer Form zu aktualisieren, finden Sie unter [Aktualisieren von nicht-Store grafisch](#OnAssociatedProperty).

 Im folgende Beispiel wird davon ausgegangen, dass Sie bereitgestellt haben `FillColor` als eine Domäneneigenschaft wie im vorherigen Abschnitt beschrieben.

```csharp
[RuleOn(typeof(ExampleElement))]
  class ExampleElementPropertyRule : ChangeRule
  {
    public override void ElementPropertyChanged(ElementPropertyChangedEventArgs e)
    {
      base.ElementPropertyChanged(e);
      ExampleElement element = e.ModelElement as ExampleElement;
      // The rule is called for every property that is updated.
      // Therefore, verify which property changed:
      if (e.DomainProperty.Id == ExampleElement.NameDomainPropertyId)
      {
        // There is usually only one shape:
        foreach (PresentationElement pel in PresentationViewsSubject.GetPresentation(element))
        {
          ExampleShape shape = pel as ExampleShape;
          // Replace this with a useful condition:
          shape.FillColor = element.Name.EndsWith("3")
                     ? System.Drawing.Color.Red : System.Drawing.Color.Green;
        }
      }
    }
  }
  // The rule must be registered:
  public partial class OnAssociatedPropertyExptDomainModel
  {
    protected override Type[] GetCustomDomainModelTypes()
    {
      List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());
      types.Add(typeof(ExampleElementPropertyRule));
      // If you add more rules, list them here.
      return types.ToArray();
    }
  }
```

## <a name="use-onchildconfigured-to-initialize-a-shapes-properties"></a>Verwenden Sie zum Initialisieren der Eigenschaften eines Shapes OnChildConfigured

Zum Festlegen der Eigenschaften einer Form, bei der anfänglichen erstellt, die Außerkraftsetzung `OnChildConfigured()` in eine partielle Definition der Diagrammklasse. Die Diagrammklasse, die in Ihrer DSL-Definition angegeben ist, und der generierte Code befindet sich in **Dsl\Generated Code\Diagram.cs**. Zum Beispiel:

```csharp
partial class MyLanguageDiagram
{
  protected override void OnChildConfigured(ShapeElement child, bool childWasPlaced, bool createdDuringViewFixup)
  {
    base.OnChildConfigured(child, childWasPlaced, createdDuringViewFixup);
    ExampleShape shape = child as ExampleShape;
    if (shape != null)
    {
      if (!createdDuringViewFixup) return; // Ignore load from file.
      ExampleElement element = shape.ModelElement as ExampleElement;
      // Replace with a useful condition:
      shape.FillColor = element.Name.EndsWith("3")
          ? System.Drawing.Color.Red : System.Drawing.Color.Green;
    }
    // else deal with other types of shapes and connectors.
  }
}
```

Diese Methode kann sowohl für Domäneneigenschaften und nicht über den Store-Features, z. B. die Größe der Form verwendet werden.

## <a name="OnAssociatedProperty"></a> Verwenden Sie zum Aktualisieren von anderen Funktionen von einer Form AssociateValueWith()

Für einige Features von einer Form, z. B., ob sie über einen Schatten oder den Pfeilstil einen Connector, verfügt ist es keine integrierte Methode, die Funktion in einer Domäneneigenschaft verfügbar zu machen.  Änderungen an Funktionen unterliegen nicht der Kontrolle über das Transaktionssystem. Aus diesem Grund ist es nicht geeignet für das Aktualisieren mithilfe von Regeln, da Regeln nicht aufgerufen werden, wenn der Benutzer den Befehl "Rückgängig" ausführt.

Stattdessen können Sie mithilfe solcher Funktionen aktualisieren <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnAssociatedPropertyChanged%2A>. Im folgenden Beispiel wird der Pfeilstil einer Verbindung durch den Wert einer Domäneneigenschaft in der Beziehung gesteuert, in dem der Connector angezeigt:

```csharp
public partial class ArrowConnector // My connector class.
{
    /// <summary>
    /// Called whenever a registered property changes in the associated model element.
    /// </summary>
    /// <param name="e"></param>
    protected override void OnAssociatedPropertyChanged(VisualStudio.Modeling.Diagrams.PropertyChangedEventArgs e)
    {
      base.OnAssociatedPropertyChanged(e);
      // Can be called for any property change. Therefore,
      // Verify that this is the property we're interested in:
      if ("IsDirected".Equals(e.PropertyName))
      {
        if (e.NewValue.Equals(true))
        { // Update the shape's built-in Decorator feature:
          this.DecoratorTo = LinkDecorator.DecoratorEmptyArrow;
        }
        else
        {
          this.DecoratorTo = null; // No arrowhead.
        }
      }
    }

    // OnAssociatedPropertyChanged is called only for properties
    // that have been registered using AssociateValueWith().
    // InitializeResources is a convenient place to call this.
    // This method is invoked only once per class, even though
    // it is an instance method.
    protected override void InitializeResources(StyleSet classStyleSet)
    {
      base.InitializeResources(classStyleSet);
      AssociateValueWith(this.Store, Wire.IsDirectedDomainPropertyId);
      // Add other properties here.
    }
}
```

`AssociateValueWith()` sollte für jede Domäneneigenschaft einmal aufgerufen werden, die Sie registrieren möchten. Nachdem es aufgerufen wurde, werden alle Änderungen an der angegebenen Eigenschaft aufrufen `OnAssociatedPropertyChanged()` in alle Formen, die der Eigenschaft Modellelement darstellen.

Es ist nicht notwendig, `AssociateValueWith()` für jede Instanz. Obwohl InitializeResources eine Instanzmethode ist, wird sie nur einmal für jede formklasse aufgerufen.
