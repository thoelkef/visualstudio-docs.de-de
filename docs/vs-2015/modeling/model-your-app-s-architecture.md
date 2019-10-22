---
title: Modellieren der APP&#39;-Architektur | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML, modeling architecture
ms.assetid: aedce746-9df5-49e1-9662-67eb1b83d313
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 41dbb7b996c32af10010694935cbd3660b462f73
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72609635"
---
# <a name="model-your-app39s-architecture"></a>Modellieren der APP&#39;-Architektur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Um sicherzustellen, dass das Softwaresystem oder die Anwendung die Anforderungen der Benutzer erfüllt, können Sie Modelle in Visual Studio als Teil ihrer Beschreibung der Gesamtstruktur und des Verhaltens des Software Systems oder der Anwendung erstellen. Mit Modellen können Sie auch Muster beschreiben, die im gesamten Entwurf verwendet werden. Mithilfe dieser Modelle können Sie die vorhandene Architektur verstehen, Änderungen erörtern und Ihre Absichten eindeutig vermitteln.

 Welche Versionen von Visual Studio dieses Features unterstützen, erfahren Sie unter [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Ein Modell soll die Mehrdeutigkeiten in Beschreibungen in natürlicher Sprache reduzieren und Ihnen und Ihren Kollegen helfen, den Entwurf visuell darzustellen sowie alternative Entwürfe zu erörtern. Ein Modell sollte zusammen mit anderen Dokumenten oder Diskussionen verwendet werden. Ein Modell an sich stellt keine vollständige Spezifikation der Architektur dar.

> [!NOTE]
> In diesem gesamten Thema wird als „System“ die Software bezeichnet, die Sie entwickeln. Dabei kann es sich um eine umfangreiche Sammlung vieler Software- und Hardwarekomponenten, eine einzelne Anwendung oder einen Teil einer Anwendung handeln.

 Die Architektur eines Systems kann in zwei Bereiche unterteilt werden:

- Allgemeiner [Entwurf](#Structure). Dieser Begriff beschreibt die Hauptkomponenten und ihre Interaktion zum Erfüllen der einzelnen Anforderungen. Wenn es sich um ein umfangreiches System handelt, kann jede Komponente über einen eigenen allgemeinen Entwurf verfügen, der darstellt, wie er aus kleineren Komponenten zusammengesetzt ist.

- [Entwurfsmuster](#Patterns) und Konventionen, die in den Entwürfen der Komponenten verwendet werden. Ein Muster beschreibt eine bestimmte Methode zum Erreichen eines Programmierziels. Wenn das Team während des gesamten Entwurfs die gleichen Entwurfsmuster verwendet, lässt sich der Aufwand zum Durchführen von Änderungen und Entwickeln neuer Software verringern.

## <a name="Structure"></a>Allgemeiner Entwurf
 Ein allgemeiner Entwurf beschreibt die Hauptkomponenten des Systems und ihre Interaktion zum Erreichen der Ziele des Entwurfs. Das Entwickeln des allgemeinen Entwurfs umfasst die Aktivitäten in der folgenden Liste, wenn auch nicht unbedingt in einer bestimmten Reihenfolge.

 Wenn Sie vorhandenen Code aktualisieren, sollten Sie zunächst die Hauptkomponenten beschreiben. Stellen Sie sicher, dass Sie ggf. vorhandene Änderungen der Benutzeranforderungen verstehen, und fügen Sie dann Interaktionen zwischen den Komponenten hinzu, oder ändern Sie diese. Wenn Sie ein neues System entwickeln, ermitteln Sie zunächst die Hauptmerkmale der Benutzeranforderungen. Sie können dann Sequenzen von Interaktionen für die Hauptanwendungsfälle untersuchen und anschließend die Sequenzen in einem Komponentenentwurf konsolidieren.

 In jedem Fall ist es hilfreich, die verschiedenen Aktivitäten parallel zu entwickeln und Code und Tests bereits in einer frühen Phase zu entwerfen. Versuchen Sie nicht, einen dieser Aspekte abzuschließen, bevor Sie mit einem anderen Aspekt beginnen. In der Regel ändern sich sowohl die Anforderungen als auch Ihre Auffassung von dem besten Verfahren zum Entwerfen des Systems, während Sie den Code schreiben und testen. Daher sollten Sie zunächst die Hauptmerkmale der Anforderungen und des Entwurfs ermitteln und codieren. Behandeln Sie die Details in späteren Iterationen des Projekts.

- Grundlegendes zu [den Anforderungen](#Requirements). Der Ausgangspunkt jedes Entwurfs sind fundierte Kenntnisse der Benutzeranforderungen.

- [Architekturmuster](#BigDecisions). Die Kerntechnologien und Architekturelemente des Systems, die Sie ausgewählt haben.

- [Komponenten und ihre Schnittstellen](#Components). Sie können Komponentendiagramme zeichnen, um die Hauptbestandteile des Systems darzustellen, und die Schnittstellen darstellen, über die sie miteinander interagieren. Die Schnittstellen jeder Komponente umfassen alle Meldungen, die Sie in den Sequenzdiagrammen identifiziert haben.

- [Interaktionen zwischen Komponenten](#Interactions). Sie können für jeden Anwendungsfall, jedes Ereignis oder jede eingehende Meldung ein Sequenzdiagramm zeichnen, das darstellt, wie die Hauptkomponenten des Systems interagieren, um die erforderliche Reaktion zu erzielen.

- [Datenmodell der Komponenten und Schnittstellen](#Data). Sie können Klassendiagramme zeichnen, um die Informationen zu beschreiben, die zwischen Komponenten übergeben und in den Komponenten gespeichert werden.

## <a name="Requirements"></a>Grundlegendes zu den Anforderungen
 Der allgemeine Entwurf für eine vollständige Anwendung wird am effektivsten zusammen mit einem Anforderungsmodell oder einer anderen Beschreibung der Benutzeranforderungen entwickelt. Weitere Informationen zu Anforderungs Modellen finden Sie unter [Modell Benutzeranforderungen](../modeling/model-user-requirements.md).

 Wenn das System, das Sie entwickeln, eine Komponente in einem größeren System ist, können Ihre Anforderungen vollständig oder teilweise in programmgesteuerte Schnittstellen aufgenommen werden.

 Das Anforderungsmodell stellt die folgenden wesentlichen Informationen bereit:

- Bereitgestellte Schnittstellen. Eine bereitgestellte Schnittstelle führt die Dienste oder Vorgänge auf, die das System oder die Komponente für die Benutzer bereitstellen muss, unabhängig davon, ob es sich um menschliche Benutzer oder andere Softwarekomponenten handelt.

- Erforderliche Schnittstellen. Eine erforderliche Schnittstelle führt die Dienste oder Vorgänge auf, die das System oder die Komponente verwenden kann. In einigen Fällen können Sie alle diese Dienste als Teil des eigenen Systems entwerfen. In anderen Fällen, insbesondere wenn Sie eine Komponente entwerfen, die mit anderen Komponenten in vielen Konfigurationen kombiniert werden kann, wird die erforderliche Schnittstelle auf Grundlage externer Aspekte festgelegt.

- Servicequalitätsanforderungen. Leistung, Sicherheit, Stabilität und andere Ziele und Einschränkungen, die das System erfüllen muss.

  Das Anforderungsmodell wird aus der Perspektive der Benutzer des Systems geschrieben, bei denen es sich um Personen oder andere Softwarekomponenten handeln kann. Die internen Funktionen des Systems sind ihnen nicht bekannt. Im Gegensatz dazu soll ein Architekturmodell die internen Funktionen beschreiben und darstellen, wie sie die Anforderungen der Benutzer erfüllen.

  Die Anforderungen und Architekturmodelle sollten getrennt bleiben, um das Erörtern der Anforderungen mit den Benutzern zu erleichtern. Dies erleichtert es außerdem, den Entwurf umzugestalten und alternative Architekturen zu erwägen, während die Anforderungen unverändert beibehalten werden.

  Sie können die Anforderungen und Architekturmodelle auf zweierlei Weise trennen:

- Speichern Sie sie in der gleichen Projektmappe, jedoch in unterschiedlichen Projekten. Sie werden im UML-Modell-Explorer als gesonderte Modelle angezeigt. Verschiedene Teammitglieder können gleichzeitig an den Modellen arbeiten. Es können eingeschränkte Arten von Ablaufverfolgung zwischen den Modellen erstellt werden.

- Platzieren Sie sie im gleichen UML-Modell, jedoch in unterschiedlichen Paketen. Dies vereinfacht die Ablaufverfolgung von Abhängigkeiten zwischen den Modellen, verhindert jedoch, dass mehrere Personen gleichzeitig an dem Modell arbeiten. Außerdem dauert es länger, ein sehr umfangreiches Modell in Visual Studio zu laden. Diese Vorgehensweise eignet sich daher weniger für umfangreiche Projekte.

  Der Umfang an Informationen, die Sie in ein Anforderungsmodell oder ein Architekturmodell aufnehmen sollten, hängt vom Umfang des Projekts sowie der Größe des Teams und der räumlichen Verteilung seiner Mitglieder ab. Ein kleines Team in einem kurzen Projekt braucht eventuell lediglich ein Klassendiagramm der Geschäftskonzepte und einige Entwurfsmuster zu skizzieren; ein großes Projekt, das über mehr als einen Bereich ausgeliefert wurde, wird deutlich mehr Details erfordern.

## <a name="BigDecisions"></a>Architekturmuster
 Sie müssen zu einem frühen Zeitpunkt der Entwicklung Optionen für die wichtigsten Technologien und Elemente auswählen, von denen der Entwurf abhängt. Diese Optionen müssen in den folgenden Bereichen ausgewählt werden:

- Optionen für die Basistechnologie, z. B. Auswahl einer Datenbank oder eines Dateisystems, Auswahl einer Netzwerkanwendung oder eines Webclients usw.

- Frameworkoptionen, z. B. Auswahl von Windows Workflow Foundation oder ADO.NET Entity Framework.

- Optionen für Integrationsmethoden, z. B. Auswahl eines Enterprise Service Bus oder eines Punkt-zu-Punkt-Channels.

  Diese Optionen werden häufig von Servicequalitätsanforderungen bestimmt, z. B. Größe und Flexibilität, und die Auswahl kann getroffen werden, bevor die Anforderungsdetails bekannt sind. In einem umfangreichen System besteht eine enge Wechselbeziehung zwischen der Konfiguration von Hardware und Software.

  Die von Ihnen ausgewählten Optionen wirken sich darauf aus, wie Sie das Architekturmodell verwenden und interpretieren. Beispielsweise können in einem System mit einer Datenbank Zuordnungen in einem Klassendiagramm Beziehungen oder Fremdschlüssel in der Datenbank darstellen, während in einem auf XML-Dateien basierenden System Zuordnungen Querverweise angeben können, die XPath verwenden. In einem verteilten System können Meldungen in einem Sequenzdiagramm Meldungen in einer Verbindung darstellen, und in einer unabhängigen Anwendung können sie Funktionsaufrufe darstellen.

## <a name="Components"></a>Komponenten und ihre Schnittstellen
 Die wichtigsten Empfehlungen dieses Abschnitts lauten wie folgt:

- Erstellen Sie Komponentendiagramme, um die Hauptbestandteile des Systems darzustellen.

- Zeichnen Sie Abhängigkeiten zwischen den Komponenten oder ihren Schnittstellen, um die Struktur des Systems darzustellen.

- Verwenden Sie Schnittstellen für die Komponenten, um die Dienste darzustellen, die jede Komponente bereitstellt oder erfordert.

- In einem umfangreichen Entwurf können Sie eigene Diagramme zeichnen, um jede Komponente in kleinere Teile zu zerlegen.

  Diese Punkte werden im Rest dieses Abschnitts ausführlicher erläutert.

### <a name="components"></a>Komponenten
 Die zentralen Ansichten eines Architekturmodells sind die Komponentendiagramme, die die Hauptbestandteile des Systems und ihre gegenseitigen Abhängigkeiten darstellen. Weitere Informationen zu Komponenten Diagrammen finden Sie unter [UML-Komponenten Diagramme: Referenz](../modeling/uml-component-diagrams-reference.md).

 ![UML-Komponenten Diagramm, das Teile anzeigt](../modeling/media/uml-barecomponent.png "UML_BareComponent")

 Ein typisches Komponentendiagramm für ein umfangreiches System kann beispielsweise folgende Komponenten enthalten:

- Präsentation. Die Komponente, die Zugriff für den Benutzer bereitstellt. Sie wird in der Regel in einem Webbrowser ausgeführt.

- Webdienstkomponenten. Stellen die Verbindung zwischen Clients und Servern bereit.

- Anwendungsfallcontroller. Führen den Benutzer durch die Schritte der einzelnen Szenarien.

- Geschäftskern. Enthält Klassen, die auf Klassen im Anforderungsmodell basieren, implementiert die wichtigsten Vorgänge und legt Geschäftseinschränkungen fest.

- Datenbank. Speichert die Geschäftsobjekte.

- Protokollierungs- und Fehlerbehandlungskomponenten.

### <a name="dependencies-between-components"></a>Abhängigkeiten zwischen Komponenten
 Zusätzlich zu den Komponenten selbst können Sie die Abhängigkeiten zwischen ihnen darstellen. Ein Abhängigkeitspfeil zwischen zwei Komponenten gibt an, dass sich Änderungen im Entwurf auf den Entwurf der anderen Komponente auswirken können. Dies ist normalerweise der Fall, wenn eine Komponente die Dienste oder Funktionen verwendet, die von der anderen Komponente direkt oder indirekt bereitgestellt werden.

 Eine gut strukturierte Architektur weist eine eindeutige Anordnung von Abhängigkeiten auf, in der die folgenden Bedingungen erfüllt sind:

- Das Abhängigkeitsdiagramm enthält keine Schleifen.

- Die Komponenten können auf Ebenen angeordnet werden, wobei es sich bei jeder Abhängigkeit um die Abhängigkeit zwischen einer Komponente auf einer Ebene und einer Komponente auf der nächsten Ebene handelt. Alle Abhängigkeiten zwischen zwei Ebenen weisen die gleiche Richtung auf.

  Sie können Abhängigkeiten direkt zwischen Komponenten darstellen oder Abhängigkeiten zwischen erforderlichen und bereitgestellten Schnittstellen darstellen, die an die Komponenten angefügt sind. Mithilfe von Schnittstellen können Sie definieren, welche Vorgänge in den einzelnen Abhängigkeiten verwendet werden. In der Regel werden Abhängigkeiten zwischen Komponenten beim ersten Zeichnen der Diagramme dargestellt und dann durch Abhängigkeiten zwischen Schnittstellen ersetzt, wenn weitere Informationen hinzugefügt werden. Beide Versionen sind ordnungsgemäße Beschreibungen der Software, jedoch stellt die Version mit Schnittstellen mehr Informationen als die frühere Version bereit.

  Das Verwalten von Abhängigkeiten ist für die Erstellung von verwaltbarer Software von größter Bedeutung. Die Komponentendiagramme sollten alle Abhängigkeiten im Code wiedergeben. Wenn der Code bereits vorhanden ist, stellen Sie sicher, dass in den Diagrammen alle Abhängigkeiten dargestellt werden. Wenn der Code entwickelt wird, stellen Sie sicher, dass er keine Abhängigkeiten enthält, die im Komponentendiagramm nicht vorgesehen sind. Sie können Ebenendiagramme generieren, um Abhängigkeiten im Code leichter zu erkennen. Sie können den Code anhand von Ebenendiagrammen überprüfen, um sicherzustellen, dass die geplanten Abhängigkeitseinschränkungen erfüllt werden. Weitere Informationen finden Sie unter [ebenendiagramme: Referenz](../modeling/layer-diagrams-reference.md).

### <a name="interfaces"></a>Schnittstellen
 Durch das Einfügen von Schnittstellen für die Komponenten können Sie die Hauptgruppen von Vorgängen trennen und benennen, die von jeder Komponente bereitgestellt werden. Beispielsweise können Komponenten in einem webbasierten Vertriebssystem eine Schnittstelle aufweisen, über die Kunden Waren kaufen können, eine Schnittstelle, über die Lieferanten ihre Kataloge aktualisieren, und eine dritte Schnittstelle, über die das System verwaltet wird.

 Eine Komponente kann über eine beliebige Anzahl von bereitgestellten und erforderlichen Schnittstellen verfügen. Bereitgestellte Schnittstellen stellen Dienste dar, die von der Komponente für die Verwendung durch andere Komponenten bereitgestellt werden. Erforderliche Schnittstellen stellen Dienste dar, die von der Komponente in anderen Komponenten verwendet wird.

 Wenn Sie sowohl bereitgestellte als auch erforderliche Schnittstellen definieren, können Sie die Komponente deutlicher vom Rest des Entwurfs trennen, sodass Sie die folgenden Verfahren verwenden können:

- Fügen Sie die Komponente in eine Testumgebung ein, in der die umgebenden Komponenten von der Testumgebung simuliert werden.

- Entwickeln Sie die Komponente unabhängig von den anderen Komponenten.

- Verwenden Sie die Komponente in anderen Kontexten erneut, indem Sie ihre Schnittstellen mit anderen Komponenten verbinden.

  Wenn Sie die Liste der Vorgänge in einer Schnittstelle definieren möchten, können Sie in einem UML-Klassendiagramm eine andere Ansicht der Schnittstelle erstellen. Suchen Sie hierzu im UML-Modell-Explorer die Schnittstelle, und ziehen Sie sie in ein Klassendiagramm. Anschließend können Sie der Schnittstelle Vorgänge hinzufügen.

  Ein Vorgang in einer UML-Schnittstelle kann jedes Verfahren darstellen, mit dem ein Verhalten einer Komponente aufgerufen werden kann. Er kann eine Webdienstanforderung, eine andere Art von Signal oder Interaktion oder einen gewöhnlichen Programmfunktionsaufruf darstellen.

  Um die hinzuzufügenden Vorgänge zu bestimmen, erstellen Sie Sequenzdiagramme, die zeigen, wie die Komponenten miteinander interagieren. Siehe [Interaktionen zwischen Komponenten](#Interactions). Jedes der Sequenzdiagramme zeigt die Interaktionen, die in einem jeweils anderen Anwendungsfall auftreten. Auf diese Weise können Sie der Liste der Vorgänge in der Schnittstelle jeder Komponente allmählich weitere Vorgänge hinzufügen, während Sie die Anwendungsfälle untersuchen.

### <a name="decomposing-a-component-into-parts"></a>Zerlegen einer Komponente in einzelne Teile
 Sie können das in den vorherigen Abschnitten beschriebene Verfahren auf jede Komponente anwenden.

 Sie können in jeder Komponente deren Unterkomponenten als Teile darstellen. Ein Teil ist eigentlich ein Attribut der übergeordneten Komponente, die wiederum eine Art von Klasse ist. Jedes Teil verfügt über einen eigenen Typ, und dieser kann eine Komponente sein. Sie können diese Komponente in ein Diagramm einfügen und ihre Teile darstellen. Weitere Informationen finden Sie unter [UML-Komponenten Diagramme: Richtlinien](../modeling/uml-component-diagrams-guidelines.md).

 Es empfiehlt sich, dieses Verfahren auf das gesamte System anzuwenden. Zeichnen Sie dieses als einzelne Komponente, und stellen Sie seine Hauptkomponenten als Teile dar. Dies erleichtert es Ihnen, die Schnittstellen des Systems mit der externen Welt eindeutig zu identifizieren.

 Wenn im Entwurf für eine Komponente eine andere Komponente verwendet wird, können Sie häufig auswählen, ob sie als Teil oder als eigene Komponente dargestellt wird, auf die Sie über eine erforderliche Schnittstelle zugreifen.

 Verwenden Sie Teile in den folgenden Situationen:

- Im Entwurf der übergeordneten Komponente muss immer der Komponententyp des Teils verwendet werden. Daher ist der Entwurf des Teils ein wesentlicher Bestandteil des Entwurfs der übergeordneten Komponente.

- Die übergeordnete Komponente ist keine reale Komponente. Beispielsweise können Sie über eine konzeptionelle Komponente mit dem Namen Darstellungsebene verfügen, die eine Auflistung von realen Komponenten darstellt, die Ansichten und Benutzerinteraktionen behandeln.

  Verwenden Sie in den folgenden Situationen gesonderte Komponenten, auf die über erforderliche Schnittstellen zugegriffen wird:

- Die Dienste erfordernde Komponente kann zur Laufzeit über ihre Schnittstellen mit anderen Komponenten, die Dienste bereitstellen, verbunden werden.

- Der Entwurf ermöglicht es, einen Anbieter problemlos durch einen anderen Anbieter zu ersetzen.

  Die Verwendung erforderlicher Schnittstellen ist normalerweise der Verwendung von Teilen vorzuziehen. Der Entwurf kann zwar mehr Zeit beanspruchen, jedoch ist das resultierende System flexibler. Es ist auch einfacher, die Komponenten getrennt zu testen. Hierdurch lässt sich die Kopplung in den Entwicklungsplänen reduzieren.

## <a name="Interactions"></a>Interaktionen zwischen Komponenten
 Die wichtigsten Empfehlungen dieses Abschnitts lauten wie folgt:

- Identifizieren Sie die Anwendungsfälle des Systems.

- Zeichnen Sie für jeden Anwendungsfall ein oder mehrere Diagramme, um darzustellen, wie die Komponenten des Systems durch die Interaktion miteinander und mit den Benutzern das erforderliche Ergebnis erzielen. Normalerweise sind diese Diagramme Sequenzdiagramme oder Aktivitätsdiagramme.

- Verwenden Sie Schnittstellen, um die von jeder Komponente empfangenen Meldungen anzugeben.

- Beschreiben Sie die Auswirkungen der Vorgänge in den Schnittstellen.

- Wiederholen Sie das Verfahren für jede Komponente, um die Interaktion ihrer Teile darzustellen.

  Beispielsweise kann in einem webbasierten Vertriebssystem das Anforderungsmodell einen Kundenkauf oder einen Anwendungsfall definieren. Sie können ein Sequenzdiagramm erstellen, um die Interaktionen des Kunden mit den Komponenten in der Darstellungsschicht und die Interaktionen der Komponenten mit der Lagerkomponente und der Buchhaltungskomponente darzustellen.

### <a name="identifying-the-initiating-events"></a>Identifizieren der auslösenden Ereignisse
 Die von den meisten Softwaresystemen ausgeführten Aktionen können bequem nach den verschiedenen Eingaben oder Ereignissen zugewiesenen Aufgaben unterteilt werden. Das auslösende Ereignis kann eines der folgenden Ereignisse sein:

- Die erste Aktion in einem Anwendungsfall. Sie kann im Anforderungsmodell als Schritt eines Anwendungsfalls oder in einem Aktivitätsdiagramm als Aktion dargestellt werden. Weitere Informationen finden Sie unter [UML-Anwendungsfall Diagramme: Richtlinien](../modeling/uml-use-case-diagrams-guidelines.md) und [UML-Aktivitätsdiagramme: Richtlinien](../modeling/uml-activity-diagrams-guidelines.md).

- Eine Meldung an einer programmgesteuerten Schnittstelle. Wenn das System, das Sie entwickeln, eine Komponente in einem größeren System ist, sollte es als Vorgang in einer der Schnittstellen der Komponente beschrieben werden. Siehe [Komponenten und ihre Schnittstellen](#Components).

- Eine bestimmte Bedingung, die vom System überwacht wird, oder ein reguläres Ereignis z. B. eine Uhrzeit.

### <a name="describe-the-computations"></a>Beschreiben der Berechnungen
 Zeichnen Sie Sequenzdiagramme, um zu zeigen, wie die Komponenten auf das auslösende Ereignis reagieren.

 Ziehen Sie eine Lebenslinie für jede Komponenteninstanz, die an einer typischen Sequenz beteiligt ist. In einigen Fällen sind möglicherweise mehrere Instanzen von jedem Typ vorhanden. Wenn Sie das Gesamtsystem als einzelne Komponente beschrieben haben, sollte für jeden Teil im Gesamtsystem eine Lebenslinie vorhanden sein.

 Weitere Informationen finden Sie unter [UML-Sequenzdiagramme: Richtlinien](../modeling/uml-sequence-diagrams-guidelines.md).

 In einigen Fällen sind auch Aktivitätsdiagramme hilfreich Wenn die Komponenten z. B. über einen fortlaufenden Datenfluss verfügen, können Sie ihn als Objektfluss beschreiben. Wenn die Komponente über einen komplexen Algorithmus verfügt, können Sie ihn als Kontrollfluss beschreiben. Machen Sie deutlich, z. B. mit Kommentaren, welche Komponente die einzelnen Aktionen ausführt. Weitere Informationen finden Sie unter [UML-Aktivitätsdiagramme: Richtlinien](../modeling/uml-activity-diagrams-guidelines.md).

### <a name="specify-the-operations"></a>Angeben von Vorgängen
 Von den einzelnen Komponenten ausgeführte Vorgänge werden als Meldungen in einem Sequenzdiagramm oder als Aktionen in einem Aktivitätsdiagramm dargestellt.

 Erfassen Sie diese Vorgänge gemeinsam für jede Komponente. Erstellen Sie bereitgestellte Schnittstellen für die Komponente, und fügen Sie den Schnittstellen die Vorgänge hinzu. In der Regel wird für jeden Typ von Client eine eigene Schnittstelle verwendet. Die Vorgänge werden am einfachsten zu den Schnittstellen im **UML-Modell-Explorer**hinzugefügt. Erfassen Sie auf die gleiche Weise die von jeder Komponente verwendeten Vorgänge aus den anderen Komponenten, und fügen Sie sie in die erforderlichen Schnittstellen ein, die an die Komponente angefügt sind.

 Es ist sinnvoll, den Aktivitäts- oder Sequenzdiagrammen Kommentare hinzuzufügen, um anzugeben, was nach jedem Vorgang erreicht wurde. Sie können auch die Auswirkung jedes Vorgangs in seine **lokale** nach Bedingungs Eigenschaft schreiben.

### <a name="Data"></a>Datenmodell der Komponenten und Schnittstellen
 Definieren Sie die Parameter und Rückgabewerte jedes Vorgangs in den Komponentenschnittstellen. Wenn die Vorgänge Aufrufe darstellen, z. B. Webdienstanforderungen, sind die Parameter die Informationen, die als Teil der Anforderung gesendet werden. Wenn mehrere Werte von einem Vorgang zurückgegeben werden, können Sie Parameter verwenden, bei denen die **Direction** -Eigenschaft auf **out**festgelegt ist.

 Jeder Parameter und Rückgabewert verfügt über einen Typ. Sie können diese Typen mit UML-Klassendiagrammen definieren. Sie müssen in diesen Diagrammen keine Implementierungsdetails darstellen. Wenn Sie z. B. Daten beschreiben, die als XML-Daten gesendet werden, können Sie mit einer Zuordnung jede Art von Querweisen zwischen XML-Knoten und mit Klassen Knoten darstellen.

 Verwenden Sie Kommentare, um Geschäftseinschränkungen der Zuordnungen und Attribute zu beschreiben. Wenn beispielsweise alle Elemente in der Bestellung eines Kunden von demselben Lieferanten geliefert werden müssen, können Sie dies mithilfe der Zuordnungen zwischen den Bestellungselementen und den Elementen im Produktkatalog sowie zwischen dem Katalogelement und dem zugehörigen Lieferanten beschreiben.

## <a name="Patterns"></a>Entwurfsmuster
 Ein Entwurfsmuster skizziert den Entwurf eines bestimmten Aspekts der Software, insbesondere eines Aspekts, der in verschiedenen Teilen des Systems vorhanden ist. Wenn Sie im gesamten Projekt eine einheitliche Vorgehensweise anwenden, können Sie den Aufwand für den Entwurf verringern, die Konsistenz der Benutzeroberfläche sicherstellen und den Aufwand für das Verstehen und Ändern des Codes reduzieren.

 Einige allgemeine Entwurfsmuster, z. B. das Beobachtermuster, sind bekannt und in vielfältigen Szenarien anwendbar. Darüber hinaus gibt es Muster, die nur auf das spezifische Projekt anwendbar sind. Beispielsweise enthält ein Webvertriebssystem mehrere Vorgänge im Code, mit denen Änderungen an einer Kundenbestellung vorgenommen werden. Um sicherzustellen dass der Zustand der Bestellung in jeder Phase korrekt angezeigt wird, müssen all diese Vorgänge einem bestimmten Protokoll zum Aktualisieren der Datenbank entsprechen.

 Das Erstellen der Softwarearchitektur umfasst das Bestimmen der Muster, die im gesamten Entwurf angewendet werden sollen. Dies ist normalerweise eine permanente Aufgabe, da während des Projekts neue Muster und Verbesserungen vorhandener Muster erkannt werden. Es ist hilfreich, den Entwicklungsplan so zu organisieren, dass Sie jedes der Hauptentwurfsmuster in einer frühen Phase ausführen.

 Die meisten Entwurfsmuster können teilweise in Frameworkcode dargestellt werden. Ein Teil des Musters kann auf die Anforderung reduziert werden, dass der Entwickler bestimmte Klassen oder Komponenten verwendet, z. B. eine Datenbankzugriffsebene, die sicherstellt, dass die Datenbank ordnungsgemäß behandelt wird.

 Ein Entwurfsmuster wird in einem Dokument beschrieben, und es enthält in der Regel die folgenden Teile:

- Name.

- Eine Beschreibung des Kontexts, in dem es anwendbar ist. Aufgrund welcher Kriterien sollte der Entwickler das Anwenden des Musters in Betracht ziehen?

- Eine kurze Erläuterung des Problems, das durch das Muster gelöst wird.

- Ein Modell der Hauptbestandteile und ihrer Beziehungen. Dabei kann es sich um Klassen oder Komponenten und Schnittstellen handeln, mit Zuordnungen und Abhängigkeiten zwischen ihnen. Die Elemente gehören normalerweise zu einer von zwei Kategorien:

  - Elemente, die der Entwickler in jedem Teil des Codes replizieren muss, in dem das Muster verwendet wird. Sie können diese mithilfe von Vorlagentypen beschreiben. Weitere Informationen finden Sie unter [UML-Anwendungsfall Diagramme: Referenz](../modeling/uml-use-case-diagrams-reference.md).

  - Elemente, die Framework-Klassen beschreiben, die der Entwickler verwenden sollte.

- Ein Modell der Interaktionen zwischen den Teilen mit Sequenz- oder Aktivitätsdiagrammen.

- Benennungskonventionen

- Eine Beschreibung, wie das Muster das Problem löst.

- Eine Beschreibung von Varianten, die Entwickler möglicherweise anwenden können.

## <a name="see-also"></a>Siehe auch
 [Bearbeiten von UML-Modellen und-Diagrammen](../modeling/edit-uml-models-and-diagrams.md) [visualisieren von Code](../modeling/visualize-code.md) [Modell-Benutzer Anforderungen](../modeling/model-user-requirements.md) [entwickeln von Tests aus einem Modell verwenden von](../modeling/develop-tests-from-a-model.md) [Modellen im Entwicklungsprozess](../modeling/use-models-in-your-development-process.md)
