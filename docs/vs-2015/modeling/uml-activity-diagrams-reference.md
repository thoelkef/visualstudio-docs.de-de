---
title: 'UML-Aktivitätsdiagramme: Referenz | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.activitydiagram.diagram
- vs.teamarch.activitydiagram.toolbox
- vs.teamarch.UMLModelExplorer.activitydiagram
helpviewer_keywords:
- UML diagrams, activity
- diagrams - modeling, activity
- diagrams - modeling, UML activity
- activity diagrams
- UML, activity diagrams
- behaviors, UML
ms.assetid: 07efcd17-2a96-4052-9957-6dcccbb725ee
caps.latest.revision: 50
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3a882867720e9cca2d51419643ebe60e692817a1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658450"
---
# <a name="uml-activity-diagrams-reference"></a>UML-Aktivitätsdiagramme: Referenz
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ein *Aktivitätsdiagramm* zeigt einen Geschäftsprozess oder einen Softwareprozess als Fluss von Arbeit durch eine Reihe von Aktionen. Diese Aktionen können von Personen, Softwarekomponenten oder Computern ausgeführt werden.

 Mithilfe eines Aktivitätsdiagramms können Sie verschiedene Arten von Prozessen beschreiben. Beispiele:

- Ein Geschäftsprozess oder Arbeitsablauf zwischen Benutzern und dem System. Weitere Informationen finden Sie unter [Modell Benutzeranforderungen](../modeling/model-user-requirements.md).

- Die in einem Anwendungsfall ausgeführten Schritte. Weitere Informationen finden Sie unter [UML-Anwendungsfall Diagramme: Richtlinien](../modeling/uml-use-case-diagrams-guidelines.md).

- Ein Softwareprotokoll, d. h. die zulässigen Sequenzen von Interaktionen zwischen Komponenten.

- Ein Softwarealgorithmus.

  In diesem Thema werden die Elemente beschrieben, die Sie in Aktivitätsdiagrammen verwenden können. Ausführlichere Informationen zu Zeichnungs Aktivitäts Diagrammen finden Sie unter [UML-Aktivitätsdiagramme: Richtlinien](../modeling/uml-activity-diagrams-guidelines.md). Um ein UML-Aktivitätsdiagramm zu erstellen, klicken Sie im Menü **Architektur** auf **neues UML-oder ebenendiagramm**. Weitere Informationen zum Erstellen von Modellierungs Diagrammen im Allgemeinen finden Sie unter [Bearbeiten von UML-Modellen und-Diagrammen](../modeling/edit-uml-models-and-diagrams.md).

## <a name="reading-activity-diagrams"></a>Lesen von Aktivitätsdiagrammen
 Die Tabellen in den folgenden Abschnitten beschreiben die Elemente für Aktivitätsdiagramme und deren Haupteigenschaften. Eine vollständige Liste der Eigenschaften der Elemente finden Sie unter [Eigenschaften von Elementen in UML-Aktivitäts Diagrammen](../modeling/properties-of-elements-on-uml-activity-diagrams.md).

 Die Aktionen und anderen Elemente, die in einem Aktivitätsdiagramm angezeigt werden, bilden eine Aktivität. Sie können die Aktivität im UML-Modell-Explorer anzeigen. Sie wird beim Hinzufügen des ersten Elements zum Diagramm erstellt.

 Stellen Sie sich zum Lesen eines Diagramms ein Token oder Kontrollthread vor, das die Konnektoren von einer Aktion an die nächste übergibt.

### <a name="simple-control-flows"></a>Einfache Ablaufsteuerungen
 Sie können eine Sequenz von Aktionen mit Verzweigungen und Schleifen darstellen. Weitere Informationen zur Verwendung der hier beschriebenen Elemente finden Sie im Abschnitt "beschreiben der Ablauf Steuerung" des Themas [UML-Aktivitätsdiagramme: Richtlinien](../modeling/uml-activity-diagrams-guidelines.md).

 ![Eine einfache Ablauf Steuerung](../modeling/media/uml-actovsimple.png "UML_ActOvSimple")

