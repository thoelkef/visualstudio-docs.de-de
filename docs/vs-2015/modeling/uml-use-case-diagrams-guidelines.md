---
title: 'UML-Anwendungsfall Diagramme: Richtlinien | Microsoft-Dokumentation'
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
ms.openlocfilehash: 2d3434236908771cbc2149e766b841e7bcf4cb4e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667843"
---
# <a name="uml-use-case-diagrams-guidelines"></a>UML-Anwendungsfalldiagramme: Richtlinien
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio können Sie ein *Anwendungsfall Diagramm* zeichnen, um zusammenzufassen, wer die Anwendung oder das System verwendet und was Sie damit tun können. Um ein UML-Anwendungsfall Diagramm zu erstellen, klicken Sie im Menü **Architektur** auf **neues UML-oder ebenendiagramm**.

 Eine videodemo finden Sie unter [Organisieren von Features in Anwendungsfällen](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-2-Organizing-Features-Into-Use-Cases/).

 Welche Versionen von Visual Studio dieses Features unterstützen, erfahren Sie unter [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Mithilfe eines Anwendungsfalldiagramms können Sie Folgendes erläutern und kommunizieren:

- Die Szenarios, in denen das System oder die Anwendung mit Personen, Organisationen oder externen Systemen interagiert.

- Die Ziele, bei deren Erreichung die Akteure unterstützt werden.

- Den Umfang des Systems.

  Ein Anwendungsfalldiagramm zeigt die Details der Anwendungsfälle nicht an: Es fasst nur einige Beziehungen zwischen Anwendungsfällen, Akteuren und Systemen zusammen. Beispielsweise zeigt das Diagramm nicht die Reihenfolge an, in der Schritte ausgeführt werden, um die Ziele der einzelnen Anwendungsfälle zu erreichen. Sie können diese Details in anderen Diagrammen und Dokumenten beschreiben, die Sie mit jedem Anwendungsfall verknüpfen können. Weitere Informationen finden Sie in diesem Thema unter [beschreiben von Anwendungsfällen im Detail](#Details) .

  Die Beschreibungen, die Sie für Anwendungsfälle angeben, verwenden verschiedene Begriffe, die sich auf die Domäne beziehen, in der das System ausgeführt wird, z. B. Angebot, Speisekarte, Kunde usw. Es ist wichtig, diese Begriffe und ihre Beziehungen eindeutig zu definieren. Dafür können Sie ein UML-Klassendiagramm verwenden. Weitere Informationen finden Sie unter [UML-Klassendiagramme: Richtlinien](../modeling/uml-class-diagrams-guidelines.md).

  Bei Anwendungsfällen geht es nur um die Funktionsanforderungen eines Systems. Andere Anforderungen wie Geschäftsregeln, Servicequalitätsanforderungen und Implementierungseinschränkungen müssen separat dargestellt werden. Die Architektur und interne Details müssen ebenfalls gesondert beschrieben werden. Weitere Informationen zum Definieren von Benutzer Anforderungen finden Sie unter [Modell Benutzeranforderungen](../modeling/model-user-requirements.md).

  Die in diesem Thema verwendeten Beispiele beziehen sich auf eine Website, auf der Kunden Gerichte bei den örtlichen Restaurants bestellen können.

  ![Elemente in einem Anwendungsfall Diagramm](../modeling/media/uml-ucovactor.png "UML_UCOvActor")

- Ein *Akteur* (1) ist eine Klasse von Person, Organisation, Gerät oder externer Softwarekomponente, die mit Ihrem System interagiert. Beispiel Akteure sind **Customer**, **Restaurant**, **Temperatur Sensor**, **Kreditkarten Autorisierung.**

- Ein *Anwendungsfall* (2) stellt die Aktionen dar, die von einem oder mehreren Akteuren bei der Verfolgung eines bestimmten Ziels ausgeführt werden. Beispiele für Anwendungsfälle sind **Bestell Mahlzeit**, **Menü Aktualisieren**, **Zahlung verarbeiten**.

   In einem Anwendungsfalldiagramm sind Anwendungsfälle (3) den Akteuren zugeordnet, die diese ausführen.

- Ihr *System (4)* ist das, was Sie entwickeln. Beispielsweise kann es sich um eine kleine Softwarekomponente handeln, deren Akteure einfach nur andere Softwarekomponenten sind. Es kann sich auch um eine vollständige Anwendung oder um eine große verteilte Suite von Anwendungen handeln, die über viele Computer und Geräte hinweg bereitgestellt werden. Beispiele für Subsysteme sind die Website für die **Essens Bestellung**, das **Essens Liefergeschäft**, die **Website Version 2**.

   Ein Anwendungsfalldiagramm kann anzeigen, welche Anwendungsfälle vom System oder seinen Subsystemen unterstützt werden.

## <a name="BasicSteps"></a>Grundlegende Schritte zum Zeichnen von Anwendungsfall Diagrammen

> [!NOTE]
> Ausführliche Schritte zum Erstellen von Modellierungs Diagrammen werden unter [Bearbeiten von UML-Modellen und-Diagrammen](../modeling/edit-uml-models-and-diagrams.md)beschrieben.

#### <a name="to-create-a-new-use-case-diagram"></a>So erstellen Sie ein neues Anwendungsfalldiagramm

1. Klicken Sie im Menü **Architektur** auf **neues UML-oder ebenendiagramm**.

2. Klicken Sie unter **Vorlagen**auf **Umschlag für Umschlag Diagramm**.

3. Benennen Sie das Diagramm.

4. Wählen Sie unter **zu Modellierungsprojekt hinzufügen**ein vorhandenes Modellierungsprojekt in der Projekt Mappe aus, oder **Erstellen Sie ein neues Modellierungsprojekt**, und klicken Sie dann auf **OK**.

#### <a name="to-draw-a-use-case-diagram"></a>So zeichnen Sie ein Anwendungsfalldiagramm

1. Ziehen Sie **Subsystem** -Begrenzungen von der Toolbox auf das Diagramm, um entweder das gesamte System oder seine Hauptkomponenten darzustellen.

    - Sie können ein Anwendungsfalldiagramm ohne Systembegrenzungen zeichnen, wenn Sie nicht beschreiben möchten, welche Anwendungsfälle vom System oder seinen Komponenten unterstützt werden.

    - Ziehen Sie die Ecke eines Systems, um es bei Bedarf größer zu machen.

    - Benennen Sie es mit einem aussagekräftigen Namen.

2. Ziehen Sie **Actors** aus der Toolbox auf das Diagramm (platzieren Sie diese außerhalb der Systemgrenze).

    - Akteure stellen Klassen von Benutzern, Organisationen und externen Systemen dar, die mit dem System interagieren.

    - Benennen Sie diese um. Beispiel: **Kunde, Restaurant, Kreditkarten Agentur.**

3. Ziehen Sie **Anwendungsfälle** aus der Toolbox auf die entsprechenden Systeme.

    - Anwendungsfälle stellen die Aktivitäten dar, die Akteure mithilfe des Systems ausführen.

    - Benennen Sie diese um, indem Sie Titel verwenden, die für die Akteure verständlich sind. Verwenden Sie keine Titel, die sich auf Ihren Code beziehen. Beispiel: **Bestell Mahlzeit, Bezahlung für Mahlzeit, bereit**Stellung von Mahlzeit.

    - Beginnen Sie mit größeren Transaktionen, wie z. b. **Bestell Mahlzeit**, bis später kleinere Interaktionen, wie z. b. **Auswahlmenü Element**.

    - Platzieren Sie jeden Anwendungsfall im System oder im unterstützenden Hauptsubsystem. (Ignorieren Sie dabei alle Fassaden oder Komponenten, die nur dem Herstellen der Verbindung zum Benutzer dienen.)

    - Sie können einen Anwendungsfall außerhalb der Systembegrenzung zeichnen, um anzugeben, dass dieser nicht vom System unterstützt wird, zum Beispiel in einer bestimmten Version.

4. Klicken Sie in der Toolbox auf **Association** , dann auf einen Anwendungsfall und dann auf einen Akteur, der am Anwendungsfall teilnimmt. Verknüpfen Sie alle Akteure auf diese Weise mit ihren Anwendungsfällen.

5. Strukturieren Sie die Anwendungsfälle mit den Beziehungen **einschließen**, **erweitern** und **Generalisierung** . Klicken Sie zum Erstellen dieser Links jeweils auf das Tool und dann auf den Quellanwendungsfall und auf das Ziel. Weitere Informationen finden Sie im folgenden Abschnitt: [Strukturieren von Anwendungsfällen](#Structuring).

6. Beschreiben Sie die Anwendungsfälle ausführlicher. Weitere Informationen finden Sie im folgenden Abschnitt: [beschreiben von Anwendungsfällen im Detail](#Details).

7. Zeichnen Sie separate Diagramme für verschiedene Subsysteme oder andere Gruppen verwandter Anwendungsfälle. Alle Diagramme in einem Modellierungsprojekt sind Ansichten des gleichen Modells.

## <a name="Actors"></a>Zeichnen von Akteuren und Anwendungsfällen
 Der Hauptzweck eines Anwendungsfalldiagramms besteht darin anzuzeigen, wer mit dem System interagiert und welche Hauptziele erreicht werden sollen.

- Erstellen Sie **Akteure** , die Personen, Organisationen, andere Systeme, Software oder Geräte darstellen, die mit Ihrem System oder Subsystem interagieren.

  - Weitere Informationen zum Zeichnen von Akteuren und anderen Elementen finden Sie unter [Bearbeiten von UML-Modellen und-Diagrammen](../modeling/edit-uml-models-and-diagrams.md).

  - Geben Sie für jeden Satz mit Zielen die Akteure nach Typ oder Rolle an, auch wenn die physischen Personen oder Entitäten ggf. gleich sind. Beispielsweise sind Restaurant und Kunden separate Akteure, obwohl ein Restaurantmitarbeiter manchmal auch ein Kunde sein kann.

- Erstellen Sie **Anwendungsfälle** für jedes der Ziele, die von jedem Akteur mit dem System erreicht werden sollen.

  - Benennen und beschreiben Sie die Anwendungsfälle in Worten, die der Akteur versteht, und verwenden Sie keine Implementierungsbegriffe.

- Verwenden Sie **Zuordnungen** , um Actors mit Anwendungsfällen zu verknüpfen.

### <a name="inheritance-between-actors"></a>Vererbung zwischen Akteuren
 ![Anwendungsfall Diagramm mit Vererbung](../modeling/media/uml-ucguideinherit.png "UML_UCGuideInherit")

 Sie können einen **Generalisierungs** Link zwischen Akteuren zeichnen. Der spezialisierte Akteur wie Clubkunde im Beispiel, erbt die Anwendungsfälle des generalisierten Akteurs, z. B. Kunde. Die Pfeilspitze sollte auf den allgemeineren Akteur zeigen, z. B. Kunde. Zeigen Sie beim Erstellen des Links zuerst auf den spezialisierteren Akteur.

 Der spezialisierte Akteur kann über seine eigenen zusätzlichen Anwendungsfälle verfügen, die für die anderen Akteure nicht verfügbar sind.

> [!CAUTION]
> Sie sollten keine Schleifen aus Generalisierungsbeziehungen erstellen, die dazu führen, dass ein Akteur sich selbst generalisiert. Schleifen können zu Fehlern führen.

### <a name="alternative-actor-icons"></a>Alternative Akteursymbole
 Sie können benutzerdefinierte Symbole verwenden, um anstelle des standardmäßigen Strichmännchens einen Akteur darzustellen. Sie können es z. B. so ändern, dass es wie ein Gerät , ein Restaurant, eine Bank usw. aussieht.

##### <a name="to-change-the-appearance-of-an-actor"></a>So ändern Sie die Darstellung eines Akteurs

1. Klicken Sie mit der rechten Maustaste auf den Actor und dann auf **Eigenschaften**.

     Das Fenster **Eigenschaften** wird angezeigt.

2. Legen Sie die Eigenschaft **Bildpfad** auf den Speicherort einer Bilddatei fest.

    - Sie können verschiedene Bildformate wie GIF, JPG und BMP verwenden.

    - Verwenden Sie eine Datei, die in der Projektmappe oder in der Quellcodeverwaltung des Projekts enthalten ist, damit diese auch dann noch verfügbar ist, wenn die Projektmappe verschoben oder kopiert wird.

3. Um diese Darstellung in anderen Anwendungsfalldiagrammen zu replizieren, kopieren Sie den Akteur und fügen ihn in ein anderes Diagramm ein.

    - Die Änderung des Bilds gilt nur für die Ansicht in einem bestimmten Diagramm. Sie gilt nicht für das zugrunde liegende Modellelement. Wenn Sie den Akteur aus dem UML-Modell-Explorer in ein anderes Diagramm ziehen, wird er als standardmäßiges Strichmännchen angezeigt.

### <a name="multiplicities-between-actors-and-use-cases"></a>Multiplizitäten zwischen Akteuren und Anwendungsfällen
 Die Zuordnung zwischen einem Akteur und einem Anwendungsfall kann an jedem *Ende eine* Multiplizität anzeigen.

 ![Verwenden Sie den Fall eins mit dem Actor.](../modeling/media/uml-ucguidemulti1.png "UML_UCGuideMulti1")

> [!NOTE]
> Die Multiplizitäten einer Zuordnung in einem Anwendungsfall Diagramm werden ausgeblendet, wenn beide **1**sind.

 Standardmäßig ist jede Multiplizität **1**. Bei einer strengen Auslegung des Modells bedeutet eine Multiplizität von 1, dass z. B. nur jeweils ein Kunde an der Bestellung eines Gerichts beteiligt ist und dass jeder Kunde nur jeweils ein Gericht bestellt.

 Sie können diese Multiplizitäten ändern.

 Beispiel:

 ![Anwendungsfall, der viele bis viele Multiplizität anzeigt](../modeling/media/uml-ucguidemulti2.png "UML_UCGuideMulti2")

- Wenn Sie angeben möchten, dass mehrere Akteure derselben Klasse an einem einzelnen Vorkommen eines Anwendungsfalls beteiligt sein können, legen Sie die Multiplizität am Actor-Ende der Zuordnung auf **1.. \*** fest.

   In der Abbildung können ein oder mehrere Restaurants an der Erledigung der gleichen Essensbestellung beteiligt sein.

- Um anzuzeigen, dass jeder Akteur in mehreren Vorkommen eines Anwendungsfalls gleichzeitig teilnehmen kann, legen Sie die Multiplizität am Anwendungsfall Ende der Zuordnung auf **\*** fest.

   In der Abbildung kann jedes Restaurant gleichzeitig an der Erledigung von mehr als einer Bestellung arbeiten.

##### <a name="to-set-multiplicities-on-an-association"></a>So legen Sie Multiplizitäten für eine Zuordnung fest

1. Klicken Sie mit der rechten Maustaste auf die Zuordnung und dann auf **Eigenschaften**.

2. Erweitern Sie entweder **erste Rolle** oder **zweite Rolle**.

    *Role* bezeichnet das Element an einem Ende der Zuordnung.

3. Legen Sie die Eigenschaft „Multiplizität“ fest, indem Sie in der Liste eine der folgenden Optionen auswählen:

   - **1** geben Sie an, dass genau eine Instanz dieser Rolle an den einzelnen Links teilnimmt.

   - **1.. \*** , dass eine oder mehrere Instanzen dieser Rolle an den einzelnen Links beteiligt sind.

   - **0.. 1** zum angeben, dass die Teilnahme optional ist.

   - **\*** , dass NULL oder mehr Instanzen dieser Rolle am Link teilnehmen.

> [!NOTE]
> Viele Teams geben in Anwendungsfalldiagrammen keine Informationen zur Multiplizität an und behalten für die Multiplizitäten den Standardwert 1 bei. Stattdessen geben sie die Informationen in separaten Beschreibungen der Anwendungsfälle an. In diesem Fall werden alle Multiplizitäten in den Anwendungsfalldiagrammen ausgeblendet.

### <a name="using-an-actor-or-use-case-on-multiple-diagrams"></a>Verwenden eine Akteurs oder eines Anwendungsfalls in mehreren Diagrammen
 Sie können die gleichen Akteure und Anwendungsfälle in mehreren Diagrammen anzeigen. Beispiel:

- Sie können in unterschiedlichen Diagrammen die verschiedenen Anwendungsfälle beschreiben, an denen ein Akteur beteiligt ist.

- Sie können ein Diagramm verwenden, um die Akteure und Subsysteme anzuzeigen, denen ein Anwendungsfall zugeordnet ist, und ein anderes Diagramm, um anzuzeigen, wie der Anwendungsfall in enthaltene und erweiterte Anwendungsfälle unterteilt ist.

##### <a name="to-show-the-same-actor-or-use-case-on-different-diagrams"></a>So zeigen Sie den gleichen Akteur bzw. den gleichen Anwendungsfall in verschiedenen Diagrammen an

1. Erstellen Sie den Akteur bzw. den Anwendungsfall in einem Diagramm.

2. Erstellen Sie ein weiteres Anwendungsfalldiagramm.

3. Ziehen Sie einen Akteur oder einen Anwendungsfall aus dem **Modell-Explorer** auf das neue Diagramm.

    > [!NOTE]
    > Wenn Sie einen bereits zugeordneten Akteur und Anwendungsfall im neuen Diagramm anordnen, wird die Zuordnung dazwischen in dem neuen Diagramm automatisch angezeigt.

## <a name="Details"></a>Beschreiben von Anwendungsfällen im Detail
 Ein Anwendungsfall stellt Folgendes dar:

- Ziel eines Actors bei der Verwendung des Systems, z. b. **kaufen einer Mahlzeit** immer

- Ein oder mehrere *Szenarien*, d. h. Sequenzen von Schritten, die bei der Verfolgung des Ziels ausgeführt werden, z. b.: {**Order Mahlzeit, Pay, Deliver**}. Zusätzlich zu den Erfolgs Szenarien kann es mehrere Ausnahme-oder Fehler Szenarien geben, wie z. b. **Kreditkarte abgelehnt**.

  Ein Anwendungsfall kann in verschiedenen Ausführlichkeitsgraden beschrieben werden. In einer frühen Phase des Entwurfs ist der Name im Anwendungsfalldiagramm ausreichend.  Später können ausführlichere Beschreibungen der Szenarios geschrieben werden.

  In Visual Studio Ultimate können Sie einen Anwendungsfall auf verschiedene Arten beschreiben. Anwendungsfälle können einzeln oder gemeinsam verwendet werden:

- Verknüpfen Sie den Anwendungsfall mit einem oder mehreren Diagrammen im Projekt.

  - Mit einem Aktivitätsdiagramm können Sie einen komplexeren Prozess mit Schleifen, Verzweigungen und parallelen Threads erläutern. Darin kann auch der Fluss der Daten zwischen Teilen des Prozesses angezeigt werden. Weitere Informationen finden Sie unter [UML-Aktivitätsdiagramme: Richtlinien](../modeling/uml-activity-diagrams-guidelines.md).

  - Mit einem Sequenzdiagramm können Sie eine komplexe Reihe von Interaktionen zwischen verschiedenen Akteuren erklären. Außerdem können Sie diese Art von Diagramm verwenden, um darzustellen, was im System als Reaktion auf die einzelnen Anwendungsfälle ausgeführt wird. Weitere Informationen finden Sie unter [UML-Sequenzdiagramme: Richtlinien](../modeling/uml-sequence-diagrams-guidelines.md).

- Verknüpfen Sie den Anwendungsfall mit einer OneNote-Seite, einem OneNote-Abschnitt oder einem OneNote-Absatz, auf der bzw. in dem der Anwendungsfall ausführlich beschrieben wird.

- Verknüpfen Sie den Anwendungsfall mit einem Word-Dokument, in dem Sie Text, Screenshots usw. verwenden, um die Szenarios des Anwendungsfalls zu beschreiben. Weitere Informationen finden Sie unter [Modell Benutzeranforderungen](../modeling/model-user-requirements.md).

#### <a name="to-link-a-use-case-to-a-diagram-or-file-in-the-same-solution"></a>So verknüpfen Sie einen Anwendungsfall mit einem Diagramm oder einer Datei in der gleichen Projektmappe

1. Zeichnen Sie ein Diagramm, um ein Szenario des Anwendungsfalls zu veranschaulichen, z. B. ein Sequenz- oder Aktivitätsdiagramm.

2. Wechseln Sie zurück zum Anwendungsfalldiagramm.

3. Ziehen Sie das Diagramm oder die Datei vom Projektmappen-Explorer auf einen leeren Teil des Anwendungsfalldiagramms.

4. Stellen Sie eine Verbindung zwischen dem Element und dem Anwendungsfall mithilfe einer **Abhängigkeit**her.

#### <a name="to-link-to-a-solution-file-such-as-a-word-document-or-powerpoint-presentation"></a>So erstellen Sie einen Link zu einer Projektmappendatei (z. B. ein Word-Dokument oder eine PowerPoint-Präsentation)

1. Erstellen Sie ein Dokument, das Text, Screenshots usw. zum Beschreiben des Szenarios des Anwendungsfalls enthält.

2. Fügen Sie das Dokument der Projektmappe hinzu.

    1. Verschieben Sie das Word-Dokument in den gleichen Windows-Ordner wie die Projektmappe.

    2. Klicken Sie in Projektmappen-Explorer mit der rechten Maustaste auf die Lösung, zeigen Sie auf **Hinzufügen**, und klicken Sie dann auf **Vorhandenes Element**.

    3. Navigieren Sie zum Word-Dokument, und klicken Sie auf **Hinzufügen**.

         Das Word-Dokument wird im Projektmappen-Explorer in einem Projektmappenordner angezeigt.

3. Ziehen Sie das Word-Dokument aus dem Projektmappen-Explorer auf einen leeren Teil des Anwendungsfalldiagramms.

     Ein neues Artefakt wird angezeigt.

4. Stellen Sie eine Verbindung zwischen dem Element und dem Anwendungsfall mithilfe einer **Abhängigkeit**her.

#### <a name="to-link-to-a-shared-document-onenote-element-or-web-page"></a>So erstellen Sie einen Link zu einem freigegebenen Dokument, einem OneNote-Element oder einer Webseite

1. Sie benötigen die URL des freigegebenen Elements. Dies kann z. b. ein Netzwerkdatei Pfad sein, der mit "\\ \\" beginnt, oder eine Webseite oder SharePoint-URL, beginnend mit "http://", oder ein Link zu einem OneNote-Abschnitt, einer Seite oder einem Absatz, beginnend mit "OneNote:".

2. Klicken Sie in der Toolbox auf **artefaktelement** , und klicken Sie dann in das Anwendungsfall Diagramm.

3. Wenn das neue Element ausgewählt ist, geben Sie die URL in die **Hyperlink** -Eigenschaft ein oder fügen Sie Sie ein.

> [!NOTE]
> Sie können auf ein Artefakt doppelklicken, um das Diagramm oder das Dokument zu öffnen, mit dem es verknüpft ist.

### <a name="linking-use-cases-to-work-items"></a>Verknüpfen von Anwendungsfällen mit Arbeitsaufgaben
 Wenn das Projekt [!INCLUDE[vstsTfsRosarioLong](../includes/vststfsrosariolong-md.md)] verwendet und Sie [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] haben, können Sie jeden Anwendungsfall mit einer Arbeitsaufgabe in [!INCLUDE[esprfound](../includes/esprfound-md.md)] verknüpfen. Informationen dazu, wie Sie diese Links erstellen, finden Sie unter [Verknüpfen von Modellelementen und Arbeits Elementen](../modeling/link-model-elements-and-work-items.md).

 Sie haben dann folgende Möglichkeiten:

- Beschreiben Sie den Anwendungsfall in der verknüpften Arbeitsaufgabe. Wenn das Projekt die Visual Studio-Prozessvorlage „Formal“ verwendet, können Sie einen Link zu einer Anwendungsfall-Arbeitsaufgabe einrichten. Dieser Arbeitsaufgabentyp stellt Felder zum Beschreiben der Ziele und Szenarios des Anwendungsfalls bereit.

- Verknüpfen Sie Testfälle mit dem Anwendungsfall, damit Sie Berichte dazu abrufen können, in welchem Umfang der entwickelte Code den Anwendungsfall implementiert.

- Verknüpfen Sie Aufgaben mit dem Anwendungsfall, damit Sie den Status der Entwicklungsarbeit nachverfolgen können.

## <a name="Structuring"></a>Strukturieren von Anwendungsfällen
 Sie sollten versuchen, das Verhalten des Systems nur mit einigen wenigen Hauptanwendungsfällen zu beschreiben. Für jeden großen Anwendungsfall ist ein Hauptziel definiert, für dessen Erreichung ein Akteur zuständig ist, z. B. das Kaufen eines Produkts oder aus Anbietersicht das Anbieten von Produkten zum Verkauf.

 Wenn Sie diese Ziele verdeutlicht haben, können Sie weitere Details dazu angeben, wie die einzelnen Ziele erreicht werden und welche Variationen es bei den grundlegenden Zielen gibt.

 Vermeiden Sie es, die Anwendungsfälle zu stark zu unterteilen. Bei Anwendungsfällen geht es um die Benutzererfahrung mit dem System, nicht so sehr um die internen Details. Außerdem ist es meist produktiver, nur erste Arbeitsversionen des Codes zu erstellen, anstatt zu viel Zeit mit dem ausführlichen Strukturieren der Anwendungsfälle zu verbringen.

 Sie können in einem Anwendungsfalldiagramm die Beziehungen zwischen den Hauptanwendungsfällen und ausführlicheren Anwendungsfällen zusammenfassen. Dies wird in den folgenden Abschnitten beschrieben:

- [Anzeigen der Details eines Anwendungsfalls mit include](#Include)

- [Gemeinsame Nutzung von Zielen mit Generalisierung](#Inheritance)

- [Aufteilen von Variant-Fällen durch Erweitern](#Extend)

### <a name="Include"></a>Anzeigen der Details eines Anwendungsfalls mit include
 Verwenden Sie eine **include** -Beziehung, um anzuzeigen, dass ein Anwendungsfall einige Details eines anderen beschreibt. Sortieren Sie in der Abbildung die **Bestellung** , **und**wählen **Sie das Menü**aus, und wählen Sie Menü **Element**aus. Jeder der enthaltenen ausführlicheren Anwendungsfälle ist ein Schritt, den der Akteur oder die Akteure ggf. ausführen müssen, um das Gesamtziel des einschließenden Anwendungsfalls zu erreichen. Der Pfeil sollte auf den ausführlicheren eingeschlossenen Anwendungsfall zeigen.

> [!CAUTION]
> Sie sollten keine Schleifen aus Beziehungen vom Typ „Einschließen“ erstellen, die dazu führen, dass ein Anwendungsfall sich selbst enthält. Schleifen können zu Fehlern führen.

 Sie können eingeschlossene Anwendungsfälle freigeben. In diesem Beispiel umfassen die Anwendungsfälle **Bestellung** und **Abonnement** Überprüfung die **Zahlen Pay**.

 ![Mit include aufgesetzte Anwendungsfälle](../modeling/media/uml-ucguideinclude.png "UML_UCGuideInclude")

 Das Ziel und die Szenarios eines eingeschlossenen Anwendungsfalls sollten auch unabhängig voneinander Sinn ergeben, damit diese in Anwendungsfälle einbezogen werden können, die später entworfen werden.

 Das Unterteilen von Anwendungsfällen in einschließende und eingeschlossene Teile ist nützlich, um die folgenden Ziele zu erreichen:

- Strukturieren der Anwendungsfallbeschreibungen in verschiedene Detailebenen

- Vermeiden der Wiederholung von freigegebenen Szenarios in verschiedenen Anwendungsfällen

#### <a name="Steps"></a>Definieren der Reihenfolge der ausführlichen Schritte
 Das Anwendungsfalldiagramm sagt weder etwas über die Reihenfolge aus, in der die ausführlicheren Schritte ausgeführt werden müssen, noch darüber, ob jeder Schritt immer erforderlich ist.

 Um die Reihenfolge der Schritte zu vereinfachen, können **Sie ein Element verwenden, um ein** separates Dokument an den einfügenden Anwendungsfall anzufügen. Im folgenden Beispiel ist ein Aktivitätsdiagramm an den Anwendungsfall Gericht bestellen angefügt. Alternativ dazu können Sie ein Textdokument verwenden, das eine Liste von Schritten oder eine Sequenz von Screenshots enthält. Weitere Informationen finden Sie [im Detail unter beschreiben von Anwendungsfällen](#Details).

 Beachten Sie beim Verwenden eines Aktivitätsdiagramms die folgenden Namenskonventionen:

- Der Name der gesamten Aktivität entspricht dem Namen des einschließenden Anwendungsfalls.

- Die Aktionen im Aktivitätsdiagramm haben die gleichen Namen wie die eingeschlossenen Anwendungsfälle.

  Weitere Informationen finden Sie unter [UML-Aktivitätsdiagramme: Richtlinien](../modeling/uml-activity-diagrams-guidelines.md).

  ![Im verknüpften Aktivitätsdiagramm gezeigte Anwendungsfall Schritte](../modeling/media/uml-ucguidesteps.png "UML_UCGuideSteps")

### <a name="Inheritance"></a>Gemeinsame Nutzung von Zielen mit Generalisierung
 Verwenden Sie eine Generalisierungs Beziehung, um anzuzeigen, dass ein *spezieller* Anwendungsfall eine bestimmte Möglichkeit zum Erreichen der Ziele ist, die von einem anderen *allgemeinen* Anwendungsfall ausgedrückt werden. Die geöffnete Pfeilspitze sollte auf den allgemeineren Anwendungsfall zeigen.

 ![Anwendungsfälle mit der Generalisierungs Beziehung](../modeling/media/uml-ucguidegeneral.png "UML_UCGuideGeneral")

 Beispiels **Weise wird die Zahlung** **per Kreditkarte** und Zahlung **per Bargeld**generalisiert.

> [!CAUTION]
> Sie sollten keine Schleifen aus Generalisierungsbeziehungen erstellen, die dazu führen, dass ein Akteur sich selbst generalisiert. Schleifen können zu Fehlern führen.

 Mithilfe von spezialisierten Anwendungsfällen können Sie andere Methoden anzeigen, mit denen das System das gleiche Ziel erreichen kann.

 Die spezialisierten Anwendungsfälle sollen die Ziele und Akteure des allgemeinen Anwendungsfalls erben. Der allgemeine Anwendungsfall muss keine eigenen Szenarios haben. Seine Spezialisierungen beschreiben verschiedene Methoden zur Erreichung der Ziele.

##### <a name="to-refactor-common-goals-from-two-or-more-use-cases"></a>So gestalten Sie allgemeine Ziele von zwei oder mehr Anwendungsfällen um

1. Erstellen und benennen Sie den neuen allgemeinen Anwendungsfall.

2. Erstellen Sie eine **Generalisierungs** Beziehung mit dem großen Pfeil, der auf den neuen allgemeinen Anwendungsfall zeigt.

    1. Klicken Sie in der Toolbox auf **Generalisierung** .

    2. Klicken Sie auf einen speziellen Anwendungsfall (im Beispiel**Zahlen per Kreditkarte** ).

    3. Klicken Sie auf den allgemeinen Anwendungsfall (im Beispiel**bezahlen** ).

3. Wenn Sie die Ziele für die spezialisierten Anwendungsfälle beschrieben haben, verschieben Sie die gemeinsamen Teile in die Beschreibung des allgemeinen Anwendungsfalls.

4. Akteure, die von den spezialisierten Anwendungsfällen gemeinsam genutzt werden, können in den allgemeinen Anwendungsfall verschoben werden.

### <a name="Extend"></a>Trennen von Variant-Fällen durch Erweitern
 Verwenden Sie einen Link vom Typ „Erweitern“, um anzugeben, dass ein Anwendungsfall einem anderen Anwendungsfall unter bestimmten Umständen Funktionen hinzufügen kann. Der Pfeil sollte auf den erweiterten Hauptanwendungsfall zeigen.

 ![Ein Anwendungsfall, der einen anderen erweitert](../modeling/media/uml-ucguideextend.png "UML_UCGuideExtend")

> [!CAUTION]
> Sie sollten keine Schleifen aus Erweiterungsbeziehungen erstellen, die dazu führen, dass ein Akteur sich selbst generalisiert. Schleifen können zu Fehlern führen.

 Beispielsweise kann der **Anmelde** Anwendungsfall einer typischen Website das **Registrieren eines neuen Benutzers** einschließen, aber nur, wenn der Benutzer nicht bereits über ein Konto verfügt.

##### <a name="to-separate-a-use-case-into-main-and-extending-parts"></a>So unterteilen Sie einen Anwendungsfall in Hauptbestandteile und Erweiterungsteile

1. Erstellen und benennen Sie den neuen erweiterten Anwendungsfall.

2. Erstellen Sie **eine Erweiterungs** Beziehung mit dem Pfeil, der auf den erweiterten Anwendungsfall zeigt.

   1. Klicken Sie in der Toolbox auf **erweitern** .

   2. Klicken Sie auf den erweiterten Anwendungsfall (registrieren Sie den**neuen Benutzer** im Beispiel).

   3. Klicken Sie auf den erweiterten Anwendungsfall (im Beispiel**Anmelden** ).

       > [!NOTE]
       > Vermeiden Sie es, im Diagramm eine Schleife von Erweiterungsbeziehungen zu erstellen. Ein Anwendungsfall darf keine Erweiterung von sich selbst darstellen.

3. Verschieben Sie die relevanten Schritte in das Szenario der Erweiterung, falls Sie für den erweiterten Anwendungsfall bereits Szenarios erstellt haben.

4. Die Beschreibung der Erweiterung (im Beispiel "**neuen Benutzer registrieren** ") sollte Details dazu enthalten, wo in den Haupt Anwendungs Szenarios, in denen Sie ausgeführt wird, und unter welchen Umständen. Sehen Sie diesen Schritt als Änderung der Beschreibung des Hauptanwendungsfalls an.

   Der Erweiterungsanwendungsfall stellt Szenarioschritte dar, die andernfalls Teil des Hauptanwendungsfall-Szenarios wären. Das Szenario und das Ziel der Erweiterung werden immer im Kontext des Hauptanwendungsfalls gelesen und müssen deshalb keinen direkten unabhängigen Nutzen aufweisen.

   Das Abtrennen von Erweiterungen kann nützlich sein, um die folgenden Situationen zu beschreiben:

- Es sind zusätzliche Akteure vorhanden, die nur am Erweiterungsanwendungsfall beteiligt sind. Beispielsweise muss ein Administrator die Registrierung eines Kunden auf der Website genehmigen.

- Ein separates Subsystem verarbeitet den Erweiterungsanwendungsfall.

- Diese Erweiterung ist nur in bestimmten Versionen des Systems verfügbar. Sie können jede Version im Anwendungsfalldiagramm als separates Subsystem anzeigen.

## <a name="Subsystems"></a>Verwenden von subsystemgrenzen
 Verwenden Sie eine Subsystembegrenzung, um anzugeben, welche Anwendungsfälle innerhalb des Bereichs des Systems liegen.

#### <a name="to-draw-a-subsystem-boundary"></a>So zeichnen Sie eine Subsystembegrenzung

1. Klicken Sie in der Toolbox auf **Subsystem**, und klicken Sie dann auf das Diagramm.

    Ein Subsystem wird im Diagramm angezeigt.

2. Ziehen Sie die Ecken des Subsystems, um seine Größe anzupassen.

3. Ziehen Sie vorhandene Anwendungsfälle in das oder aus dem Subsystem, um seinen Inhalt anzupassen.

   \- oder -

   Um einen neuen Anwendungsfall direkt in einem Subsystem zu erstellen, klicken Sie in der Toolbox auf **Anwendungsfall** , und klicken Sie dann innerhalb des Subsystems.

> [!NOTE]
> Die Eigenschaft " **Subjects** " eines Anwendungsfalls gibt an, in welchem Subsystem Sie enthalten ist.

### <a name="use-cases-outside-the-system-scope"></a>Anwendungsfälle außerhalb des Systembereichs
 Es ist häufig nützlich, Anwendungsfälle in das Diagramm einzubeziehen, die Teil des Geschäftsablaufs sind, aber nicht mit dem in der Entwicklung befindlichen System verarbeitet werden. Auf diese Weise können Entwickler den Kontext ihrer Arbeit besser verstehen. „Gericht liefern“ kann z. B. als Anwendungsfall mit den Akteuren Restaurant und Kunde angezeigt werden, jedoch außerhalb der Verantwortung der Website für die Essensbestellung.

### <a name="multiple-subsystems"></a>Mehrere Subsysteme
 Sie können mehrere Subsystembegrenzungen erstellen, um anzuzeigen, wie verschiedene Anwendungsfälle von unterschiedlichen Komponenten des Systems verarbeitet werden. Beispielsweise kann das **Hinzufügen der Restaurant Bewertung** auf einer separaten Forums Website behandelt werden. Denken Sie daran, dass es in einem Anwendungsfalldiagramm um die Dinge gehen sollte, die für die Benutzer sichtbar sind. Wenn Sie die interne Arbeitsaufteilung im System beschreiben möchten, können Sie die Verwendung eines Komponentendiagramms in Erwägung ziehen.

### <a name="system-versions"></a>Systemversionen
 Sie können verschiedene Subsystembegrenzungen verwenden, um unterschiedliche Versionen des Systems darzustellen. Der Anwendungsfall „Bezahlen“ kann z. B. in Version 2 der Website enthalten sein, aber nicht in Version 1. Dies impliziert, dass das System Kunden beim Aufgeben ihrer Bestellungen unterstützt. Die Bezahlung erfolgt jedoch direkt an das Restaurant.

 Verwenden Sie **Abhängigkeits** Beziehungen zum Verknüpfen von Subsystemen, die unterschiedliche Versionen oder Varianten darstellen.

 ![Subsysteme zeigen verschiedene Versionen eines Systems an.](../modeling/media/uml-ucguidesystem.png "UML_UCGuideSystem")

## <a name="see-also"></a>Siehe auch
 [Modell Benutzer Anforderungen](../modeling/model-user-requirements.md) [UML-Sequenzdiagramme: Richtlinien](../modeling/uml-sequence-diagrams-guidelines.md) [Bearbeiten von UML-Modellen und Diagrammen UML-](../modeling/edit-uml-models-and-diagrams.md) [Anwendungsfall Diagramme: Referenz](../modeling/uml-use-case-diagrams-reference.md) [UML-Klassendiagramme: Referenz](../modeling/uml-class-diagrams-reference.md) [UML-Komponenten Diagramme: Referenz](../modeling/uml-component-diagrams-reference.md) [UML Aktivitätsdiagramme:](../modeling/uml-activity-diagrams-guidelines.md) [richtlinienvideo: Organisieren von Features in Anwendungsfällen](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-2-Organizing-Features-Into-Use-Cases/)
