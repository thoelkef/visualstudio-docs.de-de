---
title: 'UML-Aktivitätsdiagramme: Richtlinien | Microsoft-Dokumentation'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "74298984"
---
# <a name="uml-activity-diagrams-guidelines"></a>UML-Aktivitätsdiagramme: Richtlinien
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio können Sie ein Aktivitätsdiagramm zeichnen, um einen Geschäftsprozess oder einen Softwarealgorithmus als Arbeitsfluss zu beschreiben, der eine Reihe von Aktionen durchläuft. Diese Aktionen können von Personen, Softwarekomponenten oder Geräten ausgeführt werden. Eine videodemo finden Sie unter: [Erfassen von Geschäfts Workflows mithilfe von Aktivitäts Diagrammen](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-4-capture-business-workflows).

 Welche Versionen von Visual Studio dieses Feature unterstützen, erfahren Sie unter [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Um ein UML-Aktivitätsdiagramm zu erstellen, klicken Sie im Menü **Architektur** auf **neues UML-oder ebenendiagramm**.

 Sie können ein Aktivitätsdiagramm für viele Zwecke verwenden:

- Beschreiben eines Geschäftsprozesses oder eines Arbeitsflusses zwischen Benutzern und dem System. Weitere Informationen finden Sie unter [Modell Benutzeranforderungen](../modeling/model-user-requirements.md).

- Beschreiben der Schritte, die in einem Anwendungsfall ausgeführt werden. Weitere Informationen finden Sie unter [UML-Anwendungsfall Diagramme: Richtlinien](../modeling/uml-use-case-diagrams-guidelines.md).

- Beschreiben einer Methode, einer Funktion oder eines Vorgangs in der Software. Weitere Informationen finden Sie unter [Modellieren der Architektur Ihrer APP](../modeling/model-your-app-s-architecture.md).

  Prozesse lassen sich durch das Zeichnen eines Aktivitätsdiagramms optimieren. Wenn sich das Diagramm eines vorhandenen Prozesses als sehr komplex erweist, können Sie überlegen, wie der Prozess vereinfacht werden kann.

  Referenzinformationen zu den Elementen in Aktivitäts Diagrammen finden Sie unter [UML-Aktivitätsdiagramme: Referenz](../modeling/uml-activity-diagrams-reference.md).

## <a name="relationship-to-other-diagrams"></a><a name="Relationships"></a> Beziehung zu anderen Diagrammen
 Wenn Sie ein Aktivitätsdiagramm zeichnen, um einen Geschäftsprozess oder die Art und Weise der Verwendung des Systems durch Benutzer zu beschreiben, können Sie ein Anwendungsfalldiagramm zeichnen, das eine andere Ansicht der gleichen Informationen liefert. Im Anwendungsfalldiagramm zeichnen Sie Aktionen als Anwendungsfälle. Weisen Sie den Anwendungsfällen den gleichen Namen zu wie den entsprechenden Aktionen. Die Anwendungsfallansicht bietet Ihnen folgende Vorteile:

- Sie können in einem Diagramm mithilfe einer Includes-Beziehung darstellen, wie größere Aktionen/Anwendungsfälle aus kleineren Aktionen/Anwendungsfällen zusammengesetzt sind.

- Sie können jede Aktion bzw. jeden Anwendungsfall explizit mit den Benutzern oder externen Systemen verknüpfen, die an der Ausführung beteiligt sind.

- Sie können Begrenzungen um die vom System unterstützten Aktionen/Anwendungsfälle oder jede Hauptkomponente zeichnen.

  Sie können auch ein Aktivitätsdiagramm zeichnen, um den Detailentwurf eines Softwarevorgangs zu beschreiben.

  In einem Aktivitätsdiagramm können Sie den Fluss der zwischen Aktionen übergebenen Daten darstellen. Weitere Informationen finden Sie im Abschnitt [beschreiben des Datenflusses](#DataFlows). Ein Aktivitätsdiagramm beschreibt jedoch nicht die Struktur der Daten. Zu diesem Zweck können Sie ein UML-Klassendiagramm zeichnen. Weitere Informationen finden Sie unter [UML-Klassendiagramme: Richtlinien](../modeling/uml-class-diagrams-guidelines.md).

## <a name="basic-steps-for-drawing-activity-diagrams"></a><a name="BasicSteps"></a> Grundlegende Schritte zum Zeichnen von Aktivitäts Diagrammen
 Ausführliche Schritte zum Erstellen von Modellierungs Diagrammen werden unter [Bearbeiten von UML-Modellen und-Diagrammen](../modeling/edit-uml-models-and-diagrams.md)beschrieben.

#### <a name="to-draw-an-activity-diagram"></a>So zeichnen Sie ein Aktivitätsdiagramm

1. Klicken Sie im Menü **Architektur** auf **neues UML-oder ebenendiagramm**.

2. Klicken Sie unter **Vorlagen**auf **UML-Aktivitätsdiagramm**.

3. Benennen Sie das Diagramm.

4. Wählen Sie unter **zu Modellierungsprojekt hinzufügen**ein vorhandenes Modellierungsprojekt in der Projekt Mappe aus, oder **Erstellen Sie ein neues Modellierungsprojekt**.

#### <a name="to-draw-elements-on-an-activity-diagram"></a>So zeichnen Sie Elemente in einem Aktivitätsdiagramm

1. Ziehen Sie Elemente aus der Toolbox in das Diagramm.

     Fügen Sie zunächst die Hauptaktivitäten in das Diagramm ein, verbinden Sie sie, und nehmen Sie dann letzte Änderungen vor, indem Sie z. B. den Start- und Endknoten hinzufügen.

    > [!NOTE]
    > Sie können keine vorhandenen Elemente aus dem UML-Modell-Explorer in das Diagramm ziehen.

2. Gehen Sie folgendermaßen vor, um die Elemente zu verbinden:

    1. Klicken Sie in der Toolbox **Aktivitätsdiagramm** auf **Connector**.

    2. Klicken Sie im Diagramm auf das Quellelement.

    3. Klicken Sie auf das Zielelement.

        > [!NOTE]
        > Um ein Tool mehrmals zu verwenden, doppelklicken Sie in der Toolbox auf das Tool.

#### <a name="to-move-an-activity-to-another-package"></a>So verschieben Sie eine Aktivität in ein anderes Paket

- Ziehen Sie im **UML-Modell-Explorer**die Aktivität in ein Paket.

     \- oder -

- Klicken Sie im **UML-Modell-Explorer**mit der rechten Maustaste auf die Aktivität, und klicken Sie auf **Cut** Klicken Sie dann mit der rechten Maustaste auf das Paket und dann auf **Einfügen**.

    > [!NOTE]
    > Die Aktivität wird erst dann im UML-Modell-Explorer angezeigt, wenn Sie dem Diagramm das erste Element hinzufügen.

## <a name="describing-control-flow"></a><a name="SimpleControlFlow"></a> Beschreiben der Ablauf Steuerung
 Ein Aktivitätsdiagramm beschreibt einen Geschäftsprozess oder einen Softwarealgorithmus als eine Reihe von Aktionen. Konnektorpfeile stellen dar, wie die Kontrolle nacheinander von einer Aktion an die nächste übergeben wird. Normalerweise kann eine Aktion erst gestartet werden, nachdem die vorherige Aktion abgeschlossen wurde.

 In der folgenden Beispielabbildung wird gezeigt, wie Sie eine Sequenz von Aktionen mit Aktionen, Konnektoren, Verzweigungen und Schleifen darstellen können. In den folgenden Abschnitten wird jedes Element ausführlicher erläutert.

 ![Einfaches Aktivitätsdiagramm](../modeling/media/uml-actguidectrl.png "UML_ActGuideCtrl")

 Aktivitätsdiagramme verwenden **Aktionen** und **Connectors** , um das System oder die Anwendung als eine Reihe von Aktionen zu beschreiben, bei denen das Steuerelement sequenziell von einer Aktion zum nächsten fließt.

- Erstellen Sie eine **Aktion** (1) für jede größere Aufgabe, die von einem Benutzer, dem System oder beiden in Zusammenarbeit ausgeführt wird.

  > [!NOTE]
  > Versuchen Sie, den Prozess oder Algorithmus mit nur einigen wenigen Aktionen zu beschreiben. Mithilfe von Aktionen zum Durchführen von **Aktionen** können Sie jede Aktion ausführlicher in einem separaten Diagramm definieren, wie in [beschreiben von unter Aktivitäten mit Aktionen zum Verhalten von Anrufen](#Subactivities)beschrieben.

- Stellen Sie sicher, dass der Titel jeder Aktion das standardmäßige Resultat der Aktion eindeutig angibt.

- Verknüpfen Sie die Aktionen nacheinander mit **Connectors** (2).

- Jede Aktion endet, bevor die nächste Aktion in der Ablaufsteuerung beginnt. Wenn Sie überlappende Aktionen beschreiben möchten, verwenden Sie einen **Verzweigungs Knoten** , wie im Abschnitt [parallele Flows](#Concurrent)beschrieben.

  Das Diagramm beschreibt zwar die Aktionsfolge, jedoch nicht, wie die Aktionen ausgeführt werden, oder wie die Kontrolle von einer Aktion an die nächste übergeben wird. Wenn Sie mithilfe des Diagramms einen Geschäftsprozess darstellen, kann die Kontrolle z. B. übergeben werden, wenn eine Person eine E-Mail-Nachricht an eine andere Person sendet. Wenn Sie mithilfe des Diagramms einen Softwareentwurf darstellen, wird die Kontrolle möglicherweise durch den normalen Ausführungsfluss von einer Anweisung an die nächste übergeben.

### <a name="describing-decisions-and-loops"></a>Beschreiben von Entscheidungen und Schleifen

- Verwenden Sie einen **Entscheidungs Knoten** (3), um einen Punkt anzugeben, an dem das Ergebnis einer Entscheidung den nächsten Schritt festlegt. Sie können beliebig viele ausgehende Pfade zeichnen.

- Wenn Sie mithilfe des Aktivitätsdiagramms einen Teil einer Anwendung definieren, sollten Sie die Wächter (4) definieren, um eindeutig anzugeben, unter welchen Bedingungen die einzelnen Pfade verwendet werden sollten. Klicken Sie mit der rechten Maustaste auf den Connector, klicken Sie auf **Eigenschaften**, und geben Sie im **Eigenschaften** Fenster einen Wert für das Feld **Wächter** ein.

- Es ist nicht immer erforderlich, die Wächter zu definieren. Wenn Sie z. B. mithilfe des Aktivitätsdiagramms einen Geschäftsprozess oder ein Interaktionsprotokoll beschreiben, definiert eine Verzweigung den Bereich von Optionen, die für den Benutzer oder die interagierenden Komponenten verfügbar sind.

- Verwenden Sie einen **Merge-Knoten** (5), um zwei oder mehr Alternative Flows zusammenzuführen, die an einem **Entscheidungs Knoten**verzweigt haben.

    > [!NOTE]
    > Sie sollten einen **Merge-Knoten** verwenden, um alternative Flows zusammenzuführen, anstatt die Flows bei einer Aktion zusammenzuführen. Im Beispiel wäre es nicht richtig, eine direkte Verbindung vom Entscheidungs Knoten zum **Menü Element auszuwählen**. Der Grund hierfür ist, dass eine Aktion erst gestartet wird, wenn alle Kontrollthreads an allen Eingangskonnektoren angekommen sind. Daher sollten Sie nur parallele Flüsse an einer Aktion zusammenführen. Weitere Informationen finden Sie unter [parallele Flows](#Concurrent).

- Beschreiben Sie Schleifen mithilfe von Verzweigungen, wie im Beispiel gezeigt.

    > [!NOTE]
    > Versuchen Sie, Schleifen wie in Programmcode in einer sinnvollen Struktur zu schachteln. Wenn Sie einen vorhandenen Geschäftsprozess beschreiben, lassen sich hierdurch eventuell Verbesserungsmöglichkeiten erkennen.

### <a name="starting-the-activity"></a>Starten der Aktivität
 Es gibt zwei Möglichkeiten, Einstiegspunkte einer Aktivität anzugeben:

- **Startknoten**

     Erstellen Sie einen **ersten Knoten** (6), um die erste Aktion der Aktivität anzugeben.

     Diese Methode ist besonders hilfreich, wenn Sie eine Unteraktivität beschreiben, oder wenn Sie nicht explizit angeben müssen, wodurch die Aktivität ausgelöst wird. Beispielsweise beginnt die Aktivität „Gericht bestellen“ zweifelsfrei, wenn ein Kunde hungrig wird.

- **Knoten zum Akzeptieren eines Ereignisses**

     Erstellen Sie die **Knoten "Accept Event**", wie im Abschnitt " [parallele Flows](#Concurrent)" beschrieben, um den Anfang eines Threads anzugeben, der auf ein bestimmtes Ereignis antwortet, z. b. eine Benutzereingabe. Geben Sie keinen eingehenden Fluss für den Knoten an. Wenn kein eingehender Fluss angegeben wird, bedeutet dies, dass bei jedem Eintreten des Ereignisses ein Thread gestartet wird.

     Diese Methode ist besonders hilfreich, wenn Sie eine Reaktion auf ein bestimmtes externes Ereignis beschreiben.

### <a name="ending-the-activity"></a>Beenden der Aktivität
 Verwenden Sie einen **Aktivitäts Endknoten** (7), um das Ende einer Aktivität anzugeben.

- Wenn ein Steuerungs Thread einen **Aktivitäts Endknoten**erreicht, werden alle gleichzeitigen Aktionen und unter Aktivitäten der Aktivität beendet.

- Sie können mehrere Aktivitätsendknoten verwenden, um durch eine geringere Anzahl von Konnektoren die Übersichtlichkeit zu verbessern.

### <a name="interrupting-the-activity"></a>Unterbrechen der Aktivität
 Um zu beschreiben, wie der normale Fluss einer Aktivität unterbrochen werden kann, beispielsweise wenn sich der Benutzer entscheidet, den Vorgang abzubrechen, können Sie einen Knoten zum Akzeptieren eines Ereignisses erstellen, der auf dieses Ereignis lauscht. Weitere Informationen finden Sie im Abschnitt [parallele Flows](#Concurrent). Erstellen Sie eine Ablaufsteuerung von diesem Knoten zu einem Aktivitätsendknoten (7).

### <a name="swimlanes"></a>Swimlanes
 Manchmal ist es sinnvoll, die Aktionen einer Aktivität in Bereiche aufzuteilen, die unterschiedlichen Objekten oder Geschäftsrollen entsprechen, die die Aktionen ausführen. Diese Bereiche sind konventionell in Spalten angeordnet und werden als *Verantwortlichkeits Bereiche*bezeichnet.

- Verwenden Sie Linien oder Rechtecke aus dem Abschnitt **einfache Formen** der Toolbox, um Verantwortlichkeits Bereiche oder andere Bereiche zu zeichnen.

- Um jede Swimlane zu bezeichnen, erstellen Sie einen Kommentar, und legen Sie die **transparente** Eigenschaft auf **true**fest.

  Einfache Formen sind kein Bestandteil des UML-Modells und werden nicht im UML-Modell-Explorer angezeigt.

## <a name="describing-data-flow"></a><a name="DataFlows"></a> Beschreiben des Datenflusses
 Sie können die eingehenden und ausgehenden Daten einer Aktivität auf zweierlei Weise beschreiben:

- Verwenden Sie einen **Objekt Knoten**. Dies ist die einfachste Methode, um die zwischen Aktivitäten fließenden Informationen zu beschreiben. Ein Objektknoten ist mit einer Variablen in einem Programm vergleichbar. Er stellt ein Element dar, das einen oder mehrere Werte speichert, die zwischen Aktionen übergeben werden.

- Verwenden Sie eine **Ausgabepin** und eine **Eingabe-PIN**. Mit dieser Methode können Sie die Ausgaben einer Aktion und die Eingaben einer anderen Aktion getrennt beschreiben. Pins sind mit Parametern in einem Programm vergleichbar. Pins stellen Ports dar, an denen Objekte in eine Aktion eintreten und eine Aktion verlassen können.

    > [!NOTE]
    > Eine Übersicht über die in diesem Abschnitt verwendeten Elemente finden Sie im Abschnitt Datenflüsse des Themas siehe UML- [Aktivitätsdiagramme: Referenz](../modeling/uml-activity-diagrams-reference.md).

### <a name="describing-data-flow-with-object-nodes"></a>Beschreiben des Datenflusses mit Objektknoten
 Die meisten Ablaufsteuerungen übertragen Daten. Beispielsweise überträgt der Ausgabefluss der Aktion „Kunde gibt Details an“ einen Verweis auf die Lieferadresse.

 Wenn Sie diese Daten im Diagramm beschreiben möchten, können Sie einen Konnektor durch einen Objektknoten und zwei Konnektoren ersetzen, wie in der folgenden Abbildung gezeigt.

 ![Objektknoten können zwischen Aktionen übergebene Daten anzeigen](../modeling/media/uml-actguidedata.png "UML_ActGuideData")

 Beachten Sie, dass die Rechtecke mit abgerundeten Ecken, z. B. „Waren senden“, Aktionen darstellen, bei denen eine Verarbeitung erfolgt. Die Rechtecke mit rechtwinkligen Ecken, z. B. „Lieferadresse“, stellen einen Fluss von Objekten zwischen zwei Aktionen dar.

 Weisen Sie dem Objektknoten einen Namen zu, der die Rolle des Knotens als Kanal oder Puffer der Objekte widerspiegelt, die zwischen den Aktionen übertragen werden.

 Sie können den **Typ** des Objekt Knotens im Eigenschaftenfenster festlegen. Der Typ kann ein primitiver Typ wie z. B. „Integer“ oder eine Klasse, Schnittstelle oder Enumeration sein, die Sie in einem Klassendiagramm definiert haben. Sie können z. B. die Klasse „Lieferadresse“ mit den Attributen „Anschrift“, „Ort“ usw. zusammen mit einer Zuordnung zur Klasse „Kunde“ erstellen. Weitere Informationen finden Sie unter [UML-Klassendiagramme: Richtlinien](../modeling/uml-class-diagrams-guidelines.md).

> [!NOTE]
> Wenn Sie den Namen eines Typs eingeben, der noch nicht definiert wurde, wird im UML-Modell-Explorer unter **nicht angegebene Typen** ein Element hinzugefügt. Wenn Sie anschließend einen Typ dieses Namens in einem Klassendiagramm definieren, setzen Sie den Typ des Objektknotens zurück, sodass er auf den neuen Typ verweist.

#### <a name="buffering-data-in-object-nodes"></a>Puffern von Daten in Objektknoten
 Ein Objektknoten kann als Puffer für mehrere Objekte fungieren. In der folgenden Abbildung zeigt die Ablaufsteuerung, dass der Benutzer die Schleife „[weitere auswählen]“ (1) mehrfach durchlaufen kann, während die vom Benutzer ausgewählten Gerichte im Objektknoten „Gewählte Gerichte“ (2) gesammelt werden. Wenn schließlich die Auswahl durch den Benutzer abgeschlossen ist, geht die Kontrolle an die Aktion „Bestellung bestätigen“ (3) über, mit der die vollständige Liste der ausgewählten Elemente aus dem Puffer „Gewählte Gerichte“ akzeptiert wird.

 ![Puffern von Daten in Objektknoten](../modeling/media/uml-actguidebuffer.png "UML_ActGuideBuffer")

 Sie können angeben, wie die Elemente in einem Puffer gespeichert werden, indem Sie Eigenschaften des Objektknotens festlegen:

- Legen Sie die Eigenschaft **Order** fest:

  - **Unsortiert** , um eine zufällige oder nicht angegebene Reihenfolge anzugeben. (Standardeinstellung)

  - **Sortiert** , um eine Bestellung entsprechend einem bestimmten Schlüssel anzugeben.

  - **FIFO** zum Angeben einer Reihenfolge von First in, First out.

  - **LIFO** , um die Reihenfolge von Last in, First Out anzugeben.

- Legen Sie die Eigenschaft **obere Grenze** fest, um die maximale Anzahl von Objekten anzugeben, die im Puffer enthalten sein können. Der Standardwert ist *. Dies bedeutet, dass keine Begrenzung definiert ist.

### <a name="describing-data-flow-with-input-and-output-pins"></a>Beschreiben des Datenflusses mit Eingabe- und Ausgabepins
 Verwenden Sie eine **Ausgabepin** und eine **Eingabe-PIN** , um die Ausgaben einer Aktion und die Eingaben in eine andere separat zu beschreiben.

 ![Eingabe- und Ausgabepins sind Aktionsparameter](../modeling/media/uml-actguidepins.png "UML_ActGuidePins")

 Klicken Sie zum Erstellen einer PIN auf **Eingabe-PIN** oder **Ausgabepin** in der Toolbox, und klicken Sie dann auf eine Aktion. Anschließend können Sie den Pin im Umkreis der Aktion verschieben und seinen Namen ändern. Sie können Eingabe-und Ausgabe Pins für jede Art von Aktion erstellen, einschließlich **Aktionen zum Anfügen von Verhalten**, Aktionen für den **Vorgang**zum **Senden von Signalen**und zum **akzeptieren von Ereignis Aktionen**.

 Ein Konnektor zwischen zwei Pins stellt ebenso wie die Flüsse zu und von einem Objektknoten einen Objektfluss dar.

 Weisen Sie jedem Pin einen Namen zu, der die Rolle der von ihm erzeugten bzw. akzeptierten Objekte angibt, z. B. einen Parameternamen.

 Sie können den Typ der in der **Type** -Eigenschaft übertragenen Objekte festlegen. Dies muss ein Typ sein, den Sie in einem UML-Klassendiagramm erstellt haben.

 Die Objekte, die zwischen verbundenen Pins übertragen werden, müssen auf irgendeine Weise kompatibel sein. Beispielsweise können sie kompatibel sein, weil der Typ der vom Ausgabepin erzeugten Objekte vom Typ des Eingabepins abgeleitet wird.

 Alternativ können Sie angeben, dass der Objektfluss eine Transformation einschließt, mit der Daten vom Typ des Ausgabepins in den Typ des Eingabepins (oder umgekehrt) konvertiert werden. Die häufigste Transformation dieser Art extrahiert einfach den entsprechenden Teil aus einem größeren Typ. Im Beispiel in der Abbildung wird eine Transformation vorausgesetzt, die die Lieferadresse aus den Bestellungsdetails extrahiert.

## <a name="defining-an-action-in-more-detail"></a><a name="Details"></a> Definieren einer Aktion im Detail
 Sie können nicht nur das normalerweise zu erzielende Ergebnis einer Aktion anhand ihres Namens angeben, sondern einer Aktion mit den folgenden Methoden auch weitere Informationen hinzufügen:

- Schreiben Sie in der **Body** -Eigenschaft eine ausführlichere Beschreibung. Sie können z. B. ein Fragment von Programmcode oder Pseudocode oder eine vollständige Beschreibung der erzielten Ergebnisse schreiben.

- Ersetzen Sie die Aktion durch eine Aktion zum Aufrufen eines Verhaltens, und beschreiben Sie das ausführliche Verhalten in einem eigenen Aktivitätsdiagramm. Weitere Informationen finden Sie [unter beschreiben von unter Aktivitäten mit Aktionen zum](#Subactivities)Anzeigen eines Verhaltens

- Legen Sie die Eigenschaften lokale nach Bedingungen und **lokale** **Vorbedingungen** der Aktion fest, um das Ergebnis in spezifischeren Details zu beschreiben. Weitere Informationen finden Sie unter [Definieren von nach Bedingungen und Vorbedingungen](#Postcondition).

### <a name="describing-sub-activities-with-call-behavior-actions"></a><a name="Subactivities"></a> Beschreiben von unter Aktivitäten mit Aktionen zum Verhalten von Anrufen
 Sie können das Verhalten einer Aktion mithilfe eines eigenen Aktivitätsdiagramms ausführlich beschreiben. Ein aufgerufenes Verhalten ist ein Aktivitätsdiagramm, das im Hauptaktivitätsdiagramm durch eine Aktion zum Aufrufen eines Verhaltens dargestellt wird. Sie können mit der Aktion zum Aufrufen eines Verhaltens auch Verhalten beschreiben, das unterschiedlichen Aktivitäten gemeinsam ist, sodass Sie die Unteraktivität nicht mehrmals zeichnen müssen.

 In der folgenden Abbildung zeigt Diagramm 1 eine Aktivität, die über eine Aktion zum Aufrufen eines Verhaltens verfügt, und Diagramm 2 zeigt das Unteraktivitätsdiagramm, in dem das aufgerufene Verhalten dargestellt wird.

 ![Separates Aktivitätsdiagramm mit ausführlichen Aktionen](../modeling/media/uml-actguidedetail.png "UML_ActGuideDetail")

##### <a name="to-describe-a-sub-activity-with-a-call-behavior-action"></a>So beschreiben Sie eine Unteraktivität mit einer Aktion zum Aufrufen eines Verhaltens

1. Um das Diagramm für die Unteraktivität zu erstellen, klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf das Modellierungsprojekt, zeigen Sie auf **Hinzufügen**, und klicken Sie dann auf **Neues Element**.

2. Klicken Sie im Dialogfeld **Neues Element hinzufügen** unter **Vorlagen** auf **Aktivitätsdiagramm** , und geben Sie im Feld **Name** den Namen ein, den Sie für die **Aktion zum Anrufen von Anrufen**planen.

3. Zeichnen Sie den ausführlichen Arbeitsfluss für die Unteraktivität. Dies ist das aufgerufene Verhalten.

    - Im aufgerufenen unter Aktivitätsdiagramm gibt der **anfängliche Knoten** an, wo das-Steuerelement beginnt, wenn das aufgerufene Verhalten aufgerufen wird. Der **Aktivitäts Endknoten** zeigt an, wohin das Steuerelement zur übergeordneten Aktivität zurückkehren soll.

4. Legen Sie die Eigenschaft **Verhalten** der **Aktion Aufruf Verhalten** so fest, dass Sie auf das aufgerufene Verhaltens Diagramm verweist.

    > [!NOTE]
    > Das unter Aktivitätsdiagramm muss einige Elemente enthalten, oder das Diagramm ist nicht in der Dropdown Liste für die **Behavior** -Eigenschaft verfügbar. Außerdem wird das Trident-Symbol nicht in der Form vom Typ " **aufrufsverhaltenaktion** " angezeigt, bis Sie seine **Verhaltens** Eigenschaft festlegen.

5. Legen Sie die Eigenschaft **ist synchron** der Aktion fest, um anzugeben, ob die Aktivität darauf wartet, dass die aufgerufene Aktivität beendet wird.

    - Wenn Sie den Wert synchron auf false festlegen, werden Sie angeben, dass der Flow mit der nächsten Aktion fortgesetzt werden kann, bevor die aufgerufene Aktivität abgeschlossen **wird** . Definieren Sie keine Ausgabepins oder ausgehenden Datenflüsse von der Aktion.

### <a name="describing-data-flow-in-and-out-of-sub-activities"></a>Beschreiben des Datenflusses in und aus Unteraktivitäten
 Sie können den Datenfluss in und aus Unteraktivitäten auf die gleiche Weise wie die Verwendung von Parametern in Software beschreiben.

- Erstellen Sie in der Aktion zum Aufrufen eines Verhaltens Eingabe- und Ausgabepins (1) für jedes Datenelement, das in die Aktion oder aus der Aktion fließt. Weisen Sie jedem Pin einen entsprechenden Namen zu.

- Erstellen Sie im unter Aktivitätsdiagramm einen **Aktivitäts Parameter Knoten** (2) für jede Eingabe-und Ausgabepin in der aufrufenden Aktion. Weisen Sie jedem Knoten den gleichen Namen wie dem entsprechenden Pin zu.

  > [!NOTE]
  > Ein Aktivitätsparameterknoten ähnelt einem Objektknoten. Klicken Sie mit der rechten Maustaste auf den Knoten, und klicken Sie dann auf **Eigenschaften**, um zu überprüfen, welche Art von Knoten Sie sich ansehen. Der Typ des Knotens wird in der Kopfzeile des Eigenschaftenfensters angezeigt.

- Zeichnen Sie im Unteraktivitätsdiagramm Konnektoren, die den Fluss von Objekten in die oder aus den einzelnen Aktivitätsparameterknoten darstellen.

  ![Pins werden beim Aufrufen eines Verhaltens Aktivitätsparametern zugeordnet](../modeling/media/uml-actguidesub.png "UML_ActGuideSub")

### <a name="defining-postconditions-and-preconditions"></a><a name="Postcondition"></a> Definieren von nach Bedingungen und Vorbedingungen
 Mithilfe der Eigenschaften lokale nach Bedingungen und **lokale** **Vorbedingungen** können Sie das Ergebnis einer Aktion ausführlich angeben. Diese Eigenschaften beschreiben die Auswirkung der Aktion, jedoch nicht, wie die Auswirkung erreicht wird.

 Klicken Sie zum Festlegen dieser Eigenschaften mit der rechten Maustaste auf die Aktion, und klicken Sie dann auf **Eigenschaften**. Geben Sie Werte in die Eigenschaftenfelder im Eigenschaftenfenster ein.

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

- Sie können die Eigenschaft **ist synchron** der Aktion festlegen, um anzugeben, ob die Aktivität auf den Abschluss des Vorgangs wartet.

  - Wenn Sie den Wert **synchron** auf false festlegen, werden Sie angeben, dass der Flow mit der nächsten Aktion fortgesetzt werden kann, bevor der aufgerufene Vorgang beendet wird. Definieren Sie keine Ausgabepins oder ausgehenden Datenflüsse von der Aktion.

## <a name="concurrent-flows"></a><a name="Concurrent"></a> Parallele Flows
 Sie können den **Verzweigungs Knoten** und den **joinknoten** verwenden, um zwei oder mehr Threads von Aktivitäten zu beschreiben, die gleichzeitig ausgeführt werden können.

 ![Die Zweig- und Joinknoten zeigen gleichzeitige Flüsse an](../modeling/media/uml-actguideconcurrent.png "UML_ActGuideConcurrent")

 Der **Verzweigungs Knoten** (1) bewirkt, dass der Steuerungs Thread in zwei oder mehr Threads aufgeteilt wird. Wenn die vorherige Aktion endet, können alle Aktionen auf der Ausgabeseite der Gabelung beginnen.

 Ein **joinknoten** (2) führt gleichzeitige Threads zusammen. Die Aktion nach dem **joinknoten** wird möglicherweise erst gestartet, wenn alle Aktionen, die zum **joinknoten** führen, vollständig ausgeführt werden.

### <a name="describing-signals-and-events"></a>Beschreiben von Signalen und Ereignissen
 Sie können einen Schritt in einem Prozess, der ein Signal sendet, als Aktion zum Senden eines Signals in einer Aktivität darstellen. Einen Schritt, der erst nach einem bestimmten Signal oder Ereignis fortgesetzt werden kann, können Sie als Aktion zum Akzeptieren eines Ereignisses darstellen.

 Beispielsweise können Sie einen Schritt darstellen, der eine Bestellung sendet, und dann einen weiteren Schritt, der die Bestellung empfangen muss, bevor er sie verarbeitet.

#### <a name="sending-a-signal"></a>Senden eines Signals
 Verwenden Sie eine Aktion zum Senden eines Signals (3), um anzugeben, dass ein Signal oder eine Meldung an andere Aktivitäten oder Prozesse gesendet wird. Geben Sie mit dem Namen der Aktion an, welche Art von Meldung von der Aktion gesendet wird.

- Die Kontrolle wird sofort an die nächste Aktion in der Ablaufsteuerung übergeben, sofern vorhanden.

- Sie können mit einer Aktion zum Senden eines Signals nicht beschreiben, wie der Prozess auf zurückgegebene Informationen reagiert. Verwenden Sie hierzu eine eigene Aktion zum Akzeptieren eines Ereignisses.

- Sie können den eingehenden Datenfluss einer Aktion zum Senden eines Signals darstellen, um anzugeben, welche Daten mit der ausgehenden Meldung gesendet werden können. Weitere Informationen finden Sie unter [beschreiben des Datenflusses](#DataFlows).

#### <a name="waiting-for-a-signal-or-event"></a>Warten auf ein Signal oder Ereignis
 Verwenden Sie eine Aktion zum Akzeptieren eines Ereignisses (4), um anzugeben, dass diese Aktivität auf ein externes Ereignis oder eine externe eingehende Meldung wartet. Geben Sie mit dem Namen der Aktion den Typ des Ereignisses an, auf das die Aktion wartet.

- Um darzustellen, dass die Aktivität an einem bestimmten Punkt im Fluss auf ein externes Ereignis oder eine externe Meldung wartet, zeichnen Sie an der entsprechenden Stelle in der Aktivität eine Aktion zum Akzeptieren eines Ereignisses mit einem eingehenden Fluss.

- Um darzustellen, dass die Aktivität jederzeit auf ein externes Ereignis oder eine externe Meldung reagieren kann, zeichnen Sie eine Aktion zum Akzeptieren eines Ereignisses ohne eingehenden Fluss. Wenn das benannte externe Ereignis eintritt, beginnt in der Aktivität ein neuer Thread beginnend mit der Aktion zum Akzeptieren eines Ereignisses.

- Sie können mithilfe einer Aktion zum Akzeptieren eines Ereignisses keinen vom Absender des Signals zurückgegebenen Wert beschreiben. Verwenden Sie hierzu eine eigene Aktion zum Senden eines Signals.

- Sie können ausgehende Datenflüsse der Aktion darstellen, um zu zeigen, wie die Aktivität empfangene Daten des Signals verarbeitet. Wenn Sie mehr als einen Ausgabe Fluss anzeigen möchten, sollten Sie die **IsUnmarshall** -Eigenschaft der Aktion Ereignis akzeptieren festlegen, die angibt, dass die Aktion das eingehende Signal in seine separaten Komponenten analysiert. Weitere Informationen finden Sie unter [beschreiben des Datenflusses](#DataFlows).

### <a name="describing-multiple-data-flows"></a>Beschreiben von mehreren Datenflüssen
 Sie können mehrere ausgehende Ablaufsteuerungen oder Objektflüsse einer Aktion zeichnen, um anzugeben, dass am Ende der Aktion mehrere Threads entstehen. Das Resultat ähnelt dem Ergebnis einer Gabelung, mit der Ausnahme, dass Sie eine Kombination von Ablaufsteuerungen und Objektflüssen verwenden können.

 Im folgenden Beispiel werden mehrere eingehende und ausgehende Flüsse von Aktionen gezeigt.

 ![Parallele Objektflüsse](../modeling/media/uml-actguidemulti.png "UML_ActGuideMulti")

 Wenn die Aktion „Kunde stellt genau Daten bereit“ abgeschlossen wird, erzeugt sie zwei Objekte: „Lieferadresse“ und „Kreditkartendetails“. Die beiden Objekte werden anschließend durch unterschiedliche Aktionen verarbeitet.

 Da eine Aktion erst beginnen kann, wenn alle zugehörigen Eingaben verfügbar sind, beginnt die letzte Aktion erst, wenn alle zu ihr führenden Aktionen abgeschlossen sind.

### <a name="streams"></a>Datenströme
 Sie können mit einem Aktivitätsdiagramm eine Pipeline oder eine Reihe von Aktionen beschreiben, die gleichzeitig ausgeführt werden und kontinuierlich Daten von einer Aktion an eine andere übergeben.

 Im folgenden Beispiel soll jede Aktion Objekte erzeugen können, während sie weiterhin ausgeführt wird. Da keine Ablaufsteuerungen vorhanden sind, kann jede Aktion beginnen, sobald sie die ersten Objekte empfängt.

 Beachten Sie, dass die Konnektoren in diesem Beispiel Objektflüsse sind, da sie alle über mindestens ein Ende in einem Aktivitätsparameterknoten, Objektknoten bzw. auf einem Eingabe- oder Ausgabepin verfügen.

 ![Datenfluss](../modeling/media/uml-actguidestream.png "UML_ActGuideStream")

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

  ![In einem anderen Diagramm definierte Objekttransformation](../modeling/media/uml-actguidetransform.png "UML_ActGuideTransform")

  Sie können eine Transformation oder Auswahl auf zweierlei Weise angeben:

- Fügen Sie einen Kommentar an den Eingabe- oder Ausgabepin an.

  - Um diese Beschreibung von einem allgemeinen Kommentar zu unterscheiden, können Sie den Kommentar mit <\<**transformation**>> oder <\<**selection**>> beginnen.

- Geben Sie die Details der Transformation oder Auswahl in einem eigenen Aktivitätsdiagramm an.

  - Wenn Sie diese Methode verwenden, fügen Sie auch einen Kommentar an, um für die Leser deutlich zu machen, dass die Transformation definiert wurde.

##### <a name="to-specify-a-transformation-or-selection-in-a-separate-activity-diagram"></a>So geben Sie eine Transformation oder Auswahl in einem eigenen Aktivitätsdiagramm an

1. Erstellen Sie ein neues Aktivitätsdiagramm, in dem der Transformations- oder Auswahlfluss beschrieben werden soll.

   - Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf das Projekt, zeigen Sie auf **Hinzufügen**, klicken Sie auf **Neues Element**, und klicken Sie dann auf **Aktivitätsdiagramm**. Weisen Sie dem Diagramm einen entsprechenden Namen für den Transformations- oder Auswahlfluss zu. Klicken Sie auf **Hinzufügen**.

2. Führen Sie im neuen Diagramm die folgenden Schritte aus:

   1. Erstellen Sie zwei Aktivitätsparameterknoten, einen für den Eingabefluss und einen für die Ausgabe.

   2. Erstellen Sie mit Objektflüssen verbundene Aktionen. Dies veranschaulicht die Funktionsweise der Transformation oder Auswahl.

3. Führen Sie in jedem Diagramm, in dem Sie die Transformation oder Auswahl verwenden möchten, die folgenden Schritte aus:

   1. Erstellen Sie einen Objektfluss, d. h. einen Konnektor zu oder von einem Eingabepin, Ausgabepin, Objektknoten oder Aktivitätsparameterknoten.

   2. Klicken Sie mit der rechten Maustaste auf den Objekt Fluss und dann auf **Eigenschaften**.

   3. Wählen Sie in der **Transformations** -oder **Auswahl** Eigenschaft das Diagramm aus, in dem Sie den Transformations-oder Auswahl Fluss angegeben haben.

   Sie können auch eine Auswahl für einen Objektknoten sowie für einzelne Eingabe- und Ausgabepins definieren. Definieren Sie eine auswahlaktivität wie in der vorherigen Prozedur, und legen Sie dann die **Auswahl** Eigenschaft des Objekt Knotens oder die Eingabe-oder Ausgabe-PIN fest.

## <a name="see-also"></a>Weitere Informationen
 [Bearbeiten von UML-Modellen und-Diagrammen](../modeling/edit-uml-models-and-diagrams.md) [UML-Sequenzdiagramme: Referenz](../modeling/uml-sequence-diagrams-reference.md) zu [UML-Komponenten Diagrammen: Referenz](../modeling/uml-component-diagrams-reference.md) [UML-Anwendungsfall Diagramme: Referenz](../modeling/uml-use-case-diagrams-reference.md) zu [UML-Klassendiagrammen: Referenz](../modeling/uml-class-diagrams-reference.md) [UML-Komponenten Diagramme: Referenz](../modeling/uml-component-diagrams-reference.md) [Video: Erfassen von Geschäfts Workflows mithilfe von Aktivitäts Diagrammen](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-4-capture-business-workflows)
