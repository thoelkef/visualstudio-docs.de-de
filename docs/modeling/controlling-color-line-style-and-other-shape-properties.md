---
title: Steuern von Farbe, Linienstil und anderen Eigenschaften von Formen
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: bfe0cbdda1b3eaa7d1afc936c7dbba75df6da07b
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="controlling-color-line-style-and-other-shape-properties"></a>Steuern von Farbe, Linienstil und anderen Eigenschaften von Formen
Einige Eigenschaften der Form, wie z. B. Farbe "verfügbar gemacht werden kann" - verknüpft, d. h., eine Eigenschaft "Domain" der Form. Andere Benutzer haben direkt gesteuert werden.

## <a name="exposing-a-property"></a>Verfügbarmachen einer Eigenschaft
 Einige Eigenschaften wie Farbe der Form können verknüpft werden, auf den Wert der Eigenschaft "Domain" ein.

 Wählen Sie in der DSL-Definition Form, den Connector oder Diagramm-Klasse. Wählen Sie in dessen Kontextmenü **hinzufügen verfügbar gemacht**, und wählen Sie dann die gewünschte Eigenschaft, z. B. Füllfarbe.

 Das Shape verfügt jetzt über eine Eigenschaft "Domain", die Sie im Programmcode oder als ein Benutzer festlegen können.

## <a name="dynamically-updating-an-exposed-property"></a>Dynamisch aktualisieren einer bereitgestellten Eigenschaft
 In der Regel möchten Sie die verfügbar gemachten Eigenschaft zu einer anderen Eigenschaft abhängig machen. Beispielsweise sollten Sie eine Form, um Rot, wenn eine bestimmte Domäne-Eigenschaft ist kleiner als 0 (null). Damit diese Abhängigkeit kann, erstellen eine [Regel](../modeling/rules-propagate-changes-within-the-model.md). Zum Beispiel:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
namespace ExampleNamespace
{
 // Attribute associates the rule with class:
 [RuleOn(typeof(CarShape), FireTime = TimeToFire.TopLevelCommit)]
 // The rule is a class derived from one of the abstract rules:
 class CarShapeAddRule : AddRule
 {
 // Override the abstract method:
 public override void ElementAdded(ElementAddedEventArgs e)
 {
 base.ElementAdded(e);
 CarShape shape = e.ModelElement as CarShape;
 Store store = shape.Store;
 // Ignore this call if we're currently loading a model:
 if (store.TransactionManager.CurrentTransaction.IsSerializing)
  return;
 Car car = shape.ModelElement as Car;
 // Code here propagates change as required - for example:
 shape.FillColor = car.Somebool ? System.Drawing.Color.Red : System.Drawing.Color.Green;
 }
}
 // The rule must be registered:
 public partial class ExampleDomainModel
 {
 protected override Type[] GetCustomDomainModelTypes()
 {
  List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());
  types.Add(typeof(CarShapeAddRule));
  // If you add more rules, list them here.
  return types.ToArray();
 }
 }
}
```