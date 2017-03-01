---
title: Aktualisieren von Formen und Konnektoren zur Darstellung des Modells | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 51eb2af9-00e7-4725-a87d-62fb4f39f444
caps.latest.revision: 6
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: eb2ab9d49cdeb1ed71da8ef67841f7796862dc30
ms.openlocfilehash: 97ec749c0a89dae6c5a98702926d8ad82b6af3ac
ms.lasthandoff: 02/22/2017

---
# <a name="updating-shapes-and-connectors-to-reflect-the-model"></a>Aktualisieren von Formen und Konnektoren zur Darstellung des Modells
In einer domänenspezifischen Sprache in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], Sie können die Darstellung einer Form Zustand das zugrunde liegende Modell vornehmen.  
  
 Die Codebeispiele in diesem Thema hinzugefügt werden soll eine `.cs` Datei Ihre `Dsl` Projekt. Sie benötigen diese Anweisungen in jeder Datei:  
  
```  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
  
```  
  
## <a name="set-shape-map-properties-to-control-the-visibility-of-a-decorator"></a>Formzuordnung-Eigenschaften fest, um die Sichtbarkeit eines Decorator-Elements steuern  
 Sie können die Sichtbarkeit eines Decorator-Elements steuern, ohne das Schreiben von Programmcode, durch die Zuordnung zwischen der Form und die Domänenklasse im DSL-Definition konfigurieren. Weitere Informationen finden Sie unter  [wie eine domänenspezifische Sprache definiert](../modeling/how-to-define-a-domain-specific-language.md).
  
## <a name="expose-the-color-and-style-of-a-shape-as-properties"></a>Machen Sie die Farbe und den Stil einer Form als Eigenschaften verfügbar.  
 In der DSL-Definition mit der Maustaste der Shape-Klasse, zeigen Sie auf **verfügbare hinzufügen**, und klicken Sie dann auf eines der Elemente, wie z. B. **Füllfarbe**.  
  
 Die Form ist jetzt eine Domäneneigenschaft, die Sie im Programmcode oder als ein Benutzer festlegen können. Z. B. Wenn sie in den Programmcode, der einen Befehl oder eine Regel festgelegt, könnten Sie:  
  
 `shape.FillColor = System.Drawing.Color.Red;`  
  
 Wenn Sie die eigenschaftenvariable nur in der Programmsteuerung und nicht vom Benutzer machen möchten, wählen Sie die neue Domäneneigenschaft wie **Füllfarbe** im Diagramm DSL-Definition. Legen Sie dann im Fenster Eigenschaften **kann durchsucht werden** auf `false` oder **Benutzeroberfläche Readonly ist** auf `true`.  
  
## <a name="define-change-rules-to-make-color-style-or-location-depend-on-model-element-properties"></a>Definieren von Regeln ändern, Farbe, Format oder Speicherort Modelleigenschaften Element abhängig zu machen  
 Sie können Regeln definieren, die die Darstellung der Form abhängig von anderen Teilen des Modells zu aktualisieren. Sie können z. B. eine Regel ändern auf ein Modellelement definieren, die die Farbe der Form abhängig von den Eigenschaften des Modellelements aktualisiert. Weitere Informationen zum Ändern der Regeln finden Sie unter [Regeln weitergeben Änderungen in das Modell](../modeling/rules-propagate-changes-within-the-model.md).  
  
 Sie sollten die Regeln verwenden, um nur Eigenschaften zu aktualisieren, die in den Speicher verwaltet werden, da Regeln nicht aufgerufen werden, wenn der Rückgängig-Befehl ausgeführt wird. Dies schließt nicht Einige Grafikfeatures wie z. B. die Größe und die Sichtbarkeit einer Form. Um diese Funktionen einer Form zu aktualisieren, finden Sie unter [aktualisieren nicht Store Grafikfeatures](#OnAssociatedProperty).  
  
 Im folgende Beispiel wird davon ausgegangen, dass Sie bereitgestellt haben `FillColor` als eine Domäneneigenschaft wie im vorherigen Abschnitt beschrieben.  
  
```c#  
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
  
## <a name="use-onchildconfigured-to-initialize-a-shapes-properties"></a>Verwenden Sie OnChildConfigured, um die Eigenschaften eines Shapes initialisieren  
 Festlegen der Eigenschaften eines Shapes beim ersten erstellt, die Außerkraftsetzung `OnChildConfigured()` in eine partielle Definition der Diagrammklasse. Die Diagrammklasse in der DSL-Definition angegeben ist, und der generierte Code ist **Dsl\Generated Code\Diagram.cs**. Zum Beispiel:  
  
```c#  
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
  
 Diese Methode kann sowohl für Domäneneigenschaften und nicht-Store-Features, z. B. die Größe der Form verwendet werden.  
  
##  <a name="a-nameonassociatedpropertya-use-associatevaluewith-to-update-other-features-of-a-shape"></a><a name="OnAssociatedProperty"></a>Verwenden Sie AssociateValueWith() zum Aktualisieren von anderen Funktionen von einer Form  
 Für einige Features von einer Form, z. B., ob sie über einen Schatten oder die Art des Pfeils eines Connectors verfügt besteht keine integrierte Methode, die Funktion in einer Domäneneigenschaft verfügbar zu machen.  Änderungen an Funktionen unterliegen nicht der Kontrolle über das Transaktionssystem. Es ist daher nicht geeignet für das Aktualisieren mithilfe von Regeln, da die Regeln nicht aufgerufen werden, wenn der Benutzer den Befehl "Rückgängig" ausführt.  
  
 Stattdessen können Sie diese Funktionen mithilfe von <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnAssociatedPropertyChanged%2A>.</xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnAssociatedPropertyChanged%2A> aktualisieren Im folgenden Beispiel wird die Art des Pfeils einer Verbindung durch den Wert einer Domäneneigenschaft in der Beziehung gesteuert, in der der Connector angezeigt:  
  
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
  
 `AssociateValueWith()`sollte für jede Domäneneigenschaft einmal aufgerufen werden, die Sie registrieren möchten. Nachdem es aufgerufen wurde, Änderungen an der angegebenen Eigenschaft ruft `OnAssociatedPropertyChanged()` in alle Formen, die die Eigenschaft Modellelement darstellen.  
  
 Es ist nicht notwendig, rufen Sie `AssociateValueWith()` für jede Instanz. Obwohl InitializeResources eine Instanzmethode ist, wird sie nur einmal für jede formenklasse aufgerufen.