||||
|-|-|-|
|**Gebildet**|**Element**|**Beschreibung und Haupteigenschaften**|
|1|**Aktion**|Ein Schritt in der Aktivität, in dem Benutzer oder Software eine Aufgabe ausführen.<br /><br /> Die Aktion kann beginnen, wenn ein Token bei allen eingehenden Flüssen eingetroffen ist. Wenn die Aktion endet, werden Token an alle ausgehenden Flüsse gesendet.<br /><br /> -   **Text** : gibt die Aktion ausführlich an.<br />-   **Sprache** : die Sprache des Ausdrucks in Body.<br />-   **lokale nach Bedingungen** : Einschränkungen, die bei Beendigung der Ausführung erfüllt sein müssen. Das von der Aktion erreichte Ziel.<br />-   **Lokale Vorbedingungen** : Einschränkungen, die vor Beginn der Ausführung erfüllt sein müssen.|
|2|**Ablaufsteuerung**|Ein Konnektor, der die Ablaufsteuerung zwischen Aktionen darstellt. Stellen Sie sich zum Interpretieren des Diagramms vor, dass ein Token von einer Aktion zur nächsten fließt.<br /><br /> Verwenden Sie zum Erstellen einer Ablauf Steuerung das- **Connector** -Tool.|
|3|**Ursprünglicher Knoten**|Gibt die erste(n) Aktion(en) in der Aktivität an. Wenn die Aktivität startet, fließt ein Token vom Startknoten.|
|4|**Aktivitäts abschließender Knoten**|Ein Ende für die Aktivität. Wenn ein Token ankommt, wird die Aktivität beendet.|
|5|**Entscheidungs Knoten**|Ein bedingter Zweig in einem Ablauf. Dieser verfügt über eine Eingabe und zwei oder mehrere Ausgaben. Ein eingehendes Token entsteht nur bei einer der Ausgaben.|
|6|**Torschütze**|Eine Bedingung, die angibt, ob ein Token über einen Konnektor übertragen werden kann. Diese wird am häufigsten für die ausgehenden Flüsse eines Entscheidungsknotens verwendet.<br /><br /> Klicken Sie zum Festlegen eines Schutzes mit der rechten Maustaste auf einen Flow, klicken Sie auf **Eigenschaften** , und legen Sie dann die **Guard** -Eigenschaft fest|
|7|**Merge-Knoten**|Dieser ist erforderlich, um Flüsse zusammenzuführen, die über einen Entscheidungsknoten geteilt wurden. Verfügt über zwei oder mehrere Eingaben und eine Ausgabe. Für jede Eingabe tritt bei der Ausgabe ein Token auf.|
|8|**Kommentar**|Bietet zusätzliche Informationen zu Elementen, mit denen er verknüpft ist.|
|9|**Aktion zum Abrufen des Verhaltens**|Eine Aktion, die in einem anderen Aktivitätsdiagramm ausführlicher definiert ist.<br /><br /> -   **IsSynchronous** : Wenn true, wartet die Aktion, bis die Aktivität beendet wird.<br />-   **Verhalten** : die Aktivität wurde aufgerufen.|
|(nicht angezeigt)|**Aktion zum Abrufen des Vorgangs**|Eine Aktion, die einen Vorgang für eine Instanz einer Klasse aufruft.|
||**Aktivität**|Der Arbeitsablauf, der von einem Aktivitätsdiagramm dargestellt wird. Um die Eigenschaften einer Aktivität anzuzeigen, müssen Sie Sie im UML- **Modell-Explorer**auswählen.<br /><br /> -    schreibgeschützt**ist** : Wenn true, sollte die Aktivität den Status eines Objekts nicht ändern.<br />-   **ist eine einzelne Ausführung** : bei "true" wird höchstens eine Ausführung dieses Diagramms gleichzeitig ausgeführt.|
||**UML-Aktivitätsdiagramm**|Das Diagramm, das eine Aktivität anzeigt. Um ihre Eigenschaften anzuzeigen, klicken Sie auf einen leeren Bereich des Diagramms. **Hinweis:**  Die Namen des Aktivitäts Diagramms, die Datei, die das Diagramm enthält, und die vom Diagramm angezeigte Aktivität können unterschiedlich sein.|

### <a name="concurrent-flows"></a>Parallele Flüsse
 Sie können Sequenzen von Aktionen beschreiben, die gleichzeitig ausgeführt werden. Weitere Informationen finden Sie unter „Zeichnen von parallelen Flüssen“.

 ![Aktivitätsdiagramm, das gleichzeitigen Flow anzeigt](../modeling/media/uml-actovconcurrent.png "UML_ActovConcurrent")

