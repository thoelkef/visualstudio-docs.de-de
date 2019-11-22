---
title: 'UML Activity Diagrams: Guidelines | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML diagrams, activity
- diagrams - modeling, activity
- diagrams - modeling, UML activity
- activity diagrams
- UML, activity diagrams
ms.assetid: fe5dbe96-79ab-483a-b9bc-44d0d1d3efc2
caps.latest.revision: 50
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 692859008891439e4af3d751306bfd3ee6d351e8
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298984"
---
# <a name="uml-activity-diagrams-guidelines"></a>UML-Aktivitätsdiagramme: Richtlinien
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio können Sie ein Aktivitätsdiagramm zeichnen, um einen Geschäftsprozess oder einen Softwarealgorithmus als Arbeitsfluss zu beschreiben, der eine Reihe von Aktionen durchläuft. Diese Aktionen können von Personen, Softwarekomponenten oder Geräten ausgeführt werden. For a video demonstration, see: [Capture Business Workflows by using Activity Diagrams](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-4-capture-business-workflows).

 Welche Versionen von Visual Studio dieses Features unterstützen, erfahren Sie unter [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 To create a UML activity diagram, on the **Architecture** menu, click **New UML or Layer Diagram**.

 Sie können ein Aktivitätsdiagramm für viele Zwecke verwenden:

- Beschreiben eines Geschäftsprozesses oder eines Arbeitsflusses zwischen Benutzern und dem System. For more information, see [Model user requirements](../modeling/model-user-requirements.md).

- Beschreiben der Schritte, die in einem Anwendungsfall ausgeführt werden. For more information, see [UML Use Case Diagrams: Guidelines](../modeling/uml-use-case-diagrams-guidelines.md).

- Beschreiben einer Methode, einer Funktion oder eines Vorgangs in der Software. For more information, see [Model your app's architecture](../modeling/model-your-app-s-architecture.md).

  Prozesse lassen sich durch das Zeichnen eines Aktivitätsdiagramms optimieren. Wenn sich das Diagramm eines vorhandenen Prozesses als sehr komplex erweist, können Sie überlegen, wie der Prozess vereinfacht werden kann.

  For reference information about the elements on activity diagrams, see [UML Activity Diagrams: Reference](../modeling/uml-activity-diagrams-reference.md).

## <a name="Relationships"></a> Relationship to Other Diagrams
 Wenn Sie ein Aktivitätsdiagramm zeichnen, um einen Geschäftsprozess oder die Art und Weise der Verwendung des Systems durch Benutzer zu beschreiben, können Sie ein Anwendungsfalldiagramm zeichnen, das eine andere Ansicht der gleichen Informationen liefert. Im Anwendungsfalldiagramm zeichnen Sie Aktionen als Anwendungsfälle. Weisen Sie den Anwendungsfällen den gleichen Namen zu wie den entsprechenden Aktionen. Die Anwendungsfallansicht bietet Ihnen folgende Vorteile:

- Sie können in einem Diagramm mithilfe einer Includes-Beziehung darstellen, wie größere Aktionen/Anwendungsfälle aus kleineren Aktionen/Anwendungsfällen zusammengesetzt sind.

- Sie können jede Aktion bzw. jeden Anwendungsfall explizit mit den Benutzern oder externen Systemen verknüpfen, die an der Ausführung beteiligt sind.

- Sie können Begrenzungen um die vom System unterstützten Aktionen/Anwendungsfälle oder jede Hauptkomponente zeichnen.

  Sie können auch ein Aktivitätsdiagramm zeichnen, um den Detailentwurf eines Softwarevorgangs zu beschreiben.

  In einem Aktivitätsdiagramm können Sie den Fluss der zwischen Aktionen übergebenen Daten darstellen. See the section on [Describing Data Flow](#DataFlows). Ein Aktivitätsdiagramm beschreibt jedoch nicht die Struktur der Daten. Zu diesem Zweck können Sie ein UML-Klassendiagramm zeichnen. For information see [UML Class Diagrams: Guidelines](../modeling/uml-class-diagrams-guidelines.md).

## <a name="BasicSteps"></a> Basic Steps for Drawing Activity Diagrams
 Detailed steps for creating any of the modeling diagrams are described in [Edit UML models and diagrams](../modeling/edit-uml-models-and-diagrams.md).

#### <a name="to-draw-an-activity-diagram"></a>So zeichnen Sie ein Aktivitätsdiagramm

1. On the **Architecture** menu, click **New UML or Layer Diagram**.

2. Under **Templates**, click **UML Activity Diagram**.

3. Benennen Sie das Diagramm.

4. In **Add to Modeling Project**, select an existing modeling project in your solution, or **Create a New Modeling Project**.

#### <a name="to-draw-elements-on-an-activity-diagram"></a>So zeichnen Sie Elemente in einem Aktivitätsdiagramm

1. Ziehen Sie Elemente aus der Toolbox in das Diagramm.

     Fügen Sie zunächst die Hauptaktivitäten in das Diagramm ein, verbinden Sie sie, und nehmen Sie dann letzte Änderungen vor, indem Sie z. B. den Start- und Endknoten hinzufügen.

    > [!NOTE]
    > Sie können keine vorhandenen Elemente aus dem UML-Modell-Explorer in das Diagramm ziehen.

2. Gehen Sie folgendermaßen vor, um die Elemente zu verbinden:

    1. In the **Activity Diagram** toolbox, click **Connector**.

    2. Klicken Sie im Diagramm auf das Quellelement.

    3. Klicken Sie auf das Zielelement.

        > [!NOTE]
        > Um ein Tool mehrmals zu verwenden, doppelklicken Sie in der Toolbox auf das Tool.

#### <a name="to-move-an-activity-to-another-package"></a>So verschieben Sie eine Aktivität in ein anderes Paket

- In **UML Model Explorer**, drag the activity into a package.

     \- oder -

- In **UML Model Explorer**, right-click the activity and click **Cut**. Then right-click the package and click **Paste**.

    > [!NOTE]
    > Die Aktivität wird erst dann im UML-Modell-Explorer angezeigt, wenn Sie dem Diagramm das erste Element hinzufügen.

## <a name="SimpleControlFlow"></a> Describing Control Flow
 Ein Aktivitätsdiagramm beschreibt einen Geschäftsprozess oder einen Softwarealgorithmus als eine Reihe von Aktionen. Konnektorpfeile stellen dar, wie die Kontrolle nacheinander von einer Aktion an die nächste übergeben wird. Normalerweise kann eine Aktion erst gestartet werden, nachdem die vorherige Aktion abgeschlossen wurde.

 In der folgenden Beispielabbildung wird gezeigt, wie Sie eine Sequenz von Aktionen mit Aktionen, Konnektoren, Verzweigungen und Schleifen darstellen können. In den folgenden Abschnitten wird jedes Element ausführlicher erläutert.

 ![A simple activity diagram](../modeling/media/uml-actguidectrl.png "UML_ActGuideCtrl")

 Activity diagrams use **Actions** and **Connectors** to describe your system or application as a series of actions with the control flowing sequentially from one action to the next.

- Create an **Action** (1) for each major task that is performed by a user, the system, or both in collaboration.

  > [!NOTE]
  > Versuchen Sie, den Prozess oder Algorithmus mit nur einigen wenigen Aktionen zu beschreiben. You can use **Call Behavior Actions** to define each action in more detail in a separate diagram, as described in [Describing Sub-activities with Call Behavior Actions](#Subactivities).

- Stellen Sie sicher, dass der Titel jeder Aktion das standardmäßige Resultat der Aktion eindeutig angibt.

- Link the actions in sequence with **Connectors** (2).

- Jede Aktion endet, bevor die nächste Aktion in der Ablaufsteuerung beginnt. If you want to describe actions that overlap, use a **Fork Node** as described in the section [Concurrent Flows](#Concurrent).

  Das Diagramm beschreibt zwar die Aktionsfolge, jedoch nicht, wie die Aktionen ausgeführt werden, oder wie die Kontrolle von einer Aktion an die nächste übergeben wird. Wenn Sie mithilfe des Diagramms einen Geschäftsprozess darstellen, kann die Kontrolle z. B. übergeben werden, wenn eine Person eine E-Mail-Nachricht an eine andere Person sendet. Wenn Sie mithilfe des Diagramms einen Softwareentwurf darstellen, wird die Kontrolle möglicherweise durch den normalen Ausführungsfluss von einer Anweisung an die nächste übergeben.

### <a name="describing-decisions-and-loops"></a>Beschreiben von Entscheidungen und Schleifen

- Use a **Decision Node** (3) to indicate a point where the outcome of a decision dictates the next step. Sie können beliebig viele ausgehende Pfade zeichnen.

- Wenn Sie mithilfe des Aktivitätsdiagramms einen Teil einer Anwendung definieren, sollten Sie die Wächter (4) definieren, um eindeutig anzugeben, unter welchen Bedingungen die einzelnen Pfade verwendet werden sollten. Right-click the connector, click **Properties**, and in the **Properties** window, type a value for the **Guard** field.

- Es ist nicht immer erforderlich, die Wächter zu definieren. Wenn Sie z. B. mithilfe des Aktivitätsdiagramms einen Geschäftsprozess oder ein Interaktionsprotokoll beschreiben, definiert eine Verzweigung den Bereich von Optionen, die für den Benutzer oder die interagierenden Komponenten verfügbar sind.

- Use a **Merge Node** (5) to bring together two or more alternative flows that branched at a **Decision Node**.

    > [!NOTE]
    > You should use a **Merge Node** to bring together alternative flows, instead of bringing the flows together at an action. In the example, it would not be correct to connect from the decision node directly back to **Choose Menu Item**. Der Grund hierfür ist, dass eine Aktion erst gestartet wird, wenn alle Kontrollthreads an allen Eingangskonnektoren angekommen sind. Daher sollten Sie nur parallele Flüsse an einer Aktion zusammenführen. For more information, see [Concurrent Flows](#Concurrent).

- Beschreiben Sie Schleifen mithilfe von Verzweigungen, wie im Beispiel gezeigt.

    > [!NOTE]
    > Versuchen Sie, Schleifen wie in Programmcode in einer sinnvollen Struktur zu schachteln. Wenn Sie einen vorhandenen Geschäftsprozess beschreiben, lassen sich hierdurch eventuell Verbesserungsmöglichkeiten erkennen.

### <a name="starting-the-activity"></a>Starten der Aktivität
 Es gibt zwei Möglichkeiten, Einstiegspunkte einer Aktivität anzugeben:

- **Initial Node**

     Create one **Initial Node** (6) to indicate the first action of the activity.

     Diese Methode ist besonders hilfreich, wenn Sie eine Unteraktivität beschreiben, oder wenn Sie nicht explizit angeben müssen, wodurch die Aktivität ausgelöst wird. Beispielsweise beginnt die Aktivität „Gericht bestellen“ zweifelsfrei, wenn ein Kunde hungrig wird.

- **Accept Event Node**

     Create **Accept Event Nodes**, as described in the section [Concurrent Flows](#Concurrent), to indicate the start of a thread that responds to a particular event, such as a user input. Geben Sie keinen eingehenden Fluss für den Knoten an. Wenn kein eingehender Fluss angegeben wird, bedeutet dies, dass bei jedem Eintreten des Ereignisses ein Thread gestartet wird.

     Diese Methode ist besonders hilfreich, wenn Sie eine Reaktion auf ein bestimmtes externes Ereignis beschreiben.

### <a name="ending-the-activity"></a>Beenden der Aktivität
 Use an **Activity Final Node** (7) to indicate the end of an activity.

- When a thread of control reaches an **Activity Final Node**, all the activity's concurrent actions and sub-activities terminate.

- Sie können mehrere Aktivitätsendknoten verwenden, um durch eine geringere Anzahl von Konnektoren die Übersichtlichkeit zu verbessern.

### <a name="interrupting-the-activity"></a>Unterbrechen der Aktivität
 Um zu beschreiben, wie der normale Fluss einer Aktivität unterbrochen werden kann, beispielsweise wenn sich der Benutzer entscheidet, den Vorgang abzubrechen, können Sie einen Knoten zum Akzeptieren eines Ereignisses erstellen, der auf dieses Ereignis lauscht. For more information, see the section [Concurrent Flows](#Concurrent). Erstellen Sie eine Ablaufsteuerung von diesem Knoten zu einem Aktivitätsendknoten (7).

### <a name="swimlanes"></a>Swimlanes
 Manchmal ist es sinnvoll, die Aktionen einer Aktivität in Bereiche aufzuteilen, die unterschiedlichen Objekten oder Geschäftsrollen entsprechen, die die Aktionen ausführen. These areas are conventionally arranged in columns and are called *swimlanes*.

- Use lines or rectangles from the **Simple Shapes** section of the Toolbox to draw swimlanes or other areas.

- To label each swimlane, create a comment and set its **Transparent** property to **True**.

  Einfache Formen sind kein Bestandteil des UML-Modells und werden nicht im UML-Modell-Explorer angezeigt.

## <a name="DataFlows"></a> Describing Data Flow
 Sie können die eingehenden und ausgehenden Daten einer Aktivität auf zweierlei Weise beschreiben:

- Use an **Object Node**. Dies ist die einfachste Methode, um die zwischen Aktivitäten fließenden Informationen zu beschreiben. Ein Objektknoten ist mit einer Variablen in einem Programm vergleichbar. Er stellt ein Element dar, das einen oder mehrere Werte speichert, die zwischen Aktionen übergeben werden.

- Use an **Output Pin** and an **Input Pin**. Mit dieser Methode können Sie die Ausgaben einer Aktion und die Eingaben einer anderen Aktion getrennt beschreiben. Pins sind mit Parametern in einem Programm vergleichbar. Pins stellen Ports dar, an denen Objekte in eine Aktion eintreten und eine Aktion verlassen können.

    > [!NOTE]
    > For an overview of the elements used in this section, see the Data Flows section of the topic see [UML Activity Diagrams: Reference](../modeling/uml-activity-diagrams-reference.md).

### <a name="describing-data-flow-with-object-nodes"></a>Beschreiben des Datenflusses mit Objektknoten
 Die meisten Ablaufsteuerungen übertragen Daten. Beispielsweise überträgt der Ausgabefluss der Aktion „Kunde gibt Details an“ einen Verweis auf die Lieferadresse.

 Wenn Sie diese Daten im Diagramm beschreiben möchten, können Sie einen Konnektor durch einen Objektknoten und zwei Konnektoren ersetzen, wie in der folgenden Abbildung gezeigt.

 ![Object nodes can show data passed between actions](../modeling/media/uml-actguidedata.png "UML_ActGuideData")

 Beachten Sie, dass die Rechtecke mit abgerundeten Ecken, z. B. „Waren senden“, Aktionen darstellen, bei denen eine Verarbeitung erfolgt. Die Rechtecke mit rechtwinkligen Ecken, z. B. „Lieferadresse“, stellen einen Fluss von Objekten zwischen zwei Aktionen dar.

 Weisen Sie dem Objektknoten einen Namen zu, der die Rolle des Knotens als Kanal oder Puffer der Objekte widerspiegelt, die zwischen den Aktionen übertragen werden.

 You can set the **Type** of the object node in the Properties window. Der Typ kann ein primitiver Typ wie z. B. „Integer“ oder eine Klasse, Schnittstelle oder Enumeration sein, die Sie in einem Klassendiagramm definiert haben. Sie können z. B. die Klasse „Lieferadresse“ mit den Attributen „Anschrift“, „Ort“ usw. zusammen mit einer Zuordnung zur Klasse „Kunde“ erstellen. For more information, see [UML Class Diagrams: Guidelines](../modeling/uml-class-diagrams-guidelines.md).

> [!NOTE]
> If you type the name of a type that has not yet been defined, an item will be added under **Unspecified Types** in UML Model Explorer. Wenn Sie anschließend einen Typ dieses Namens in einem Klassendiagramm definieren, setzen Sie den Typ des Objektknotens zurück, sodass er auf den neuen Typ verweist.

#### <a name="buffering-data-in-object-nodes"></a>Puffern von Daten in Objektknoten
 Ein Objektknoten kann als Puffer für mehrere Objekte fungieren. In der folgenden Abbildung zeigt die Ablaufsteuerung, dass der Benutzer die Schleife „[weitere auswählen]“ (1) mehrfach durchlaufen kann, während die vom Benutzer ausgewählten Gerichte im Objektknoten „Gewählte Gerichte“ (2) gesammelt werden. Wenn schließlich die Auswahl durch den Benutzer abgeschlossen ist, geht die Kontrolle an die Aktion „Bestellung bestätigen“ (3) über, mit der die vollständige Liste der ausgewählten Elemente aus dem Puffer „Gewählte Gerichte“ akzeptiert wird.

 ![Buffering data in object nodes](../modeling/media/uml-actguidebuffer.png "UML_ActGuideBuffer")

 Sie können angeben, wie die Elemente in einem Puffer gespeichert werden, indem Sie Eigenschaften des Objektknotens festlegen:

- Set the **Ordering** property:

  - **Unordered** to specify a random or unspecified order. (Standardeinstellung)

  - **Ordered** to specify an order according to a specific key.

  - **Fifo** to specify an order of first-in, first-out.

  - **Lifo** to specify an order of last-in, first-out.

- Set the **Upper Bound** property to specify the maximum number of objects that can be contained in the buffer. Der Standardwert ist *. Dies bedeutet, dass keine Begrenzung definiert ist.

### <a name="describing-data-flow-with-input-and-output-pins"></a>Beschreiben des Datenflusses mit Eingabe- und Ausgabepins
 Use an **Output Pin** and an **Input Pin** to separately describe the outputs from one action and the inputs to another.

 ![Input and output pins are action parameters](../modeling/media/uml-actguidepins.png "UML_ActGuidePins")

 To create a pin, click **Input Pin** or **Output Pin** on the toolbox and then click an action. Anschließend können Sie den Pin im Umkreis der Aktion verschieben und seinen Namen ändern. You can create input and output pins on any kind of action, including **Call Behavior Actions**, **Call Operation Actions**, **Send Signal Actions**, and **Accept Event Actions**.

 Ein Konnektor zwischen zwei Pins stellt ebenso wie die Flüsse zu und von einem Objektknoten einen Objektfluss dar.

 Weisen Sie jedem Pin einen Namen zu, der die Rolle der von ihm erzeugten bzw. akzeptierten Objekte angibt, z. B. einen Parameternamen.

 You can set the type of objects transmitted in the **Type** property. Dies muss ein Typ sein, den Sie in einem UML-Klassendiagramm erstellt haben.

 Die Objekte, die zwischen verbundenen Pins übertragen werden, müssen auf irgendeine Weise kompatibel sein. Beispielsweise können sie kompatibel sein, weil der Typ der vom Ausgabepin erzeugten Objekte vom Typ des Eingabepins abgeleitet wird.

 Alternativ können Sie angeben, dass der Objektfluss eine Transformation einschließt, mit der Daten vom Typ des Ausgabepins in den Typ des Eingabepins (oder umgekehrt) konvertiert werden. Die häufigste Transformation dieser Art extrahiert einfach den entsprechenden Teil aus einem größeren Typ. Im Beispiel in der Abbildung wird eine Transformation vorausgesetzt, die die Lieferadresse aus den Bestellungsdetails extrahiert.

## <a name="Details"></a> Defining an Action in More Detail
 Sie können nicht nur das normalerweise zu erzielende Ergebnis einer Aktion anhand ihres Namens angeben, sondern einer Aktion mit den folgenden Methoden auch weitere Informationen hinzufügen:

- Write a more detailed description in the **Body** property. Sie können z. B. ein Fragment von Programmcode oder Pseudocode oder eine vollständige Beschreibung der erzielten Ergebnisse schreiben.

- Ersetzen Sie die Aktion durch eine Aktion zum Aufrufen eines Verhaltens, und beschreiben Sie das ausführliche Verhalten in einem eigenen Aktivitätsdiagramm. See [Describing Sub-activities with Call Behavior Actions](#Subactivities).

- Set the action's **Local Postconditions** and **Local Preconditions** properties to describe its outcome in more specific detail. For more information, see [Defining Postconditions and Preconditions](#Postcondition).

### <a name="Subactivities"></a> Describing Sub-activities with Call Behavior Actions
 Sie können das Verhalten einer Aktion mithilfe eines eigenen Aktivitätsdiagramms ausführlich beschreiben. Ein aufgerufenes Verhalten ist ein Aktivitätsdiagramm, das im Hauptaktivitätsdiagramm durch eine Aktion zum Aufrufen eines Verhaltens dargestellt wird. Sie können mit der Aktion zum Aufrufen eines Verhaltens auch Verhalten beschreiben, das unterschiedlichen Aktivitäten gemeinsam ist, sodass Sie die Unteraktivität nicht mehrmals zeichnen müssen.

 In der folgenden Abbildung zeigt Diagramm 1 eine Aktivität, die über eine Aktion zum Aufrufen eines Verhaltens verfügt, und Diagramm 2 zeigt das Unteraktivitätsdiagramm, in dem das aufgerufene Verhalten dargestellt wird.

 ![A separate activity diagram shows detailed actions](../modeling/media/uml-actguidedetail.png "UML_ActGuideDetail")

##### <a name="to-describe-a-sub-activity-with-a-call-behavior-action"></a>So beschreiben Sie eine Unteraktivität mit einer Aktion zum Aufrufen eines Verhaltens

1. To create the diagram for the sub-activity, in **Solution Explorer**, right-click your modeling project, point to **Add**, and then click **New Item**.

2. In the **Add New Item** dialog box, under **Templates** click **Activity Diagram** and in the **Name** box type the name that you plan to give your **Call Behavior Action**.

3. Zeichnen Sie den ausführlichen Arbeitsfluss für die Unteraktivität. Dies ist das aufgerufene Verhalten.

    - In the called sub-activity diagram, the **Initial Node** indicates where control starts when the called behavior is invoked. The **Activity Final Node** shows where control should return to the parent activity.

4. Set the **Behavior** property of the **Call Behavior Action** to refer to the called behavior diagram.

    > [!NOTE]
    > The sub-activity diagram must have some elements on it or the diagram will not be available in the drop-down list for the **Behavior** property. Also, the trident icon will not appear on your **Call Behavior Action** shape until you set its **Behavior** property.

5. Set the **Is Synchronous** property of the action to indicate whether your activity waits for the called activity to complete.

    - If you set **Is Synchronous** to false, you are indicating that the flow can continue to the next action before the called activity finishes. Definieren Sie keine Ausgabepins oder ausgehenden Datenflüsse von der Aktion.

### <a name="describing-data-flow-in-and-out-of-sub-activities"></a>Beschreiben des Datenflusses in und aus Unteraktivitäten
 Sie können den Datenfluss in und aus Unteraktivitäten auf die gleiche Weise wie die Verwendung von Parametern in Software beschreiben.

- Erstellen Sie in der Aktion zum Aufrufen eines Verhaltens Eingabe- und Ausgabepins (1) für jedes Datenelement, das in die Aktion oder aus der Aktion fließt. Weisen Sie jedem Pin einen entsprechenden Namen zu.

- In the sub-activity diagram, create an **Activity Parameter Node** (2) for each input and output pin on the calling action. Weisen Sie jedem Knoten den gleichen Namen wie dem entsprechenden Pin zu.

  > [!NOTE]
  > Ein Aktivitätsparameterknoten ähnelt einem Objektknoten. To check what type of node that you are looking at, right-click the node and then click **Properties**. Der Typ des Knotens wird in der Kopfzeile des Eigenschaftenfensters angezeigt.

- Zeichnen Sie im Unteraktivitätsdiagramm Konnektoren, die den Fluss von Objekten in die oder aus den einzelnen Aktivitätsparameterknoten darstellen.

  ![Pins on Call Behavior map to activity parameters](../modeling/media/uml-actguidesub.png "UML_ActGuideSub")

### <a name="Postcondition"></a> Defining Postconditions and Preconditions
 You can use the **Local Postconditions** and **Local Preconditions** properties to specify in detail the outcome of an action. Diese Eigenschaften beschreiben die Auswirkung der Aktion, jedoch nicht, wie die Auswirkung erreicht wird.

 To set these properties, right-click the action and then click **Properties**. Geben Sie Werte in die Eigenschaftenfelder im Eigenschaftenfenster ein.

#### <a name="local-postconditions"></a>Lokale Nachbedingungen
 Eine Nachbedingung ist eine Bedingung, die erfüllt sein muss, bevor die Aktion als abgeschlossen betrachtet werden kann. In der Beispielaktion „Bestellung bestätigen“ kann die Nachbedingung wie folgt lauten:

 Der Kunde hat vollständige und gültige Informationen angegeben, die zum Verarbeiten seiner Kreditkartendaten erforderlich sind.

 Eine Nachbedingung kann eine Beziehung zwischen den Zuständen vor und nach dem Eintreten einer Aktion beschreiben. Beispiel:

 Der Zinssatz ist doppelt so hoch wie vorher.

 Sie können Nachbedingungen auf formalere Weise schreiben, indem Sie auf bestimmte Attribute der in den Aktionen behandelten Daten verweisen. Beispiel:

 `InvoiceTotal == Sum(OrderItem.MenuItem.Price)`

#### <a name="local-preconditions"></a>Lokale Nachbedingungen
 Eine Vorbedingung ist eine Bedingung, die erfüllt sein muss, wenn die Aktion beginnen kann. Beispielsweise kann die Aktion „Bestellung bestätigen“ die folgende Vorbedingung aufweisen:

 Der Kunde hat mindestens ein Gericht ausgewählt.

### <a name="describing-calls-to-operations"></a>Beschreiben der Aufrufe von Vorgängen
 Im Allgemeinen beschreibt eine Aktion Arbeit, die von einer beliebigen Kombination von Personen, Software oder Computern ausgeführt wird. Sie können jedoch mit einer Aktion zum Aufrufen eines Vorgangs den Aufruf einer bestimmten Softwaremethode oder -funktion beschreiben.

- Legen Sie den Namen der Aktion zum Aufrufen eines Vorgangs fest, um anzugeben, welcher Vorgang für welches Objekt bzw. welche Komponente aufgerufen wird.

- Fügen Sie der Aktion zum Aufrufen eines Vorgangs Eingabe- und Ausgabepins hinzu, um Parameter und Rückgabewerte zu beschreiben.

- You can set the **Is Synchronous** property of the action to indicate whether your activity waits for the operation to complete.

  - If you set **Is Synchronous** to false, you are indicating that the flow can continue to the next action before the called operation is complete. Definieren Sie keine Ausgabepins oder ausgehenden Datenflüsse von der Aktion.

## <a name="Concurrent"></a> Concurrent Flows
 You can use the **Fork Node** and the **Join Node** to describe two or more threads of activities that can execute at the same time.

 ![The fork and join nodes show concurrent flows](../modeling/media/uml-actguideconcurrent.png "UML_ActGuideConcurrent")

 The effect of the **Fork Node** (1) is to divide the thread of control into two or more threads. Wenn die vorherige Aktion endet, können alle Aktionen auf der Ausgabeseite der Gabelung beginnen.

 A **Join Node** (2) brings concurrent threads together. The action after the **Join Node** may not start until all the actions leading to the **Join Node** are complete.

### <a name="describing-signals-and-events"></a>Beschreiben von Signalen und Ereignissen
 Sie können einen Schritt in einem Prozess, der ein Signal sendet, als Aktion zum Senden eines Signals in einer Aktivität darstellen. Einen Schritt, der erst nach einem bestimmten Signal oder Ereignis fortgesetzt werden kann, können Sie als Aktion zum Akzeptieren eines Ereignisses darstellen.

 Beispielsweise können Sie einen Schritt darstellen, der eine Bestellung sendet, und dann einen weiteren Schritt, der die Bestellung empfangen muss, bevor er sie verarbeitet.

#### <a name="sending-a-signal"></a>Senden eines Signals
 Verwenden Sie eine Aktion zum Senden eines Signals (3), um anzugeben, dass ein Signal oder eine Meldung an andere Aktivitäten oder Prozesse gesendet wird. Geben Sie mit dem Namen der Aktion an, welche Art von Meldung von der Aktion gesendet wird.

- Die Kontrolle wird sofort an die nächste Aktion in der Ablaufsteuerung übergeben, sofern vorhanden.

- Sie können mit einer Aktion zum Senden eines Signals nicht beschreiben, wie der Prozess auf zurückgegebene Informationen reagiert. Verwenden Sie hierzu eine eigene Aktion zum Akzeptieren eines Ereignisses.

- Sie können den eingehenden Datenfluss einer Aktion zum Senden eines Signals darstellen, um anzugeben, welche Daten mit der ausgehenden Meldung gesendet werden können. For more information, see [Describing Data Flow](#DataFlows).

#### <a name="waiting-for-a-signal-or-event"></a>Warten auf ein Signal oder Ereignis
 Verwenden Sie eine Aktion zum Akzeptieren eines Ereignisses (4), um anzugeben, dass diese Aktivität auf ein externes Ereignis oder eine externe eingehende Meldung wartet. Geben Sie mit dem Namen der Aktion den Typ des Ereignisses an, auf das die Aktion wartet.

- Um darzustellen, dass die Aktivität an einem bestimmten Punkt im Fluss auf ein externes Ereignis oder eine externe Meldung wartet, zeichnen Sie an der entsprechenden Stelle in der Aktivität eine Aktion zum Akzeptieren eines Ereignisses mit einem eingehenden Fluss.

- Um darzustellen, dass die Aktivität jederzeit auf ein externes Ereignis oder eine externe Meldung reagieren kann, zeichnen Sie eine Aktion zum Akzeptieren eines Ereignisses ohne eingehenden Fluss. Wenn das benannte externe Ereignis eintritt, beginnt in der Aktivität ein neuer Thread beginnend mit der Aktion zum Akzeptieren eines Ereignisses.

- Sie können mithilfe einer Aktion zum Akzeptieren eines Ereignisses keinen vom Absender des Signals zurückgegebenen Wert beschreiben. Verwenden Sie hierzu eine eigene Aktion zum Senden eines Signals.

- Sie können ausgehende Datenflüsse der Aktion darstellen, um zu zeigen, wie die Aktivität empfangene Daten des Signals verarbeitet. If you want to show more than one output flow, you should set the **IsUnmarshall** property of the Accept Event Action, which indicates that the action parses the incoming signal into its separate components. For more information, see [Describing Data Flow](#DataFlows).

### <a name="describing-multiple-data-flows"></a>Beschreiben von mehreren Datenflüssen
 Sie können mehrere ausgehende Ablaufsteuerungen oder Objektflüsse einer Aktion zeichnen, um anzugeben, dass am Ende der Aktion mehrere Threads entstehen. Das Resultat ähnelt dem Ergebnis einer Gabelung, mit der Ausnahme, dass Sie eine Kombination von Ablaufsteuerungen und Objektflüssen verwenden können.

 Im folgenden Beispiel werden mehrere eingehende und ausgehende Flüsse von Aktionen gezeigt.

 ![Parallel object flows](../modeling/media/uml-actguidemulti.png "UML_ActGuideMulti")

 Wenn die Aktion „Kunde stellt genau Daten bereit“ abgeschlossen wird, erzeugt sie zwei Objekte: „Lieferadresse“ und „Kreditkartendetails“. Die beiden Objekte werden anschließend durch unterschiedliche Aktionen verarbeitet.

 Da eine Aktion erst beginnen kann, wenn alle zugehörigen Eingaben verfügbar sind, beginnt die letzte Aktion erst, wenn alle zu ihr führenden Aktionen abgeschlossen sind.

### <a name="streams"></a>Streams
 Sie können mit einem Aktivitätsdiagramm eine Pipeline oder eine Reihe von Aktionen beschreiben, die gleichzeitig ausgeführt werden und kontinuierlich Daten von einer Aktion an eine andere übergeben.

 Im folgenden Beispiel soll jede Aktion Objekte erzeugen können, während sie weiterhin ausgeführt wird. Da keine Ablaufsteuerungen vorhanden sind, kann jede Aktion beginnen, sobald sie die ersten Objekte empfängt.

 Beachten Sie, dass die Konnektoren in diesem Beispiel Objektflüsse sind, da sie alle über mindestens ein Ende in einem Aktivitätsparameterknoten, Objektknoten bzw. auf einem Eingabe- oder Ausgabepin verfügen.

 ![A data flow](../modeling/media/uml-actguidestream.png "UML_ActGuideStream")

 1. Das Beispiel enthält drei Aktivitätsparameterknoten, die die Eingaben und Ausgaben darstellen.

 2. Objektknoten, Eingabepins und Ausgabepins können Puffer darstellen. Sie können die Eigenschaft „Upper Bound“ eines Objektknoten festlegen, um die Anzahl der Objekte anzugeben, die gleichzeitig im Puffer vorhanden sein können.

 3. Mithilfe von Entscheidungsknoten können Sie zeigen, dass ein Stream unterteilt ist und unterschiedliche Objekte in unterschiedlichen Verzweigungen sendet. Mithilfe von Kommentaren oder der Titel der Knoten können Sie das Teilungskriterium erläutern.

 4. Mithilfe von Gabelungsknoten können Sie zeigen, dass zwei oder mehr Kopien der Objekte erstellt und zur gleichzeitigen Verarbeitung gesendet werden.

 5. Mithilfe von Joinknoten können Sie zeigen, dass zwei Verarbeitungsstreams zu einem einzigen Stream zusammengeführt werden.

### <a name="selection-and-transformation"></a>Auswahl und Transformation
 Sie können angeben, dass die Objekte in einem Objektfluss transformiert und/oder ausgewählt werden. Ein Objektfluss ist ein Fluss zu oder von einem Pin oder Objektknoten.

- Eine Transformation beschreibt, wie in einen Fluss eintretende Objekte in einen anderen Typ konvertiert werden.

- Eine Auswahl beschreibt, wie nur einige der in einen Fluss eintretenden Objekte an die empfangende Aktion übertragen werden.

  Im Beispiel wird eine Transformation veranschaulicht. Die erste Aktion in Diagramm 1 erzeugt an einem Ausgabepin eine Postleitzahl. Dieser Pin ist mit einem Eingabepin der zweiten Aktion verbunden. Die zweite Aktion erwartet jedoch eine vollständige Adresse. Die Konvertierung von einem Typ in einen anderen wird in einer zweiten Aktivität (AddressLookup) angegeben. Auf diese wird in der Transformation-Eigenschaft des Objektflusses verwiesen. Die AddressLookup-Aktivität enthält einen Aktivitätsparameterknoten für die eingehende Postleitzahl und einen weiteren Aktivitätsparameterknoten für die ausgehende vollständige Adresse.

  ![Object transformation defined in another diagram](../modeling/media/uml-actguidetransform.png "UML_ActGuideTransform")

  Sie können eine Transformation oder Auswahl auf zweierlei Weise angeben:

- Fügen Sie einen Kommentar an den Eingabe- oder Ausgabepin an.

  - To distinguish this description from a general comment, you can begin the comment with <\<**transformation**>> or <\<**selection**>>.

- Geben Sie die Details der Transformation oder Auswahl in einem eigenen Aktivitätsdiagramm an.

  - Wenn Sie diese Methode verwenden, fügen Sie auch einen Kommentar an, um für die Leser deutlich zu machen, dass die Transformation definiert wurde.

##### <a name="to-specify-a-transformation-or-selection-in-a-separate-activity-diagram"></a>So geben Sie eine Transformation oder Auswahl in einem eigenen Aktivitätsdiagramm an

1. Erstellen Sie ein neues Aktivitätsdiagramm, in dem der Transformations- oder Auswahlfluss beschrieben werden soll.

   - In **Solution Explorer**, right-click your project, point to **Add**, click **New Item**, and then click **Activity Diagram**. Weisen Sie dem Diagramm einen entsprechenden Namen für den Transformations- oder Auswahlfluss zu. Klicken Sie auf **Hinzufügen**.

2. Führen Sie im neuen Diagramm die folgenden Schritte aus:

   1. Erstellen Sie zwei Aktivitätsparameterknoten, einen für den Eingabefluss und einen für die Ausgabe.

   2. Erstellen Sie mit Objektflüssen verbundene Aktionen. Dies veranschaulicht die Funktionsweise der Transformation oder Auswahl.

3. Führen Sie in jedem Diagramm, in dem Sie die Transformation oder Auswahl verwenden möchten, die folgenden Schritte aus:

   1. Erstellen Sie einen Objektfluss, d. h. einen Konnektor zu oder von einem Eingabepin, Ausgabepin, Objektknoten oder Aktivitätsparameterknoten.

   2. Right-click the object flow and then click **Properties**.

   3. In the **Transformation** or **Selection** property, select the diagram where you specified the transformation or selection flow.

   Sie können auch eine Auswahl für einen Objektknoten sowie für einzelne Eingabe- und Ausgabepins definieren. Define a selection activity as in the previous procedure, and then set the **Selection** property of the object node, or input or output pin.

## <a name="see-also"></a>Siehe auch
 [Edit UML models and diagrams](../modeling/edit-uml-models-and-diagrams.md) [UML Sequence Diagrams: Reference](../modeling/uml-sequence-diagrams-reference.md) [UML Component Diagrams: Reference](../modeling/uml-component-diagrams-reference.md) [UML Use Case Diagrams: Reference](../modeling/uml-use-case-diagrams-reference.md) [UML Class Diagrams: Reference](../modeling/uml-class-diagrams-reference.md) [UML Component Diagrams: Reference](../modeling/uml-component-diagrams-reference.md) [Video: Capture Business Workflows by using Activity Diagrams](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-4-capture-business-workflows)
