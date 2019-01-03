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
ms.openlocfilehash: a741a506338066dddbee2cdbfd701ad3bfb4c922
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53929697"
---
# <a name="controlling-color-line-style-and-other-shape-properties"></a>Steuern von Farbe, Linienstil und anderen Eigenschaften von Formen
Einige Eigenschaften der Form, wie z. B. Farbe "verfügbar gemacht werden kann' - verknüpft, d. h. einer Domäneneigenschaft der Form. Andere haben direkt gesteuert werden.

## <a name="exposing-a-property"></a>Verfügbarmachen einer Eigenschaft
 Einige Eigenschaften wie Farbe der Form können auf den Wert einer Domäneneigenschaft verknüpft werden.

 Wählen Sie in der DSL-Definition einer Form, den Connector oder die Diagrammklasse aus. Wählen Sie auf das Kontextmenü zu öffnen, **verfügbare hinzufügen**, und wählen Sie dann die gewünschte Eigenschaft, z. B. Farbe füllen.

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