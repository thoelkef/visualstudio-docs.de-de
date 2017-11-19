---
title: Aktualisieren von Formen und Konnektoren entsprechend das Modell | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 51eb2af9-00e7-4725-a87d-62fb4f39f444
caps.latest.revision: "6"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: ae3a0d952b8ff88f2df4d297509d01d1a6731d56
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="updating-shapes-and-connectors-to-reflect-the-model"></a>Aktualisieren von Formen und Konnektoren zur Darstellung des Modells
In einer domänenspezifischen Sprache in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], Sie können die Darstellung einer Form, die den Status der zugrunde liegenden Modell wieder vornehmen.  
  
 Die Codebeispiele in diesem Thema hinzugefügt werden sollen, um eine `.cs` in der Datei Ihrer `Dsl` Projekt. Sie benötigen diese Anweisungen in jeder Datei:  
  
```  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
  
```  
  
## <a name="set-shape-map-properties-to-control-the-visibility-of-a-decorator"></a>Legen Sie Flächenkartogramm Eigenschaften zur Steuerung der Sichtbarkeit des einen Decorator-Element  
 Sie können die Sichtbarkeit der einen Decorator-Element steuern, ohne Programmcode zu schreiben, indem Sie die Zuordnung zwischen der Form "und der Domänenklasse in der DSL-Definition konfigurieren. Weitere Informationen finden Sie unter [zum Definieren einer domänenspezifischen Sprache](../modeling/how-to-define-a-domain-specific-language.md).
  
## <a name="expose-the-color-and-style-of-a-shape-as-properties"></a>Machen Sie die Farbe und den Stil einer Form als Eigenschaften verfügbar.  
 DSL-Definition mit der Maustaste der Form "-Klasse, zeigen Sie auf **hinzufügen verfügbar gemachten**, und klicken Sie dann auf eines der Elemente wie z. B. **Füllfarbe**.  
  
 Das Shape verfügt jetzt über eine Eigenschaft "Domain", die Sie im Programmcode oder als ein Benutzer festlegen können. Beispielsweise konnte um sie in den Programmcode, der einen Befehl oder eine Regel festgelegt, Sie schreiben:  
  
 `shape.FillColor = System.Drawing.Color.Red;`  
  
 Wenn Sie der eigenschaftsvariablen nur unter Programmsteuerung steuern und nicht vom Benutzer vornehmen möchten, wählen Sie die Eigenschaft "Domain" neue wie **Füllfarbe** in der DSL-Definitionsdiagramm. Schalten Sie dann im Fenster Eigenschaften **durchsuchbar ist** auf `false` oder legen Sie **ist UI Readonly** auf `true`.  
  
## <a name="define-change-rules-to-make-color-style-or-location-depend-on-model-element-properties"></a>Definieren der Regeln ändern, um Farbe, Format oder Speicherort Element Modelleigenschaften abhängig zu machen  
 Sie können Regeln definieren, die die Darstellung der Form abhängig von anderen Teilen des Modells zu aktualisieren. Z. B. können Sie eine Regel ändern auf ein Modellelement definieren, die die Farbe der die Form abhängig von den Eigenschaften des Modellelements aktualisiert. Weitere Informationen zum Ändern der Regeln finden Sie unter [weitergeben Änderungen innerhalb des Modells](../modeling/rules-propagate-changes-within-the-model.md).  
  
 Sie sollten den Regeln verwenden, nur für die Updateeigenschaften, die in den Speicher verwaltet werden, da Regeln nicht aufgerufen werden, wenn der Befehl "Rückgängig" ausgeführt wird. Dies schließt nicht einige grafische Funktionen wie die Größe und die Sichtbarkeit einer Form. Um diese Funktionen einer Form zu aktualisieren, finden Sie unter [aktualisieren nicht Store Grafikfeatures](#OnAssociatedProperty).  
  
 Im folgende Beispiel wird davon ausgegangen, dass Sie verfügbar gemacht haben `FillColor` als eine Eigenschaft "Domain" wie im vorherigen Abschnitt beschrieben.  
  
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
 Festlegen der Eigenschaften einer Form beim ersten erstellt, die Außerkraftsetzung `OnChildConfigured()` in eine partielle Definition der Klasse Diagramm. Die Diagramm-Klasse wird angegeben, in der DSL-Definition und der generierte Code befindet sich im **Dsl\Generated Code\Diagram.cs**. Zum Beispiel:  
  
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
  
 Diese Methode kann sowohl für Domäneneigenschaften und nicht aus dem Store-Features, z. B. die Größe der Form verwendet werden.  
  
##  <a name="OnAssociatedProperty"></a>Verwenden Sie zum Aktualisieren von anderen Funktionen von einer Form AssociateValueWith()  
 Es gibt keine integrierte Methode verfügbar machen, die Funktion als eine Eigenschaft "Domain" vorhanden, für einige Funktionen von einer Form ", z. B. ob sie einen Schatten oder die Art des Pfeils eines Connectors besitzt.  Änderungen an Funktionen sind nicht unter der Kontrolle des Systems Transaktion. Es ist daher nicht angemessen Aktualisieren mithilfe von Regeln, da Regeln nicht aufgerufen werden, wenn der Benutzer den Befehl "Rückgängig" ausführt.  
  
 Stattdessen können Sie solche Funktionen aktualisieren, indem Sie mithilfe von <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnAssociatedPropertyChanged%2A>. Im folgenden Beispiel wird die Art des Pfeils eines Connectors durch den Wert einer Eigenschaft "Domain" in der Beziehung gesteuert, in dem der Connector angezeigt:  
  
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
  
 `AssociateValueWith()`sollte für jede Eigenschaft "Domain" einmal aufgerufen werden, die Sie registrieren möchten. Nachdem er aufgerufen wurde, ruft alle Änderungen an der angegebenen Eigenschaft `OnAssociatedPropertyChanged()` in alle Formen, die die Eigenschaft Modellelement darstellen.  
  
 Es ist nicht notwendig, `AssociateValueWith()` für jede Instanz. Obwohl InitializeResources eine Instanzmethode ist, wird es nur ein Mal für jede Form "-Klasse aufgerufen.
