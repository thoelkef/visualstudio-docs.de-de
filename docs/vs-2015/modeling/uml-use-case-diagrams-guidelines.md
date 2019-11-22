---
title: 'UML Use Case Diagrams: Guidelines | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- diagrams - modeling, use case
- UML, use case diagrams
- diagrams - modeling, UML use case
- use case diagrams
- UML diagrams, use case
ms.assetid: b1ae8ed0-d00b-4f9b-8e23-733e09e81e9b
caps.latest.revision: 38
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7c9ccd5285f9a2744704c0ee13094a1dac31c53b
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302833"
---
# <a name="uml-use-case-diagrams-guidelines"></a>UML-Anwendungsfalldiagramme: Richtlinien
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio, you can draw a *use case diagram* to summarize who uses your application or system, and what they can do with it. To create a UML use case diagram, on the **Architecture** menu, click **New UML or Layer Diagram**.

 For a video demonstration, see [Organizing Features into Use Cases](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-2-organizing-features-into-use-cases).

 Welche Versionen von Visual Studio dieses Features unterstützen, erfahren Sie unter [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Mithilfe eines Anwendungsfalldiagramms können Sie Folgendes erläutern und kommunizieren:

- Die Szenarios, in denen das System oder die Anwendung mit Personen, Organisationen oder externen Systemen interagiert.

- Die Ziele, bei deren Erreichung die Akteure unterstützt werden.

- Den Umfang des Systems.

  Ein Anwendungsfalldiagramm zeigt die Details der Anwendungsfälle nicht an: Es fasst nur einige Beziehungen zwischen Anwendungsfällen, Akteuren und Systemen zusammen. Beispielsweise zeigt das Diagramm nicht die Reihenfolge an, in der Schritte ausgeführt werden, um die Ziele der einzelnen Anwendungsfälle zu erreichen. Sie können diese Details in anderen Diagrammen und Dokumenten beschreiben, die Sie mit jedem Anwendungsfall verknüpfen können. For more information, see [Describing Use Cases in Detail](#Details) in this topic.

  Die Beschreibungen, die Sie für Anwendungsfälle angeben, verwenden verschiedene Begriffe, die sich auf die Domäne beziehen, in der das System ausgeführt wird, z. B. Angebot, Speisekarte, Kunde usw. Es ist wichtig, diese Begriffe und ihre Beziehungen eindeutig zu definieren. Dafür können Sie ein UML-Klassendiagramm verwenden. For more information, see [UML Class Diagrams: Guidelines](../modeling/uml-class-diagrams-guidelines.md).

  Bei Anwendungsfällen geht es nur um die Funktionsanforderungen eines Systems. Andere Anforderungen wie Geschäftsregeln, Servicequalitätsanforderungen und Implementierungseinschränkungen müssen separat dargestellt werden. Die Architektur und interne Details müssen ebenfalls gesondert beschrieben werden. For more information about how to define user requirements, see [Model user requirements](../modeling/model-user-requirements.md).

  Die in diesem Thema verwendeten Beispiele beziehen sich auf eine Website, auf der Kunden Gerichte bei den örtlichen Restaurants bestellen können.

  ![Elements in a use case diagram](../modeling/media/uml-ucovactor.png "UML_UCOvActor")

- An *actor* (1) is a class of person, organization, device, or external software component that interacts with your system. Example actors are **Customer**, **Restaurant**, **Temperature Sensor**, **Credit Card Authorizer.**

- A *use case* (2) represents the actions that are performed by one or more actors in the pursuit of a particular goal. Example use cases are **Order Meal**, **Update Menu**, **Process Payment**.

   In einem Anwendungsfalldiagramm sind Anwendungsfälle (3) den Akteuren zugeordnet, die diese ausführen.

- Your *system (4)* is whatever you are developing. Beispielsweise kann es sich um eine kleine Softwarekomponente handeln, deren Akteure einfach nur andere Softwarekomponenten sind. Es kann sich auch um eine vollständige Anwendung oder um eine große verteilte Suite von Anwendungen handeln, die über viele Computer und Geräte hinweg bereitgestellt werden. Example subsystems are **Meal Ordering Website**, **Meal Delivery Business**, **Website Version 2**.

   Ein Anwendungsfalldiagramm kann anzeigen, welche Anwendungsfälle vom System oder seinen Subsystemen unterstützt werden.

## <a name="BasicSteps"></a> Basic Steps for Drawing Use Case Diagrams

> [!NOTE]
> Detailed steps for creating any of the modeling diagrams are described in [Edit UML models and diagrams](../modeling/edit-uml-models-and-diagrams.md).

#### <a name="to-create-a-new-use-case-diagram"></a>So erstellen Sie ein neues Anwendungsfalldiagramm

1. On the **Architecture** menu, click **New UML or Layer Diagram**.

2. Under **Templates**, click **UMLUse Case Diagram**.

3. Benennen Sie das Diagramm.

4. In **Add to Modeling Project**, select an existing modeling project in your solution, or **Create a New Modeling Project**, and then click **OK**.

#### <a name="to-draw-a-use-case-diagram"></a>So zeichnen Sie ein Anwendungsfalldiagramm

1. Drag **Subsystem** boundaries from the toolbox onto the diagram, to represent either your whole system or its major components.

    - Sie können ein Anwendungsfalldiagramm ohne Systembegrenzungen zeichnen, wenn Sie nicht beschreiben möchten, welche Anwendungsfälle vom System oder seinen Komponenten unterstützt werden.

    - Ziehen Sie die Ecke eines Systems, um es bei Bedarf größer zu machen.

    - Benennen Sie es mit einem aussagekräftigen Namen.

2. Drag **Actors** from the toolbox onto the diagram (placing them outside any system boundary).

    - Akteure stellen Klassen von Benutzern, Organisationen und externen Systemen dar, die mit dem System interagieren.

    - Benennen Sie diese um. For example: **Customer, Restaurant, Credit card agency.**

3. Drag **Use Cases** from the toolbox onto the appropriate systems.

    - Anwendungsfälle stellen die Aktivitäten dar, die Akteure mithilfe des Systems ausführen.

    - Benennen Sie diese um, indem Sie Titel verwenden, die für die Akteure verständlich sind. Verwenden Sie keine Titel, die sich auf Ihren Code beziehen. For example: **Order Meal, Pay for Meal, Deliver Meal**.

    - Begin with major transactions such as **Order Meal**, leaving until later smaller interactions such as **Select Menu Item**.

    - Platzieren Sie jeden Anwendungsfall im System oder im unterstützenden Hauptsubsystem. (Ignorieren Sie dabei alle Fassaden oder Komponenten, die nur dem Herstellen der Verbindung zum Benutzer dienen.)

    - Sie können einen Anwendungsfall außerhalb der Systembegrenzung zeichnen, um anzugeben, dass dieser nicht vom System unterstützt wird, zum Beispiel in einer bestimmten Version.

4. Click **Association** on the toolbox, then a use case, and then an actor that participates in the use case. Verknüpfen Sie alle Akteure auf diese Weise mit ihren Anwendungsfällen.

5. Structure the use cases with the **Include**, **Extend** and **Generalization** relationships. Klicken Sie zum Erstellen dieser Links jeweils auf das Tool und dann auf den Quellanwendungsfall und auf das Ziel. See the following section titled [Structuring Use Cases](#Structuring).

6. Beschreiben Sie die Anwendungsfälle ausführlicher. See the following section titled [Describing Use Cases in Detail](#Details).

7. Zeichnen Sie separate Diagramme für verschiedene Subsysteme oder andere Gruppen verwandter Anwendungsfälle. Alle Diagramme in einem Modellierungsprojekt sind Ansichten des gleichen Modells.

## <a name="Actors"></a> Drawing Actors and Use Cases
 Der Hauptzweck eines Anwendungsfalldiagramms besteht darin anzuzeigen, wer mit dem System interagiert und welche Hauptziele erreicht werden sollen.

- Create **Actors** to represent classes of people, organizations, other systems, software or devices that interact with your system or subsystem.

  - To learn how to draw actors and other elements, see [Edit UML models and diagrams](../modeling/edit-uml-models-and-diagrams.md).

  - Geben Sie für jeden Satz mit Zielen die Akteure nach Typ oder Rolle an, auch wenn die physischen Personen oder Entitäten ggf. gleich sind. Beispielsweise sind Restaurant und Kunden separate Akteure, obwohl ein Restaurantmitarbeiter manchmal auch ein Kunde sein kann.

- Create **Use Cases** for each of the goals that each actor seeks to achieve with the system.

  - Benennen und beschreiben Sie die Anwendungsfälle in Worten, die der Akteur versteht, und verwenden Sie keine Implementierungsbegriffe.

- Use **Associations** to link actors to use cases.

### <a name="inheritance-between-actors"></a>Vererbung zwischen Akteuren
 ![Use case diagram showing inheritance](../modeling/media/uml-ucguideinherit.png "UML_UCGuideInherit")

 You can draw a **Generalization** link between Actors. Der spezialisierte Akteur wie Clubkunde im Beispiel, erbt die Anwendungsfälle des generalisierten Akteurs, z. B. Kunde. Die Pfeilspitze sollte auf den allgemeineren Akteur zeigen, z. B. Kunde. Zeigen Sie beim Erstellen des Links zuerst auf den spezialisierteren Akteur.

 Der spezialisierte Akteur kann über seine eigenen zusätzlichen Anwendungsfälle verfügen, die für die anderen Akteure nicht verfügbar sind.

> [!CAUTION]
> Sie sollten keine Schleifen aus Generalisierungsbeziehungen erstellen, die dazu führen, dass ein Akteur sich selbst generalisiert. Schleifen können zu Fehlern führen.

### <a name="alternative-actor-icons"></a>Alternative Akteursymbole
 Sie können benutzerdefinierte Symbole verwenden, um anstelle des standardmäßigen Strichmännchens einen Akteur darzustellen. Sie können es z. B. so ändern, dass es wie ein Gerät , ein Restaurant, eine Bank usw. aussieht.

##### <a name="to-change-the-appearance-of-an-actor"></a>So ändern Sie die Darstellung eines Akteurs

1. Right-click the actor and then click **Properties**.

     Das Fenster **Eigenschaften** wird angezeigt.

2. Set the **Image Path** property to the location of an image file.

    - Sie können verschiedene Bildformate wie GIF, JPG und BMP verwenden.

    - Verwenden Sie eine Datei, die in der Projektmappe oder in der Quellcodeverwaltung des Projekts enthalten ist, damit diese auch dann noch verfügbar ist, wenn die Projektmappe verschoben oder kopiert wird.

3. Um diese Darstellung in anderen Anwendungsfalldiagrammen zu replizieren, kopieren Sie den Akteur und fügen ihn in ein anderes Diagramm ein.

    - Die Änderung des Bilds gilt nur für die Ansicht in einem bestimmten Diagramm. Sie gilt nicht für das zugrunde liegende Modellelement. Wenn Sie den Akteur aus dem UML-Modell-Explorer in ein anderes Diagramm ziehen, wird er als standardmäßiges Strichmännchen angezeigt.

### <a name="multiplicities-between-actors-and-use-cases"></a>Multiplizitäten zwischen Akteuren und Anwendungsfällen
 The association between an actor and a use case can show a *multiplicity* at each end.

 ![Use case one to one with actor](../modeling/media/uml-ucguidemulti1.png "UML_UCGuideMulti1")

> [!NOTE]
> The multiplicities of an association on a use case diagram are hidden if they are both **1**.

 By default, each multiplicity is **1**. Bei einer strengen Auslegung des Modells bedeutet eine Multiplizität von 1, dass z. B. nur jeweils ein Kunde an der Bestellung eines Gerichts beteiligt ist und dass jeder Kunde nur jeweils ein Gericht bestellt.

 Sie können diese Multiplizitäten ändern.

 Beispiel:

 ![Use case showing many to many multiplicity](../modeling/media/uml-ucguidemulti2.png "UML_UCGuideMulti2")

- To state that several actors of the same class can take part in a single occurrence of a use case, set the multiplicity at the actor end of the association to **1..\*** .

   In der Abbildung können ein oder mehrere Restaurants an der Erledigung der gleichen Essensbestellung beteiligt sein.

- To show that each actor can participate at the same time in several occurrences of a use case, set the multiplicity at the use case end of the association to **\*** .

   In der Abbildung kann jedes Restaurant gleichzeitig an der Erledigung von mehr als einer Bestellung arbeiten.

##### <a name="to-set-multiplicities-on-an-association"></a>So legen Sie Multiplizitäten für eine Zuordnung fest

1. Right-click the association and then click **Properties**.

2. Expand either **First Role** or **Second Role**.

    *Role* means the element at one end of the association.

3. Legen Sie die Eigenschaft „Multiplizität“ fest, indem Sie in der Liste eine der folgenden Optionen auswählen:

   - **1** to state that exactly one instance of this role participates in each link.

   - **1..\*** to state that one or more instance of this role participate in each link.

   - **0..1** to state that participation is optional.

   - **\*** to state that zero or more instances of this role participate in the link.

> [!NOTE]
> Viele Teams geben in Anwendungsfalldiagrammen keine Informationen zur Multiplizität an und behalten für die Multiplizitäten den Standardwert 1 bei. Stattdessen geben sie die Informationen in separaten Beschreibungen der Anwendungsfälle an. In diesem Fall werden alle Multiplizitäten in den Anwendungsfalldiagrammen ausgeblendet.

### <a name="using-an-actor-or-use-case-on-multiple-diagrams"></a>Verwenden eine Akteurs oder eines Anwendungsfalls in mehreren Diagrammen
 Sie können die gleichen Akteure und Anwendungsfälle in mehreren Diagrammen anzeigen. Beispiel:

- Sie können in unterschiedlichen Diagrammen die verschiedenen Anwendungsfälle beschreiben, an denen ein Akteur beteiligt ist.

- Sie können ein Diagramm verwenden, um die Akteure und Subsysteme anzuzeigen, denen ein Anwendungsfall zugeordnet ist, und ein anderes Diagramm, um anzuzeigen, wie der Anwendungsfall in enthaltene und erweiterte Anwendungsfälle unterteilt ist.

##### <a name="to-show-the-same-actor-or-use-case-on-different-diagrams"></a>So zeigen Sie den gleichen Akteur bzw. den gleichen Anwendungsfall in verschiedenen Diagrammen an

1. Erstellen Sie den Akteur bzw. den Anwendungsfall in einem Diagramm.

2. Erstellen Sie ein weiteres Anwendungsfalldiagramm.

3. Drag an actor or use case off **Model Explorer** onto the new diagram.

    > [!NOTE]
    > Wenn Sie einen bereits zugeordneten Akteur und Anwendungsfall im neuen Diagramm anordnen, wird die Zuordnung dazwischen in dem neuen Diagramm automatisch angezeigt.

## <a name="Details"></a> Describing use cases in detail
 Ein Anwendungsfall stellt Folgendes dar:

- A goal of an actor in using the system, such as **Buy a Meal**; and

- One or more *scenarios*, that is, sequences of steps performed in pursuing the goal, such as: {**Order Meal, Pay, Deliver**}. In addition to success scenarios, there might be several exception or failure scenarios, such as **Credit Card Rejected**.

  Ein Anwendungsfall kann in verschiedenen Ausführlichkeitsgraden beschrieben werden. In einer frühen Phase des Entwurfs ist der Name im Anwendungsfalldiagramm ausreichend.  Später können ausführlichere Beschreibungen der Szenarios geschrieben werden.

  In Visual Studio Ultimate können Sie einen Anwendungsfall auf verschiedene Arten beschreiben. Anwendungsfälle können einzeln oder gemeinsam verwendet werden:

- Verknüpfen Sie den Anwendungsfall mit einem oder mehreren Diagrammen im Projekt.

  - Mit einem Aktivitätsdiagramm können Sie einen komplexeren Prozess mit Schleifen, Verzweigungen und parallelen Threads erläutern. Darin kann auch der Fluss der Daten zwischen Teilen des Prozesses angezeigt werden. For more information, see [UML Activity Diagrams: Guidelines](../modeling/uml-activity-diagrams-guidelines.md).

  - Mit einem Sequenzdiagramm können Sie eine komplexe Reihe von Interaktionen zwischen verschiedenen Akteuren erklären. Außerdem können Sie diese Art von Diagramm verwenden, um darzustellen, was im System als Reaktion auf die einzelnen Anwendungsfälle ausgeführt wird. For more information, see [UML Sequence Diagrams: Guidelines](../modeling/uml-sequence-diagrams-guidelines.md).

- Verknüpfen Sie den Anwendungsfall mit einer OneNote-Seite, einem OneNote-Abschnitt oder einem OneNote-Absatz, auf der bzw. in dem der Anwendungsfall ausführlich beschrieben wird.

- Verknüpfen Sie den Anwendungsfall mit einem Word-Dokument, in dem Sie Text, Screenshots usw. verwenden, um die Szenarios des Anwendungsfalls zu beschreiben. For more information, see [Model user requirements](../modeling/model-user-requirements.md).

#### <a name="to-link-a-use-case-to-a-diagram-or-file-in-the-same-solution"></a>So verknüpfen Sie einen Anwendungsfall mit einem Diagramm oder einer Datei in der gleichen Projektmappe

1. Zeichnen Sie ein Diagramm, um ein Szenario des Anwendungsfalls zu veranschaulichen, z. B. ein Sequenz- oder Aktivitätsdiagramm.

2. Wechseln Sie zurück zum Anwendungsfalldiagramm.

3. Ziehen Sie das Diagramm oder die Datei vom Projektmappen-Explorer auf einen leeren Teil des Anwendungsfalldiagramms.

4. Connect from the artifact to the use case using a **Dependency**.

#### <a name="to-link-to-a-solution-file-such-as-a-word-document-or-powerpoint-presentation"></a>So erstellen Sie einen Link zu einer Projektmappendatei (z. B. ein Word-Dokument oder eine PowerPoint-Präsentation)

1. Erstellen Sie ein Dokument, das Text, Screenshots usw. zum Beschreiben des Szenarios des Anwendungsfalls enthält.

2. Fügen Sie das Dokument der Projektmappe hinzu.

    1. Verschieben Sie das Word-Dokument in den gleichen Windows-Ordner wie die Projektmappe.

    2. In Solution Explorer, right-click the solution, point to **Add**, and then click **Existing Item**.

    3. Navigate to the Word document and click **Add**.

         Das Word-Dokument wird im Projektmappen-Explorer in einem Projektmappenordner angezeigt.

3. Ziehen Sie das Word-Dokument aus dem Projektmappen-Explorer auf einen leeren Teil des Anwendungsfalldiagramms.

     Ein neues Artefakt wird angezeigt.

4. Connect from the artifact to the use case using a **Dependency**.

#### <a name="to-link-to-a-shared-document-onenote-element-or-web-page"></a>So erstellen Sie einen Link zu einem freigegebenen Dokument, einem OneNote-Element oder einer Webseite

1. Sie benötigen die URL des freigegebenen Elements. This can be, for example, a network file path beginning '\\\\', or a web page or Sharepoint URL beginning 'http://', or a link to a OneNote section, page, or paragraph beginning 'onenote:'.

2. In the Toolbox, click **Artifact** and then click in the use case diagram.

3. With the new artifact selected, type or paste the URL into the **Hyperlink** property.

> [!NOTE]
> Sie können auf ein Artefakt doppelklicken, um das Diagramm oder das Dokument zu öffnen, mit dem es verknüpft ist.

### <a name="linking-use-cases-to-work-items"></a>Verknüpfen von Anwendungsfällen mit Arbeitsaufgaben
 If your project uses [!INCLUDE[vstsTfsRosarioLong](../includes/vststfsrosariolong-md.md)] and you have [!INCLUDE[esprtfc](../includes/esprtfc-md.md)], you can link each use case to a work item in [!INCLUDE[esprfound](../includes/esprfound-md.md)]. To learn how to make these links, see [Link model elements and work items](../modeling/link-model-elements-and-work-items.md).

 Sie haben dann folgende Möglichkeiten:

- Beschreiben Sie den Anwendungsfall in der verknüpften Arbeitsaufgabe. Wenn das Projekt die Visual Studio-Prozessvorlage „Formal“ verwendet, können Sie einen Link zu einer Anwendungsfall-Arbeitsaufgabe einrichten. Dieser Arbeitsaufgabentyp stellt Felder zum Beschreiben der Ziele und Szenarios des Anwendungsfalls bereit.

- Verknüpfen Sie Testfälle mit dem Anwendungsfall, damit Sie Berichte dazu abrufen können, in welchem Umfang der entwickelte Code den Anwendungsfall implementiert.

- Verknüpfen Sie Aufgaben mit dem Anwendungsfall, damit Sie den Status der Entwicklungsarbeit nachverfolgen können.

## <a name="Structuring"></a> Structuring Use Cases
 Sie sollten versuchen, das Verhalten des Systems nur mit einigen wenigen Hauptanwendungsfällen zu beschreiben. Für jeden großen Anwendungsfall ist ein Hauptziel definiert, für dessen Erreichung ein Akteur zuständig ist, z. B. das Kaufen eines Produkts oder aus Anbietersicht das Anbieten von Produkten zum Verkauf.

 Wenn Sie diese Ziele verdeutlicht haben, können Sie weitere Details dazu angeben, wie die einzelnen Ziele erreicht werden und welche Variationen es bei den grundlegenden Zielen gibt.

 Vermeiden Sie es, die Anwendungsfälle zu stark zu unterteilen. Bei Anwendungsfällen geht es um die Benutzererfahrung mit dem System, nicht so sehr um die internen Details. Außerdem ist es meist produktiver, nur erste Arbeitsversionen des Codes zu erstellen, anstatt zu viel Zeit mit dem ausführlichen Strukturieren der Anwendungsfälle zu verbringen.

 Sie können in einem Anwendungsfalldiagramm die Beziehungen zwischen den Hauptanwendungsfällen und ausführlicheren Anwendungsfällen zusammenfassen. Dies wird in den folgenden Abschnitten beschrieben:

- [Showing the details of a use case with Include](#Include)

- [Sharing goals with Generalization](#Inheritance)

- [Separating out variant cases with Extend](#Extend)

### <a name="Include"></a> Showing the details of a use case with Include
 Use an **Include** relation to show that one use case describes some of the detail of another. In the illustration, **Order a Meal** includes **Pay**, **Choose Menu**, and **Choose Menu Item**. Jeder der enthaltenen ausführlicheren Anwendungsfälle ist ein Schritt, den der Akteur oder die Akteure ggf. ausführen müssen, um das Gesamtziel des einschließenden Anwendungsfalls zu erreichen. Der Pfeil sollte auf den ausführlicheren eingeschlossenen Anwendungsfall zeigen.

> [!CAUTION]
> Sie sollten keine Schleifen aus Beziehungen vom Typ „Einschließen“ erstellen, die dazu führen, dass ein Anwendungsfall sich selbst enthält. Schleifen können zu Fehlern führen.

 Sie können eingeschlossene Anwendungsfälle freigeben. In the example, the **Order a Meal** and **Subscribe to Reviews** use cases both include **Pay**.

 ![Use cases decomposed with include](../modeling/media/uml-ucguideinclude.png "UML_UCGuideInclude")

 Das Ziel und die Szenarios eines eingeschlossenen Anwendungsfalls sollten auch unabhängig voneinander Sinn ergeben, damit diese in Anwendungsfälle einbezogen werden können, die später entworfen werden.

 Das Unterteilen von Anwendungsfällen in einschließende und eingeschlossene Teile ist nützlich, um die folgenden Ziele zu erreichen:

- Strukturieren der Anwendungsfallbeschreibungen in verschiedene Detailebenen

- Vermeiden der Wiederholung von freigegebenen Szenarios in verschiedenen Anwendungsfällen

#### <a name="Steps"></a> Defining the order of the detailed steps
 Das Anwendungsfalldiagramm sagt weder etwas über die Reihenfolge aus, in der die ausführlicheren Schritte ausgeführt werden müssen, noch darüber, ob jeder Schritt immer erforderlich ist.

 To make the order of the steps clear, you can use an **Artifact** to attach a separate document to the including use case. Im folgenden Beispiel ist ein Aktivitätsdiagramm an den Anwendungsfall Gericht bestellen angefügt. Alternativ dazu können Sie ein Textdokument verwenden, das eine Liste von Schritten oder eine Sequenz von Screenshots enthält. For more information, see [Describing Use Cases in Detail](#Details).

 Beachten Sie beim Verwenden eines Aktivitätsdiagramms die folgenden Namenskonventionen:

- Der Name der gesamten Aktivität entspricht dem Namen des einschließenden Anwendungsfalls.

- Die Aktionen im Aktivitätsdiagramm haben die gleichen Namen wie die eingeschlossenen Anwendungsfälle.

  For more information, see [UML Activity Diagrams: Guidelines](../modeling/uml-activity-diagrams-guidelines.md).

  ![Use case steps shown in linked activity diagram](../modeling/media/uml-ucguidesteps.png "UML_UCGuideSteps")

### <a name="Inheritance"></a> Sharing goals with Generalization
 Use a Generalization relation to show that a *specialized* use case is a particular way to achieve the goals expressed by another *general* use case. Die geöffnete Pfeilspitze sollte auf den allgemeineren Anwendungsfall zeigen.

 ![Use cases showing the generalization relation](../modeling/media/uml-ucguidegeneral.png "UML_UCGuideGeneral")

 For example, **Pay** generalizes **Pay by Credit Card** and **Pay by Cash**.

> [!CAUTION]
> Sie sollten keine Schleifen aus Generalisierungsbeziehungen erstellen, die dazu führen, dass ein Akteur sich selbst generalisiert. Schleifen können zu Fehlern führen.

 Mithilfe von spezialisierten Anwendungsfällen können Sie andere Methoden anzeigen, mit denen das System das gleiche Ziel erreichen kann.

 Die spezialisierten Anwendungsfälle sollen die Ziele und Akteure des allgemeinen Anwendungsfalls erben. Der allgemeine Anwendungsfall muss keine eigenen Szenarios haben. Seine Spezialisierungen beschreiben verschiedene Methoden zur Erreichung der Ziele.

##### <a name="to-refactor-common-goals-from-two-or-more-use-cases"></a>So gestalten Sie allgemeine Ziele von zwei oder mehr Anwendungsfällen um

1. Erstellen und benennen Sie den neuen allgemeinen Anwendungsfall.

2. Create a **Generalization** relation with the large arrow pointing at the new general use case.

    1. Click **Generalization** in the toolbox.

    2. Click a specialized use case (**Pay by Credit Card** in the example).

    3. Click the general use case (**Pay** in the example).

3. Wenn Sie die Ziele für die spezialisierten Anwendungsfälle beschrieben haben, verschieben Sie die gemeinsamen Teile in die Beschreibung des allgemeinen Anwendungsfalls.

4. Akteure, die von den spezialisierten Anwendungsfällen gemeinsam genutzt werden, können in den allgemeinen Anwendungsfall verschoben werden.

### <a name="Extend"></a> Separating variant cases with Extend
 Verwenden Sie einen Link vom Typ „Erweitern“, um anzugeben, dass ein Anwendungsfall einem anderen Anwendungsfall unter bestimmten Umständen Funktionen hinzufügen kann. Der Pfeil sollte auf den erweiterten Hauptanwendungsfall zeigen.

 ![One use case extending another](../modeling/media/uml-ucguideextend.png "UML_UCGuideExtend")

> [!CAUTION]
> Sie sollten keine Schleifen aus Erweiterungsbeziehungen erstellen, die dazu führen, dass ein Akteur sich selbst generalisiert. Schleifen können zu Fehlern führen.

 For example, the **Login** use case of a typical Web site can include **Register New User** - but only when the user does not already have an account.

##### <a name="to-separate-a-use-case-into-main-and-extending-parts"></a>So unterteilen Sie einen Anwendungsfall in Hauptbestandteile und Erweiterungsteile

1. Erstellen und benennen Sie den neuen erweiterten Anwendungsfall.

2. Create an **Extend** relation with the arrow pointing at the extended use case.

   1. Click **Extend** in the toolbox.

   2. Click the extending use case (**Register New User** in the example).

   3. Click the extended use case (**Login** in the example).

       > [!NOTE]
       > Vermeiden Sie es, im Diagramm eine Schleife von Erweiterungsbeziehungen zu erstellen. Ein Anwendungsfall darf keine Erweiterung von sich selbst darstellen.

3. Verschieben Sie die relevanten Schritte in das Szenario der Erweiterung, falls Sie für den erweiterten Anwendungsfall bereits Szenarios erstellt haben.

4. The description of the extension (**Register New User** in the example) should include details of where in the main use case scenarios it will occur, and under what circumstances. Sehen Sie diesen Schritt als Änderung der Beschreibung des Hauptanwendungsfalls an.

   Der Erweiterungsanwendungsfall stellt Szenarioschritte dar, die andernfalls Teil des Hauptanwendungsfall-Szenarios wären. Das Szenario und das Ziel der Erweiterung werden immer im Kontext des Hauptanwendungsfalls gelesen und müssen deshalb keinen direkten unabhängigen Nutzen aufweisen.

   Das Abtrennen von Erweiterungen kann nützlich sein, um die folgenden Situationen zu beschreiben:

- Es sind zusätzliche Akteure vorhanden, die nur am Erweiterungsanwendungsfall beteiligt sind. Beispielsweise muss ein Administrator die Registrierung eines Kunden auf der Website genehmigen.

- Ein separates Subsystem verarbeitet den Erweiterungsanwendungsfall.

- Diese Erweiterung ist nur in bestimmten Versionen des Systems verfügbar. Sie können jede Version im Anwendungsfalldiagramm als separates Subsystem anzeigen.

## <a name="Subsystems"></a> Using Subsystem Boundaries
 Verwenden Sie eine Subsystembegrenzung, um anzugeben, welche Anwendungsfälle innerhalb des Bereichs des Systems liegen.

#### <a name="to-draw-a-subsystem-boundary"></a>So zeichnen Sie eine Subsystembegrenzung

1. In the toolbox, click **Subsystem**, then click the diagram.

    Ein Subsystem wird im Diagramm angezeigt.

2. Ziehen Sie die Ecken des Subsystems, um seine Größe anzupassen.

3. Ziehen Sie vorhandene Anwendungsfälle in das oder aus dem Subsystem, um seinen Inhalt anzupassen.

   \- oder -

   To create a new use case directly in a subsystem, click **Use Case** in the toolbox, then click inside the subsystem.

> [!NOTE]
> The **Subjects** property of a use case indicates what subsystem it is contained within.

### <a name="use-cases-outside-the-system-scope"></a>Anwendungsfälle außerhalb des Systembereichs
 Es ist häufig nützlich, Anwendungsfälle in das Diagramm einzubeziehen, die Teil des Geschäftsablaufs sind, aber nicht mit dem in der Entwicklung befindlichen System verarbeitet werden. Auf diese Weise können Entwickler den Kontext ihrer Arbeit besser verstehen. „Gericht liefern“ kann z. B. als Anwendungsfall mit den Akteuren Restaurant und Kunde angezeigt werden, jedoch außerhalb der Verantwortung der Website für die Essensbestellung.

### <a name="multiple-subsystems"></a>Mehrere Subsysteme
 Sie können mehrere Subsystembegrenzungen erstellen, um anzuzeigen, wie verschiedene Anwendungsfälle von unterschiedlichen Komponenten des Systems verarbeitet werden. For example, **Add Restaurant Appraisal** may be dealt with on a separate forum Web site. Denken Sie daran, dass es in einem Anwendungsfalldiagramm um die Dinge gehen sollte, die für die Benutzer sichtbar sind. Wenn Sie die interne Arbeitsaufteilung im System beschreiben möchten, können Sie die Verwendung eines Komponentendiagramms in Erwägung ziehen.

### <a name="system-versions"></a>Systemversionen
 Sie können verschiedene Subsystembegrenzungen verwenden, um unterschiedliche Versionen des Systems darzustellen. Der Anwendungsfall „Bezahlen“ kann z. B. in Version 2 der Website enthalten sein, aber nicht in Version 1. Dies impliziert, dass das System Kunden beim Aufgeben ihrer Bestellungen unterstützt. Die Bezahlung erfolgt jedoch direkt an das Restaurant.

 Use **Dependency** relations to link subsystems representing different versions or variants.

 ![Subsystems show different versions of a system](../modeling/media/uml-ucguidesystem.png "UML_UCGuideSystem")

## <a name="see-also"></a>Siehe auch
 [Model user requirements](../modeling/model-user-requirements.md) [UML Sequence Diagrams: Guidelines](../modeling/uml-sequence-diagrams-guidelines.md) [Edit UML models and diagrams](../modeling/edit-uml-models-and-diagrams.md) [UML Use Case Diagrams: Reference](../modeling/uml-use-case-diagrams-reference.md) [UML Class Diagrams: Reference](../modeling/uml-class-diagrams-reference.md) [UML Component Diagrams: Reference](../modeling/uml-component-diagrams-reference.md) [UML Activity Diagrams: Guidelines](../modeling/uml-activity-diagrams-guidelines.md) [Video: Organizing Features into Use Cases](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-2-organizing-features-into-use-cases)
