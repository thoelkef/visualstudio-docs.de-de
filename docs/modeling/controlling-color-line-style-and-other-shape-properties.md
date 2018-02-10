---
title: Steuern der Farbe, Linienart und andere Eigenschaften der Form | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 5903c6cc79e637514b75c9e44cb4cbe5c0342ee7
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
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