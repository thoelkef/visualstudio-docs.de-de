---
title: "Anpassen von Elementtools | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6dac48b6-db68-4bcd-8aa2-422c2ad5d28b
caps.latest.revision: 6
caps.handback.revision: 6
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Anpassen von Elementtools
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In einigen DSL\-Definitionen stellen Sie ein einzelnes Konzept als eine Gruppe von Elementen dar. Wenn Sie ein Modell, in dem eine Komponente einen festen Satz von Ports erstellen, z. B. Sie immer die Ports, die zur gleichen Zeit wie die übergeordnete Komponente erstellt werden. Daher müssen Sie das Element Creation\-Tool so anpassen, dass es sich um eine Gruppe von Elementen statt einem erstellt. Um dies zu erreichen, können Sie anpassen, wie das Tool zur Erstellung von Element initialisiert wird.  
  
 Sie können auch überschreiben, was geschieht, wenn das Tool auf das Diagramm oder ein Element gezogen wird.  
  
## Anpassen des Inhalts eines Elementtools  
 Jedes Elementtool speichert eine Instanz einer <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> \(EGP\), die eine serialisierte Version des einen oder mehrere Modellelemente und Links enthält. Standardmäßig enthält die EGP eines Elementtools eine Instanz der Klasse, die Sie für das Tool angeben. Sie können dies ändern, indem Sie überschreiben *Ihresprache*`ToolboxHelper.CreateElementToolPrototype`. Diese Methode wird aufgerufen, wenn die DSL\-Paket geladen wird.  
  
 Ein Parameter der Methode ist die ID der Klasse, die Sie in der DSL\-Definition angegeben. Wenn die Methode mit der Klasse, die Sie interessiert sind aufgerufen wird, können Sie zusätzliche Elemente, die in der EGP hinzufügen.  
  
 Die EGP muss einbetten Links von einem Haupt\-Element an die untergeordnete Elemente enthalten. Er kann auch Ressourcenlinks enthalten.  
  
 Das folgende Beispiel erstellt ein Hauptelement und zwei eingebettete Elemente. Die Hauptklasse Widerstand bezeichnet wird, und es hat zwei einbettende Beziehungen zu Elementen, die mit dem Namen Terminal. Die Einbetten von Rolleneigenschaften heißen Terminal1 und Terminal2, und beide verfügen über eine Multiplizität von 1..1.  
  
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
  
## Siehe auch  
 [Anpassen der Elementerstellung und \-verschiebung](../modeling/customizing-element-creation-and-movement.md)