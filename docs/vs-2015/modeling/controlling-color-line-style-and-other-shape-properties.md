---
title: Steuern von Farbe, Linienart und anderen Formeigenschaften | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: c06d0066-24aa-4c65-b91c-c2089b81ec8d
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d5d296f5ab3f5c584558b373b57c175fb2bacef4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667860"
---
# <a name="controlling-color-line-style-and-other-shape-properties"></a>Steuern von Farbe, Linienstil und anderen Eigenschaften von Formen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Einige Formeigenschaften, z. b. Farbe, können "verfügbar" sein – d. h., Sie sind mit einer Domänen Eigenschaft der Form verknüpft. Andere müssen direkt gesteuert werden.

## <a name="exposing-a-property"></a>Verfügbar machen einer Eigenschaft
 Einige Formeigenschaften, z. b. Farbe, können mit dem Wert einer Domänen Eigenschaft verknüpft werden.

 Wählen Sie in der DSL-Definition eine Form, einen Connector oder eine Diagramm Klasse aus. Wählen Sie im Kontextmenü die Option verfügbar **Hinzufügen**aus, und wählen Sie dann die gewünschte Eigenschaft aus, z. b. Füllfarbe.

 Die Form verfügt jetzt über eine Domänen Eigenschaft, die Sie im Programmcode oder als Benutzer festlegen können.

## <a name="dynamically-updating-an-exposed-property"></a>Dynamisches Aktualisieren einer verfügbar gemachten Eigenschaft
 In der Regel möchten Sie die verfügbar gemachte Eigenschaft von einer anderen Eigenschaft abhängig machen. Beispielsweise kann es vorkommen, dass eine Form rot werden soll, wenn eine bestimmte Domänen Eigenschaft kleiner als 0 (null) ist. Erstellen Sie eine [Regel](../modeling/rules-propagate-changes-within-the-model.md), um diese Abhängigkeit zu treffen. Beispiel:

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
