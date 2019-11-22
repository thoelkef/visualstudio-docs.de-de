---
title: 'UML Component Diagrams: Guidelines | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML diagrams, component
- diagrams - modeling, component
- diagrams - modeling, UML component
- UML, component diagrams
- component diagrams
ms.assetid: 6c1bdd60-369e-477e-83ed-7f6fe75c9f0b
caps.latest.revision: 37
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 99f2b67d264edcaab5272d0224d4450ee2e8a6f6
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297162"
---
# <a name="uml-component-diagrams-guidelines"></a>UML-Komponentendiagramme: Richtlinien
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio, you can draw a *component diagram* to show the structure a software system. For a video demonstration, see [Designing the Physical Structure by using Component Diagrams](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-6-designing-a-projects-physical-structure).

 Welche Versionen von Visual Studio dieses Features unterstützen, erfahren Sie unter [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 To create a UML component diagram, on the **Architecture** menu, click **New UML or Layer Diagram**.

 Eine Komponente ist eine modulare Einheit, die innerhalb ihrer Umgebung austauschbar ist. Its internals are hidden, but it has one or more well-defined *provided interfaces* through which its functions can be accessed. A component can also have *required interfaces*. Eine erforderliche Schnittstelle definiert, welche Funktionen oder Dienste von anderen Komponenten benötigt werden. Indem die angebotenen und erforderlichen Schnittstellen mehrerer Komponenten verknüpft werden, kann eine größere Komponente erstellt werden. Ein vollständiges Softwaresystem kann auch als Komponente verstanden werden.

 Das Zeichnen von Komponentendiagrammen hat mehrere Vorteile:

- Wenn sich das Entwicklungsteam auf die Hauptblöcke eines Entwurfs konzentriert, kann es ein besseres Verständnis des vorhandenen Entwurfs entwickeln und einen entsprechenden neuen Entwurf erstellen.

- Indem Sie sich Ihr System als Auflistung von Komponenten mit klar definierten angebotenen und erforderlichen Schnittstellen vorstellen, optimieren Sie die Abgrenzung zwischen den Komponenten. Dadurch ist der Entwurf einfacher zu verstehen, und der Entwurf kann bei sich ändernden Anforderungen auch einfacher angepasst werden.

  Sie können ein Komponentendiagramm verwenden, um den Entwurf unabhängig von der verwendeten Sprache oder Plattform darzustellen.

## <a name="OtherDiagrams"></a> Relationship to Other Diagrams
 Sie können ein Komponentendiagramm in Verbindung mit anderen Diagrammen verwenden.

|Anderes Diagramm|Unterstützt Sie beim Diskutieren und Kommunizieren dieser Aspekte des Entwurfs.|
|-------------------|--------------------------------------------------------------------|
|UML-Sequenzdiagramm|-   Interactions between a system's components<br />-   Interactions and between the parts inside a component.<br /><br /> For more information, see [UML Sequence Diagrams: Guidelines](../modeling/uml-sequence-diagrams-guidelines.md).|
|UML-Klassendiagramm|-   The interfaces of a component. Mit dem Klassendiagramm können Sie die Methoden der Schnittstelle detailliert angeben.<br />-   The data sent in parameters across the components' interfaces.<br /><br /> For more information, see [UML Class Diagrams: Guidelines](../modeling/uml-class-diagrams-guidelines.md).|
|Aktivitätsdiagramme|-   The internal processing performed by a component in response to incoming messages.<br /><br /> For more information, see [UML Activity Diagrams: Guidelines](../modeling/uml-activity-diagrams-guidelines.md).|
|Ebenendiagramme|-   Logical architectural tiers for your components.<br /><br /> For more information, see [Layer Diagrams: Reference](../modeling/layer-diagrams-reference.md).|

## <a name="Basics"></a> Basic Steps for Drawing Component Diagrams
 For reference information about the elements on component diagrams, see [UML Component Diagrams: Reference](../modeling/uml-component-diagrams-reference.md).

 For more information about how to use component diagrams in the process of design, see [Model your app's architecture](../modeling/model-your-app-s-architecture.md).

> [!NOTE]
> Detailed steps for creating any of the modeling diagrams are described in [Edit UML models and diagrams](../modeling/edit-uml-models-and-diagrams.md).

#### <a name="to-create-a-component-diagram"></a>So erstellen Sie ein Komponentendiagramm

1. On the **Architecture** menu, click **New UML or Layer Diagram**.

2. Under **Templates**, click **UML Component Diagram**.

3. Benennen Sie das Diagramm.

4. In **Add to Modeling Project**, select an existing modeling project in your solution, or **Create a New Modeling Project**, and then click **OK**..

     A new component diagram appears with the UML **Component Diagram** toolbox. Die Toolbox enthält die erforderlichen Elemente und Beziehungen.

### <a name="drawing-components"></a>Zeichnen von Komponenten
 ![Components with interfaces](../modeling/media/uml-compdrawing.png "UML_CompDrawing")

 Create a *component* (1) for each major functional unit in your system or application.

 Beispiele hierfür sind eine Anwendung, ein Hardwaregerät, ein Webdienst, eine .NET-Assembly, eine Programmklasse oder eine Gruppe von Klassen oder ein beliebiges anderes Hauptsegment eines Programms.

##### <a name="to-create-components"></a>So erstellen Sie Komponenten

1. Click **Component** in the toolbox, and then click a blank part of the diagram.

     \- oder -

     Kopieren Sie eine vorhandene Komponente, und fügen Sie diese ein.

    1. Find an existing component in a diagram or in **UML Model Explorer**.

    2. Right-click the component and then click **Copy**.

    3. Öffnen Sie das Diagramm, in dem die kopierte Komponente angezeigt werden soll.

    4. Right-click a blank part of the diagram and then click **Paste**.

         Eine Kopie der Komponente wird unter einem neuen Namen angezeigt.

2. Klicken Sie auf den Namen der Komponente, um ihn zu ändern.

3. Klicken Sie auf das Chevron (5), wenn Sie nur den Header der Komponente anzeigen möchten.

### <a name="showing-the-ports-of-a-component"></a>Anzeigen der Ports einer Komponente
 A *port* (2, 3) represents a group of messages or operation calls that pass either into or out of a component. Die Gruppe wird von einer Schnittstelle beschrieben, die den Typ des Ports definiert. Ein Port kann entweder eine Schnittstelle anbieten oder eine Schnittstelle erfordern.

 A port with a *provided interface* (2) supplies operations that are implemented by the component, and that can be used by other components.

 Beispiele sind eine Benutzeroberfläche, ein Webdienst, eine .NET-Schnittstelle oder eine Auflistung von Funktionen in einer beliebigen Programmiersprache.

 A port with a *required interface* (3) represents a component's requirement for a group of operations or services to be provided by other components or external systems.

 Ein Webbrowser erfordert z. B. Webserver, und ein Anwendungs-Add-In erfordert die Dienste einer Anwendung.

 Eine Komponente kann über eine beliebige Anzahl von Ports verfügen.

##### <a name="to-add-ports-to-a-component"></a>So fügen Sie einer Komponente Ports hinzu

1. In the toolbox, click **Provided Interface** or **Required Interface**.

2. Klicken Sie auf die Komponente, der Sie Ports hinzufügen möchten.

    Ein Port wird an der Begrenzung der Komponente angezeigt.

    Eine neue Schnittstelle wird als Typ des Ports erstellt. This interface appears in **UML Model Explorer**.

3. Ziehen Sie den Port mit der Maus entlang der Komponentenbegrenzung, um ihn wie gewünscht zu platzieren.

4. Ziehen Sie die Bezeichnung des Ports, um die Position anzupassen.

5. Klicken Sie auf die Bezeichnung, um sie zu ändern. Die Bezeichnung zeigt den Namen der Schnittstelle an. Wenn Sie diesen ändern, ändern Sie den Namen der Schnittstelle.

   Wenn Sie die Attribute und Vorgänge der Schnittstelle aufführen möchten, fügen Sie sie der Schnittstelle im UML-Modell-Explorer hinzu. Alternativ können Sie die Schnittstelle aus dem UML-Modell-Explorer in ein Klassendiagramm ziehen und dort die Vorgänge und Attribute hinzufügen.

### <a name="linking-between-components"></a>Erstellen von Verknüpfungen zwischen Komponenten
 Verwenden Sie eine Abhängigkeit (4), um anzuzeigen, dass die Anforderung einer Komponente von den Vorgängen oder Diensten erfüllt werden kann, die von einer anderen Komponente bereitgestellt werden.

##### <a name="to-show-that-a-provided-interface-can-satisfy-a-required-interface"></a>So zeigen Sie an, dass eine angebotene Schnittstelle die Anforderungen einer erforderlichen Schnittstelle erfüllen kann

1. In the toolbox, click **Dependency**.

2. Klicken Sie in einer Komponente auf den Port mit der erforderlichen Schnittstelle und dann in einer anderen Komponente auf den Port mit der angebotenen Schnittstelle.

   Sie sollten es vermeiden, Abhängigkeitsschleifen zu entwerfen, bei denen alle Komponenten einer Gruppe von allen anderen Komponenten abhängig sind.

##### <a name="to-add-a-port-for-an-existing-interface-to-a-component"></a>So fügen Sie einer Komponente einen Port für eine vorhandene Schnittstelle hinzu

- Find the interface in **UML Model Explorer** and then drag it from there onto the component.

     - oder -

- Kopieren Sie einen Verweis auf eine Schnittstelle aus einem Diagramm, und fügen Sie ihn ein.

    1. On a class diagram or a component diagram, right-click the interface and then click **Copy**.

    2. On the component diagram, right-click the component, and then click **Paste Reference**.

         Eine angebotene Schnittstelle wird auf der Komponente angezeigt. Daneben wird ein Aktionstag angezeigt.

        > [!NOTE]
        > If you use **Paste** instead of **Paste Reference**, a new interface that has a new name will be created.

    3. If you wanted to create a required interface, click the Action tag and then click **Convert to Required Interface**.

## <a name="Parts"></a> Showing the Internal Parts of a Component
 ![Component diagram showing internal parts](../modeling/media/uml-compshowing.png "UML_CompShowing")

 Sie können Teile (3) in einer Komponente (1) platzieren, um anzuzeigen, wie diese aus kleineren Komponenten zusammengesetzt ist, die miteinander interagieren.

 Das Diagramm in der Abbildung gibt an, dass jede Instanz vom Typ "Dinner Now Web Service" eine Instanz von "Customer Server" und eine Instanz von "Kitchen Server" enthält.

 Ein Teil ist eine Eigenschaft seiner übergeordneten Komponente, so wie ein Attribut einer normalen Klasse angehört. Ein Teil hat seinen eigenen Typ, der normalerweise auch eine Komponente ist. Die Bezeichnung des Teils hat die gleiche Form wie ein normales Attribut:

 `+ partName : TypeName`

 In der übergeordneten Komponente zeigt jeder Teil die angebotenen und erforderlichen Schnittstellen an, die für seinen Typ (4, 5) definiert sind. Die Vorgänge und Dienste, die für einen Teil erforderlich sind, können von einem anderen Teil bereitgestellt werden. You can use **Part Assembly** connectors to show how parts are connected with one another (6).

 Sie können auch anzeigen, dass eine Schnittstelle der übergeordneten Komponente von einem ihrer Teile angeboten wird oder dafür erforderlich ist. You can connect a port of the parent to a port of an internal part using a **Delegation** relation (9). Die zwei Ports müssen vom gleichen Typ sein (angeboten oder erforderlich), und ihre Schnittstellentypen müssen kompatibel sein.

 Sie können einen neuen Teil entweder mit einem neuen Typ oder aus einem vorhandenen Typ erstellen.

#### <a name="to-add-parts-to-a-component"></a>So fügen Sie einer Komponente Teile hinzu

1. Erstellen Sie einen Teil für jede Hauptfunktionseinheit, die Bestandteil der übergeordneten Komponente ist.

    1. Click **Component** in the toolbox, and then click inside the parent component (1).

         Ein neuer Teil (3) wird in der übergeordneten Komponente angezeigt.

         A new component is created in **UML Model Explorer**. Dies ist der Typ des neuen Teils.

         \- oder -

         Ziehen Sie eine vorhandene Komponente aus dem UML-Modell-Explorer auf die übergeordnete Komponente.

         Ein neuer Teil (3) wird in der übergeordneten Komponente angezeigt. Der Typ ist die Komponente, die Sie aus dem UML-Modell-Explorer gezogen haben.

         \- oder -

         Right-click a component, either in a diagram or in UML Model Explorer, and then click **Copy**.

         Right-click on the parent component, and then click **Paste Reference**.

         Ein neuer Teil (3) wird in der übergeordneten Komponente angezeigt. Sein Typ ist die Komponente, die Sie kopiert haben.

    2. Klicken Sie auf den Namen des neuen Teils, um ihn zu ändern. Seinen Typ können Sie nicht ändern.

    3. Sie können dem neuen Teil angebotene und erforderliche Schnittstellen (4, 5) hinzufügen. Click the **Provided Interface** or **Required Interface** tool, and then click in the part.

         \- oder -

         Drag an existing interface from **UML Model Explorer** onto the part.

         Die Schnittstellen werden dem Typ des Teils hinzugefügt und auf dem Teil selbst angezeigt. Die übergeordnete Komponente passt bei Bedarf die Größe an.

2. Verbinden Sie die Teile miteinander.

    - Use the **Dependency** tool to connect the ports of different parts (6).

3. Verbinden Sie die Teile mit den Ports der übergeordneten Komponente:

    1. Erstellen Sie auf der übergeordneten Komponente einen oder mehrere Ports (7). Click **Required Interface** or **Provided Interface** on the toolbox, and then click the parent component.

    2. Delegieren (9) Sie den Port an einen oder mehrere Teile. Click the **Delegation** tool, then a port on the parent component, and then a port on a part. Sie können Ports, die Schnittstellen entweder anbieten oder erfordern, auf dieselbe Weise verbinden.

### <a name="showing-the-parts-of-a-part"></a>Anzeigen der Teile eines Teils
 Nachdem Sie eine Komponente in ihre Teile zerlegt haben, können Sie jeden Teiltyp in seine eigenen internen Bestandteile zerlegen.

 Es ist am einfachsten, jede Ebene der Zerlegung in einem separaten Komponentendiagramm durchzuführen. Sie müssen zuerst den Typ des Teils ermitteln. In der Abbildung hat einer der Teile z. B. den Namen `DNCustomerServer`, und der Typ ist eine Komponente mit dem Namen `CustomerServer`. Sie finden diesen Typ im UML-Modell-Explorer und können ihn in ein anderes Diagramm einfügen. Dann können Sie seine eigenen internen Teile erstellen.

##### <a name="to-place-a-parts-type-on-a-diagram"></a>So platzieren Sie den Typ eines Teils in einem Diagramm

1. Ermitteln Sie den vollqualifizierten Namen für den Typ des Teils.

     Right-click the part and then click **Properties**.

     The type name appears in the **Type** field of the Properties window.

2. Locate the part's type in **UML Model Explorer**.

     Click **View**, point to **Other Windows**, and then click **UML Model Explorer**.

     Erweitern Sie das Projekt und bei Bedarf alle Pakete, zu denen der Typ gehört.

     The type will be listed as a **Component**.

     Sie können seinen Namen hier ändern, wenn Sie dies möchten.

3. Öffnen oder erstellen Sie ein weiteres Komponentendiagramm.

4. Führen Sie mit der Maus eine Ziehbewegung aus dem Typ im UML-Modell-Explorer auf das Diagramm durch.

     Eine Ansicht des Typs wird als Komponente im Diagramm angezeigt.

     Sie verfügt über die gleichen Schnittstellen, die Sie für den Teil definiert haben.

     Sie können darin jetzt Teile hinzufügen.

## <a name="Designing"></a> Designing the Component

### <a name="describing-how-the-parts-collaborate"></a>Beschreiben der Zusammenarbeit der Teile
 Sie können ein Sequenzdiagramm zeichnen, um darzustellen, wie die Teile als Reaktion auf eine Meldung zusammenarbeiten, die bei der übergeordneten Komponente eingeht.

 Sie können diese Diagramme verwenden, um eine vorhandene Komponente zu erläutern und um eine neue Komponente zu entwerfen.

 Wenn Sie den Entwurf der Komponente noch nicht abgeschlossen haben, können Sie Sequenzdiagramme zeichnen, bevor Sie sich entschieden haben, welche Teile darin enthalten sein sollen. Sie können Sequenzdiagramme auch verwenden, um mit verschiedenen Teilen, erforderlichen Schnittstellen und Meldungssequenzen zu experimentieren. Zeichnen Sie Sequenzdiagramme für die häufigsten und wichtigsten eingehenden Meldungen. Sie können in der Komponente dann Teile erstellen, die den Lebenslinien entsprechen, für die Sie sich entschieden haben.

 Verwenden Sie die Sequenzdiagramme, um zu bewerten, wie die Arbeitsschritte des Systems auf die verschiedenen Komponenten verteilt sind.

- Wenn ein Teil zu viele Schritte ausführen muss, ist die Anwendung möglicherweise schwieriger zu aktualisieren, als wenn die Arbeitsschritte gleichmäßig verteilt werden.

- Falls die Arbeitsschritte sehr stark verteilt sind und viele Interaktionen stattfinden, kann dies die Leistung und die Verständlichkeit des Systems beeinträchtigen.

  ![Sequence diagram showing collaborating parts](../modeling/media/uml-compdescparts.png "UML_CompDescParts")

##### <a name="to-draw-a-sequence-diagram-that-shows-collaboration-between-parts"></a>So zeichnen Sie ein Sequenzdiagramm, das die Zusammenarbeit zwischen Teilen veranschaulicht

1. Erstellen Sie ein neues Sequenzdiagramm.

     For more information, see [UML Sequence Diagrams: Guidelines](../modeling/uml-sequence-diagrams-guidelines.md).

2. Erstellen Sie eine Lebenslinie für eine externe Komponente, einen Benutzer, ein Gerät oder einen anderen Akteur (1), der Meldungen an diese Komponente sendet.

     You can set the **Actor** property of this lifeline to true, to indicate that it is external to the component under consideration. Über der Lebenslinie wird ein Strichmännchen angezeigt.

3. Erstellen Sie eine Lebenslinie für die angebotene Schnittstelle (2) dieser Komponente, an die der ausgewählte Akteur Meldungen sendet.

4. Erstellen Sie eine Lebenslinie für jeden Teil (3) der Komponente.

5. Erstellen Sie eine Lebenslinie für jede erforderliche Schnittstelle (4) der Komponente.

6. Ziehen Sie Meldungen aus dem externen Akteur (5). Veranschaulichen Sie, wie die Meldung an die Teile übergeben wird und wie diese zusammenarbeiten, um auf die Meldung zu reagieren.

7. Zeigen Sie an eine erforderliche Schnittstelle (6) gesendete Meldungen an, wo dies notwendig ist. Zeigen Sie keine Details der Ausführung der Meldung an.

### <a name="is-the-component-more-than-its-parts"></a>Ist die Komponente mehr als die Summe ihrer Teile?
 In einigen Fällen ist eine Komponente lediglich ein Name für eine Auflistung von Teilen. Die gesamte Arbeit wird von den Teilen erledigt, und zur Laufzeit gibt es keinen Code oder anderes Artefakt, das die Komponente darstellt.

 You can indicate this in the model by setting the **Is Indirectly Instantiated** property of the component. In diesem Fall sollten sich alle Schnittstellen der Komponente auf Ports befinden und über Delegierungen zu internen Teilen verfügen.

### <a name="describing-the-process-inside-each-part"></a>Beschreiben des Prozesses in den einzelnen Teilen
 Mithilfe von Aktivitätsdiagrammen können Sie anzeigen, wie eine Komponente die einzelnen eingehenden Meldungen verarbeitet. For more information, see [UML Activity Diagrams: Guidelines](../modeling/uml-activity-diagrams-guidelines.md).

 ![Activity diagram with data buffer](../modeling/media/uml-compdescribingproc.png "UML_CompDescribingProc")

 Verwenden Sie "Ereignisaktion akzeptieren" (1), um anzuzeigen, dass eine eingehende Meldung einen neuen Thread startet.

 Verwenden Sie Objektknoten und Eingabe-/Ausgabepins, um den Informationsfluss und die Speicherorte der Informationen anzuzeigen. Im Beispiel wird ein Objektknoten (2) verwendet, um Elemente anzuzeigen, die zwischen zwei Threads gepuffert werden.

### <a name="defining-data-and-classes"></a>Definieren von Daten und Klassen
 Mit einem UML-Klassendiagramm können Sie den ausführlichen Inhalt von folgenden Elementen beschreiben:

- Schnittstellen der Komponenten Wenn Sie eine erforderliche Komponente hinzufügen oder einen Port für eine Komponente bereitstellen, wird eine Schnittstelle im UML-Modell-Explorer angezeigt. Sie können dieses in ein UML-Klassendiagramm ziehen oder kopieren, um die Attribute und Vorgänge sowie die Beziehungen zu anderen Schnittstellen anzuzeigen.

- In den Schnittstellen über Vorgangsparameter übergebene Daten

- In den Komponenten gespeicherte Daten, wie z. B. in den Objektflüssen von Aktivitätsdiagrammen dargestellt

### <a name="general-dependencies-between-components"></a>Allgemeine Abhängigkeiten zwischen Komponenten
 Mit einem Komponentendiagramm können Sie auch nur die Hauptbestandteile des Entwurfs und deren Abhängigkeiten anzeigen.

 ![A dependency between components](../modeling/media/uml-compdepend.png "UML_CompDepend")

 Use the **Dependency** tool to draw a dependency. Dies gibt an, dass der Entwurf einer Komponente von einer anderen Komponente abhängt.

 Es gibt folgende typische Arten von Abhängigkeit:

- Eine Komponente ruft Code in einer anderen Komponente auf.

- Eine Komponente instanziiert eine Klasse, die innerhalb einer anderen Klasse definiert ist.

- Eine Komponente verwendet Informationen, die von einer anderen Komponente erstellt wurden.

  Sie können den Namen des Abhängigkeitspfeils verwenden, um eine bestimmte Art der Verwendung anzugeben. To set the name, right-click the arrow, then click **Properties**, and set the **Name** field in the properties window.

## <a name="see-also"></a>Siehe auch
 [Edit UML models and diagrams](../modeling/edit-uml-models-and-diagrams.md) [UML Component Diagrams: Reference](../modeling/uml-component-diagrams-reference.md) [UML Sequence Diagrams: Reference](../modeling/uml-sequence-diagrams-reference.md) [UML Use Case Diagrams: Reference](../modeling/uml-use-case-diagrams-reference.md) [UML Class Diagrams: Reference](../modeling/uml-class-diagrams-reference.md) [UML Component Diagrams: Reference](../modeling/uml-component-diagrams-reference.md) [Video: Designing the Physical Structure by using Component Diagrams](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-6-designing-a-projects-physical-structure)
