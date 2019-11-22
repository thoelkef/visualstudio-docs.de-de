---
title: 'UML Sequence Diagrams: Guidelines | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.sequencediagram.linktosequencediagram
- vs.teamarch.logicalclassdiagram.createlifeline
- vs.teamarch.componentdiagram.createlifeline
helpviewer_keywords:
- diagrams - modeling, sequence
- sequence diagrams
- UML diagrams, sequence
- interactions, UML
- diagrams - modeling, UML sequence
- UML interactions
- UML, sequence diagrams
- UML sequence diagrams
- behaviors, UML
ms.assetid: 5990ef7c-ba60-4e20-a36d-e29c1fa6c8bb
caps.latest.revision: 55
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8c5906084fc7db96ddf304e8362bf7692dac62d5
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297145"
---
# <a name="uml-sequence-diagrams-guidelines"></a>UML Sequence Diagrams: Guidelines
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio, you can draw a *sequence diagram* to show an interaction. Eine Interaktion ist eine Sequenz von Meldungen zwischen typischen Instanzen von Klassen, Komponenten, Subsystemen oder Akteuren.

 UML-Sequenzdiagramme sind Teil eines UML-Modells und nur innerhalb von UML-Modellierungsprojekten vorhanden. To create a UML sequence diagram, on the **Architecture** menu, click **New UML or Layer Diagram**. Find out more about [UML sequence diagram elements](../modeling/uml-sequence-diagrams-reference.md) or [UML modeling diagrams](../modeling/edit-uml-models-and-diagrams.md) in general. For a video demonstration, see [Sketching Interactions by using Sequence Diagrams (2010)](https://channel9.msdn.com/Blogs/clinted/UML-with-VS-2010-Part-7-Sketching-Interactions-with-Sequence-Diagrams).

 Welche Versionen von Visual Studio dieses Features unterstützen, erfahren Sie unter [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="in-this-topic"></a>In diesem Thema
 [Using UML Sequence Diagrams](#Using)

 [Basic Steps for Drawing Sequence Diagrams](#BasicSteps)

 [Creating and Using Simple Sequence Diagrams](#Simple)

 [Classes and Lifelines](#ClassesAndLifelines)

 [Creating Reusable Interaction Sequences](#Multiple)

 [Collapsing Groups of Lifelines](#Collapse)

 [Describing Control Structures with Fragments](#Fragments)

## <a name="Using"></a> Using UML Sequence Diagrams
 Sie können Sequenzdiagramme für eine Vielzahl von Zwecken auf unterschiedlichen Programmdetailebenen verwenden. Nachfolgend sind typische Situationen aufgeführt, in denen Sequenzdiagramme gezeichnet werden:

- Wenn Sie über ein Anwendungsfalldiagramm verfügen, das Systembenutzer und ihre Ziele zusammenfasst, können Sie Sequenzdiagramme zeichnen, um zu beschreiben, wie die Hauptkomponenten des Systems interagieren, um das Ziel der einzelnen Anwendungsfälle zu erreichen. For more information, see [UML Use Case Diagrams: Guidelines](../modeling/uml-use-case-diagrams-guidelines.md).

- Wenn Sie Nachrichten identifiziert haben, die bei einer Schnittstelle einer Komponente eingehen, können Sie Sequenzdiagramme zeichnen, um zu beschreiben, wie die internen Teile der Komponente interagieren, um das für die einzelnen eingehenden Meldungen erforderliche Ergebnis zu erzielen. For more information, see [UML Component Diagrams: Guidelines](../modeling/uml-component-diagrams-guidelines.md).

  Das Zeichnen von Sequenzdiagrammen hat mehrere Vorteile:

- Sie können leicht erkennen, wie Aufgaben zwischen Komponenten verteilt sind.

- Sie können Interaktionsmuster identifizieren, die die Aktualisierung der Software erschweren.

## <a name="relationship-to-other-diagrams"></a>Beziehung zu anderen Diagrammen
 Sie können UML-Sequenzdiagramme auf verschiedene Arten zusammen mit anderen Diagrammen verwenden.

#### <a name="lifelines-and-types"></a>Lebenslinien und Typen
 Die Lebenslinien, die Sie in einem Sequenzdiagramm zeichnen, können typische Instanzen der Komponenten oder Klassen im System darstellen. Sie können Lebenslinien aus Typen und Typen aus Lebenslinien erstellen und die Typen in UML-Klassendiagrammen und UML-Komponentendiagrammen anzeigen. For more information, see [Classes and Lifelines](#ClassesAndLifelines).

#### <a name="parameter-types"></a>Parametertypen
 Sie können in einem UML-Klassendiagramm auch die Typen der Parameter und der zurückgegebenen Werte beschreiben, die in den zwischen den Lebenslinien gesendeten Meldungen verwendet wurden.

#### <a name="use-case-details"></a>Anwendungsfalldetails
 Ein Anwendungsfall stellt das Ziel eines Benutzers zusammen mit einer Sequenz von Schritten zum Erreichen des Ziels dar. Die Sequenz der Schritte kann auf verschiedene Weise beschrieben werden. Eine Option besteht im Zeichnen eines Sequenzdiagramms, das die Interaktionen zwischen den Benutzern und den Hauptkomponenten des Systems zeigt. For more information, see [UML Use Case Diagrams: Guidelines](../modeling/uml-use-case-diagrams-guidelines.md).

## <a name="BasicSteps"></a> Basic Steps for Drawing Sequence Diagrams
 For a complete list of elements on sequence diagrams, see [UML Sequence Diagrams: Reference](../modeling/uml-sequence-diagrams-reference.md).

> [!NOTE]
> Detailed steps for how to create any of the modeling diagrams are described in [Edit UML models and diagrams](../modeling/edit-uml-models-and-diagrams.md).

#### <a name="to-create-a-sequence-diagram"></a>So erstellen Sie ein Sequenzdiagramm

1. On the **Architecture** menu, click **New UML or Layer Diagram**.

2. Under **Templates**, click **UML Sequence Diagram**.

3. Benennen Sie das Diagramm.

4. In **Add to Modeling Project**, select an existing modeling project in your solution, or **Create a new modeling project**, and then click **OK**.

    A new sequence diagram appears with the **Sequence Diagram** toolbox. Die Toolbox enthält die erforderlichen Elemente und Konnektoren.

   ![Parts of a sequence diagram](../modeling/media/uml-sequence.png "UML_Sequence")

#### <a name="to-draw-a-sequence-diagram"></a>So zeichnen Sie ein Sequenzdiagramm

1. Drag **Lifelines** (1) from the **Toolbox** onto the diagram to represent instances of classes, components, actors, or devices.

    > [!NOTE]
    > You can also create a lifeline by dragging an existing class, interface, actor or component from **UML Model Explorer** onto the diagram. Dadurch wird eine Lebenslinie erstellt, die eine Instanz des ausgewählten Typs darstellt.

2. Zeichnen Sie Meldungen, um darzustellen, wie die Lebenslinien zusammenarbeiten, um ein bestimmtes Ziel zu erreichen.

     Um eine Meldung (3, 4, 6, 7) zu erstellen, klicken Sie auf ein Meldungstool. Klicken Sie dann an dem Punkt auf die sendende Lebenslinie, an dem die Meldung beginnen soll, und klicken Sie anschließend auf die empfangende Lebenslinie.

     An der empfangenden Lebenslinie wird eine Vorkommnisausführung (5) angezeigt. Die Vorkommnisausführung stellt einen Zeitraum dar, während dem die Instanz eine Methode ausführt. Sie können andere Meldungen erstellen, die an einer Vorkommnisausführung beginnen.

3. Zum Anzeigen einer Meldung, die aus einer unbekannten Ereignisquelle (9) stammt oder an unbekannte Empfänger (10) überträgt, zeichnen Sie eine asynchrone Meldung von oder zu einem Leerraum im Diagramm. These messages are called *found messages* (9) and *lost messages* (10).

    > [!NOTE]
    > To move a group of lifelines that have lost or found messages, follow these steps to select the lifelines before you move them: Draw a rectangle around those lifelines, or press and hold the **CTRL** key while you click each lifeline. If you use **Select All** or **CTRL**+**A** to select all lifelines, and then move them, any lost or found messages attached to these lifelines will not move. Wenn diese Situation eintritt, können Sie diese Meldungen separat verschieben.

4. Zeichnen Sie Sequenzdiagramme für jede wichtige Meldung in der gleichen Komponente oder im gleichen System.

#### <a name="to-change-the-order-of-messages"></a>So ändern Sie die Reihenfolge der Meldungen

- Ziehen Sie eine Meldung in der zugehörigen Lebenslinie aufwärts oder abwärts. Sie können sie über andere Meldungen oder in einen bzw. aus einem Ausführungsblock ziehen.

     \- oder -

- Click the message and use the **UP ARROW** and **DOWN ARROW** keys to adjust message positions. Use **SHIFT+UP ARROW** and **SHIFT+DOWN ARROW** to change the order of the messages.

#### <a name="to-move-or-copy-message-sequences-on-the-sequence-diagram"></a>So verschieben oder kopieren Sie Meldungssequenzen im Sequenzdiagramm

1. Right-click a message (3, 4) and then click **Copy**.

2. Right-click the execution occurrence (5) or a lifeline (1) from which you want the new message to be sent, and then click **Paste**. Der neue Absender kann sich in einem anderen Diagramm befinden.

     Eine Kopie der Meldung und all ihrer untergeordneten Meldungen wird am Ende der Vorkommnisausführung oder am Ende der Lebenslinie hinzugefügt.

    > [!NOTE]
    > Die eingefügte Meldung wird immer am Ende der Vorkommnisausführung oder der Lebenslinie angezeigt. Nachdem Sie sie eingefügt haben, können Sie sie an eine höhere Position ziehen.

#### <a name="to-display-and-edit-the-signature-text-for-a-message"></a>So zeigen Sie den Signaturtext einer Meldung an und bearbeiten ihn

- Die Ziel-Lebenslinie muss an Typen gebunden oder Typen zugeordnet sein, damit der Signaturtext sichtbar ist. Um diese Aufgabe auszuführen, führen Sie einen der folgenden Schritte aus:

  - Right-click the lifeline, and then choose **Create Class**.

     - oder -

  - Select the lifeline, press **F4**, and then in the **Properties** window, set the **Type** property to an existing type or specify the name for a new type. Right-click the message label, and then choose **Create Operation**.

    Der Signaturtext wird unterhalb der Meldungsbezeichnung angezeigt. Sie können den Signaturtext jetzt bearbeiten. For more information, see [Classes and Lifelines](#ClassesAndLifelines).

#### <a name="to-improve-the-layout-of-a-sequence-diagram"></a>So verbessern Sie das Layout eines Sequenzdiagramms

- Right-click a blank part of the diagram, and then click **Rearrange Layout**.

- To undo the operation, click **Edit**, and then click **Undo**.

#### <a name="to-change-the-package-that-owns-the-interaction"></a>So ändern Sie das Paket, das die Interaktion besitzt

1. In **UML Model Explorer**, find the Interaction that the sequence diagram displays.

    > [!NOTE]
    > The interaction will not appear in **UML Model Explorer** until you add the first lifeline to the sequence diagram.

2. Ziehen Sie die Interaktion in das Paket.

     \- oder -

     Right-click the Interaction, and then click **Cut**. Right-click the Package, and then click **Paste**.

## <a name="Simple"></a> Creating and Using Simple Sequence Diagrams
 Die einfachste und am häufigsten verwendete Form des Sequenzdiagramms enthält nur Lebenslinien und Meldungen. Mit einem Diagramm dieser Art können Sie deutlich eine typische Sequenz von Interaktionen zwischen Objekten im Entwurf oder zwischen Ihrem System und dessen Benutzern anzeigen. Dies reicht häufig aus, um den Entwurf zu verdeutlichen und zu diskutieren.

 Nachfolgend sind einige Punkte aufgeführt, die Sie beim Zeichnen eines einfachen Sequenzdiagramms beachten sollten.

### <a name="types-of-message"></a>Meldungstypen
 Es gibt drei Tools, die Sie verwenden können, um Meldungen zu erstellen.

- Use the **Synchronous** tool to describe an interaction in which the sender waits for the receiver to return a response (3).

     A **<\<return>>** arrow will be shown at the end of the execution occurrence. Er zeigt die Rückgabe der Steuerung an den Absender an.

- Use the **Asynchronous** tool to describe an interaction in which the sender can continue immediately without waiting for the receiver (4).

- Use the **Create** tool to describe an interaction in which the sender creates the receiver (8).

     Eine Create-Meldung sollte die erste Meldung sein, die der Empfänger erhält.

### <a name="annotating-the-interactions"></a>Kommentieren der Interaktionen
 To describe more detail about the sequence, you can place a **Comment** anywhere on the diagram.

 Using **Comment Links**, you can link a comment to lifelines, executions, interaction uses, and fragments.

> [!CAUTION]
> Wenn Sie einen Kommentar an einem bestimmten Punkt in der Sequenz anfügen möchten, verknüpfen Sie ihn mit einer Vorkommnisausführung, einer Interaktionsverwendung oder einem Fragment. Verknüpfen Sie ihn nicht mit einer Lebenslinie, da er in diesem Fall nicht am richtigen Punkt in der Sequenz bleibt.

 Verwenden Sie zu folgenden Zwecken einen Kommentar:

- Anmerken, was an wichtigen Punkten in der Sequenz erreicht wurde. Dadurch können Leser die Ziele der Interaktionen erkennen.

- Beschreiben des Hauptziels der gesamten Sequenz. Fügen Sie den Kommentar an die erste Vorkommnisausführung an, oder weisen Sie ihn nicht zu. Zum Beispiel: „Der Kunde hat Gerichte aus der Speisekarte ausgewählt, und ihm wurde ein Preis genannt.“

- Beschreiben der Verantwortlichkeiten der einzelnen Lebenslinien. Fügen Sie den Kommentar an die Lebenslinie an. Zum Beispiel: „Bestellmanager nimmt die Essenswünsche des Kunden auf.“

- Anmerken von Ausnahmen oder Alternativen, die als Alternative zu der typischen angezeigten Sequenz ausgeführt werden können. Zum Beispiel: „Der Kunde kann wählen, den Rest dieser Sequenz zu überspringen.“

  - Erwägen Sie die Verwendung von Fragmenten als formalere Alternativen zu dieser Art von Anmerkung. See [Describing Control Structures with Fragments](#Fragments)

## <a name="deciding-the-scope-of-the-diagram"></a>Festlegen des Diagrammumfangs
 Es ist wichtig, deutlich hervorzuheben, was das Diagramm darstellen soll.

#### <a name="initiating-event"></a>Auslösendes Ereignis
 Jedes Diagramm sollte die Sequenz der Interaktionen zeigen, die sich aus einem auslösenden Ereignis ergibt. Beispielsweise könnte dies Folgendes sein:

- Ein Benutzer, der einen Anwendungsfall auslöst, z. B. indem er die Webseite für den Kauf eines Gerichts öffnet.

- Eine Meldung von einer Systemkomponente an eine andere, z. B. die Abfrage der Verfügbarkeit von Positionen, die ein Kunde kaufen möchte.

- Ein durch eine Statusänderung ausgelöstes Ereignis, z. B. Fallen des Bestands einer Position unter einen bestimmten Schwellenwert.

#### <a name="level-of-detail"></a>Detailgrad
 Sequenzdiagramme können einen unterschiedliche Grad der Detaillierung aufweisen. Sie können den Detailgrad in zwei separaten Dimensionen fast unabhängig voneinander festlegen:

 Lebenslinien können einen dieser Detailgrade darstellen:

- Objekte im Programmcode, der entweder bereits vorhanden ist oder noch entwickelt wird.

- Komponenten oder ihre Unterkomponenten, wobei normalerweise Fassaden, Proxys und andere Bindemechanismen ausgelassen werden.

- Das System und externe Akteure

  Meldungen können einen dieser Detailgrade darstellen:

- Softwaremeldungen im Programmcode, an einer API oder einer Webschnittstelle.

- Transaktionen oder untergeordnete Transaktionen, z. B. zwischen Benutzern und dem System oder zwischen Code und Datenbank.

- Anwendungsfälle – wichtige Interaktionen zwischen Benutzern und dem System.

  Unabhängig davon, ob Sie vorhandenen Code untersuchen oder einen neuen Entwurf beschreiben, ist es häufig nützlich, weniger detaillierte Ansichten zu zeichnen und zu diskutieren.

## <a name="describing-variations"></a>Beschreiben von Variationen
 Das Diagramm zeigt eine einzelne, typische Sequenz von Ereignissen. Wenn Sie alternative Möglichkeiten zeigen möchten, z. B. Fehlerszenarien, können Sie eine der folgenden Optionen verwenden:

- Zeichnen Sie separate Sequenzdiagramme, um solche Szenarien zu beschreiben.

- Use [Describing Control Structures with Fragments](#Fragments) to show loops, alternatives, and so on.

## <a name="assessing-the-design"></a>Bewerten des Entwurfs
 Sie können das Diagramm verwenden, um die Verteilung der Aufgaben zwischen den Objekten oder Komponenten zu bewerten. Ziehen Sie eine Umgestaltung in Erwägung, wenn Sie diese Muster sehen:

- Eine Lebenslinie scheint alle Aufgaben durchzuführen, Aufrufe an alles andere zu tätigen, während die anderen Lebenslinien nur passiv reagieren.

- Viele Meldungen kreuzen die Lebenslinien. Jede Lebenslinie sollte Meldungen nur an ein paar Nachbarn senden und nicht mit den Nachbarn ihrer Nachbarn kommunizieren. Es sollte in der Regel möglich sein, die Lebenslinien so anzuordnen, dass sich Meldungen und Lebenslinien nur an wenigen Stellen kreuzen, und wo sie sich kreuzen, sollte die Ziel-Lebenslinie keine Meldungen austauschen, die kreuzende Lebenslinien aufweisen.

- Einige Lebenslinien scheinen mehr als eine Art von Aufgabe zu behandeln. Es sollte einfach sein, die Verantwortlichkeiten der einzelnen Lebenslinien in einem kurzen Satz zu beschreiben,der die Arbeit zusammenfasst, die sie als Antwort auf die empfangenen Meldungen ausführen.

## <a name="ClassesAndLifelines"></a> Classes and Lifelines
 Die Lebenslinien in den Sequenzdiagrammen zeigen Instanzen von Klassen oder Komponentenschnittstellen. Sie können eine Lebenslinie auf zweierlei Weise benennen:

|**For this purpose**|**Use this format**|
|--------------------------|-------------------------|
|Anonyme Instanz eines Typs.<br /><br /> Verwenden Sie diese Option, wenn Sie nur über eine Lebenslinie jedes Typs verfügen.|*typeName*|
|Benannte Instanz eines Typs.<br /><br /> Verwenden Sie diese Option, wenn Sie eine Sequenz darstellen möchten, die mehr als eine Instanz des gleichen Typs umfasst.|*objectName*:*typeName*|

### <a name="creating-lifelines-from-types"></a>Erstellen von Lebenslinien aus Typen
 Sie können neue Lebenslinien aus Klassen erstellen, die Sie bereits definiert haben, z. B. in einem Klassendiagramm.

> [!NOTE]
> Stellen Sie sicher, dass Sie über ein Sequenzdiagramm verfügen, bevor Sie diese Aufgabe ausführen.

##### <a name="to-create-a-lifeline-from-an-existing-type"></a>So erstellen Sie eine Lebenslinie aus einem vorhandenen Typ

- Ziehen Sie eine Klasse, Komponente oder Schnittstelle aus dem UML-Modell-Explorer in ein Sequenzdiagramm.

   \- oder -

  1. Right-click the class, component, or interface on its respective diagram, and then click **Create Lifeline**.

  2. In the **Create Lifeline** dialog box, select a sequence diagram, and then click **OK**.

     Eine neue benannte Instanzlebenslinie wird angezeigt, deren Typ dem Typ entspricht, den Sie gezogen haben.

  > [!NOTE]
  > Sie können diese Aktion so oft wie gewünscht wiederholen. Dadurch werden Lebenslinien mit unterschiedlichen Instanznamen erstellt.

##### <a name="to-change-the-type-of-a-lifeline"></a>So ändern Sie den Typ einer Lebenslinie

1. Right-click a lifeline, and then click **Properties**.

2. In the **Properties** window, set the **Type** property. Sie können einen Typ aus dem Dropdown-Menü auswählen oder einen neuen Namen eingeben.

### <a name="creating-classes-from-lifelines"></a>Erstellen von Klassen aus Lebenslinien
 Wenn Sie ein oder mehrere Sequenzdiagramme erstellt haben, können Sie die Lebenslinien zusammenfassen, indem Sie Klassen oder Schnittstellen daraus erstellen.

##### <a name="to-create-a-class-or-interface-from-a-lifeline"></a>So erstellen Sie eine Klasse oder Schnittstelle aus einer Lebenslinie

1. Right-click the lifeline, and then click **Create Class** or **Create Interface**.

     Eine neue Klasse oder Schnittstelle wird im UML-Modell-Explorer angezeigt.

2. Erstellen Sie Vorgänge in der Klasse oder Schnittstelle für jede Meldung, die die Lebenslinie empfängt:

    1. Wählen Sie alle Meldungen, die Sie einschließen möchten.

    2. Right-click one of the messages, and then click **Create Method**.

         Die neue Klasse oder Schnittstelle verfügt über Vorgänge für jede ausgewählte Meldung.

         The operation name appears below each message arrow, and in the **Operation** property of the message.

         Wenn die Meldung Parameter im Format „(Parameter : Typ)“ enthalten hat, werden sie in der Parameterliste des neuen Vorgangs angezeigt.

        > [!NOTE]
        > Wiederholen Sie diesen Schritt, wenn Sie neue Meldungen im Sequenzdiagramm hinzufügen.

3. Um die neue Klasse oder Schnittstelle im Detail anzuzeigen, fügen Sie sie einem Klassen- oder Komponentendiagramm hinzu.

    1. Öffnen oder erstellen Sie ein Klassen- oder Komponentendiagramm.

    2. Drag the new class or interface from **UML Model Explorer** to a class diagram.

         Die Klasse oder Schnittstelle wird im Klassendiagramm angezeigt.

         \- oder -

    3. Drag the new interface from **UML Model Explorer** onto a component or port in a component diagram.

         Die Schnittstelle wird auf der Komponente als Lollipop angezeigt.

### <a name="creating-classes-for-parameters"></a>Erstellen von Klassen für Parameter
 Sie können Parameter in die Meldungen in einem Sequenzdiagramm einschließen. Mit einem UML-Klassendiagramm können Sie die Parametertypen beschreiben.

## <a name="Multiple"></a> Creating Reusable Interaction Sequences
 Sie können ein separates Diagramm verwenden, um eine Sequenz zu beschreiben, die Details enthält, die Sie herausstellen möchten oder die mehreren Diagrammen gemeinsam sind.

 Sie können ein Interaktionsverwendungsrechteck (12) in einem Diagramm erstellen, das auf die Details in einem anderen Diagramm verweist.

 Doppelklicken Sie auf eine Interaktionsverwendung, um das Sequenzdiagramm zu öffnen, das mit dieser verknüpft ist.

#### <a name="to-create-a-reusable-interaction-sequence-from-existing-lifelines"></a>So erstellen Sie eine wiederverwendbare Interaktionssequenz aus vorhandenen Lebenslinien

1. In the **Toolbox**, click **Interaction Use**.

2. Halten Sie im Sequenzdiagramm die Maustaste gedrückt, während Sie über die Lebenslinien ziehen, die Sie in die wiederverwendbare Sequenz einschließen möchten. Starten Sie an der vertikalen Position, an der Sie die Interaktionsverwendung einfügen möchten.

     Eine Interaktionsverwendung wird über die ausgewählten Lebenslinien im Sequenzdiagramm angezeigt.

3. Doppelklicken Sie auf den Namen der Interaktionsverwendung, und benennen Sie sie um, um die Wirkung der wiederverwendbaren Sequenz in diesem Diagramm zu beschreiben.

     \- oder -

     Schreiben Sie den Namen wie einen Funktionsaufruf mit Parametern.

4. Verknüpfen Sie die Interaktionsverwendung mit einem anderen Sequenzdiagramm. Klicken Sie mit der rechten Maustaste auf die Interaktionsverwendung, und führen Sie dann eine der folgenden Aktionen durch:

     Click **Create New Sequence** to create a new sequence diagram

     \- oder -

     Click **Link to Sequence** to link to an existing diagram.

     Visual Studio erstellt eine Verknüpfung zwischen der Interaktionsverwendung und der neuen Interaktionssequenz.

     Ein neues Sequenzdiagramm wird in der Projektmappe angezeigt. Es enthält die Lebenslinien, mit der Sie die Interaktionsverwendung erstellt haben.

    > [!NOTE]
    > Es werden nur die Lebenslinien einbezogen, die Sie zum Erstellen der Interaktionsverwendung verwendet haben. Das neue Diagramm umfasst keine Lebenslinien, die Sie nach der Interaktionsverwendung erstellt haben, auch wenn die Interaktionsverwendung Sie jetzt abdeckt.

#### <a name="to-create-a-reusable-sequence-from-existing-messages"></a>So erstellen Sie eine wiederverwendbare Sequenz aus vorhandenen Meldungen

- Right-click the message that you want to move, and then click **Move to Diagram**.

  Visual Studio:

  - Ersetzt die ausgewählte Meldung und alle untergeordneten Meldungen durch eine Interaktionsverwendung.

  - Verschiebt die ersetzten Meldungen in ein neues Sequenzdiagramm.

  - Erstellt eine Verknüpfung zwischen der Interaktionsverwendung und dem neuen Sequenzdiagramm.

#### <a name="to-navigate-to-the-sequence-referenced-by-an-interaction-use"></a>So navigieren Sie zur Sequenz, auf die eine Interaktionsverwendung verweist

- Doppelklicken Sie auf die Interaktionsverwendung.

     \- oder -

     Right-click the interaction use and then click **Go to Sequence**.

### <a name="creating-a-placeholder-with-an-interaction-use"></a>Erstellen eines Platzhalters mit einer Interaktionsverwendung
 Sie können eine Interaktionsverwendung erstellen, ohne sie mit einem anderen Diagramm zu verknüpfen. You can use this as a placeholder for a part of the sequence whose details are yet to be worked out. Use the name of the interaction use to indicate the outcome that you want.

## <a name="Collapse"></a> Collapsing Groups of Lifelines
 Sie können eine Gruppe von Lebenslinien so reduzieren, dass die Gruppe als eine Lebenslinie angezeigt wird. Dadurch können Sie eine Gruppe von Objekten als einzelne Komponente visualisieren. Meldungen und Interaktionsverwendungen zwischen Lebenslinien in einer reduzierten Gruppe werden ausgeblendet. Meldungen und Interaktionssequenzen, die andere Lebenslinien einschließen, werden angezeigt.

#### <a name="to-collapse-a-group-of-lifelines-together"></a>So reduzieren Sie eine Gruppe von Lebenslinien

1. Wählen Sie zwei oder mehr Lebenslinien aus.

2. Right-click one of them, and then click **Collapse**.

     Die separaten Lebenslinien werden durch eine einzelne Lebenslinie ersetzt.

     Meldungen und Interaktionsverwendungen, die nur Mitglieder der Gruppe betreffen, werden ausgeblendet.

3. Um die Gruppe umzubenennen, klicken Sie auf den Namen.

    > [!NOTE]
    > Der Gruppenname geht verloren, wenn Sie die Gruppe erweitern.

#### <a name="to-expand-a-collapsed-group"></a>So erweitern Sie eine reduzierte Gruppe

- Right-click the collapsed lifeline, and then click **Expand**.

    > [!NOTE]
    > Der Name der Gruppe geht zusammen mit allen Verknüpfungen von der Gruppe zu Kommentaren oder Arbeitsaufgaben verloren.

## <a name="Fragments"></a> Describing Control Structures with Fragments
 Sie können kombinierte Fragmente (13) verwenden, um Schleifen, Verzweigungen und die gleichzeitige Verarbeitung in einem Sequenzdiagramm zu definieren. Ziehen Sie alternativ die Verwendung eines Aktivitätsdiagramms in Erwägung. Das Aktivitätsdiagramm ist nicht so nützlich, um Meldungen zwischen Akteuren darzustellen, aber in einigen Fällen ist es besser geeignet, um Schleifen, Verzweigungen und Parallelität zu zeigen.

 For a full list of the types of fragment, see [Describe control flow with fragments on UML sequence diagrams](../modeling/describe-control-flow-with-fragments-on-uml-sequence-diagrams.md).

#### <a name="to-create-a-combined-fragment"></a>So erstellen Sie ein kombiniertes Fragment

1. Wählen Sie eine Meldung oder eine Sequenz von Meldungen, die alle mit der gleichen Vorkommnisausführung oder Lebenslinie beginnen.

    > [!NOTE]
    > Wählen Sie die Meldungspfeile, nicht die Vorkommnisausführungen, auf die die Meldungen verweisen.

2. Right-click one of the messages, point to **Surround With**, and then click the type of fragment that you require.

     Ein neues Fragment wird angezeigt. Es enthält die ausgewählten Meldungen.

     Wenn der kombinierte Fragmenttyp mehrere Fragmente zulässt, wird auch ein leeres Fragment angezeigt.

3. To set the guard of a fragment, right-click the fragment border, and then click **Properties**. Set the **Guard** property.

     Mit dem Wächter wird die Bedingung einer Verzweigung oder Schleife definiert.

4. To add a new fragment to a kind that allows multiple fragments, right-click the boundary of a fragment, and point to **Add**. Click either **Interaction Operand Before** or **Interaction Operand After**.

5. Um neue Meldungen zu einem Fragment hinzuzufügen, verwenden Sie die Meldungstools oder die Funktion zum Kopieren und Einfügen.

## <a name="see-also"></a>Siehe auch
 [UML Sequence Diagrams: Reference](../modeling/uml-sequence-diagrams-reference.md) [Edit UML models and diagrams](../modeling/edit-uml-models-and-diagrams.md) [UML Use Case Diagrams: Reference](../modeling/uml-use-case-diagrams-reference.md) [UML Class Diagrams: Reference](../modeling/uml-class-diagrams-reference.md) [UML Component Diagrams: Reference](../modeling/uml-component-diagrams-reference.md) [UML Component Diagrams: Reference](../modeling/uml-component-diagrams-reference.md) [Video: Sketching Interactions by using Sequence Diagrams](https://go.microsoft.com/fwlink/?LinkId=201113)
