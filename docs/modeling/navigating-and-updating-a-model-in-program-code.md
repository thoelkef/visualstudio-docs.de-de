---
title: Navigieren in und Aktualisieren eines Modells im Programmcode | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, programming domain models
ms.assetid: 1427ae91-be8a-4ce7-85df-00038faa2cbb
caps.latest.revision: 26
author: alancameronwills
ms.author: awills
manager: douge
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: eb2ab9d49cdeb1ed71da8ef67841f7796862dc30
ms.openlocfilehash: f17f676025a19efb09184b7a49645986723cb29f
ms.lasthandoff: 02/22/2017

---
# <a name="navigating-and-updating-a-model-in-program-code"></a>Navigieren in und Aktualisieren von Modellen im Programmcode
Sie können Code zum Erstellen und Löschen von Modellelementen, Festlegen ihrer Eigenschaften und erstellen und Löschen von Verknüpfungen zwischen Elementen schreiben. Alle Änderungen müssen innerhalb einer Transaktion vorgenommen werden. Wenn die Elemente in einem Diagramm angezeigt werden, wird das Diagramm "automatisch am Ende der Transaktion angepasst werden".  
  
## <a name="in-this-topic"></a>In diesem Thema  
 [Ein Beispiel-DSL-Definition](#example)  
  
 [Das Modell navigieren](#navigation)  
  
 [Zugreifen auf Klasseninformationen](#metadata)  
  
 [Führen Sie die Änderung innerhalb einer Transaktion](#transaction)  
  
 [Erstellen von Modellelementen](#elements)  
  
 [Erstellen von Beziehungslinks](#links)  
  
 [Löschen von Elementen](#deleteelements)  
  
 [Löschen von Beziehungslinks](#deletelinks)  
  
 [Neuanordnen von Links einer Beziehung](#reorder)  
  
 [Sperren](#locks)  
  
 [Kopieren und einfügen](#copy)  
  
 [Navigieren in und Aktualisieren von Diagrammen](#diagrams)  
  
 [Navigieren zwischen Formen und Elemente](#views)  
  
 [Eigenschaften von Formen und Konnektoren](#shapeProperties)  
  
 [DocView und DocData](#docdata)  
  
##  <a name="a-nameexamplea-an-example-dsl-definition"></a><a name="example"></a>Ein Beispiel-DSL-Definition  
 Dies ist der wichtigste Aspekt "DslDefinition.DSL" für die Beispiele in diesem Thema:  
  
 ![DSL-Definitionsdiagramm - stammbaummodell](../modeling/media/familyt_person.png "FamilyT_Person")  
  
 Dieses Modell ist eine Instanz dieser DSL:  
  
 ![Tudor-Stammbaummodell](../modeling/media/tudor_familytreemodel.png "Tudor_FamilyTreeModel")  
  
### <a name="references-and-namespaces"></a>Verweise und Namespaces  
 Zum Ausführen des Codes in diesem Thema sollten Sie verweisen:  
  
 `Microsoft.VisualStudio.Modeling.Sdk.11.0.dll`  
  
 Im Code wird dieser Namespace verwendet:  
  
 `using Microsoft.VisualStudio.Modeling;`  
  
 Wenn Sie den Code in einem anderen Projekt als dem Schreiben in denen DSL definiert ist, sollten Sie außerdem die Assembly importieren, die von Dsl-Projekt erstellt wird.  
  
##  <a name="a-namenavigationa-navigating-the-model"></a><a name="navigation"></a>Das Modell navigieren  
  
### <a name="properties"></a>Eigenschaften  
 Eigenschaften von Domänen, die Sie in der DSL-Definition definieren werden die Eigenschaften, die Sie im Programmcode zugreifen können:  
  
 `Person henry = ...;`  
  
 `if (henry.BirthDate < 1500) ...`  
  
 `if (henry.Name.EndsWith("VIII")) ...`  
  
 Wenn Sie eine Eigenschaft festlegen möchten, müssen Sie dazu in einem [Transaktion](#transaction):  
  
 `henry.Name = "Henry VIII";`  
  
 Sofern in der DSL-Definition einer Eigenschaft des **Art** ist **berechnet**, Sie können nicht festlegen. Weitere Informationen finden Sie unter [berechnete und benutzerdefinierte Speichereigenschaften](../modeling/calculated-and-custom-storage-properties.md).  
  
### <a name="relationships"></a>Beziehungen  
 Zwischen Domänen, die Sie in der DSL-Definition definieren werden die Paare von Eigenschaften, auf die Klasse an beiden Enden der Beziehung. Die Namen der Eigenschaften, die als Beschriftung für die Rollen auf beiden Seiten der Beziehung im Diagramm DslDefinition angezeigt werden. Abhängig von der Multiplizität der Rolle ist der Typ der Eigenschaft der Klasse am anderen Ende der Beziehung, oder eine Auflistung von dieser Klasse.  
  
 `foreach (Person child in henry.Children) { ... }`  
  
 `FamilyTreeModel ftree = henry.FamilyTreeModel;`  
  
 Die Eigenschaften auf die entgegengesetzten Enden einer Beziehung sind immer Kehrwert. Wenn eine Verknüpfung erstellt oder gelöscht wird, werden die Eigenschaften der Benutzerrolle für beide Elemente aktualisiert. Der folgende Ausdruck (verwendet die Erweiterungen der `System.Linq`) gilt immer für die ParentsHaveChildren-Beziehung im Beispiel:  
  
 `(Person p) => p.Children.All(child => child.Parents.Contains(p))`  
  
 `&& p.Parents.All(parent => parent.Children.Contains(p));`  
  
 **ElementLinks**. Eine Beziehung durch ein Modellelement aufgerufen dargestellt eine *Link*, also eine Instanz des Beziehungstyps Domäne. Eine Verknüpfung enthält immer eine Source-Element und einem Zielelement. Das Quellelement und das Zielelement können identisch sein.  
  
 Sie können einen Link und deren Eigenschaften zugreifen:  
  
 `ParentsHaveChildren link = ParentsHaveChildren.GetLink(henry, edward);`  
  
 `// This is now true:`  
  
 `link == null || link.Parent == henry && link.Child == edward`  
  
 Standardmäßig ist nicht mehr als eine Instanz einer Beziehung zulässig, ein Paar von Modellelementen verknüpfen. Aber wenn Sie sich in der DSL-Definition der `Allow Duplicates` Flag gilt für die Beziehung, und klicken Sie dann möglicherweise mehr als einen Link, und verwenden Sie `GetLinks`:  
  
 `foreach (ParentsHaveChildren link in ParentsHaveChildren.GetLinks(henry, edward)) { ... }`  
  
 Es gibt auch andere Methoden für den Zugriff auf Links. Zum Beispiel:  
  
 `foreach (ParentsHaveChildren link in     ParentsHaveChildren.GetLinksToChildren(henry)) { ... }`  
  
 **Ausgeblendete Rollen.** Wenn in der DSL-Definition **Eigenschaft generiert** ist **false** für eine bestimmte Rolle dann keine Eigenschaft generiert, die dieser Rolle zugeordnet. Sie können jedoch immer noch Zugriff auf die Links und durchlaufen die Links mit den Methoden der Beziehung:  
  
 `foreach (Person p in ParentsHaveChildren.GetChildren(henry)) { ... }`  
  
 Die am häufigsten verwendete Beispiel ist die <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject>Beziehung ein Modellelement mit der Form verknüpft, die sie in einem Diagramm anzeigt:</xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject>  
  
 `PresentationViewsSubject.GetPresentation(henry)[0] as PersonShape`  
  
### <a name="the-element-directory"></a>Das Element-Verzeichnis  
 Sie können alle Elemente im Speicher mit dem Element-Verzeichnis zugreifen:  
  
 `store.ElementDirectory.AllElements`  
  
 Es gibt auch Methoden zum Suchen von Elementen, z. B. die folgenden:  
  
 `store.ElementDirectory.FindElements(Person.DomainClassId);`  
  
 `store.ElementDirectory.GetElement(elementId);`  
  
##  <a name="a-namemetadataa-accessing-class-information"></a><a name="metadata"></a>Zugreifen auf Klasseninformationen  
 Sie erhalten Informationen zu den Klassen, Beziehungen und andere Aspekte der DSL-Definition. Zum Beispiel:  
  
 `DomainClassInfo personClass = henry.GetDomainClass();`  
  
 `DomainPropertyInfo birthProperty =`  
  
 `personClass.FindDomainProperty("BirthDate")`  
  
 `DomainRelationshipInfo relationship =`  
  
 `link.GetDomainRelationship();`  
  
 `DomainRoleInfo sourceRole = relationship.DomainRole[0];`  
  
 Die übergeordneten Klassen von Modellelementen lauten wie folgt:  
  
-   Modellelement - alle Elemente und Beziehungen werden ModelElements  
  
-   ElementLink - sind alle Beziehungen ElementLinks  
  
##  <a name="a-nametransactiona-perform-changes-inside-a-transaction"></a><a name="transaction"></a>Führen Sie die Änderung innerhalb einer Transaktion  
 Wenn Programmcode nichts im Speicher ändert, muss dies innerhalb einer Transaktion erfolgen. Dies gilt für alle Modellelemente, Beziehungen, Formen, Diagrammen und deren Eigenschaften. Weitere Informationen finden Sie unter <xref:Microsoft.VisualStudio.Modeling.Transaction>.</xref:Microsoft.VisualStudio.Modeling.Transaction>  
  
 Die einfachste Methode zum Verwalten von einer Transaktion wird mit einem `using` -Anweisung eingeschlossen werden, eine `try...catch` Anweisung:  
  
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
  
 Um die Änderungen permanent zu machen, sollten Sie `Commit` der Transaktion, bevor es gelöscht wird. Wenn eine Ausnahme, die innerhalb der Transaktion nicht aufgefangen werden kann auftritt, wird der Speicher in dem Zustand vor der Änderung zurückgesetzt werden.  
  
##  <a name="a-nameelementsa-creating-model-elements"></a><a name="elements"></a>Erstellen von Modellelementen  
 Dieses Beispiel fügt ein Element zu einem vorhandenen Modell:  
  
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
  
-   Erstellen Sie das neue Element in einer bestimmten Partition des Speichers. Für Modellelemente und Beziehungen, jedoch keine Formen ist dies normalerweise die Standardpartition.  
  
-   Erleichtern Sie das Ziel einer einbettenden Beziehung. In den DslDefinition dieses Beispiels muss jede Person die einbettende Beziehung FamilyTreeHasPeople Ziel sein. Um dies zu erreichen, können wir die FamilyTreeModel Rolle-Eigenschaft der Person-Objekt festlegen oder die Person, die an die Personen Role-Eigenschaft des Objekts FamilyTreeModel hinzufügen.  
  
-   Legen Sie die Eigenschaften eines neuen Elements an, vor allem die Eigenschaft für die `IsName` ist in der DslDefinition. Dieses Flag kennzeichnet die Eigenschaft, die das Element eindeutig in seinem Besitzer identifiziert dient. In diesem Fall hat die Name-Eigenschaft Flags.  
  
-   Die DSL-Definition dieser DSL muss in den Speicher geladen worden sein. Wenn Sie eine Erweiterung, z. B. einen Menübefehl schreiben, wird dies in der Regel bereits true sein. In anderen Fällen explizit Laden des Modells in den Speicher, oder verwenden, <xref:Microsoft.VisualStudio.Modeling.Integration.ModelBus>um das Laden der it.</xref:Microsoft.VisualStudio.Modeling.Integration.ModelBus> Weitere Informationen finden Sie unter [Gewusst wie: Öffnen eines Modells aus einer Datei im Programmcode](../modeling/how-to-open-a-model-from-file-in-program-code.md).  
  
 Wenn Sie ein Element auf diese Weise erstellen, wird eine Form (wenn die DSL ein Diagramm verfügt) automatisch erstellt. Er wird in einem Speicherort automatisch zugewiesenen mit Standardform, Farbe und andere Funktionen. Wenn Sie möchten steuern, wo und wie die zugeordnete Form angezeigt wird, finden Sie unter [erstellen ein Element und seine Form](#merge).  
  
##  <a name="a-namelinksa-creating-relationship-links"></a><a name="links"></a>Erstellen von Beziehungslinks  
 Es gibt zwei Beziehungen, die im Beispiel DSL-Definition definiert. Jede Beziehung definiert eine *Rolleneigenschaft* für die Klasse an beiden Enden der Beziehung.  
  
 Es gibt drei Möglichkeiten, die in denen Sie eine Instanz einer Beziehung erstellen können. Jede dieser drei Methoden hat die gleiche Auswirkung:  
  
-   Legen Sie die Eigenschaft von der Quelle der Rolleninhaber. Zum Beispiel:  
  
    -   `familyTree.People.Add(edward);`  
  
    -   `edward.Parents.Add(henry);`  
  
-   Legen Sie die Eigenschaft für den Zielrolleninhaber. Zum Beispiel:  
  
    -   `edward.familyTreeModel = familyTree;`  
  
         Die Multiplizität dieser Rolle ist `1..1`, sodass wir den Wert zuzuweisen.  
  
    -   `henry.Children.Add(edward);`  
  
         Die Multiplizität dieser Rolle ist `0..*`, sodass der Auflistung hinzugefügt.  
  
-   Erstellen Sie explizit eine Instanz der Beziehung. Zum Beispiel:  
  
    -   `FamilyTreeHasPeople edwardLink = new FamilyTreeHasPeople(familyTreeModel, edward);`  
  
    -   `ParentsHaveChildren edwardHenryLink = new ParentsHaveChildren(henry, edward);`  
  
 Die letzte Methode ist nützlich, wenn Sie Eigenschaften für die Beziehung selbst festlegen möchten.  
  
 Wenn Sie ein Element auf diese Weise erstellen, ein Connector im Diagramm wird automatisch erstellt, aber er verfügt über eine Standardform, Farbe und andere Funktionen. Um zu steuern, wie die zugeordnete Connector erstellt wird, finden Sie unter [erstellen ein Element und seine Form](#merge).  
  
##  <a name="a-namedeleteelementsa-deleting-elements"></a><a name="deleteelements"></a>Löschen von Elementen  
 Löschen eines Elements durch Aufrufen von `Delete()`:  
  
 `henry.Delete();`  
  
 Dieser Vorgang wird auch löschen:  
  
-   Beziehungslinks in und aus dem Element. Beispielsweise `edward.Parents` enthält dann nicht mehr `henry`.  
  
-   Rollen für die Elemente der `PropagatesDelete` Flag gilt. Beispielsweise wird die Form, die das Element anzeigt, gelöscht werden.  
  
 Standardmäßig hat jede einbettende Beziehung `PropagatesDelete` an die Zielrolle "true". Löschen von `henry` löscht nicht die `familyTree`, aber `familyTree.Delete()` würde, löschen Sie alle die `Persons`. Weitere Informationen finden Sie unter [Löschverhalten anpassen](../modeling/customizing-deletion-behavior.md).  
  
 In der Standardeinstellung `PropagatesDelete` gilt nicht für die Rollen des verweisbeziehungen.  
  
 Sie können dazu führen, dass die Löschregeln, die bestimmte Schutzverfahren weglassen, wenn Sie ein Objekt löschen. Dies ist hilfreich, wenn Sie ein Element für einen anderen ersetzt werden. Sie geben die GUID für eine oder mehrere Rollen, die für die Löschung nicht weitergegeben werden sollen. Die GUID kann über die Beziehungsklasse abgerufen werden:  
  
 `henry.Delete(ParentsHaveChildren.SourceDomainRoleId);`  
  
 (In diesem Beispiel müssten keine Auswirkung, da `PropagatesDelete` ist `false` für die Rollen der `ParentsHaveChildren` Beziehung.)  
  
 In einigen Fällen wird Löschen verhindert, indem das Vorhandensein einer Sperre, die auf das Element oder auf ein Element, das durch die Weitergabe gelöscht wird. Sie können `element.CanDelete()` zu überprüfen, ob das Element gelöscht werden kann.  
  
##  <a name="a-namedeletelinksa-deleting-relationship-links"></a><a name="deletelinks"></a>Löschen von Beziehungslinks  
 Sie können einen Beziehungslink Entfernen eines Elements aus einer Rolleneigenschaft löschen:  
  
 `henry.Children.Remove(edward); // or:`  
  
 `edward.Parents.Remove(henry);  // or:`  
  
 Sie können auch den Link explizit löschen:  
  
 `edwardHenryLink.Delete();`  
  
 Alle diese drei Methoden haben die gleiche Wirkung. Sie müssen nur eine davon verwenden.  
  
 Wenn die Rolle eine Multiplizität von 0.. 1 oder 1..1 aufweist, können Sie sie festlegen, um `null`, oder auf einen anderen Wert:  
  
 `edward.FamilyTreeModel = null;`oder:  
  
 `edward.FamilyTreeModel = anotherFamilyTree;`  
  
##  <a name="a-namereordera-re-ordering-the-links-of-a-relationship"></a><a name="reorder"></a>Neuordnen der Verknüpfungen eine Beziehung  
 Alle Links von einer bestimmten Beziehung, die erstellt oder auf ein bestimmtes Modellelement ausgerichtet sind eine bestimmte Reihenfolge. Sie werden in der Reihenfolge, in der sie hinzugefügt wurden. Diese Anweisung ergibt z. B. immer die untergeordneten Elemente in der gleichen Reihenfolge:  
  
 `foreach (Person child in henry.Children) ...`  
  
 Sie können die Reihenfolge der Links ändern:  
  
 `ParentsHaveChildren link = GetLink(henry,edward);`  
  
 `ParentsHaveChildren nextLink = GetLink(henry, elizabeth);`  
  
 `DomainRoleInfo role =`  
  
 `link.GetDomainRelationship().DomainRoles[0];`  
  
 `link.MoveBefore(role, nextLink);`  
  
##  <a name="a-namelocksa-locks"></a><a name="locks"></a>Sperren  
 Die Änderungen möglicherweise durch eine Sperre verhindert werden. Sperren können für einzelne Elemente, für die Partitionen und im Speicher festgelegt werden. Wenn einer dieser Ebenen verfügt eine Sperre, die verhindert, dass die Art der Änderung, die Sie vornehmen möchten, möglicherweise eine Ausnahme ausgelöst werden, wenn Sie es versuchen. Sie können ermitteln, ob Sperren mit Element festgelegt werden. GetLocks(), die eine Erweiterungsmethode ist, die im Namespace <xref:Microsoft.VisualStudio.Modeling.Immutability>.</xref:Microsoft.VisualStudio.Modeling.Immutability> definiert ist  
  
 Weitere Informationen finden Sie unter [Definieren einer Sperrrichtlinie zum Erstellen schreibgeschützter Segmente](../modeling/defining-a-locking-policy-to-create-read-only-segments.md).  
  
##  <a name="a-namecopya-copy-and-paste"></a><a name="copy"></a>Kopieren und einfügen  
 Sie können Elemente oder Elementgruppen kopieren nach einer <xref:System.Windows.Forms.IDataObject>:</xref:System.Windows.Forms.IDataObject>  
  
```  
Person person = personShape.ModelElement as Person;  
Person adopter = adopterShape.ModelElement as Person;  
IDataObject data = new DataObject();  
personShape.Diagram.ElementOperations  
      .Copy(data, person.Children.ToList<ModelElement>());  
```  
  
 Die Elemente werden als eine serialisierte Elementgruppe gespeichert.  
  
 Sie können Elemente aus IDataObject in ein Modell zusammenführen:  
  
```  
using (Transaction t = targetDiagram.Store.  
        TransactionManager.BeginTransaction("paste"))  
{  
  adopterShape.Diagram.ElementOperations.Merge(adopter, data);  
}  
```  
  
 `Merge ()`akzeptiert entweder eine `PresentationElement` oder `ModelElement`. Wenn Sie ihm geben eine `PresentationElement`, Sie können auch eine Position im Ziel-Diagramm als dritten Parameter angeben.  
  
##  <a name="a-namediagramsa-navigating-and-updating-diagrams"></a><a name="diagrams"></a>Navigieren in und Aktualisieren von Diagrammen  
 In einer DSL ist das Modellelement Domäne, das ein Konzept wie z. B. Person oder Musiktitel darstellt, unabhängig von der FormElement, das Anzeige im Diagramm darstellt. Das Modellelement Domäne speichert die wichtigen Eigenschaften und Beziehungen der Konzepte. Das FormElement speichert die Größe, Position und Farbe der Ansicht des Objekts im Diagramm und das Layout seiner Komponenten.  
  
### <a name="presentation-elements"></a>Presentation-Elemente  
 ![Klassendiagramm für grundlegende Form- und Elementtypen](../modeling/media/dslshapesandelements.png "DSLshapesAndElements")  
  
 In der DSL-Definition erstellt jedes Element, das Sie angeben, eine Klasse, die von einer der folgenden standard-Klassen abgeleitet ist.  
  
|Art des Elements|Basisklasse|  
|---------------------|----------------|  
|Domain-Klasse|<xref:Microsoft.VisualStudio.Modeling.ModelElement></xref:Microsoft.VisualStudio.Modeling.ModelElement>|  
|Zwischen Domäne|<xref:Microsoft.VisualStudio.Modeling.ElementLink></xref:Microsoft.VisualStudio.Modeling.ElementLink>|  
|Form|<xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape></xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>|  
|Verbindung|<xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape></xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>|  
|Diagramm|<xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram></xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>|  
  
 Ein Element in einem Diagramm stellt normalerweise ein Modellelement dar. In der Regel (aber nicht immer) eine <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>stellt eine Klasseninstanz für die Domäne, und ein <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>repräsentiert eine Beziehung Domäneninstanz.</xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape> </xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape> Die <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject>Beziehung verknüpft ein Knoten oder Link-Shape auf das Modellelement, das diese darstellt.</xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject>  
  
 Jeder Knoten oder Link Form gehört zu einem Diagramm. Eine binäre Beziehung-Shape verbindet zwei Knoten Formen.  
  
 Formen können in zwei untergeordnete Formen besitzen. Eine Form in die `NestedChildShapes` Satz auf das umgebende Feld des übergeordneten beschränkt ist. Eine Form in der `RelativeChildShapes` Liste kann außerhalb oder teilweise außerhalb der Grenzen des übergeordneten Elements – z. B. eine Bezeichnung oder einen Port angezeigt. Ein Diagramm verfügt über keine `RelativeChildShapes` und `Parent`.  
  
###  <a name="a-nameviewsa-navigating-between-shapes-and-elements"></a><a name="views"></a>Navigieren zwischen Formen und Elemente  
 Domäne Modellelemente und Formelemente beziehen sich durch die <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject>Beziehung.</xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject>  
  
```c#  
// using Microsoft.VisualStudio.Modeling;  
// using Microsoft.VisualStudio.Modeling.Diagrams;  
// using System.Linq;  
Person henry = ...;  
PersonShape henryShape =   
  PresentationViewsSubject.GetPresentation(henry)  
    .FirstOrDefault() as PersonShape;  
```  
  
 Die gleiche Beziehung verknüpft Beziehungen mit Konnektoren im Diagramm:  
  
```  
Descendants link = Descendants.GetLink(henry, edward);  
DescendantConnector dc =  
   PresentationViewsSubject.GetPresentation(link)  
     .FirstOrDefault() as DescendantConnector;  
// dc.FromShape == henryShape && dc.ToShape == edwardShape  
```  
  
 Diese Beziehung enthält außerdem den Stamm des Modells auf das Diagramm links:  
  
```  
FamilyTreeDiagram diagram =   
   PresentationViewsSubject.GetPresentation(familyTree)  
      .FirstOrDefault() as FamilyTreeDiagram;  
```  
  
 Verwenden Sie zum Abrufen der Modellelement, das durch eine Form dargestellt:  
  
 `henryShape.ModelElement as Person`  
  
 `diagram.ModelElement as FamilyTreeModel`  
  
### <a name="navigating-around-the-diagram"></a>Navigieren Sie in das Diagramm  
 Im Allgemeinen ist es nicht empfehlenswert, zwischen Formen und Konnektoren im Diagramm zu navigieren. Es ist besser, die Beziehungen im Modell verschieben zwischen Formen und Konnektoren, nur bei Bedarf auf die Darstellung des Diagramms zu navigieren. Diese Methoden verknüpfen Connectors Formen an beiden Enden:  
  
 `personShape.FromRoleLinkShapes, personShape.ToRoleLinkShapes`  
  
 `connector.FromShape, connector.ToShape`  
  
 Viele Shapes sind kombiniert. Sie eine übergeordnete Form und eine oder mehrere Ebenen von untergeordneten Elementen bestehen. Formen, die einer anderen Form ausgerichtete gelten als seine *Kinder*. Wenn die übergeordnete Form bewegt wird, werden die untergeordneten Elemente mit verschoben.  
  
 *Relative untergeordnete* kann außerhalb des Begrenzungsrahmens für die übergeordnete Form angezeigt werden. *Geschachtelte* untergeordneten Elementen ausschließlich innerhalb der Grenzen des übergeordneten Elements angezeigt.  
  
 Verwenden Sie zum Abrufen des oberen Satz von Formen in einem Diagramm:  
  
 `Diagram.NestedChildShapes`  
  
 Die übergeordneten Klassen von Formen und Konnektoren sind:  
  
 <xref:Microsoft.VisualStudio.Modeling.ModelElement></xref:Microsoft.VisualStudio.Modeling.ModelElement>  
  
 --<xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationElement></xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationElement>  
  
 --<xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement></xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement>  
  
 -----<xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape></xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>  
  
 -------<xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram></xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>  
  
 ------- *YourShape*  
  
 -----<xref:Microsoft.VisualStudio.Modeling.Diagrams.LinkShape></xref:Microsoft.VisualStudio.Modeling.Diagrams.LinkShape>  
  
 -------<xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape></xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>  
  
 --------- *YourConnector*  
  
###  <a name="a-nameshapepropertiesa-properties-of-shapes-and-connectors"></a><a name="shapeProperties"></a>Eigenschaften von Formen und Konnektoren  
 In den meisten Fällen ist es nicht notwendig, explizite Formen ändern. Wenn Sie die Modellelemente geändert haben, aktualisieren Sie die Regeln "Reparieren", Formen und Konnektoren. Weitere Informationen finden Sie unter [Weitergabe von Änderungen und reagieren auf](../modeling/responding-to-and-propagating-changes.md).  
  
 Es ist jedoch hilfreich, einige explizite Formen in Eigenschaften ändern, die der Modellelemente unabhängig sind. Beispielsweise können Sie diese Eigenschaften ändern:  
  
-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Size%2A>– Bestimmt die Höhe und Breite der Form.</xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Size%2A>  
  
-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Location%2A>-die Position relativ zu die übergeordnete Form oder das Diagramm</xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Location%2A>  
  
-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.StyleSet%2A>-die Menge der Stifte und Pinsel zum Zeichnen der Form oder der Connector</xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.StyleSet%2A>  
  
-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Hide%2A>-die Form unsichtbar</xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Hide%2A>  
  
-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Show%2A>– macht die Form sichtbar, nachdem ein`Hide()`</xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Show%2A>  
  
###  <a name="a-namemergea-creating-an-element-and-its-shape"></a><a name="merge"></a>Erstellen ein Element und seine Form  
 Wenn Sie ein Element erstellen und in die Struktur einbettender Beziehungen verknüpfen, wird eine Form automatisch erstellt und zugeordnet. Dies erfolgt durch die "Korrektur" Regeln, die am Ende der Transaktion ausgeführt. Allerdings die Form wird angezeigt, in einem Verzeichnis automatisch zugewiesen, und seine Form, Farbe und andere Funktionen über Standardwerte verfügen. Um zu steuern, wie das Shape erstellt wird, können Sie die Merge-Funktion verwenden. Sie müssen zuerst die Elemente, die Sie in eine ElementGroup hinzufügen möchten, und die Gruppe in das Diagramm zusammenführen.  
  
 Diese Methode:  
  
-   Legt den Namen fest, wenn Sie eine Eigenschaft als Elementname zugeordnet haben.  
  
-   Berücksichtigt alle Direktiven, die Sie in der DSL-Definition angegeben.  
  
 Dieses Beispiel erstellt eine Form an der Position des Mauszeigers, wenn der Benutzer im Diagramm doppelklickt. In der DSL-Definition für dieses Beispiel die `FillColor` -Eigenschaft des `ExampleShape` verfügbar gemacht wurde.  
  
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
  
 Sie können auch die Farbe und andere verfügbar gemachten Eigenschaften des Connectors, die mit dieser Methode festlegen.  
  
### <a name="use-transactions"></a>Verwenden von Transaktionen  
 Formen, Konnektoren und Diagrammen sind Untertypen von <xref:Microsoft.VisualStudio.Modeling.ModelElement>und im Speicher live.</xref:Microsoft.VisualStudio.Modeling.ModelElement> Sie müssen daher diese nur innerhalb einer Transaktion ändern. Weitere Informationen finden Sie unter [Gewusst wie: Verwenden von Transaktionen zum Aktualisieren des Modells](../modeling/how-to-use-transactions-to-update-the-model.md).  
  
##  <a name="a-namedocdataa-document-view-and-document-data"></a><a name="docdata"></a>Ansicht des Dokuments und Dokumentdaten  
 ![Klassendiagramm für Standarddiagrammtypen](../modeling/media/dsldiagramsanddocs.png "DSLDiagramsandDocs")  
  
## <a name="store-partitions"></a>Partitionen speichern  
 Wenn ein Modell geladen wird, wird im zugehörige Diagramm zur gleichen Zeit geladen. In der Regel das Modell in Store.DefaultPartition geladen wird, und der Inhalt des Diagramms in einer anderen Partition geladen wird. In der Regel wird der Inhalt der einzelnen Partitionen geladen und in einer separaten Datei gespeichert.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Modeling.ModelElement></xref:Microsoft.VisualStudio.Modeling.ModelElement>   
 [Überprüfung in einer domänenspezifischen Sprache](../modeling/validation-in-a-domain-specific-language.md)   
 [Generieren von Code für eine domänenspezifische Sprache](../modeling/generating-code-from-a-domain-specific-language.md)   
 [Gewusst wie: Verwenden von Transaktionen zum Aktualisieren des Modells](../modeling/how-to-use-transactions-to-update-the-model.md)   
 [Integrieren von Modellen mit Visual Studio-Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)   
 [Reagieren auf und Propagieren von Änderungen](../modeling/responding-to-and-propagating-changes.md)

