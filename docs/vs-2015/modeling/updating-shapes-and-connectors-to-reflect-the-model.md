---
title: Aktualisieren von Formen und Konnektoren zur Darstellung des Modells | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 51eb2af9-00e7-4725-a87d-62fb4f39f444
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c8520084b57fdf0f831f62626593832d03c25636
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68183919"
---
# <a name="updating-shapes-and-connectors-to-reflect-the-model"></a>Aktualisieren von Formen und Konnektoren zur Darstellung des Modells
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In einer domänenspezifischen Sprache im [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], Sie können die Darstellung einer Form, die den Zustand der zugrunde liegenden Modell widerspiegeln vornehmen.  
  
 Die Codebeispiele in diesem Thema hinzugefügt werden sollen eine `.cs` Datei Ihre `Dsl` Projekt. Sie benötigen diese Anweisungen in jeder Datei ein:  
  
```  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
  
```  
  
## <a name="set-shape-map-properties-to-control-the-visibility-of-a-decorator"></a>Formzuordnung Eigenschaften zum Steuern der Sichtbarkeit eines Decorator-Elements  
 Sie können die Sichtbarkeit eines Decorator-Elements steuern, ohne das Schreiben von Programmcode, indem Sie die Zuordnung zwischen der Form und die Domänenklasse in der DSL-Definition konfigurieren. Weitere Informationen finden Sie unter den folgenden Themen:  
  
- [Vorgehensweise: Steuern der Sichtbarkeit eines Decorator-Elements-umleiten](../misc/how-to-control-the-visibility-of-a-decorator-redirect.md)  
  
- [So definieren Sie eine domänenspezifische Sprache](../modeling/how-to-define-a-domain-specific-language.md)  
  
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
 Zum Festlegen der Eigenschaften einer Form, bei der anfänglichen erstellt, die Außerkraftsetzung `OnChildConfigured()` in eine partielle Definition der Diagrammklasse. Die Diagrammklasse, die in Ihrer DSL-Definition angegeben ist, und der generierte Code befindet sich in **Dsl\Generated Code\Diagram.cs**. Beispiel:  
  
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
  
```  
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
        { // Update the shape’s built-in Decorator feature:  
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
