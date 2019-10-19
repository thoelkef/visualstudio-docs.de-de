---
title: 'UML-Sequenzdiagramme: Richtlinien | Microsoft-Dokumentation'
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
ms.openlocfilehash: 88c72ecaf44855badfd42456d9818f2ba9168a49
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661731"
---
# <a name="uml-sequence-diagrams-guidelines"></a>UML Sequence Diagrams: Guidelines
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio können Sie ein *Sequenzdiagramm* zeichnen, um eine Interaktion anzuzeigen. Eine Interaktion ist eine Sequenz von Meldungen zwischen typischen Instanzen von Klassen, Komponenten, Subsystemen oder Akteuren.

 UML-Sequenzdiagramme sind Teil eines UML-Modells und nur innerhalb von UML-Modellierungsprojekten vorhanden. Um ein UML-Sequenzdiagramm zu erstellen, klicken Sie im Menü **Architektur** auf **neues UML-oder ebenendiagramm**. Erfahren Sie mehr über [UML-Sequenzdiagramm Elemente](../modeling/uml-sequence-diagrams-reference.md) oder [UML-Modellierungs Diagramme](../modeling/edit-uml-models-and-diagrams.md) im Allgemeinen. Eine videodemo finden Sie unter [Verwenden von Sequenzdiagrammen (2010)](http://channel9.msdn.com/Blogs/clinted/UML-with-VS-2010-Part-7-Sketching-Interactions-with-Sequence-Diagrams).

 Welche Versionen von Visual Studio dieses Features unterstützen, erfahren Sie unter [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="in-this-topic"></a>In diesem Thema
 [Verwenden von UML-Sequenzdiagrammen](#Using)

 [Grundlegende Schritte zum Zeichnen von Sequenzdiagrammen](#BasicSteps)

 [Erstellen und Verwenden von einfachen Sequenzdiagrammen](#Simple)

 [Klassen und Lebenslinien](#ClassesAndLifelines)

 [Erstellen von wiederverwendbaren Interaktions Sequenzen](#Multiple)

 [Reduzieren von Lebenslinien Gruppen](#Collapse)

 [Beschreiben von Steuerungsstrukturen mit Fragmenten](#Fragments)

## <a name="Using"></a>Verwenden von UML-Sequenzdiagrammen
 Sie können Sequenzdiagramme für eine Vielzahl von Zwecken auf unterschiedlichen Programmdetailebenen verwenden. Nachfolgend sind typische Situationen aufgeführt, in denen Sequenzdiagramme gezeichnet werden:

- Wenn Sie über ein Anwendungsfalldiagramm verfügen, das Systembenutzer und ihre Ziele zusammenfasst, können Sie Sequenzdiagramme zeichnen, um zu beschreiben, wie die Hauptkomponenten des Systems interagieren, um das Ziel der einzelnen Anwendungsfälle zu erreichen. Weitere Informationen finden Sie unter [UML-Anwendungsfall Diagramme: Richtlinien](../modeling/uml-use-case-diagrams-guidelines.md).

- Wenn Sie Nachrichten identifiziert haben, die bei einer Schnittstelle einer Komponente eingehen, können Sie Sequenzdiagramme zeichnen, um zu beschreiben, wie die internen Teile der Komponente interagieren, um das für die einzelnen eingehenden Meldungen erforderliche Ergebnis zu erzielen. Weitere Informationen finden Sie unter [UML-Komponenten Diagramme: Richtlinien](../modeling/uml-component-diagrams-guidelines.md).

  Das Zeichnen von Sequenzdiagrammen hat mehrere Vorteile:

- Sie können leicht erkennen, wie Aufgaben zwischen Komponenten verteilt sind.

- Sie können Interaktionsmuster identifizieren, die die Aktualisierung der Software erschweren.

## <a name="relationship-to-other-diagrams"></a>Beziehung zu anderen Diagrammen
 Sie können UML-Sequenzdiagramme auf verschiedene Arten zusammen mit anderen Diagrammen verwenden.

#### <a name="lifelines-and-types"></a>Lebenslinien und Typen
 Die Lebenslinien, die Sie in einem Sequenzdiagramm zeichnen, können typische Instanzen der Komponenten oder Klassen im System darstellen. Sie können Lebenslinien aus Typen und Typen aus Lebenslinien erstellen und die Typen in UML-Klassendiagrammen und UML-Komponentendiagrammen anzeigen. Weitere Informationen finden Sie unter [Klassen und Lebenslinien](#ClassesAndLifelines).

#### <a name="parameter-types"></a>Parametertypen
 Sie können in einem UML-Klassendiagramm auch die Typen der Parameter und der zurückgegebenen Werte beschreiben, die in den zwischen den Lebenslinien gesendeten Meldungen verwendet wurden.

#### <a name="use-case-details"></a>Anwendungsfalldetails
 Ein Anwendungsfall stellt das Ziel eines Benutzers zusammen mit einer Sequenz von Schritten zum Erreichen des Ziels dar. Die Sequenz der Schritte kann auf verschiedene Weise beschrieben werden. Eine Option besteht im Zeichnen eines Sequenzdiagramms, das die Interaktionen zwischen den Benutzern und den Hauptkomponenten des Systems zeigt. Weitere Informationen finden Sie unter [UML-Anwendungsfall Diagramme: Richtlinien](../modeling/uml-use-case-diagrams-guidelines.md).

## <a name="BasicSteps"></a>Grundlegende Schritte zum Zeichnen von Sequenzdiagrammen
 Eine umfassende Liste der Elemente in Sequenzdiagrammen finden Sie unter [UML-Sequenzdiagramme: Referenz](../modeling/uml-sequence-diagrams-reference.md).

> [!NOTE]
> Ausführliche Schritte zum Erstellen von Modellierungs Diagrammen finden Sie unter [Bearbeiten von UML-Modellen und-Diagrammen](../modeling/edit-uml-models-and-diagrams.md).

#### <a name="to-create-a-sequence-diagram"></a>So erstellen Sie ein Sequenzdiagramm

1. Klicken Sie im Menü **Architektur** auf **neues UML-oder ebenendiagramm**.

2. Klicken Sie unter **Vorlagen**auf **UML-Sequenzdiagramm**.

3. Benennen Sie das Diagramm.

4. Wählen Sie unter **zu Modellierungsprojekt hinzufügen**ein vorhandenes Modellierungsprojekt in der Projekt Mappe aus, oder **Erstellen Sie ein neues Modellierungsprojekt**, und klicken Sie dann auf **OK**.

    Ein neues Sequenzdiagramm wird mit der Toolbox **Sequenzdiagramm** angezeigt. Die Toolbox enthält die erforderlichen Elemente und Konnektoren.

   ![Teile eines Sequenz Diagramms](../modeling/media/uml-sequence.png "UML_Sequence")

#### <a name="to-draw-a-sequence-diagram"></a>So zeichnen Sie ein Sequenzdiagramm

1. Ziehen Sie Lebens **Linien** (1) aus der **Toolbox** auf das Diagramm, um Instanzen von Klassen, Komponenten, Actors oder Geräten darzustellen.

    > [!NOTE]
    > Sie können auch eine Lebenslinie erstellen, indem Sie eine vorhandene Klasse, Schnittstelle, Actor oder Komponente aus dem **UML-Modell-Explorer** in das Diagramm ziehen. Dadurch wird eine Lebenslinie erstellt, die eine Instanz des ausgewählten Typs darstellt.

2. Zeichnen Sie Meldungen, um darzustellen, wie die Lebenslinien zusammenarbeiten, um ein bestimmtes Ziel zu erreichen.

     Um eine Meldung (3, 4, 6, 7) zu erstellen, klicken Sie auf ein Meldungstool. Klicken Sie dann an dem Punkt auf die sendende Lebenslinie, an dem die Meldung beginnen soll, und klicken Sie anschließend auf die empfangende Lebenslinie.

     An der empfangenden Lebenslinie wird eine Vorkommnisausführung (5) angezeigt. Die Vorkommnisausführung stellt einen Zeitraum dar, während dem die Instanz eine Methode ausführt. Sie können andere Meldungen erstellen, die an einer Vorkommnisausführung beginnen.

3. Zum Anzeigen einer Meldung, die aus einer unbekannten Ereignisquelle (9) stammt oder an unbekannte Empfänger (10) überträgt, zeichnen Sie eine asynchrone Meldung von oder zu einem Leerraum im Diagramm. Diese Nachrichten werden als *gefundene Meldungen* (9) und *verlorene Nachrichten* (10) bezeichnet.

    > [!NOTE]
    > Um eine Gruppe von Lebenslinien zu verschieben, die über verlorene oder gefundene Meldungen verfügen, führen Sie die folgenden Schritte aus, um die Lebenslinien vor dem Verschieben auszuwählen: Zeichnen Sie ein Rechteck um diese Lebenslinien, oder halten Sie die **STRG** -Taste gedrückt, während Sie auf die einzelnen Lebenslinien klicken. Wenn Sie alle **auswählen** oder **STRG** +**A** verwenden, um alle Lebenslinien auszuwählen, und Sie dann verschieben, werden verlorene oder gefundene Meldungen, die diesen Lebenslinien zugeordnet sind, nicht verschoben. Wenn diese Situation eintritt, können Sie diese Meldungen separat verschieben.

4. Zeichnen Sie Sequenzdiagramme für jede wichtige Meldung in der gleichen Komponente oder im gleichen System.

#### <a name="to-change-the-order-of-messages"></a>So ändern Sie die Reihenfolge der Meldungen

- Ziehen Sie eine Meldung in der zugehörigen Lebenslinie aufwärts oder abwärts. Sie können sie über andere Meldungen oder in einen bzw. aus einem Ausführungsblock ziehen.

     \- oder -

- Klicken Sie auf die Meldung, und verwenden Sie die nach- **oben** -und **nach-unten** -Taste, um die Nachrichten Verwenden Sie **UMSCHALT +** nach-oben und **UMSCHALT + nach-unten-Taste** , um die Reihenfolge der Meldungen zu ändern.

#### <a name="to-move-or-copy-message-sequences-on-the-sequence-diagram"></a>So verschieben oder kopieren Sie Meldungssequenzen im Sequenzdiagramm

1. Klicken Sie mit der rechten Maustaste auf eine Meldung (3, 4), und klicken Sie dann auf **Kopieren**.

2. Klicken Sie mit der rechten Maustaste auf die Ausführung (5) oder eine Lebenslinie (1), von der die neue Nachricht gesendet werden soll, und klicken Sie dann auf **Einfügen**. Der neue Absender kann sich in einem anderen Diagramm befinden.

     Eine Kopie der Meldung und all ihrer untergeordneten Meldungen wird am Ende der Vorkommnisausführung oder am Ende der Lebenslinie hinzugefügt.

    > [!NOTE]
    > Die eingefügte Meldung wird immer am Ende der Vorkommnisausführung oder der Lebenslinie angezeigt. Nachdem Sie sie eingefügt haben, können Sie sie an eine höhere Position ziehen.

#### <a name="to-display-and-edit-the-signature-text-for-a-message"></a>So zeigen Sie den Signaturtext einer Meldung an und bearbeiten ihn

- Die Ziel-Lebenslinie muss an Typen gebunden oder Typen zugeordnet sein, damit der Signaturtext sichtbar ist. Um diese Aufgabe auszuführen, führen Sie einen der folgenden Schritte aus:

  - Klicken Sie mit der rechten Maustaste auf die Lebenslinie, und wählen Sie dann **Klasse erstellen**.

     - oder -

  - Wählen Sie die Lebenslinie aus, drücken Sie **F4**, und legen Sie dann im **Eigenschaften** Fenster die **Type** -Eigenschaft auf einen vorhandenen Typ fest, oder geben Sie den Namen für einen neuen Typ an. Klicken Sie mit der rechten Maustaste auf die Bezeichnung Nachricht, und wählen Sie dann **Vorgang erstellen**aus.

    Der Signaturtext wird unterhalb der Meldungsbezeichnung angezeigt. Sie können den Signaturtext jetzt bearbeiten. Weitere Informationen finden Sie unter [Klassen und Lebenslinien](#ClassesAndLifelines).

#### <a name="to-improve-the-layout-of-a-sequence-diagram"></a>So verbessern Sie das Layout eines Sequenzdiagramms

- Klicken Sie mit der rechten Maustaste auf einen leeren Bereich des Diagramms, und klicken Sie dann auf **Layout neu anordnen**.

- Um den Vorgang rückgängig zu machen, klicken Sie auf **Bearbeiten**und dann auf **Rückgängig**.

#### <a name="to-change-the-package-that-owns-the-interaction"></a>So ändern Sie das Paket, das die Interaktion besitzt

1. Suchen Sie im **UML-Modell-Explorer**die Interaktion, die im Sequenzdiagramm angezeigt wird.

    > [!NOTE]
    > Die Interaktion wird erst dann im **UML-Modell-Explorer** angezeigt, wenn Sie die erste Lebenslinie zum Sequenzdiagramm hinzufügen.

2. Ziehen Sie die Interaktion in das Paket.

     \- oder -

     Klicken Sie mit der rechten Maustaste auf die Interaktion und dann auf **Ausschneiden**. Klicken Sie mit der rechten Maustaste auf das Paket, und klicken Sie auf **Einfügen**.

## <a name="Simple"></a>Erstellen und Verwenden von einfachen Sequenzdiagrammen
 Die einfachste und am häufigsten verwendete Form des Sequenzdiagramms enthält nur Lebenslinien und Meldungen. Mit einem Diagramm dieser Art können Sie deutlich eine typische Sequenz von Interaktionen zwischen Objekten im Entwurf oder zwischen Ihrem System und dessen Benutzern anzeigen. Dies reicht häufig aus, um den Entwurf zu verdeutlichen und zu diskutieren.

 Nachfolgend sind einige Punkte aufgeführt, die Sie beim Zeichnen eines einfachen Sequenzdiagramms beachten sollten.

### <a name="types-of-message"></a>Meldungstypen
 Es gibt drei Tools, die Sie verwenden können, um Meldungen zu erstellen.

- Verwenden Sie das **synchrone** Tool, um eine Interaktion zu beschreiben, bei der der Absender darauf wartet, dass der Empfänger eine Antwort zurückgibt (3).

     Am Ende der vorkommnisausführung wird eine **< \<return > >** Pfeil angezeigt. Er zeigt die Rückgabe der Steuerung an den Absender an.

- Verwenden Sie das **asynchrone** Tool, um eine Interaktion zu beschreiben, bei der der Absender sofort fortfahren kann, ohne auf den Empfänger zu warten (4).

- Verwenden Sie das Tool **Erstellen** , um eine Interaktion zu beschreiben, bei der der Absender den Empfänger erstellt (8).

     Eine Create-Meldung sollte die erste Meldung sein, die der Empfänger erhält.

### <a name="annotating-the-interactions"></a>Kommentieren der Interaktionen
 Wenn Sie weitere Details zur Sequenz beschreiben möchten, können Sie einen **Kommentar** an beliebiger Stelle im Diagramm platzieren.

 Mithilfe von **Kommentar Verknüpfungen**können Sie einen Kommentar mit Lebenslinien, Ausführungen, Interaktions Verwendungsmöglichkeiten und Fragmenten verknüpfen.

> [!CAUTION]
> Wenn Sie einen Kommentar an einem bestimmten Punkt in der Sequenz anfügen möchten, verknüpfen Sie ihn mit einer Vorkommnisausführung, einer Interaktionsverwendung oder einem Fragment. Verknüpfen Sie ihn nicht mit einer Lebenslinie, da er in diesem Fall nicht am richtigen Punkt in der Sequenz bleibt.

 Verwenden Sie zu folgenden Zwecken einen Kommentar:

- Anmerken, was an wichtigen Punkten in der Sequenz erreicht wurde. Dadurch können Leser die Ziele der Interaktionen erkennen.

- Beschreiben des Hauptziels der gesamten Sequenz. Fügen Sie den Kommentar an die erste Vorkommnisausführung an, oder weisen Sie ihn nicht zu. Zum Beispiel: „Der Kunde hat Gerichte aus der Speisekarte ausgewählt, und ihm wurde ein Preis genannt.“

- Beschreiben der Verantwortlichkeiten der einzelnen Lebenslinien. Fügen Sie den Kommentar an die Lebenslinie an. Zum Beispiel: „Bestellmanager nimmt die Essenswünsche des Kunden auf.“

- Anmerken von Ausnahmen oder Alternativen, die als Alternative zu der typischen angezeigten Sequenz ausgeführt werden können. Zum Beispiel: „Der Kunde kann wählen, den Rest dieser Sequenz zu überspringen.“

  - Erwägen Sie die Verwendung von Fragmenten als formalere Alternativen zu dieser Art von Anmerkung. Siehe [beschreiben von Steuerungsstrukturen mit Fragmenten](#Fragments)

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

- Verwenden Sie das [beschreiben von Steuerungsstrukturen mit Fragmenten](#Fragments) , um Schleifen, Alternativen usw. anzuzeigen.

## <a name="assessing-the-design"></a>Bewerten des Entwurfs
 Sie können das Diagramm verwenden, um die Verteilung der Aufgaben zwischen den Objekten oder Komponenten zu bewerten. Ziehen Sie eine Umgestaltung in Erwägung, wenn Sie diese Muster sehen:

- Eine Lebenslinie scheint alle Aufgaben durchzuführen, Aufrufe an alles andere zu tätigen, während die anderen Lebenslinien nur passiv reagieren.

- Viele Meldungen kreuzen die Lebenslinien. Jede Lebenslinie sollte Meldungen nur an ein paar Nachbarn senden und nicht mit den Nachbarn ihrer Nachbarn kommunizieren. Es sollte in der Regel möglich sein, die Lebenslinien so anzuordnen, dass sich Meldungen und Lebenslinien nur an wenigen Stellen kreuzen, und wo sie sich kreuzen, sollte die Ziel-Lebenslinie keine Meldungen austauschen, die kreuzende Lebenslinien aufweisen.

- Einige Lebenslinien scheinen mehr als eine Art von Aufgabe zu behandeln. Es sollte einfach sein, die Verantwortlichkeiten der einzelnen Lebenslinien in einem kurzen Satz zu beschreiben,der die Arbeit zusammenfasst, die sie als Antwort auf die empfangenen Meldungen ausführen.

## <a name="ClassesAndLifelines"></a>Klassen und Lebenslinien
 Die Lebenslinien in den Sequenzdiagrammen zeigen Instanzen von Klassen oder Komponentenschnittstellen. Sie können eine Lebenslinie auf zweierlei Weise benennen:

|**Zu diesem Zweck**|**Dieses Format verwenden**|
|--------------------------|-------------------------|
|Anonyme Instanz eines Typs.<br /><br /> Verwenden Sie diese Option, wenn Sie nur über eine Lebenslinie jedes Typs verfügen.|*typeName*|
|Benannte Instanz eines Typs.<br /><br /> Verwenden Sie diese Option, wenn Sie eine Sequenz darstellen möchten, die mehr als eine Instanz des gleichen Typs umfasst.|*objectName*:*Typname*|

### <a name="creating-lifelines-from-types"></a>Erstellen von Lebenslinien aus Typen
 Sie können neue Lebenslinien aus Klassen erstellen, die Sie bereits definiert haben, z. B. in einem Klassendiagramm.

> [!NOTE]
> Stellen Sie sicher, dass Sie über ein Sequenzdiagramm verfügen, bevor Sie diese Aufgabe ausführen.

##### <a name="to-create-a-lifeline-from-an-existing-type"></a>So erstellen Sie eine Lebenslinie aus einem vorhandenen Typ

- Ziehen Sie eine Klasse, Komponente oder Schnittstelle aus dem UML-Modell-Explorer in ein Sequenzdiagramm.

   \- oder -

  1. Klicken Sie im jeweiligen Diagramm mit der rechten Maustaste auf die Klasse, Komponente oder Schnittstelle, und klicken Sie dann auf **Lebenslinie erstellen**.

  2. Wählen Sie im Dialogfeld **Lebenslinie erstellen** ein Sequenzdiagramm aus, und klicken Sie dann auf **OK**.

     Eine neue benannte Instanzlebenslinie wird angezeigt, deren Typ dem Typ entspricht, den Sie gezogen haben.

  > [!NOTE]
  > Sie können diese Aktion so oft wie gewünscht wiederholen. Dadurch werden Lebenslinien mit unterschiedlichen Instanznamen erstellt.

##### <a name="to-change-the-type-of-a-lifeline"></a>So ändern Sie den Typ einer Lebenslinie

1. Klicken Sie mit der rechten Maustaste auf eine Lebenslinie und dann auf **Eigenschaften**.

2. Legen Sie im **Eigenschaften** Fenster die **Type** -Eigenschaft fest. Sie können einen Typ aus dem Dropdown-Menü auswählen oder einen neuen Namen eingeben.

### <a name="creating-classes-from-lifelines"></a>Erstellen von Klassen aus Lebenslinien
 Wenn Sie ein oder mehrere Sequenzdiagramme erstellt haben, können Sie die Lebenslinien zusammenfassen, indem Sie Klassen oder Schnittstellen daraus erstellen.

##### <a name="to-create-a-class-or-interface-from-a-lifeline"></a>So erstellen Sie eine Klasse oder Schnittstelle aus einer Lebenslinie

1. Klicken Sie mit der rechten Maustaste auf die Lebenslinie, und klicken Sie auf **Klasse erstellen** oder **Schnittstelle erstellen**.

     Eine neue Klasse oder Schnittstelle wird im UML-Modell-Explorer angezeigt.

2. Erstellen Sie Vorgänge in der Klasse oder Schnittstelle für jede Meldung, die die Lebenslinie empfängt:

    1. Wählen Sie alle Meldungen, die Sie einschließen möchten.

    2. Klicken Sie mit der rechten Maustaste auf eine der Nachrichten, und klicken Sie dann auf **Methode erstellen**.

         Die neue Klasse oder Schnittstelle verfügt über Vorgänge für jede ausgewählte Meldung.

         Der Vorgangs Name wird unter jedem Nachrichten Pfeil und in der Eigenschaft **Vorgang** der Nachricht angezeigt.

         Wenn die Meldung Parameter im Format „(Parameter : Typ)“ enthalten hat, werden sie in der Parameterliste des neuen Vorgangs angezeigt.

        > [!NOTE]
        > Wiederholen Sie diesen Schritt, wenn Sie neue Meldungen im Sequenzdiagramm hinzufügen.

3. Um die neue Klasse oder Schnittstelle im Detail anzuzeigen, fügen Sie sie einem Klassen- oder Komponentendiagramm hinzu.

    1. Öffnen oder erstellen Sie ein Klassen- oder Komponentendiagramm.

    2. Ziehen Sie die neue Klasse oder Schnittstelle aus dem **UML-Modell-Explorer** in ein Klassendiagramm.

         Die Klasse oder Schnittstelle wird im Klassendiagramm angezeigt.

         \- oder -

    3. Ziehen Sie die neue Schnittstelle aus dem **UML-Modell-Explorer** auf eine Komponente oder einen Port in einem Komponenten Diagramm.

         Die Schnittstelle wird auf der Komponente als Lollipop angezeigt.

### <a name="creating-classes-for-parameters"></a>Erstellen von Klassen für Parameter
 Sie können Parameter in die Meldungen in einem Sequenzdiagramm einschließen. Mit einem UML-Klassendiagramm können Sie die Parametertypen beschreiben.

## <a name="Multiple"></a>Erstellen von wiederverwendbaren Interaktions Sequenzen
 Sie können ein separates Diagramm verwenden, um eine Sequenz zu beschreiben, die Details enthält, die Sie herausstellen möchten oder die mehreren Diagrammen gemeinsam sind.

 Sie können ein Interaktionsverwendungsrechteck (12) in einem Diagramm erstellen, das auf die Details in einem anderen Diagramm verweist.

 Doppelklicken Sie auf eine Interaktionsverwendung, um das Sequenzdiagramm zu öffnen, das mit dieser verknüpft ist.

#### <a name="to-create-a-reusable-interaction-sequence-from-existing-lifelines"></a>So erstellen Sie eine wiederverwendbare Interaktionssequenz aus vorhandenen Lebenslinien

1. Klicken Sie in der **Toolbox**auf **Interaktions Verwendung**.

2. Halten Sie im Sequenzdiagramm die Maustaste gedrückt, während Sie über die Lebenslinien ziehen, die Sie in die wiederverwendbare Sequenz einschließen möchten. Starten Sie an der vertikalen Position, an der Sie die Interaktionsverwendung einfügen möchten.

     Eine Interaktionsverwendung wird über die ausgewählten Lebenslinien im Sequenzdiagramm angezeigt.

3. Doppelklicken Sie auf den Namen der Interaktionsverwendung, und benennen Sie sie um, um die Wirkung der wiederverwendbaren Sequenz in diesem Diagramm zu beschreiben.

     \- oder -

     Schreiben Sie den Namen wie einen Funktionsaufruf mit Parametern.

4. Verknüpfen Sie die Interaktionsverwendung mit einem anderen Sequenzdiagramm. Klicken Sie mit der rechten Maustaste auf die Interaktionsverwendung, und führen Sie dann eine der folgenden Aktionen durch:

     Klicken Sie auf **neue Sequenz erstellen** , um ein neues Sequenzdiagramm zu erstellen.

     \- oder -

     Klicken Sie auf **verknüpfen,** um eine Verknüpfung mit einem vorhandenen Diagramm zu verknüpfen.

     Visual Studio erstellt eine Verknüpfung zwischen der Interaktionsverwendung und der neuen Interaktionssequenz.

     Ein neues Sequenzdiagramm wird in der Projektmappe angezeigt. Es enthält die Lebenslinien, mit der Sie die Interaktionsverwendung erstellt haben.

    > [!NOTE]
    > Es werden nur die Lebenslinien einbezogen, die Sie zum Erstellen der Interaktionsverwendung verwendet haben. Das neue Diagramm umfasst keine Lebenslinien, die Sie nach der Interaktionsverwendung erstellt haben, auch wenn die Interaktionsverwendung Sie jetzt abdeckt.

#### <a name="to-create-a-reusable-sequence-from-existing-messages"></a>So erstellen Sie eine wiederverwendbare Sequenz aus vorhandenen Meldungen

- Klicken Sie mit der rechten Maustaste auf die Meldung, die Sie verschieben möchten, und klicken Sie dann **auf in Diagramm verschieben**.

  Visual Studio:

  - Ersetzt die ausgewählte Meldung und alle untergeordneten Meldungen durch eine Interaktionsverwendung.

  - Verschiebt die ersetzten Meldungen in ein neues Sequenzdiagramm.

  - Erstellt eine Verknüpfung zwischen der Interaktionsverwendung und dem neuen Sequenzdiagramm.

#### <a name="to-navigate-to-the-sequence-referenced-by-an-interaction-use"></a>So navigieren Sie zur Sequenz, auf die eine Interaktionsverwendung verweist

- Doppelklicken Sie auf die Interaktionsverwendung.

     \- oder -

     Klicken Sie mit der rechten Maustaste auf die Interaktion, und klicken Sie dann auf **Gehe zu Sequenz**.

### <a name="creating-a-placeholder-with-an-interaction-use"></a>Erstellen eines Platzhalters mit einer Interaktionsverwendung
 Sie können eine Interaktionsverwendung erstellen, ohne sie mit einem anderen Diagramm zu verknüpfen. Sie können dies als Platzhalter für einen Teil der Sequenz verwenden, deren Details noch nicht verarbeitet werden sollen. Verwenden Sie den Namen der Interaktion, um das gewünschte Ergebnis anzugeben.

## <a name="Collapse"></a>Reduzieren von Lebenslinien Gruppen
 Sie können eine Gruppe von Lebenslinien so reduzieren, dass die Gruppe als eine Lebenslinie angezeigt wird. Dadurch können Sie eine Gruppe von Objekten als einzelne Komponente visualisieren. Meldungen und Interaktionsverwendungen zwischen Lebenslinien in einer reduzierten Gruppe werden ausgeblendet. Meldungen und Interaktionssequenzen, die andere Lebenslinien einschließen, werden angezeigt.

#### <a name="to-collapse-a-group-of-lifelines-together"></a>So reduzieren Sie eine Gruppe von Lebenslinien

1. Wählen Sie zwei oder mehr Lebenslinien aus.

2. Klicken Sie mit der rechten Maustaste auf eine dieser Elemente, und klicken Sie dann auf **reduzieren.**

     Die separaten Lebenslinien werden durch eine einzelne Lebenslinie ersetzt.

     Meldungen und Interaktionsverwendungen, die nur Mitglieder der Gruppe betreffen, werden ausgeblendet.

3. Um die Gruppe umzubenennen, klicken Sie auf den Namen.

    > [!NOTE]
    > Der Gruppenname geht verloren, wenn Sie die Gruppe erweitern.

#### <a name="to-expand-a-collapsed-group"></a>So erweitern Sie eine reduzierte Gruppe

- Klicken Sie mit der rechten Maustaste auf die reduzierte Lebenslinie und dann auf **erweitern**.

    > [!NOTE]
    > Der Name der Gruppe geht zusammen mit allen Verknüpfungen von der Gruppe zu Kommentaren oder Arbeitsaufgaben verloren.

## <a name="Fragments"></a>Beschreiben von Steuerungsstrukturen mit Fragmenten
 Sie können kombinierte Fragmente (13) verwenden, um Schleifen, Verzweigungen und die gleichzeitige Verarbeitung in einem Sequenzdiagramm zu definieren. Ziehen Sie alternativ die Verwendung eines Aktivitätsdiagramms in Erwägung. Das Aktivitätsdiagramm ist nicht so nützlich, um Meldungen zwischen Akteuren darzustellen, aber in einigen Fällen ist es besser geeignet, um Schleifen, Verzweigungen und Parallelität zu zeigen.

 Eine vollständige Liste der fragmenttypen finden Sie unter [beschreiben der Ablauf Steuerung mit Fragmenten in UML-Sequenzdiagrammen](../modeling/describe-control-flow-with-fragments-on-uml-sequence-diagrams.md).

#### <a name="to-create-a-combined-fragment"></a>So erstellen Sie ein kombiniertes Fragment

1. Wählen Sie eine Meldung oder eine Sequenz von Meldungen, die alle mit der gleichen Vorkommnisausführung oder Lebenslinie beginnen.

    > [!NOTE]
    > Wählen Sie die Meldungspfeile, nicht die Vorkommnisausführungen, auf die die Meldungen verweisen.

2. Klicken Sie mit der rechten Maustaste auf eine der Meldungen, zeigen Sie auf **Umschließen mit**, und klicken Sie dann auf den gewünschten fragmenttyp.

     Ein neues Fragment wird angezeigt. Es enthält die ausgewählten Meldungen.

     Wenn der kombinierte Fragmenttyp mehrere Fragmente zulässt, wird auch ein leeres Fragment angezeigt.

3. Wenn Sie den Wächter eines Fragments festlegen möchten, klicken Sie mit der rechten Maustaste auf den fragmentrahmen, und klicken Sie dann auf **Eigenschaften**. Legen Sie die **Guard** -Eigenschaft fest.

     Mit dem Wächter wird die Bedingung einer Verzweigung oder Schleife definiert.

4. Wenn Sie ein neues Fragment zu einer Art hinzufügen möchten, die mehrere Fragmente zulässt, klicken Sie mit der rechten Maustaste auf die Grenze eines Fragments, und zeigen Sie auf **Hinzufügen**. Klicken Sie entweder auf **Interaktions Operand vor** oder **Interaktions Operand after**.

5. Um neue Meldungen zu einem Fragment hinzuzufügen, verwenden Sie die Meldungstools oder die Funktion zum Kopieren und Einfügen.

## <a name="see-also"></a>Siehe auch
 [UML-Sequenzdiagramme: Referenz](../modeling/uml-sequence-diagrams-reference.md) zur [Bearbeitung von UML-Modellen und-Diagrammen](../modeling/edit-uml-models-and-diagrams.md) [UML-Anwendungsfall Diagramme: Referenz](../modeling/uml-use-case-diagrams-reference.md) für UML- [Klassendiagramme: Referenz](../modeling/uml-class-diagrams-reference.md) für UML- [Komponenten Diagramme:](../modeling/uml-component-diagrams-reference.md) [Referenz](../modeling/uml-component-diagrams-reference.md) [ Video: Entfernen von Interaktionen mit Sequenzdiagrammen](http://go.microsoft.com/fwlink/?LinkId=201113)
