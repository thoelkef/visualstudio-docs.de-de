---
title: Navigieren in Beziehungen mit der UML-API | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API
ms.assetid: a4d11d45-b8c0-40f9-a597-363f07659610
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f19208e886eb499c825b119ad4ade7e8b52ab88f
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300241"
---
# <a name="navigate-relationships-with-the-uml-api"></a>Navigieren in Beziehungen mit der UML-API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ein Modell besteht aus Elementen, die über unterschiedliche Beziehungen miteinander verknüpft sind. In diesem Thema wird beschrieben, wie Sie im Programmcode im Modell navigieren.

## <a name="traversing-relationships"></a>Durchlaufen von Beziehungen

### <a name="any-relationship"></a>Beliebige Beziehung
 Verwenden Sie `GetRelatedElements<T>()`, um nach allen Elementen zu suchen, die mit einem angegebenen Element verbunden sind. Legen Sie entweder `T` auf `IRelationship` fest, um Beziehungen aller Arten zu durchlaufen, oder verwenden Sie einen spezifischeren Typ wie `IAssociation`, um nur diesen Typ zu durchlaufen.

```
IElement anElement;
// Select all elements related to anElement.
Context.CurrentDiagram.SelectShapes (
   anElement.GetRelatedElements<IRelationship>()
    .SelectMany(e=>e.Shapes()).ToArray());

```

 Verwenden Sie `GetRelatedLinks<T>()`, um nach allen Beziehungen zu suchen, die mit einem Element verbunden sind.

```
// Process all relationships connected to an element.
foreach (IRelationship relationship in
   anElement.GetRelatedLinks<IRelationship>())
{
  Debug.Assert(relationship.SourceElement == anElement
      || relationship.TargetElement == anElement);
}

```

### <a name="association"></a>Zuordnung
 Eine Zuordnung ist eine Beziehung zwischen zwei Eigenschaften, die jeweils zu einem Klassifizierer gehören.

```
IClassifier classifier; // class, interface, component, actor, ...
// Get all the associations sourced from this classifier
foreach (IProperty p in classifier.GetOutgoingAssociationEnds())
{
  // p represents the end further end of an association.
  IType oppositeElement = p.Type;
    // The type to which this association connects classifier

  IProperty oppositeProperty = p.Opposite;
    // The nearer end of the association.
  Debug.Assert(oppositeProperty.Type == classifier);
  IAssociation association = p.Association;
  Debug.Assert(association.MemberEnds.Contains(p)
     && association.MemberEnds.Contains(oppositeProperty));
}
```

### <a name="generalization-and-realization"></a>Generalisierung und Realisierung
 Greifen Sie auf die entgegengesetzten Enden der Generalisierung zu:

```
foreach (IClassifier supertype in classifier.Generals) {…}
foreach (IClassifier subtype in classifier.GetSpecifics()) {…}
Access the relationship itself:
foreach (IGeneralization gen in classifier.Generalizations)
{ Debug.Assert(classifier == gen.Specific); }
```

```

/// InterfaceRealization:
IEnumerable<IInterface> GetRealizedInterfaces
    (this IBehavioredClassifier classifier);
IEnumerable<IBehavioredClassifier> GetRealizingClassifiers
    (this IInterface interface);

```

### <a name="dependency"></a>Abhängigkeit

```
/// Returns the elements depending on this element
IEnumerable<INamedElement> GetDependencyClients(this INamedElement element);
/// Returns the elements this element depends on
IEnumerable<INamedElement> INamedElement GetDependencySuppliers(this INamedElement element);

```

### <a name="activity-edge"></a>Aktivitätsrand

```
/// Returns the nodes targeted by edges outgoing from this one
IEnumerable<IActivityNode> GetActivityEdgeTargets(this IActivityNode node);
/// Returns the nodes sourcing edges incoming to this one
IEnumerable<IActivityNode> GetActivityEdgeSources(this IActivityNode node);

```

### <a name="connector-assembly-and-delegation"></a>Konnektor (Assembly und Delegierung)

```
/// Returns the elements connected via assembly
/// or delegation to this one
IEnumerable<IConnectableElement> GetConnectedElements(this IConnectableElement element);

```

### <a name="messages-and-lifelines"></a>Meldungen und Lebenslinien

```
IEnumerable<IMessage> GetAllOutgoingMessages(this ILifeline  lifeline);
// both from lifeline and execution occurrences
IEnumerable<IMessage> GetAllIncomingMessages(this ILifeline  lifeline);
ILifeline GetSourceLifeline(this IMessage message);
    // may return null for found messages
ILifeline GetTargetLifeline(this IMessage message);
    // may return null for lost messages

```

### <a name="package-import"></a>Paketimport

```
IEnumerable<IPackage>GetImportedPackages(this INamespace namespace);
IEnumerable<INamespace> GetImportingNamespaces(this IPackage package);

```

### <a name="use-case-extend-and-include"></a>Anwendungsfall (Extend/Include)

```
IEnumerable<IUseCase>GetExtendedCases(this IUseCase usecase);
IEnumerable<IUseCase>GetExtendingCases(this IUseCase usecase);
IEnumerable<IUseCase>GetIncludedCases(this IUseCase usecase);
IEnumerable<IUseCase>GetIncludingCases(this IUseCase usecase);
```

## <a name="enumerating-relationships"></a>Auflisten von Beziehungen
 Alle Eigenschaften des UML-Modells, die mehrere Werte zurückgeben, entsprechen der IEnumerable-< >-Schnittstelle. Dies bedeutet, dass Sie [LINQ-Abfrage Ausdrücke](https://go.microsoft.com/fwlink/?LinkId=168834) und die Erweiterungs Methoden verwenden können, die im **System. Linq** -Namespace definiert sind.

 Beispiel:

```
from shape in     Context.CurrentDiagram.GetSelectedShapes<IClassifier>()
where shape.Color == System.Drawing.Color.Red
select shape.Element

```

## <a name="see-also"></a>Siehe auch
 [Erweitern von UML-Modellen und-Diagrammen](../modeling/extend-uml-models-and-diagrams.md) [Navigieren im UML-Modell](../modeling/navigate-the-uml-model.md)
