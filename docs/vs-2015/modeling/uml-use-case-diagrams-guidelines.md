---
title: 'UML-Anwendungsfalldiagramme: Richtlinien | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- diagrams - modeling, use case
- UML, use case diagrams
- diagrams - modeling, UML use case
- use case diagrams
- UML diagrams, use case
ms.assetid: b1ae8ed0-d00b-4f9b-8e23-733e09e81e9b
caps.latest.revision: 38
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 4abd008584732955bdac982dbaa0a629bd9ef90e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49214239"
---
# <a name="uml-use-case-diagrams-guidelines"></a>UML-Anwendungsfalldiagramme: Richtlinien
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können in Visual Studio zeichnen eine *Anwendungsfalldiagramm* zusammengefasst, die Ihre Anwendung oder das System verwendet und wie sie es verwenden können. Erstellen Sie ein UML-Anwendungsfalldiagramm, auf die **Architektur** Menü klicken Sie auf **neues UML- oder Ebenendiagramm**.  
  
 Eine Videodemo finden Sie unter [Organisieren von Funktionen in Anwendungsfällen](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-2-Organizing-Features-Into-Use-Cases/).  
  
 Welche Versionen von Visual Studio dieses Feature unterstützen, erfahren Sie unter [Versionsunterstützung für Architektur- und Modellierungstools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Mithilfe eines Anwendungsfalldiagramms können Sie Folgendes erläutern und kommunizieren:  
  
-   Die Szenarios, in denen das System oder die Anwendung mit Personen, Organisationen oder externen Systemen interagiert.  
  
-   Die Ziele, bei deren Erreichung die Akteure unterstützt werden.  
  
-   Den Umfang des Systems.  
  
 Ein Anwendungsfalldiagramm zeigt die Details der Anwendungsfälle nicht an: Es fasst nur einige Beziehungen zwischen Anwendungsfällen, Akteuren und Systemen zusammen. Beispielsweise zeigt das Diagramm nicht die Reihenfolge an, in der Schritte ausgeführt werden, um die Ziele der einzelnen Anwendungsfälle zu erreichen. Sie können diese Details in anderen Diagrammen und Dokumenten beschreiben, die Sie mit jedem Anwendungsfall verknüpfen können. Weitere Informationen finden Sie unter [Ausführliches Beschreiben von Anwendungsfällen](#Details) in diesem Thema.  
  
 Die Beschreibungen, die Sie für Anwendungsfälle angeben, verwenden verschiedene Begriffe, die sich auf die Domäne beziehen, in der das System ausgeführt wird, z. B. Angebot, Speisekarte, Kunde usw. Es ist wichtig, diese Begriffe und ihre Beziehungen eindeutig zu definieren. Dafür können Sie ein UML-Klassendiagramm verwenden. Weitere Informationen finden Sie unter [UML-Klassendiagramme: Richtlinien](../modeling/uml-class-diagrams-guidelines.md).  
  
 Bei Anwendungsfällen geht es nur um die Funktionsanforderungen eines Systems. Andere Anforderungen wie Geschäftsregeln, Servicequalitätsanforderungen und Implementierungseinschränkungen müssen separat dargestellt werden. Die Architektur und interne Details müssen ebenfalls gesondert beschrieben werden. Weitere Informationen dazu, wie Sie die Definition der benutzeranforderungen finden Sie unter [Modellieren von benutzeranforderungen](../modeling/model-user-requirements.md).  
  
 Die in diesem Thema verwendeten Beispiele beziehen sich auf eine Website, auf der Kunden Gerichte bei den örtlichen Restaurants bestellen können.  
  
 ![Elemente in einem Anwendungsfalldiagramm](../modeling/media/uml-ucovactor.png "UML_UCOvActor")  
  
-   Ein *Actor* (1) ist eine Klasse von Person, Organisation, Gerät oder externer Softwarekomponente, die mit dem System interagiert. Beispielakteure sind **Kunden**, **Restaurant**, **Temperatursensor**, **Kreditkartenprüfung.**  
  
-   Ein *Anwendungsfall* (2) stellt die Aktionen, die von einem oder mehreren Akteuren zur Erreichung eines bestimmten Ziels ausgeführt werden. Beispiele für Anwendungsfälle sind **Gericht bestellen**, **Speisekarte aktualisieren**, **Zahlung verarbeiten**.  
  
     In einem Anwendungsfalldiagramm sind Anwendungsfälle (3) den Akteuren zugeordnet, die diese ausführen.  
  
-   Ihre *System (4)* ist, was Sie entwickeln. Beispielsweise kann es sich um eine kleine Softwarekomponente handeln, deren Akteure einfach nur andere Softwarekomponenten sind. Es kann sich auch um eine vollständige Anwendung oder um eine große verteilte Suite von Anwendungen handeln, die über viele Computer und Geräte hinweg bereitgestellt werden. Beispiele für Subsysteme sind **Meal Ordering Website**, **Mahlzeit Essenslieferservice**, **Version 2 der Website**.  
  
     Ein Anwendungsfalldiagramm kann anzeigen, welche Anwendungsfälle vom System oder seinen Subsystemen unterstützt werden.  
  
##  <a name="BasicSteps"></a> Grundlegende Schritte zum Zeichnen von Anwendungsfalldiagrammen  
  
> [!NOTE]
>  Ausführliche Schritte zum Erstellen der Modellierungsdiagramme beschrieben sind [Bearbeiten von UML-Modellen und Diagrammen](../modeling/edit-uml-models-and-diagrams.md).  
  
#### <a name="to-create-a-new-use-case-diagram"></a>So erstellen Sie ein neues Anwendungsfalldiagramm  
  
1.  Auf der **Architektur** Menü klicken Sie auf **neues UML- oder Ebenendiagramm**.  
  
2.  Klicken Sie unter **Vorlagen**, klicken Sie auf **UMLUse Fall Diagramm**.  
  
3.  Benennen Sie das Diagramm.  
  
4.  In **zu Modellierungsprojekt hinzufügen**, wählen Sie ein vorhandenes Modellierungsprojekt aus, in der Projektmappe oder **Neues Modellierungsprojekt erstellen**, und klicken Sie dann auf **OK**.  
  
#### <a name="to-draw-a-use-case-diagram"></a>So zeichnen Sie ein Anwendungsfalldiagramm  
  
1.  Ziehen Sie **Subsystem** -Begrenzungen aus der Toolbox in das Diagramm, um entweder das ganze System oder seine Hauptkomponenten darzustellen.  
  
    -   Sie können ein Anwendungsfalldiagramm ohne Systembegrenzungen zeichnen, wenn Sie nicht beschreiben möchten, welche Anwendungsfälle vom System oder seinen Komponenten unterstützt werden.  
  
    -   Ziehen Sie die Ecke eines Systems, um es bei Bedarf größer zu machen.  
  
    -   Benennen Sie es mit einem aussagekräftigen Namen.  
  
2.  Ziehen Sie **Actors** aus der Toolbox auf das Diagramm (Platzierung außerhalb aller systembegrenzungen).  
  
    -   Akteure stellen Klassen von Benutzern, Organisationen und externen Systemen dar, die mit dem System interagieren.  
  
    -   Benennen Sie diese um. Zum Beispiel: **Kunde, Restaurant, Kreditkartenanbieter.**  
  
3.  Ziehen Sie **Anwendungsfälle** aus der Toolbox auf die entsprechenden Systeme.  
  
    -   Anwendungsfälle stellen die Aktivitäten dar, die Akteure mithilfe des Systems ausführen.  
  
    -   Benennen Sie diese um, indem Sie Titel verwenden, die für die Akteure verständlich sind. Verwenden Sie keine Titel, die sich auf Ihren Code beziehen. Zum Beispiel: **Gericht bestellen, Gericht bezahlen, Gericht liefern**.  
  
    -   Beginnen Sie mit Haupttransaktionen wie z. B. **Gericht bestellen**dadurch bleibt bis zum höher kleinere Interaktionen wie z. B. **Gericht auswählen auf**.  
  
    -   Platzieren Sie jeden Anwendungsfall im System oder im unterstützenden Hauptsubsystem. (Ignorieren Sie dabei alle Fassaden oder Komponenten, die nur dem Herstellen der Verbindung zum Benutzer dienen.)  
  
    -   Sie können einen Anwendungsfall außerhalb der Systembegrenzung zeichnen, um anzugeben, dass dieser nicht vom System unterstützt wird, zum Beispiel in einer bestimmten Version.  
  
4.  Klicken Sie auf **Zuordnung** auf der Toolbox, und klicken Sie dann einen Anwendungsfall und dann auf einen Akteur, die am Anwendungsfall beteiligt ist. Verknüpfen Sie alle Akteure auf diese Weise mit ihren Anwendungsfällen.  
  
5.  Strukturieren Sie die Anwendungsfälle mit den **Include**, **erweitern** und **Generalisierung** Beziehungen. Klicken Sie zum Erstellen dieser Links jeweils auf das Tool und dann auf den Quellanwendungsfall und auf das Ziel. Finden Sie im folgenden Abschnitt [Strukturieren von Anwendungsfällen](#Structuring).  
  
6.  Beschreiben Sie die Anwendungsfälle ausführlicher. Finden Sie im folgenden Abschnitt [Ausführliches Beschreiben von Anwendungsfällen](#Details).  
  
7.  Zeichnen Sie separate Diagramme für verschiedene Subsysteme oder andere Gruppen verwandter Anwendungsfälle. Alle Diagramme in einem Modellierungsprojekt sind Ansichten des gleichen Modells.  
  
##  <a name="Actors"></a> Zeichnen von Akteuren und Anwendungsfällen  
 Der Hauptzweck eines Anwendungsfalldiagramms besteht darin anzuzeigen, wer mit dem System interagiert und welche Hauptziele erreicht werden sollen.  
  
-   Erstellen Sie **Actors** zur Darstellung der Klassen von Personen, Organisationen, anderen Systemen, Software oder Geräten, die mit dem System oder Subsystem interagieren.  
  
    -   Gewusst wie: Zeichnen von Akteuren und anderen Elementen finden Sie unter [Bearbeiten von UML-Modellen und Diagrammen](../modeling/edit-uml-models-and-diagrams.md).  
  
    -   Geben Sie für jeden Satz mit Zielen die Akteure nach Typ oder Rolle an, auch wenn die physischen Personen oder Entitäten ggf. gleich sind. Beispielsweise sind Restaurant und Kunden separate Akteure, obwohl ein Restaurantmitarbeiter manchmal auch ein Kunde sein kann.  
  
-   Erstellen Sie **Anwendungsfälle** für jedes einzelne Ziel, die einzelnen Akteure mithilfe des Systems erreichen.  
  
    -   Benennen und beschreiben Sie die Anwendungsfälle in Worten, die der Akteur versteht, und verwenden Sie keine Implementierungsbegriffe.  
  
-   Verwenden Sie **Zuordnungen** Akteure mit Anwendungsfällen zu verknüpfen.  
  
### <a name="inheritance-between-actors"></a>Vererbung zwischen Akteuren  
 ![Anwendungsfalldiagramm mit Vererbung](../modeling/media/uml-ucguideinherit.png "UML_UCGuideInherit")  
  
 Sie können zeichnen eine **Generalisierung** Link zwischen Akteuren. Der spezialisierte Akteur wie Clubkunde im Beispiel, erbt die Anwendungsfälle des generalisierten Akteurs, z. B. Kunde. Die Pfeilspitze sollte auf den allgemeineren Akteur zeigen, z. B. Kunde. Zeigen Sie beim Erstellen des Links zuerst auf den spezialisierteren Akteur.  
  
 Der spezialisierte Akteur kann über seine eigenen zusätzlichen Anwendungsfälle verfügen, die für die anderen Akteure nicht verfügbar sind.  
  
> [!CAUTION]
>  Sie sollten keine Schleifen aus Generalisierungsbeziehungen erstellen, die dazu führen, dass ein Akteur sich selbst generalisiert. Schleifen können zu Fehlern führen.  
  
### <a name="alternative-actor-icons"></a>Alternative Akteursymbole  
 Sie können benutzerdefinierte Symbole verwenden, um anstelle des standardmäßigen Strichmännchens einen Akteur darzustellen. Sie können es z. B. so ändern, dass es wie ein Gerät , ein Restaurant, eine Bank usw. aussieht.  
  
##### <a name="to-change-the-appearance-of-an-actor"></a>So ändern Sie die Darstellung eines Akteurs  
  
1.  Mit der rechten Maustaste des Akteurs, und klicken Sie dann auf **Eigenschaften**.  
  
     Die **Eigenschaften** Fenster wird angezeigt.  
  
2.  Legen Sie die **Bildpfad** Eigenschaft, um den Speicherort der Bilddatei.  
  
    -   Sie können verschiedene Bildformate wie GIF, JPG und BMP verwenden.  
  
    -   Verwenden Sie eine Datei, die in der Projektmappe oder in der Quellcodeverwaltung des Projekts enthalten ist, damit diese auch dann noch verfügbar ist, wenn die Projektmappe verschoben oder kopiert wird.  
  
3.  Um diese Darstellung in anderen Anwendungsfalldiagrammen zu replizieren, kopieren Sie den Akteur und fügen ihn in ein anderes Diagramm ein.  
  
    -   Die Änderung des Bilds gilt nur für die Ansicht in einem bestimmten Diagramm. Sie gilt nicht für das zugrunde liegende Modellelement. Wenn Sie den Akteur aus dem UML-Modell-Explorer in ein anderes Diagramm ziehen, wird er als standardmäßiges Strichmännchen angezeigt.  
  
### <a name="multiplicities-between-actors-and-use-cases"></a>Multiplizitäten zwischen Akteuren und Anwendungsfällen  
 Die Zuordnung zwischen einem Akteur und Anwendungsfall kann anzeigen, eine *Multiplizität* an beiden Enden.  
  
 ![Anwendungsfall 1: 1 mit Akteur](../modeling/media/uml-ucguidemulti1.png "UML_UCGuideMulti1")  
  
> [!NOTE]
>  Die Multiplizitäten einer Zuordnung in einem Anwendungsfalldiagramm sind ausgeblendet, wenn beide **1**.  
  
 Wird standardmäßig jede Multiplizität **1**. Bei einer strengen Auslegung des Modells bedeutet eine Multiplizität von 1, dass z. B. nur jeweils ein Kunde an der Bestellung eines Gerichts beteiligt ist und dass jeder Kunde nur jeweils ein Gericht bestellt.  
  
 Sie können diese Multiplizitäten ändern.  
  
 Zum Beispiel:  
  
 ![Anwendungsfall mit m: n-Multiplizität](../modeling/media/uml-ucguidemulti2.png "UML_UCGuideMulti2")  
  
-   Um darauf hinzuweisen, dass mehrere Akteure der gleichen Klasse ein einzelnes Vorkommen eines Anwendungsfalls teilnehmen können, legen Sie die Multiplizität am Akteursende der Zuordnung auf **1..\*** .  
  
     In der Abbildung können ein oder mehrere Restaurants an der Erledigung der gleichen Essensbestellung beteiligt sein.  
  
-   Um anzuzeigen, dass jeder Akteur gleichzeitig an mehreren Vorkommen eines Anwendungsfalls beteiligt sein kann, legen Sie die Multiplizität am Anwendungsfallende der Zuordnung auf **\***.  
  
     In der Abbildung kann jedes Restaurant gleichzeitig an der Erledigung von mehr als einer Bestellung arbeiten.  
  
##### <a name="to-set-multiplicities-on-an-association"></a>So legen Sie Multiplizitäten für eine Zuordnung fest  
  
1.  Mit der rechten Maustaste in der Zuordnung, und klicken Sie dann auf **Eigenschaften**.  
  
2.  Erweitern Sie entweder **erste Rolle** oder **zweite Rolle**.  
  
     *Rolle* steht für das Element an einem Ende der Zuordnung.  
  
3.  Legen Sie die Eigenschaft „Multiplizität“ fest, indem Sie in der Liste eine der folgenden Optionen auswählen:  
  
    -   **1** angeben, dass genau eine Instanz dieser Rolle jedem Link teilnimmt.  
  
    -   **1..\***  , Status, der eine oder mehrere Instanzen dieser Rolle, die jedem Link teilnehmen.  
  
    -   **0.. 1** um anzugeben, dass die Teilnahme optional ist.  
  
    -   **\*** um anzugeben, dass NULL oder mehr Instanzen dieser Rolle am Link teilnehmen.  
  
> [!NOTE]
>  Viele Teams geben in Anwendungsfalldiagrammen keine Informationen zur Multiplizität an und behalten für die Multiplizitäten den Standardwert 1 bei. Stattdessen geben sie die Informationen in separaten Beschreibungen der Anwendungsfälle an. In diesem Fall werden alle Multiplizitäten in den Anwendungsfalldiagrammen ausgeblendet.  
  
### <a name="using-an-actor-or-use-case-on-multiple-diagrams"></a>Verwenden eine Akteurs oder eines Anwendungsfalls in mehreren Diagrammen  
 Sie können die gleichen Akteure und Anwendungsfälle in mehreren Diagrammen anzeigen. Zum Beispiel:  
  
-   Sie können in unterschiedlichen Diagrammen die verschiedenen Anwendungsfälle beschreiben, an denen ein Akteur beteiligt ist.  
  
-   Sie können ein Diagramm verwenden, um die Akteure und Subsysteme anzuzeigen, denen ein Anwendungsfall zugeordnet ist, und ein anderes Diagramm, um anzuzeigen, wie der Anwendungsfall in enthaltene und erweiterte Anwendungsfälle unterteilt ist.  
  
##### <a name="to-show-the-same-actor-or-use-case-on-different-diagrams"></a>So zeigen Sie den gleichen Akteur bzw. den gleichen Anwendungsfall in verschiedenen Diagrammen an  
  
1.  Erstellen Sie den Akteur bzw. den Anwendungsfall in einem Diagramm.  
  
2.  Erstellen Sie ein weiteres Anwendungsfalldiagramm.  
  
3.  Ziehen Sie einen Akteur oder Anwendungsfall aus **Modell-Explorer** in das neue Diagramm.  
  
    > [!NOTE]
    >  Wenn Sie einen bereits zugeordneten Akteur und Anwendungsfall im neuen Diagramm anordnen, wird die Zuordnung dazwischen in dem neuen Diagramm automatisch angezeigt.  
  
##  <a name="Details"></a> Beschreiben von Anwendungsfällen  
 Ein Anwendungsfall stellt Folgendes dar:  
  
-   Ein Ziel eines Akteurs bei Verwendung des Systems, z. B. **Gericht kaufen**; und  
  
-   Eine oder mehrere *Szenarien*, d. h. Sequenzen von Schritten ausgeführt, in die Erreichung eines Ziels, z. B.: {**Gericht bestellen, bezahlen, Gericht liefern**}. Zusätzlich zu Erfolgsszenarios möglicherweise mehrere Ausnahme oder Fehlerszenarien beschrieben, wie z. B. **Kreditkarte abgelehnt**.  
  
 Ein Anwendungsfall kann in verschiedenen Ausführlichkeitsgraden beschrieben werden. In einer frühen Phase des Entwurfs ist der Name im Anwendungsfalldiagramm ausreichend.  Später können ausführlichere Beschreibungen der Szenarios geschrieben werden.  
  
 In Visual Studio Ultimate können Sie einen Anwendungsfall auf verschiedene Arten beschreiben. Anwendungsfälle können einzeln oder gemeinsam verwendet werden:  
  
-   Verknüpfen Sie den Anwendungsfall mit einem oder mehreren Diagrammen im Projekt.  
  
    -   Mit einem Aktivitätsdiagramm können Sie einen komplexeren Prozess mit Schleifen, Verzweigungen und parallelen Threads erläutern. Darin kann auch der Fluss der Daten zwischen Teilen des Prozesses angezeigt werden. Weitere Informationen finden Sie unter [UML-Aktivitätsdiagramme: Richtlinien](../modeling/uml-activity-diagrams-guidelines.md).  
  
    -   Mit einem Sequenzdiagramm können Sie eine komplexe Reihe von Interaktionen zwischen verschiedenen Akteuren erklären. Außerdem können Sie diese Art von Diagramm verwenden, um darzustellen, was im System als Reaktion auf die einzelnen Anwendungsfälle ausgeführt wird. Weitere Informationen finden Sie unter [UML-Sequenzdiagramme: Richtlinien](../modeling/uml-sequence-diagrams-guidelines.md).  
  
-   Verknüpfen Sie den Anwendungsfall mit einer OneNote-Seite, einem OneNote-Abschnitt oder einem OneNote-Absatz, auf der bzw. in dem der Anwendungsfall ausführlich beschrieben wird.  
  
-   Verknüpfen Sie den Anwendungsfall mit einem Word-Dokument, in dem Sie Text, Screenshots usw. verwenden, um die Szenarios des Anwendungsfalls zu beschreiben. Weitere Informationen finden Sie unter [Modellieren von benutzeranforderungen](../modeling/model-user-requirements.md).  
  
#### <a name="to-link-a-use-case-to-a-diagram-or-file-in-the-same-solution"></a>So verknüpfen Sie einen Anwendungsfall mit einem Diagramm oder einer Datei in der gleichen Projektmappe  
  
1.  Zeichnen Sie ein Diagramm, um ein Szenario des Anwendungsfalls zu veranschaulichen, z. B. ein Sequenz- oder Aktivitätsdiagramm.  
  
2.  Wechseln Sie zurück zum Anwendungsfalldiagramm.  
  
3.  Ziehen Sie das Diagramm oder die Datei vom Projektmappen-Explorer auf einen leeren Teil des Anwendungsfalldiagramms.  
  
4.  Verbinden Sie das Artefakt mit die Verwendung von Groß-/Kleinschreibung mit einem **Abhängigkeit**.  
  
#### <a name="to-link-to-a-solution-file-such-as-a-word-document-or-powerpoint-presentation"></a>So erstellen Sie einen Link zu einer Projektmappendatei (z. B. ein Word-Dokument oder eine PowerPoint-Präsentation)  
  
1.  Erstellen Sie ein Dokument, das Text, Screenshots usw. zum Beschreiben des Szenarios des Anwendungsfalls enthält.  
  
2.  Fügen Sie das Dokument der Projektmappe hinzu.  
  
    1.  Verschieben Sie das Word-Dokument in den gleichen Windows-Ordner wie die Projektmappe.  
  
    2.  Im Projektmappen-Explorer mit der Maustaste der Projektmappe, zeigen Sie auf **hinzufügen**, und klicken Sie dann auf **vorhandenes Element**.  
  
    3.  Navigieren Sie zum Word-Dokument, und klicken Sie auf **hinzufügen**.  
  
         Das Word-Dokument wird im Projektmappen-Explorer in einem Projektmappenordner angezeigt.  
  
3.  Ziehen Sie das Word-Dokument aus dem Projektmappen-Explorer auf einen leeren Teil des Anwendungsfalldiagramms.  
  
     Ein neues Artefakt wird angezeigt.  
  
4.  Verbinden Sie das Artefakt mit die Verwendung von Groß-/Kleinschreibung mit einem **Abhängigkeit**.  
  
#### <a name="to-link-to-a-shared-document-onenote-element-or-web-page"></a>So erstellen Sie einen Link zu einem freigegebenen Dokument, einem OneNote-Element oder einer Webseite  
  
1.  Sie benötigen die URL des freigegebenen Elements. Dies kann sein, z. B. eine beginnender Netzwerkdateipfad "\\\\", oder die Seite einer Webseite oder Sharepoint-URL "http://" beginnende oder ein Link zu einem OneNote-Abschnitt oder-Absatz "Onenote:".  
  
2.  Klicken Sie in der Toolbox auf **Artefakt** , und klicken Sie dann in das Anwendungsfalldiagramm.  
  
3.  Das neue Artefakt aus, und geben oder fügen Sie die URL in die **Hyperlink** Eigenschaft.  
  
> [!NOTE]
>  Sie können auf ein Artefakt doppelklicken, um das Diagramm oder das Dokument zu öffnen, mit dem es verknüpft ist.  
  
### <a name="linking-use-cases-to-work-items"></a>Verknüpfen von Anwendungsfällen mit Arbeitsaufgaben  
 Wenn Ihr Projekt verwendet [!INCLUDE[vstsTfsRosarioLong](../includes/vststfsrosariolong-md.md)] und [!INCLUDE[esprtfc](../includes/esprtfc-md.md)], Sie können jeden Anwendungsfall mit einer Arbeitsaufgabe in verknüpfen [!INCLUDE[esprfound](../includes/esprfound-md.md)]. Wie Sie diesen Links finden Sie unter [Verknüpfen von Modellelementen und Arbeitsaufgaben](../modeling/link-model-elements-and-work-items.md).  
  
 Sie haben dann folgende Möglichkeiten:  
  
-   Beschreiben Sie den Anwendungsfall in der verknüpften Arbeitsaufgabe. Wenn das Projekt die Visual Studio-Prozessvorlage „Formal“ verwendet, können Sie einen Link zu einer Anwendungsfall-Arbeitsaufgabe einrichten. Dieser Arbeitsaufgabentyp stellt Felder zum Beschreiben der Ziele und Szenarios des Anwendungsfalls bereit.  
  
-   Verknüpfen Sie Testfälle mit dem Anwendungsfall, damit Sie Berichte dazu abrufen können, in welchem Umfang der entwickelte Code den Anwendungsfall implementiert.  
  
-   Verknüpfen Sie Aufgaben mit dem Anwendungsfall, damit Sie den Status der Entwicklungsarbeit nachverfolgen können.  
  
##  <a name="Structuring"></a> Strukturieren von Anwendungsfällen  
 Sie sollten versuchen, das Verhalten des Systems nur mit einigen wenigen Hauptanwendungsfällen zu beschreiben. Für jeden großen Anwendungsfall ist ein Hauptziel definiert, für dessen Erreichung ein Akteur zuständig ist, z. B. das Kaufen eines Produkts oder aus Anbietersicht das Anbieten von Produkten zum Verkauf.  
  
 Wenn Sie diese Ziele verdeutlicht haben, können Sie weitere Details dazu angeben, wie die einzelnen Ziele erreicht werden und welche Variationen es bei den grundlegenden Zielen gibt.  
  
 Vermeiden Sie es, die Anwendungsfälle zu stark zu unterteilen. Bei Anwendungsfällen geht es um die Benutzererfahrung mit dem System, nicht so sehr um die internen Details. Außerdem ist es meist produktiver, nur erste Arbeitsversionen des Codes zu erstellen, anstatt zu viel Zeit mit dem ausführlichen Strukturieren der Anwendungsfälle zu verbringen.  
  
 Sie können in einem Anwendungsfalldiagramm die Beziehungen zwischen den Hauptanwendungsfällen und ausführlicheren Anwendungsfällen zusammenfassen. Dies wird in den folgenden Abschnitten beschrieben:  
  
-   [Zeigt die Details eines Anwendungsfalls mit Include](#Include)  
  
-   [Gemeinsames Nutzen von Zielen per Generalisierung](#Inheritance)  
  
-   [Abtrennen von Varianten mit "Erweitern"](#Extend)  
  
###  <a name="Include"></a> Zeigt die Details eines Anwendungsfalls mit Include  
 Verwenden Sie eine **Include** Beziehung zu zeigen, dass ein Anwendungsfall beschreibt einige der Details eines anderen. In der Abbildung **zum Bestellen einer Mahlzeit** enthält **Zahlen**, **wählen Sie im Menü**, und **Menüpunkt wählen**. Jeder der enthaltenen ausführlicheren Anwendungsfälle ist ein Schritt, den der Akteur oder die Akteure ggf. ausführen müssen, um das Gesamtziel des einschließenden Anwendungsfalls zu erreichen. Der Pfeil sollte auf den ausführlicheren eingeschlossenen Anwendungsfall zeigen.  
  
> [!CAUTION]
>  Sie sollten keine Schleifen aus Beziehungen vom Typ „Einschließen“ erstellen, die dazu führen, dass ein Anwendungsfall sich selbst enthält. Schleifen können zu Fehlern führen.  
  
 Sie können eingeschlossene Anwendungsfälle freigeben. Im Beispiel die **zum Bestellen einer Mahlzeit** und **Bewertungen abonnieren** Anwendungsfälle bieten **Zahlen**.  
  
 ![Anwendungsfälle mit zerlegt](../modeling/media/uml-ucguideinclude.png "UML_UCGuideInclude")  
  
 Das Ziel und die Szenarios eines eingeschlossenen Anwendungsfalls sollten auch unabhängig voneinander Sinn ergeben, damit diese in Anwendungsfälle einbezogen werden können, die später entworfen werden.  
  
 Das Unterteilen von Anwendungsfällen in einschließende und eingeschlossene Teile ist nützlich, um die folgenden Ziele zu erreichen:  
  
-   Strukturieren der Anwendungsfallbeschreibungen in verschiedene Detailebenen  
  
-   Vermeiden der Wiederholung von freigegebenen Szenarios in verschiedenen Anwendungsfällen  
  
####  <a name="Steps"></a> Festlegen der Reihenfolge der ausführlichen Schritte  
 Das Anwendungsfalldiagramm sagt weder etwas über die Reihenfolge aus, in der die ausführlicheren Schritte ausgeführt werden müssen, noch darüber, ob jeder Schritt immer erforderlich ist.  
  
 Um die Reihenfolge der Schritte verdeutlichen möchten, können Sie eine **Artefakt** , fügen Sie ein separates Dokument an den einschließenden Anwendungsfall. Im folgenden Beispiel ist ein Aktivitätsdiagramm an den Anwendungsfall Gericht bestellen angefügt. Alternativ dazu können Sie ein Textdokument verwenden, das eine Liste von Schritten oder eine Sequenz von Screenshots enthält. Weitere Informationen finden Sie unter [Ausführliches Beschreiben von Anwendungsfällen](#Details).  
  
 Beachten Sie beim Verwenden eines Aktivitätsdiagramms die folgenden Namenskonventionen:  
  
-   Der Name der gesamten Aktivität entspricht dem Namen des einschließenden Anwendungsfalls.  
  
-   Die Aktionen im Aktivitätsdiagramm haben die gleichen Namen wie die eingeschlossenen Anwendungsfälle.  
  
 Weitere Informationen finden Sie unter [UML-Aktivitätsdiagramme: Richtlinien](../modeling/uml-activity-diagrams-guidelines.md).  
  
 ![Anwendungsfallschritte in verknüpftem Aktivitätsdiagramm](../modeling/media/uml-ucguidesteps.png "UML_UCGuideSteps")  
  
###  <a name="Inheritance"></a> Gemeinsames Nutzen von Zielen per Generalisierung  
 Verwenden Sie eine generalisierungsbeziehung, um anzugeben, dass eine *spezielle* Anwendungsfall ist eine bestimmte Weise zum Erreichen der Ziele, die von einem anderen ausgedrückt *allgemeine* Groß-/Kleinschreibung aufweisen. Die geöffnete Pfeilspitze sollte auf den allgemeineren Anwendungsfall zeigen.  
  
 ![Anwendungsfälle mit generalisierungsbeziehung](../modeling/media/uml-ucguidegeneral.png "UML_UCGuideGeneral")  
  
 Z. B. **Zahlen** generalisiert **bezahlen mit Kreditkarte** und **bar bezahlen**.  
  
> [!CAUTION]
>  Sie sollten keine Schleifen aus Generalisierungsbeziehungen erstellen, die dazu führen, dass ein Akteur sich selbst generalisiert. Schleifen können zu Fehlern führen.  
  
 Mithilfe von spezialisierten Anwendungsfällen können Sie andere Methoden anzeigen, mit denen das System das gleiche Ziel erreichen kann.  
  
 Die spezialisierten Anwendungsfälle sollen die Ziele und Akteure des allgemeinen Anwendungsfalls erben. Der allgemeine Anwendungsfall muss keine eigenen Szenarios haben. Seine Spezialisierungen beschreiben verschiedene Methoden zur Erreichung der Ziele.  
  
##### <a name="to-refactor-common-goals-from-two-or-more-use-cases"></a>So gestalten Sie allgemeine Ziele von zwei oder mehr Anwendungsfällen um  
  
1.  Erstellen und benennen Sie den neuen allgemeinen Anwendungsfall.  
  
2.  Erstellen Sie eine **Generalisierung** Beziehung mit der große Pfeil auf den neuen allgemeinen Anwendungsfall zeigt.  
  
    1.  Klicken Sie auf **Generalisierung** in der Toolbox.  
  
    2.  Klicken Sie auf einen spezialisierten Anwendungsfall (**bezahlen mit Kreditkarte** im Beispiel).  
  
    3.  Klicken Sie auf den allgemeinen Anwendungsfall (**Zahlen** im Beispiel).  
  
3.  Wenn Sie die Ziele für die spezialisierten Anwendungsfälle beschrieben haben, verschieben Sie die gemeinsamen Teile in die Beschreibung des allgemeinen Anwendungsfalls.  
  
4.  Akteure, die von den spezialisierten Anwendungsfällen gemeinsam genutzt werden, können in den allgemeinen Anwendungsfall verschoben werden.  
  
###  <a name="Extend"></a> Abtrennen von Varianten mit "Erweitern"  
 Verwenden Sie einen Link vom Typ „Erweitern“, um anzugeben, dass ein Anwendungsfall einem anderen Anwendungsfall unter bestimmten Umständen Funktionen hinzufügen kann. Der Pfeil sollte auf den erweiterten Hauptanwendungsfall zeigen.  
  
 ![Ein Anwendungsfall, die einen anderen erweitert](../modeling/media/uml-ucguideextend.png "UML_UCGuideExtend")  
  
> [!CAUTION]
>  Sie sollten keine Schleifen aus Erweiterungsbeziehungen erstellen, die dazu führen, dass ein Akteur sich selbst generalisiert. Schleifen können zu Fehlern führen.  
  
 Z. B. die **Anmeldung** Anwendungsfall einer typischen Website zählen **Registrieren neuer Benutzer** -nur wenn der Benutzer verfügt jedoch nicht bereits ein Konto.  
  
##### <a name="to-separate-a-use-case-into-main-and-extending-parts"></a>So unterteilen Sie einen Anwendungsfall in Hauptbestandteile und Erweiterungsteile  
  
1.  Erstellen und benennen Sie den neuen erweiterten Anwendungsfall.  
  
2.  Erstellen Sie eine **erweitern** Beziehung mit der Pfeil auf den erweiterten Anwendungsfall zeigt.  
  
    1.  Klicken Sie auf **erweitern** in der Toolbox.  
  
    2.  Klicken Sie auf den erweiternden Anwendungsfall (**Registrieren neuer Benutzer** im Beispiel).  
  
    3.  Klicken Sie auf den erweiterten Anwendungsfall (**Anmeldung** im Beispiel).  
  
        > [!NOTE]
        >  Vermeiden Sie es, im Diagramm eine Schleife von Erweiterungsbeziehungen zu erstellen. Ein Anwendungsfall darf keine Erweiterung von sich selbst darstellen.  
  
3.  Verschieben Sie die relevanten Schritte in das Szenario der Erweiterung, falls Sie für den erweiterten Anwendungsfall bereits Szenarios erstellt haben.  
  
4.  Die Beschreibung der Erweiterung (**Registrieren neuer Benutzer** im Beispiel) sollte Details an, wo in den Szenarios des Hauptanwendungsfalls auftritt, und unter welchen Umständen einschließen. Sehen Sie diesen Schritt als Änderung der Beschreibung des Hauptanwendungsfalls an.  
  
 Der Erweiterungsanwendungsfall stellt Szenarioschritte dar, die andernfalls Teil des Hauptanwendungsfall-Szenarios wären. Das Szenario und das Ziel der Erweiterung werden immer im Kontext des Hauptanwendungsfalls gelesen und müssen deshalb keinen direkten unabhängigen Nutzen aufweisen.  
  
 Das Abtrennen von Erweiterungen kann nützlich sein, um die folgenden Situationen zu beschreiben:  
  
-   Es sind zusätzliche Akteure vorhanden, die nur am Erweiterungsanwendungsfall beteiligt sind. Beispielsweise muss ein Administrator die Registrierung eines Kunden auf der Website genehmigen.  
  
-   Ein separates Subsystem verarbeitet den Erweiterungsanwendungsfall.  
  
-   Diese Erweiterung ist nur in bestimmten Versionen des Systems verfügbar. Sie können jede Version im Anwendungsfalldiagramm als separates Subsystem anzeigen.  
  
##  <a name="Subsystems"></a> Verwenden von Subsystembegrenzungen  
 Verwenden Sie eine Subsystembegrenzung, um anzugeben, welche Anwendungsfälle innerhalb des Bereichs des Systems liegen.  
  
#### <a name="to-draw-a-subsystem-boundary"></a>So zeichnen Sie eine Subsystembegrenzung  
  
1.  Klicken Sie in der Toolbox auf **Subsystem**, klicken Sie dann auf das Diagramm.  
  
     Ein Subsystem wird im Diagramm angezeigt.  
  
2.  Ziehen Sie die Ecken des Subsystems, um seine Größe anzupassen.  
  
3.  Ziehen Sie vorhandene Anwendungsfälle in das oder aus dem Subsystem, um seinen Inhalt anzupassen.  
  
 \- oder –  
  
 Klicken Sie zum Erstellen eines neuen Anwendungsfall direkt in einem Subsystem **Anwendungsfall** klicken Sie dann in der Toolbox in das Subsystem.  
  
> [!NOTE]
>  Die **Themen** Eigenschaft eines Anwendungsfalls gibt an, welchem Subsystem dieser enthalten ist.  
  
### <a name="use-cases-outside-the-system-scope"></a>Anwendungsfälle außerhalb des Systembereichs  
 Es ist häufig nützlich, Anwendungsfälle in das Diagramm einzubeziehen, die Teil des Geschäftsablaufs sind, aber nicht mit dem in der Entwicklung befindlichen System verarbeitet werden. Auf diese Weise können Entwickler den Kontext ihrer Arbeit besser verstehen. „Gericht liefern“ kann z. B. als Anwendungsfall mit den Akteuren Restaurant und Kunde angezeigt werden, jedoch außerhalb der Verantwortung der Website für die Essensbestellung.  
  
### <a name="multiple-subsystems"></a>Mehrere Subsysteme  
 Sie können mehrere Subsystembegrenzungen erstellen, um anzuzeigen, wie verschiedene Anwendungsfälle von unterschiedlichen Komponenten des Systems verarbeitet werden. Z. B. **"Restaurantbewertung hinzufügen"** kann auf einer separaten Forum-Website behandelt werden. Denken Sie daran, dass es in einem Anwendungsfalldiagramm um die Dinge gehen sollte, die für die Benutzer sichtbar sind. Wenn Sie die interne Arbeitsaufteilung im System beschreiben möchten, können Sie die Verwendung eines Komponentendiagramms in Erwägung ziehen.  
  
### <a name="system-versions"></a>Systemversionen  
 Sie können verschiedene Subsystembegrenzungen verwenden, um unterschiedliche Versionen des Systems darzustellen. Der Anwendungsfall „Bezahlen“ kann z. B. in Version 2 der Website enthalten sein, aber nicht in Version 1. Dies impliziert, dass das System Kunden beim Aufgeben ihrer Bestellungen unterstützt. Die Bezahlung erfolgt jedoch direkt an das Restaurant.  
  
 Verwendung **Abhängigkeit** Beziehungen verknüpfen Subsysteme, die verschiedene Versionen oder Varianten darstellt.  
  
 ![Subsysteme weisen unterschiedliche Versionen eines Systems](../modeling/media/uml-ucguidesystem.png "UML_UCGuideSystem")  
  
## <a name="see-also"></a>Siehe auch  
 [Modellieren von benutzeranforderungen](../modeling/model-user-requirements.md)   
 [UML-Sequenzdiagramme: Richtlinien](../modeling/uml-sequence-diagrams-guidelines.md)   
 [Bearbeiten von UML-Modellen und-Diagrammen](../modeling/edit-uml-models-and-diagrams.md)   
 [UML-Anwendungsfalldiagramme: Referenz](../modeling/uml-use-case-diagrams-reference.md)   
 [UML-Klassendiagramme: Referenz](../modeling/uml-class-diagrams-reference.md)   
 [UML-Komponentendiagramme: Referenz](../modeling/uml-component-diagrams-reference.md)   
 [UML-Aktivitätsdiagramme: Richtlinien](../modeling/uml-activity-diagrams-guidelines.md)   
 [Video: Organisieren von Funktionen in Anwendungsfällen](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-2-Organizing-Features-Into-Use-Cases/)



