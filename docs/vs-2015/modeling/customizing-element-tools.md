---
title: Anpassen von Element Tools | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 6dac48b6-db68-4bcd-8aa2-422c2ad5d28b
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b6b35bbb0592f7ec9f8defcd9d78dbba5a6a47a5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655012"
---
# <a name="customizing-element-tools"></a>Anpassen von Elementtools
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In einigen DSL-Definitionen stellen Sie ein einzelnes Konzept als eine Gruppe von Elementen dar. Wenn Sie z. b. ein Modell erstellen, in dem eine Komponente einen festgelegten Satz an Ports aufweist, sollten Sie die Ports immer gleichzeitig mit der übergeordneten Komponente erstellen. Daher müssen Sie das Tool zum Erstellen von Elementen so anpassen, dass es eine Gruppe von Elementen anstelle von nur einem erstellt. Um dies zu erreichen, können Sie anpassen, wie das Element Erstellungs Tool initialisiert wird.

 Sie können auch überschreiben, was geschieht, wenn das Tool auf das Diagramm oder ein Element gezogen wird.

## <a name="customizing-the-content-of-an-element-tool"></a>Anpassen des Inhalts eines Element Tools
 Jedes Element Tool speichert eine Instanz eines <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> (EGP), das eine serialisierte Version von mindestens einem Modellelement und Verknüpfungen enthält. Standardmäßig enthält der EGP eines Element Tools eine Instanz der-Klasse, die Sie für das Tool angeben. Sie können dies ändern, indem Sie *YourLanguage* `ToolboxHelper.CreateElementToolPrototype` außer Kraft setzen. Diese Methode wird aufgerufen, wenn das DSL-Paket geladen wird.

 Ein Parameter der-Methode ist die ID der Klasse, die Sie in der DSL-Definition angegeben haben. Wenn die-Methode mit der-Klasse aufgerufen wird, an der Sie interessiert sind, können Sie dem EGP zusätzliche Elemente hinzufügen.

 Der EGP muss Einbett Ende Verknüpfungen von einem Hauptelement zu den untergeordneten Elementen enthalten. Sie kann auch Verweis Links enthalten.

 Im folgenden Beispiel werden ein Hauptelement und zwei eingebettete Elemente erstellt. Die Hauptklasse wird als "resistenor" bezeichnet und verfügt über zwei Einbettungs Beziehungen zu den Elementen mit dem Namen "Terminal". Die Eigenschaften der Einbettungs Rolle heißen Terminal1 und Terminal2, und beide verfügen über eine Multiplizität von 1.. 1.

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
