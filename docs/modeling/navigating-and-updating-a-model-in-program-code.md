---
title: Navigieren in und Aktualisieren von Modellen im Programmcode
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 18f4153db019dd6ded97337d4599f02a6b02ef49
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34748933"
---
# <a name="navigate-and-update-a-model-in-program-code"></a>Navigieren in und Aktualisieren von Modellen im Programmcode

Sie können Code zum Erstellen und Löschen von Modellelementen, Festlegen ihrer Eigenschaften und erstellen und Löschen von Verknüpfungen zwischen den Elementen schreiben. Alle Änderungen müssen innerhalb einer Transaktion ausgeführt werden. Wenn die Elemente in einem Diagramm angezeigt werden, wird das Diagramm "automatisch am Ende der Transaktion behoben einrichten".

## <a name="in-this-topic"></a>In diesem Thema
 [Bibliotheksbeispiel DSL-Definition](#example)

 [Navigieren in das Modell](#navigation)

 [Zugreifen auf Klasseninformationen](#metadata)

 [Ausführen von Änderungen innerhalb einer Transaktion](#transaction)

 [Erstellen von Modellelementen](#elements)

 [Erstellen von Beziehungslinks](#links)

 [Löschen von Elementen](#deleteelements)

 [Löschen von Beziehungslinks](#deletelinks)

 [Neuanordnen von Verknüpfungen eine Beziehung](#reorder)

 [Sperren](#locks)

 [Kopieren und Einfügen](#copy)

 [Navigieren in und Aktualisieren von Diagrammen](#diagrams)

 [Navigieren zwischen Formen und Elemente](#views)

 [Eigenschaften von Formen und Konnektoren](#shapeProperties)

 [DocView und DocData](#docdata)

##  <a name="example"></a> Bibliotheksbeispiel DSL-Definition
 Dies ist der Hauptteil der DslDefinition.dsl bei den Beispielen in diesem Thema:

 ![DSL-Definitionsdiagramm &#45; stammbaummodell](../modeling/media/familyt_person.png)

 Dieses Modell ist eine Instanz dieser DSL:

 ![Tudor-Stammstrukturmodell](../modeling/media/tudor_familytreemodel.png)

### <a name="references-and-namespaces"></a>Verweise und Namespaces
 Zum Ausführen des Codes in diesem Thema sollten Sie verweisen:

 `Microsoft.VisualStudio.Modeling.Sdk.11.0.dll`

 Im Code wird dieser Namespace verwendet werden:

 `using Microsoft.VisualStudio.Modeling;`

 Wenn Sie den Code in einem anderen Projekt als dem Schreiben in denen der DSL definiert ist, sollten Sie darüber hinaus die Assembly importieren, die von der Dsl-Projekt erstellt wird.

##  <a name="navigation"></a> Navigieren in das Modell

### <a name="properties"></a>Eigenschaften
 Domäneneigenschaften fest, die Sie in der DSL-Definition definieren, werden die Eigenschaften, die Sie im Programmcode zugreifen können:

 `Person henry = ...;`

 `if (henry.BirthDate < 1500) ...`

 `if (henry.Name.EndsWith("VIII")) ...`

 Wenn Sie eine Eigenschaft festlegen möchten, müssen Sie dazu in einem [Transaktion](#transaction):

 `henry.Name = "Henry VIII";`

 Sofern in der DSL-Definition, eine Eigenschaft des **Art** ist **berechnete**, Sie können ihn nicht festlegen. Weitere Informationen finden Sie unter [berechnet und benutzerdefinierte Speichereigenschaften](../modeling/calculated-and-custom-storage-properties.md).

### <a name="relationships"></a>Beziehungen
 Zwischen Domänen, die Sie in der DSL-Definition definieren, werden die Paare von Eigenschaften dar, auf die Klasse an beiden Enden der Beziehung. Die Namen der Eigenschaften, die im Diagramm DslDefinition als Beschriftung für die Rollen auf jeder Seite der Beziehung angezeigt wird. Abhängig von die Multiplizität der Rolle ist der Typ der Eigenschaft der Klasse am anderen Ende der Beziehung, oder aber eine Auflistung von dieser Klasse.

 `foreach (Person child in henry.Children) { ... }`

 `FamilyTreeModel ftree = henry.FamilyTreeModel;`

 Die Eigenschaften am entgegengesetzten Ende einer Beziehung sind immer Kehrwert. Wenn ein Link erstellt oder gelöscht wird, werden die Rolleneigenschaften für beide Elemente aktualisiert. Der folgende Ausdruck (Dabei wird die Erweiterungen der `System.Linq`) ist immer "true" für die Beziehung ParentsHaveChildren im Beispiel:

 `(Person p) => p.Children.All(child => child.Parents.Contains(p))`

 `&& p.Parents.All(parent => parent.Children.Contains(p));`

 **ElementLinks**. Eine Beziehung wird auch durch ein Modellelement aufgerufen dargestellt eine *Link*, also in einer Instanz von der Beziehungstyp "Domäne". Einen Link enthält immer eine Source-Element und ein Target-Element. Die Source-Element und das Zielelement können identisch sein.

 Sie können einen Link und seine Eigenschaften zugreifen:

 `ParentsHaveChildren link = ParentsHaveChildren.GetLink(henry, edward);`

 `// This is now true:`

 `link == null || link.Parent == henry && link.Child == edward`

 Standardmäßig ist nicht mehr als eine Instanz einer Beziehung zulässig, um ein beliebiges Paar von Modellelementen verknüpfen. Aber wenn Sie in der DSL-Definition, die `Allow Duplicates` Flag für die Beziehung "true" ist möglicherweise mehr als einen Link und verwenden Sie `GetLinks`:

 `foreach (ParentsHaveChildren link in ParentsHaveChildren.GetLinks(henry, edward)) { ... }`

 Es gibt auch andere Methoden für den Zugriff auf die Links. Zum Beispiel:

 `foreach (ParentsHaveChildren link in     ParentsHaveChildren.GetLinksToChildren(henry)) { ... }`

 **Ausgeblendete Rollen.** Wenn Sie in der Definition der DSL **Eigenschaft generiert** ist **"false"** für eine bestimmte Rolle keine Eigenschaft wird generiert, die diese Rolle entspricht. Sie können jedoch weiterhin Zugriff auf die Links und durchlaufen die Links mit den Methoden der Beziehung:

 `foreach (Person p in ParentsHaveChildren.GetChildren(henry)) { ... }`

 Die am häufigsten verwendete Beispiel ist die <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject> Beziehung, die einem Modellelement mit der Form verknüpft ist, die in einem Diagramm angezeigt:

 `PresentationViewsSubject.GetPresentation(henry)[0] as PersonShape`

### <a name="the-element-directory"></a>Das Element-Verzeichnis
 Sie können alle Elemente im Speicher mit dem Element-Verzeichnis zugreifen:

 `store.ElementDirectory.AllElements`

 Es gibt auch Methoden zum Suchen von Elementen, z. B. folgende:

 `store.ElementDirectory.FindElements(Person.DomainClassId);`

 `store.ElementDirectory.GetElement(elementId);`

##  <a name="metadata"></a> Zugreifen auf Klasseninformationen
 Sie erhalten Informationen über die Klassen, Beziehungen und andere Aspekte der DSL-Definition. Zum Beispiel:

 `DomainClassInfo personClass = henry.GetDomainClass();`

 `DomainPropertyInfo birthProperty =`

 `personClass.FindDomainProperty("BirthDate")`

 `DomainRelationshipInfo relationship =`

 `link.GetDomainRelationship();`

 `DomainRoleInfo sourceRole = relationship.DomainRole[0];`

 Die übergeordneten Klassen von Modellelementen lauten wie folgt:

-   Modellelement - alle Elemente und Beziehungen werden ModelElements

-   ElementLink - sind alle Beziehungen ElementLinks

##  <a name="transaction"></a> Ausführen von Änderungen innerhalb einer Transaktion
 Bei jeder Änderung des Programm-Codes nichts im Store, müssen sie innerhalb einer Transaktion. Dies gilt für alle betroffenen Modellelemente, Beziehungen, Formen, Diagramme und ihre Eigenschaften. Weitere Informationen finden Sie unter <xref:Microsoft.VisualStudio.Modeling.Transaction>.

 Die einfachste Methode zur Verwaltung einer Transaktions wird mit einem `using` -Anweisung eingeschlossen werden, eine `try...catch` Anweisung:

```
Store store; ...
try
{
  using (Transaction transaction =
    store.TransactionManager.BeginTransaction("update model"))
    // Outermost transaction must always have a name.
  {
    // Make several changes in Store:
    Person p = new Person(store);
    p.FamilyTreeModel = familyTree;
    p.Name = "Edward VI";
    // end of changes to Store

    transaction.Commit(); // Don't forget this!
  } // transaction disposed here
}
catch (Exception ex)
{
  // If an exception occurs, the Store will be
  // rolled back to its previous state.
}
```

 Sie können eine beliebige Anzahl von Änderungen innerhalb einer Transaktion vornehmen. Sie können neue Transaktionen innerhalb einer aktiven Transaktion öffnen.

 Um Ihre Änderungen permanent zu machen, sollten Sie `Commit` der Transaktion, bevor sie freigegeben ist. Wenn eine Ausnahme, die innerhalb der Transaktion nicht aufgefangen werden kann auftritt, wird der Speicher in dem Zustand vor der Änderungen zurückgesetzt.

##  <a name="elements"></a> Erstellen von Modellelementen
 In diesem Beispiel fügt ein Element zu einem vorhandenen Modell:

```
FamilyTreeModel familyTree = ...; // The root of the model.
using (Transaction t =
    familyTree.Store.TransactionManager
    .BeginTransaction("update model"))
{
  // Create a new model element
  // in the same partition as the model root:
  Person edward = new Person(familyTree.Partition);
  // Set its embedding relationship:
  edward.FamilyTreeModel = familyTree;
          // same as: familyTree.People.Add(edward);
  // Set its properties:
  edward.Name = "Edward VII";
  t.Commit(); // Don't forget this!
}
```

 Dieses Beispiel veranschaulicht diese wichtige Punkte zum Erstellen eines Elements:

-   Erstellen Sie das neue Element in einer bestimmten Partition des Speichers. Für die betroffenen Modellelemente und Beziehungen, jedoch nicht die Formen ist dies normalerweise die Standardpartition.

-   Stellen sie das Ziel ein Einbetten von Beziehung. In der DslDefinition dieses Beispiels muss jede Person das Ziel der Beziehung FamilyTreeHasPeople einbetten. Um dies zu erreichen, können wir legen Sie die FamilyTreeModel Rolle-Eigenschaft des Person-Objekts oder die Person, die für die Personen Rolle-Eigenschaft des Objekts FamilyTreeModel hinzufügen.

-   Legen Sie die Eigenschaften eines neuen Elements an, vor allem die Eigenschaft für die `IsName` ist "true" in der DslDefinition. Dieses Flag markiert die Eigenschaft, die dazu verwendet wird, das Element innerhalb eines Eigentümer eindeutig zu identifizieren. In diesem Fall hat die Name-Eigenschaft dieses Flag angibt.

-   DSL-Definition für diese DSL muss in den Speicher geladen wurden. Wenn Sie eine Erweiterung wie einen Menübefehl schreiben, wird dies in der Regel bereits "true" sein. In anderen Fällen können Sie explizit das Modell in den Speicher geladen, oder <xref:Microsoft.VisualStudio.Modeling.Integration.ModelBus> zu laden. Weitere Informationen finden Sie unter [Vorgehensweise: Öffnen Sie ein Modell aus der Datei im Programmcode](../modeling/how-to-open-a-model-from-file-in-program-code.md).

 Wenn Sie ein Element auf diese Weise erstellen, wird eine Form "(wenn der DSL ein Diagramm enthält) automatisch erstellt. Er wird in einen automatisch zugewiesenen Speicherort mit Standardform, Farbe und andere Funktionen. Wenn Sie möchten steuern, wo und wie die zugeordnete Form angezeigt wird, finden Sie unter [erstellen ein Element und seine Form](#merge).

##  <a name="links"></a> Erstellen von Beziehungslinks
 Es gibt zwei Beziehungen, die im Beispiel DSL-Definition definiert. Jede Beziehung definiert eine *Rolleneigenschaft* für die Klasse an beiden Enden der Beziehung.

 Es gibt drei Möglichkeiten, die in denen Sie eine Instanz einer Beziehung erstellen können. Jede dieser drei Methoden hat dieselbe Wirkung:

-   Legen Sie die Eigenschaft der Quelle-Rolleninhaber. Zum Beispiel:

    -   `familyTree.People.Add(edward);`

    -   `edward.Parents.Add(henry);`

-   Legen Sie die Eigenschaft von der Zielrolleninhaber. Zum Beispiel:

    -   `edward.familyTreeModel = familyTree;`

         Die Multiplizität der diese Rolle wird `1..1`, damit wir den Wert zuzuweisen.

    -   `henry.Children.Add(edward);`

         Die Multiplizität der diese Rolle wird `0..*`, damit es der Auflistung hinzugefügt werden.

-   Erstellen Sie eine Instanz der Beziehung explizit an. Zum Beispiel:

    -   `FamilyTreeHasPeople edwardLink = new FamilyTreeHasPeople(familyTreeModel, edward);`

    -   `ParentsHaveChildren edwardHenryLink = new ParentsHaveChildren(henry, edward);`

 Die letzte Methode ist nützlich, wenn Sie Eigenschaften für die Beziehung selbst festlegen möchten.

 Wenn Sie ein Element auf diese Weise erstellen, ein Connectors für das Diagramm wird automatisch erstellt, aber es wurde eine Standardform, Farbe und andere Funktionen. Um zu steuern, wie die zugeordnete Connector erstellt wird, finden Sie unter [erstellen ein Element und seine Form](#merge).

##  <a name="deleteelements"></a> Löschen von Elementen
 Löschen eines Elements durch den Aufruf `Delete()`:

 `henry.Delete();`

 Dieser Vorgang wird auch gelöscht:

-   Beziehungslinks zum und vom Element. Beispielsweise `edward.Parents` wird nicht mehr enthalten `henry`.

-   Rollen für die Elemente der `PropagatesDelete` Flag ist "true". Beispielsweise wird das Shape, das das Element anzeigt, gelöscht werden.

 Standardmäßig verfügt jede Einbetten von Beziehung `PropagatesDelete` an die Zielrolle "true". Löschen von `henry` löscht keine der `familyTree`, aber `familyTree.Delete()` würde, löschen Sie alle die `Persons`. Weitere Informationen finden Sie unter [anpassen, löschen Sie das Verhalten](../modeling/customizing-deletion-behavior.md).

 Standardmäßig `PropagatesDelete` gilt nicht für die Rollen der verweisbeziehungen.

 Sie können dazu führen, dass die Löschregeln, um bestimmte Weitergaben zu unterdrücken, wenn Sie ein Objekt löschen. Dies ist hilfreich, wenn Sie ein Element für eine andere ersetzt werden. Geben Sie an die GUID des eine oder mehrere Rollen für die Löschung nicht weitergegeben werden sollen. Die GUID kann von der Beziehungsklasse abgerufen werden:

 `henry.Delete(ParentsHaveChildren.SourceDomainRoleId);`

 (Diesem speziellen Beispiel würde wirken sich nicht, da `PropagatesDelete` ist `false` für die Rollen der `ParentsHaveChildren` Beziehung.)

 In einigen Fällen wird das Löschen verhindert, durch das Vorhandensein einer Sperre, die auf das Element oder auf ein Element, das durch Weitergabe gelöscht würden. Sie können `element.CanDelete()` zu überprüfen, ob das Element gelöscht werden kann.

##  <a name="deletelinks"></a> Löschen von Beziehungslinks
 Sie können einen Beziehungslink löschen, indem Sie ein Element aus einer Rolleneigenschaft entfernt:

 `henry.Children.Remove(edward); // or:`

 `edward.Parents.Remove(henry);  // or:`

 Sie können auch den Link explizit löschen:

 `edwardHenryLink.Delete();`

 Diese drei Methoden, die alle haben dieselbe Wirkung. Sie müssen nur eine davon verwenden.

 Wenn die Rolle 0.. 1 oder 1..1 Multiplizität aufweist, können Sie ihn auf einstellen `null`, oder ein anderer Wert:

 `edward.FamilyTreeModel = null;` oder:

 `edward.FamilyTreeModel = anotherFamilyTree;`

##  <a name="reorder"></a> Neusortierung der Links in einer Beziehung
 Die Links von einer bestimmten Beziehung, die Quelle oder auf ein bestimmtes Modellelement ausgerichtet haben eine bestimmte Reihenfolge. Sie werden in der Reihenfolge, in der sie hinzugefügt wurden. Diese Anweisung ergibt sich z. B. immer auf die untergeordneten Elemente in der gleichen Reihenfolge aus:

 `foreach (Person child in henry.Children) ...`

 Sie können die Reihenfolge der Links ändern:

 `ParentsHaveChildren link = GetLink(henry,edward);`

 `ParentsHaveChildren nextLink = GetLink(henry, elizabeth);`

 `DomainRoleInfo role =`

 `link.GetDomainRelationship().DomainRoles[0];`

 `link.MoveBefore(role, nextLink);`

##  <a name="locks"></a> Sperren
 Die Änderungen möglicherweise durch eine Sperre verhindert werden. Sperren können für einzelne Elemente, für Partitionen und des Speichers festgelegt werden. Wenn einer dieser Ebenen verfügt über eine Sperre, die verhindert, dass die Art der Änderung, die Sie vornehmen möchten, möglicherweise eine Ausnahme ausgelöst werden, wenn Sie in ihr versucht werden. Sie können ermitteln, ob Sperren festgelegt werden, indem Sie mithilfe des Elements. GetLocks(), die eine Erweiterungsmethode ist, die im Namespace definiert ist <xref:Microsoft.VisualStudio.Modeling.Immutability>.

 Weitere Informationen finden Sie unter [definieren eine Richtlinie Sperren für Read-Only-Segmente erstellen](../modeling/defining-a-locking-policy-to-create-read-only-segments.md).

##  <a name="copy"></a> Kopieren und einfügen
 Sie können Elemente oder Elementgruppen zum Kopieren einer <xref:System.Windows.Forms.IDataObject>:

```
Person person = personShape.ModelElement as Person;
Person adopter = adopterShape.ModelElement as Person;
IDataObject data = new DataObject();
personShape.Diagram.ElementOperations
      .Copy(data, person.Children.ToList<ModelElement>());
```

 Die Elemente werden als eine serialisierte Elementgruppe gespeichert.

 Sie können Elemente aus einer "IDataObject" in ein Modell zusammenführen:

```
using (Transaction t = targetDiagram.Store.
        TransactionManager.BeginTransaction("paste"))
{
  adopterShape.Diagram.ElementOperations.Merge(adopter, data);
}
```

 `Merge ()` akzeptiert entweder eine `PresentationElement` oder ein `ModelElement`. Wenn Sie geben eine `PresentationElement`, Sie können auch eine Position in das Zieldiagramm als dritten Parameter angeben.

##  <a name="diagrams"></a> Navigieren in und Aktualisieren von Diagrammen
 In eine DSL ist die Domäne Modellelement, das ein Konzept wie z. B. die Person oder Musiktitel darstellt, aus dem FormElement, das darstellt, sehen Sie im Diagramm getrennt. Das Modellelement Domäne speichert die wichtigen Eigenschaften und die Beziehungen der Konzepte erläutert. Das FormElement speichert die Größe, Position und Farbe der Ansicht des Objekts, auf das Diagramm, und das Layout seiner Komponenten.

### <a name="presentation-elements"></a>Presentation-Elemente
 ![Klassendiagramm für grundlegende Form- und Elementtypen](../modeling/media/dslshapesandelements.png)

 In der DSL-Definition erstellt jedes Element, das Sie angeben, eine Klasse, die von einer der folgenden standard-Klassen abgeleitet ist.

|Art des Elements|Basisklasse|
|---------------------|----------------|
|Domänenklasse|<xref:Microsoft.VisualStudio.Modeling.ModelElement>|
|Domänenbeziehung|<xref:Microsoft.VisualStudio.Modeling.ElementLink>|
|Form|<xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>|
|Verbindung|<xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>|
|Diagramm|<xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>|

 Ein Element in einem Diagramm stellt normalerweise eine Modellelement. In der Regel (aber nicht immer) eine <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape> stellt eine Domäne-Klasseninstanz und eine <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape> eine Instanz der Anwendungsdomäne Beziehung darstellt. Die <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject> Beziehung verknüpft eine Form "Knoten" oder "Link" mit dem Modellelement, die es darstellt.

 Jede Form "Knoten" oder "Link" gehört zu einem Diagramm. Eine binäre Linkform verbindet zwei Knoten Formen.

 Formen können in zwei Sätze untergeordneten Formen besitzen. Eine Form in der `NestedChildShapes` Satz auf Begrenzungsrahmens seines übergeordneten Elements beschränkt wird. Eine Form in der `RelativeChildShapes` Liste kann außerhalb oder teilweise außerhalb des gültigen Bereichs des übergeordneten Elements – z. B. eine Bezeichnung oder einen Port angezeigt. Ein Diagramm verfügt über keinen `RelativeChildShapes` und keine `Parent`.

###  <a name="views"></a> Navigieren zwischen Formen und Elemente
 Domäne von Modellelementen und Formelemente sind verknüpft sind, indem die <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject> Beziehung.

```csharp
// using Microsoft.VisualStudio.Modeling;
// using Microsoft.VisualStudio.Modeling.Diagrams;
// using System.Linq;
Person henry = ...;
PersonShape henryShape =
  PresentationViewsSubject.GetPresentation(henry)
    .FirstOrDefault() as PersonShape;
```

 Die gleiche Beziehung verknüpft Beziehungen mit Verbindungen im Diagramm:

```
Descendants link = Descendants.GetLink(henry, edward);
DescendantConnector dc =
   PresentationViewsSubject.GetPresentation(link)
     .FirstOrDefault() as DescendantConnector;
// dc.FromShape == henryShape && dc.ToShape == edwardShape
```

 Diese Beziehung wird der Stamm des Modells auch in das Diagramm verknüpft:

```
FamilyTreeDiagram diagram =
   PresentationViewsSubject.GetPresentation(familyTree)
      .FirstOrDefault() as FamilyTreeDiagram;
```

 Um eine Form dargestellte Modellelement abrufen möchten, verwenden Sie:

 `henryShape.ModelElement as Person`

 `diagram.ModelElement as FamilyTreeModel`

### <a name="navigating-around-the-diagram"></a>Navigieren Sie in das Diagramm
 Im Allgemeinen ist es nicht empfehlenswert, die zwischen Formen und Konnektoren im Diagramm zu navigieren. Es ist besser, die Beziehungen im Modell verschieben zwischen den Formen und-Verbindern nur bei Bedarf auf die Darstellung des Diagramms zu navigieren. Diese Methoden werden Connectors mit Formen an beiden Enden verknüpft:

 `personShape.FromRoleLinkShapes, personShape.ToRoleLinkShapes`

 `connector.FromShape, connector.ToShape`

 Viele Formen sind aus Komponenten zusammengesetzt. Sie werden von einer Form "Parent" und eine oder mehrere Ebenen von untergeordneten Elementen besteht. Formen, die in Bezug auf eine andere Form positioniert sind gelten als seine *Kinder*. Wenn die Form "übergeordneten" verschoben wird, werden die untergeordneten Elemente mit verschoben.

 *Relative Kinder* kann außerhalb des umgebenden Felds der übergeordneten Form angezeigt werden. *Geschachtelte* untergeordneten Elementen strikt innerhalb der Begrenzung des übergeordneten Elements angezeigt.

 Um den oberen Satz von Formen in einem Diagramm zu erhalten, verwenden Sie Folgendes:

 `Diagram.NestedChildShapes`

 Die übergeordneten Klassen von Formen und Verbindern sind:

 <xref:Microsoft.VisualStudio.Modeling.ModelElement>

 -- <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationElement>

 -- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement>

 ----- <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>

 ------- <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>

 ------- *YourShape*

 ----- <xref:Microsoft.VisualStudio.Modeling.Diagrams.LinkShape>

 ------- <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>

 --------- *YourConnector*

###  <a name="shapeProperties"></a> Eigenschaften von Formen und Konnektoren
 In den meisten Fällen ist es nicht notwendig, explizite Änderungen an den Formen vornehmen. Wenn Sie die betroffenen Modellelemente geändert haben, aktualisieren Sie die Regeln "Reparieren", die Formen und Konnektoren. Weitere Informationen finden Sie unter [Weitergeben von Änderungen und reagieren auf](../modeling/responding-to-and-propagating-changes.md).

 Allerdings ist es hilfreich, die einige explizite Formen in den Eigenschaften ändern, die die betroffenen Modellelemente unabhängig sind. Beispielsweise können Sie diese Eigenschaften ändern:

-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Size%2A> – Bestimmt die Höhe und Breite der Form.

-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Location%2A> -Position relativ zum übergeordneten Form oder Diagramm

-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.StyleSet%2A> -der Satz der Stifte und Pinsel, der zum Zeichnen der Form oder den Verbinder

-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Hide%2A> -unsichtbar die Form "

-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Show%2A> – Stellt die Form sichtbar, nachdem ein `Hide()`

###  <a name="merge"></a> Erstellen ein Element und seine Form
 Wenn Sie ein Element erstellen und ihn in die Struktur der Einbettung Beziehungen verknüpfen, wird eine Form automatisch erstellt und zugeordnet. Dies erfolgt durch die Regeln "Reparieren", die am Ende der Transaktion ausgeführt. Allerdings die Form wird angezeigt, an einem Speicherort automatisch zugewiesen, und die Form, Farbe und andere Funktionen über Standardwerte verfügen. Um zu steuern, wie die Form "erstellt wird, können Sie den Merge-Funktion verwenden. Sie müssen zuerst die Elemente, die Sie in einer ElementGroup hinzufügen möchten, und dann die Gruppe in das Diagramm zusammenführen.

 Diese Methode:

-   Legt den Namen fest, wenn eine Eigenschaft als Elementname zugewiesen wurden.

-   Berücksichtigt alle-Element Merge-Anweisungen, die Sie in der DSL-Definition angegeben.

 In diesem Beispiel wird an der Position des Mauszeigers ein Shape erstellt, wenn der Benutzer im Diagramm doppelklickt. In der DSL-Definition für dieses Beispiel die `FillColor` Eigenschaft `ExampleShape` verfügbar gemacht wurde.

```

using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
partial class MyDiagram
{
  public override void OnDoubleClick(DiagramPointEventArgs e)
  {
    base.OnDoubleClick(e);

    using (Transaction t = this.Store.TransactionManager
        .BeginTransaction("double click"))
    {
      ExampleElement element = new ExampleElement(this.Store);
      ElementGroup group = new ElementGroup(element);

      { // To use a shape of a default size and color, omit this block.
        ExampleShape shape = new ExampleShape(this.Partition);
        shape.ModelElement = element;
        shape.AbsoluteBounds = new RectangleD(0, 0, 1.5, 1.0);
        shape.FillColor = System.Drawing.Color.Azure;
        group.Add(shape);
      }

      this.ElementOperations.MergeElementGroupPrototype(
        this,
        group.CreatePrototype(),
        PointD.ToPointF(e.MousePosition));
      t.Commit();
    }
  }
}

```

 Wenn Sie mehr als eine Form angeben, legen Sie ihre relativen Positionen, die mit der `AbsoluteBounds`.

 Sie können auch die Farbe und die andere verfügbar gemachten Eigenschaften des Connectors, die mit dieser Methode festlegen.

### <a name="use-transactions"></a>Verwenden von Transaktionen
 Formen, Connectors und Diagramme werden Untertypen von <xref:Microsoft.VisualStudio.Modeling.ModelElement> und live im Speicher. Sie müssen daher werden nur innerhalb einer Transaktion ändern. Weitere Informationen finden Sie unter [wie: Verwenden von Transaktionen zum Aktualisieren des Modells](../modeling/how-to-use-transactions-to-update-the-model.md).

##  <a name="docdata"></a> Ansicht des Dokuments und Dokumentdaten
 ![Klassendiagramm für Standarddiagrammtypen](../modeling/media/dsldiagramsanddocs.png)

## <a name="store-partitions"></a>Speichern von Partitionen
 Wenn ein Modell geladen wird, wird das begleitende Diagramm zur gleichen Zeit geladen. In der Regel das Modell in Store.DefaultPartition geladen werden, und der Inhalt des Diagramms in einer anderen Partition geladen wird. In der Regel wird der Inhalt der einzelnen Partitionen geladen und in einer separaten Datei gespeichert.

## <a name="see-also"></a>Siehe auch

- <xref:Microsoft.VisualStudio.Modeling.ModelElement>
- [Validierung in einer domänenspezifischen Sprache](../modeling/validation-in-a-domain-specific-language.md)
- [Generieren von Code für eine domänenspezifische Sprache](../modeling/generating-code-from-a-domain-specific-language.md)
- [Gewusst wie: Verwenden von Transaktionen zum Aktualisieren des Modells](../modeling/how-to-use-transactions-to-update-the-model.md)
- [Integrieren von Modellen mit Visual Studio-ModelBus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [Reagieren auf und Propagieren von Änderungen](../modeling/responding-to-and-propagating-changes.md)