||||
|-|-|-|
|**Gebildet**|**Element**|**Beschreibung**|
|11|**Verzweigungs Knoten**|Unterteilt einen einzelnen Fluss in parallele Flüsse. Jedes eingehende Token erzeugt ein Token an jedem ausgehenden Konnektor.|
|12|**Knoten beitreten**|Fasst parallele Flüsse zu einem einzelnen Fluss zusammen. Wenn für jeden eingehender Fluss ein wartendes Token vorhanden ist, wird in der Ausgabe ein Token erzeugt.|
|13|**Aktion zum Senden eines Signals**|Eine Aktion, die eine Nachricht oder ein Signal an eine andere Aktivität oder an einen parallelen Thread in der gleichen Aktivität sendet. Typ und Inhalt der Nachricht werden durch den Titel der Aktion impliziert oder in zusätzlichen Kommentaren angegeben.<br /><br /> Die Aktion kann Daten im Signal senden, die in einem Objektfluss oder Eingabepin (16) an die Aktion übergeben werden können.|
|14|**Ereignis Aktion akzeptieren**|Eine Aktion, die auf eine Nachricht oder ein Signal wartet, bevor die Aktion fortgesetzt werden kann. Der Typ der Nachricht, der von der Aktion abgerufen werden kann, wird durch den Titel der Aktion impliziert oder in zusätzlichen Kommentaren angegeben.<br /><br /> Weist die Aktion keine eingehende Ablaufsteuerung auf, erzeugt sie beim Erhalten einer Nachricht ein Token.<br /><br /> Die Aktion kann Daten im Signal empfangen, die in einem Objektfluss oder Ausgabepin (17) übergeben werden können.<br /><br /> -   **IsUnmarshall** : bei "true" können mehrere typisierte Ausgabe Pins vorhanden sein, und die Daten werden auf die Daten gemarshallt. Bei „False“ werden alle Daten auf einem Pin angezeigt.|

### <a name="DataFlow"></a>Datenflüsse
 Sie können den Fluss der Daten von einer Aktion zu einer anderen beschreiben. Weitere Informationen zu den in diesem Abschnitt verwendeten Elementen finden Sie im Abschnitt „Zeichnen von Datenflüssen“ des Themas „Richtlinien zum Zeichnen eines Aktivitätsdiagramms“.

 ![Aktivitätsdiagramm mit Datenfluss](../modeling/media/uml-actovdata.png "UML_ActOvData")

||||
|-|-|-|
|**Gebildet**|**Element**|**Beschreibung**|
|15|**Objekt Knoten**|Stellt die Daten dar, die in einem Fluss übertragen werden.<br /><br /> -   **Reihen** Folge: gibt an, wie mehrere Token gespeichert werden.<br />-   **Auswahl** : Ruft einen Prozess auf, der in einem anderen Diagramm definiert werden kann, der die Daten filtert.<br />-   **obere Grenze** -0 gibt an, dass Daten direkt entlang des Flusses übergeben werden müssen.  \* gibt an, dass Daten im Datenfluss gespeichert werden können.<br />-   **Typ** : der Typ der gespeicherten und übertragenen Objekte.|
|16|**Eingabepin**|Stellt die Daten dar, die eine Aktion bei ihrer Ausführung empfangen kann.<br /><br /> -   **Typ** : der Typ der übertragenen Objekte.|
|17|**Ausgabepin**|Stellt Daten dar, die eine Aktion bei ihrer Ausführung erzeugt.<br /><br /> -   **Typ** : der Typ der übertragenen Objekte.|
|18|**Aktivitäts Parameter Knoten**|Ein Objektknoten, über den Daten von der Aktivität empfangen oder erzeugt werden können.<br /><br /> Dieser wird verwendet, wenn die vom Diagramm dargestellte Aktivität von einer anderen Aktivität aufgerufen wird, oder wenn das Diagramm einen Vorgang oder eine Funktion beschreibt.<br /><br /> -   **Typ** : der Typ der übertragenen Objekte.|
|(nicht angezeigt)|**Objekt Fluss**|Ein Konnektor, der den Datenfluss zwischen Aktionen und Objektknoten darstellt.<br /><br /> Verwenden Sie zum Erstellen eines Objekt Flusses das Tool **Connector** , um eine Eingabe-oder Ausgabepin oder einen Objekt Knoten mit einem anderen Element zu verknüpfen.<br /><br /> -   **Auswahl** : Ruft einen Prozess auf, der in einem anderen Diagramm definiert werden kann, der die Daten filtert.<br />-   **Transformation** : Ruft einen Prozess auf, der in einem anderen Diagramm definiert werden kann, in dem die Daten transformiert werden.<br />-   **IsMulticast** : gibt an, dass mehrere Empfänger Objekte oder-Komponenten vorhanden sein können.<br />-   **IsMultiReceive** : gibt an, dass Eingaben von mehreren Objekten oder Komponenten empfangen werden können.|

## <a name="see-also"></a>Siehe auch
 [Bearbeiten von UML-Modellen und-Diagrammen UML-](../modeling/edit-uml-models-and-diagrams.md) [Aktivitätsdiagramme: Richtlinien](../modeling/uml-activity-diagrams-guidelines.md)
