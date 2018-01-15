---
title: Anpassen von Elementtools | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ec997cfe101c5148f901c23356592016b72d4791
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2018
---
# <a name="customizing-element-tools"></a>Anpassen von Elementtools
In einigen DSL-Definitionen stellen Sie ein einzelnes Konzept als eine Gruppe von Elementen dar. Wenn Sie ein Modell, in dem eine Komponente einen festen Satz von Ports erstellen, möchten Sie z. B. immer die Ports, die zur gleichen Zeit wie die übergeordnete Komponente erstellt werden. Aus diesem Grund müssen Sie die Element-Creation-Tool anpassen, sodass es sich um eine Gruppe von Elementen, die statt einem erstellt. Um dies zu erreichen, können Sie anpassen, wie das Tool zur Erstellung von Element initialisiert wird.  
  
 Sie können auch überschreiben, was geschieht, wenn das Tool auf das Diagramm oder ein Element gezogen wird.  
  
## <a name="customizing-the-content-of-an-element-tool"></a>Anpassen des Inhalts der Elementtool  
 Jedes Elementtool speichert eine Instanz von einem <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> (EGP), die eine serialisierte Version ist eine oder mehrere Modellelemente und Links enthält. Standardmäßig enthält die EGP eine Element-Tools eine Instanz der Klasse, die Sie für das Tool angeben. Sie können ändern, indem überschreiben *YourLanguage*`ToolboxHelper.CreateElementToolPrototype`. Diese Methode wird aufgerufen, wenn der DSL-Paket geladen wird.  
  
 Ein Parameter der Methode ist die ID der Klasse, die Sie in der DSL-Definition angegeben. Wenn die Methode mit der Klasse, die Sie interessiert sind aufgerufen wird, können Sie zusätzliche Elemente in der EGP hinzufügen.  
  
 Die EGP muss das Einbetten von Links von einem Haupt Element an die untergeordnete Elemente enthalten. Er kann auch Links zu Referenzen enthalten.  
  
 Das folgende Beispiel erstellt eine main-Element und zwei eingebetteten Elemente. Die Hauptklasse wird Widerstand aufgerufen, und er verfügt über zwei Einbetten von Beziehungen zu Elementen, die mit dem Namen Terminaldienste. Einbetten von Rolleneigenschaften heißen Terminal1 und Terminal2, und beide verfügen über eine Multiplizität von 1..1.  
  
```  
using Microsoft.VisualStudio.Modeling; ...    
public partial class CircuitDiagramToolboxHelper  
{  
  protected override ElementGroupPrototype    CreateElementToolPrototype(Store store, Guid domainClassId)  
  {  
    // A case for each tool to customize:    
    if (domainClassId == Resistor.DomainClassId)  
    {  
      // Set up the prototype elements and links:  
      Resistor resistor = new Resistor(store);  
      resistor.Terminal1 = new Terminal(store);   
      resistor.Terminal2 = new Terminal(store);  
      resistor.Terminal1.Name = "T1"; // embedding  
      resistor.Terminal2.Name = "T2"; // embedding  
      // We could also set up reference links.  
  
      // Create an element group prototype for the toolbox:  
      ElementGroup egp = new ElementGroup(store.DefaultPartition);  
      egp.AddGraph(resistor, true);  
      // We do not have to explicitly include embedded children.  
      return egp.CreatePrototype();  
    }  
    // Element tools for other classes:  
    else  
      return base.CreateElementToolPrototype(store, domainClassId);  
  }  
}  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Anpassen der Elementerstellung und -verschiebung](../modeling/customizing-element-creation-and-movement.md)