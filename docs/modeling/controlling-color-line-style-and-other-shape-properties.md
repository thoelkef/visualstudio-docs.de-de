---
title: Steuern von Farbe, Linienstil und anderen Eigenschaften von Formen
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d1783ecf3b30207838d93fdb9cda93e3ed7e232c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62422926"
---
# <a name="controlling-color-line-style-and-other-shape-properties"></a>Steuern von Farbe, Linienstil und anderen Eigenschaften von Formen

Einige Eigenschaften von Formen wie z. B. Farbe können "verfügbar gemacht werden". D. h. können die Eigenschaften einer Domäneneigenschaft der Form verknüpft werden. Andere haben direkt gesteuert werden.

## <a name="exposing-a-property"></a>Verfügbarmachen einer Eigenschaft
 Einige Eigenschaften wie Farbe der Form können auf den Wert einer Domäneneigenschaft verknüpft werden.

 Wählen Sie in der DSL-Definition einer Form, den Connector oder die Diagrammklasse aus. Wählen Sie auf der rechten Maustaste, **verfügbare hinzufügen**, und wählen Sie dann die gewünschte Eigenschaft, z. B. Farbe füllen.

 Die Form verfügt jetzt über eine Eigenschaft "Domain", die Sie im Programmcode oder als Benutzer festlegen können.

## <a name="dynamically-updating-an-exposed-property"></a>Dynamisches Aktualisieren einer verfügbar gemachten Eigenschaft
 In der Regel möchten Sie die freigelegte Eigenschaft einer anderen Eigenschaft abhängig machen. Beispielsweise sollten Sie eine Form, um die Rot, wenn eine bestimmte Domäne-Eigenschaft ist kleiner als 0 (null). Mit dieser Abhängigkeit können, erstellen eine [Regel](../modeling/rules-propagate-changes-within-the-model.md). Zum Beispiel:

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