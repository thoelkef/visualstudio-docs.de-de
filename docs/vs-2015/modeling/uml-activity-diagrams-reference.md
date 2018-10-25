---
title: 'UML-Aktivitätsdiagramme: Verweisen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: eed16e010c4fc070b9cc8be57731c97c2f03b2ab
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49862280"
---
# <a name="uml-activity-diagrams-reference"></a>UML-Aktivitätsdiagramme: Referenz
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ein *Aktivitätsdiagramm* zeigt einen Geschäfts- oder Softwareprozess als Arbeitsablauf durch eine Reihe von Aktionen. Diese Aktionen können von Personen, Softwarekomponenten oder Computern ausgeführt werden.  
  
 Mithilfe eines Aktivitätsdiagramms können Sie verschiedene Arten von Prozessen beschreiben. Beispiele:  
  
- Ein Geschäftsprozess oder Arbeitsablauf zwischen Benutzern und dem System. Weitere Informationen finden Sie unter [Modellieren von benutzeranforderungen](../modeling/model-user-requirements.md).  
  
- Die in einem Anwendungsfall ausgeführten Schritte. Weitere Informationen finden Sie unter [UML-Anwendungsfalldiagramme: Richtlinien](../modeling/uml-use-case-diagrams-guidelines.md).  
  
- Ein Softwareprotokoll, d. h. die zulässigen Sequenzen von Interaktionen zwischen Komponenten.  
  
- Ein Softwarealgorithmus.  
  
  In diesem Thema werden die Elemente beschrieben, die Sie in Aktivitätsdiagrammen verwenden können. Weitere Informationen finden Sie unter Informationen zum Zeichnen Diagramme finden Sie unter [UML-Aktivitätsdiagramme: Richtlinien](../modeling/uml-activity-diagrams-guidelines.md). Zum Erstellen eines UML-Aktivitätsdiagramms, auf die **Architektur** Menü klicken Sie auf **neues UML- oder Ebenendiagramm**. Weitere Informationen zum allgemeinen Zeichnen von Modellierungsdiagrammen finden Sie unter [Bearbeiten von UML-Modellen und Diagrammen](../modeling/edit-uml-models-and-diagrams.md).  
  
## <a name="reading-activity-diagrams"></a>Lesen von Aktivitätsdiagrammen  
 Die Tabellen in den folgenden Abschnitten beschreiben die Elemente für Aktivitätsdiagramme und deren Haupteigenschaften. Eine vollständige Liste der Eigenschaften der Elemente, finden Sie unter [Eigenschaften von Elementen in UML-Aktivitätsdiagramme](../modeling/properties-of-elements-on-uml-activity-diagrams.md).  
  
 Die Aktionen und anderen Elemente, die in einem Aktivitätsdiagramm angezeigt werden, bilden eine Aktivität. Sie können die Aktivität im UML-Modell-Explorer anzeigen. Sie wird beim Hinzufügen des ersten Elements zum Diagramm erstellt.  
  
 Stellen Sie sich zum Lesen eines Diagramms ein Token oder Kontrollthread vor, das die Konnektoren von einer Aktion an die nächste übergibt.  
  
### <a name="simple-control-flows"></a>Einfache Ablaufsteuerungen  
 Sie können eine Sequenz von Aktionen mit Verzweigungen und Schleifen darstellen. Weitere Informationen dazu, wie Sie die hier beschriebenen Elemente zu verwenden, finden Sie im Abschnitt beschreiben des Kontrollflusses des Themas [UML-Aktivitätsdiagramme: Richtlinien](../modeling/uml-activity-diagrams-guidelines.md).  
  
 ![Einfache ablaufsteuerung](../modeling/media/uml-actovsimple.png "UML_ActOvSimple")  
  
||||  
|-|-|-|  
|**Form "**|**Element**|**Beschreibung und Haupteigenschaften**|  
|1|**Aktion**|Ein Schritt in der Aktivität, in dem Benutzer oder Software eine Aufgabe ausführen.<br /><br /> Die Aktion kann beginnen, wenn ein Token bei allen eingehenden Flüssen eingetroffen ist. Wenn die Aktion endet, werden Token an alle ausgehenden Flüsse gesendet.<br /><br /> -   **Text** -gibt die Aktion ausführlich an.<br />-   **Sprache** – die Sprache des Ausdrucks im Textkörper.<br />-   **Lokale Nachbedingungen** -Einschränkungen, die am Ende der Ausführung erfüllt sein müssen. Das von der Aktion erreichte Ziel.<br />-   **Lokale Vorbedingungen** -Einschränkungen, die vor Beginn der Ausführung erfüllt sein müssen.|  
|2|**Ablaufsteuerung**|Ein Konnektor, der die Ablaufsteuerung zwischen Aktionen darstellt. Stellen Sie sich zum Interpretieren des Diagramms vor, dass ein Token von einer Aktion zur nächsten fließt.<br /><br /> Verwenden Sie zum Erstellen einer ablaufsteuerung das **Connector** Tool.|  
|3|**Startknoten**|Gibt die erste(n) Aktion(en) in der Aktivität an. Wenn die Aktivität startet, fließt ein Token vom Startknoten.|  
|4|**Aktivitätsendknoten**|Ein Ende für die Aktivität. Wenn ein Token ankommt, wird die Aktivität beendet.|  
|5|**Entscheidungsknoten**|Ein bedingter Zweig in einem Ablauf. Dieser verfügt über eine Eingabe und zwei oder mehrere Ausgaben. Ein eingehendes Token entsteht nur bei einer der Ausgaben.|  
|6|**Guard**|Eine Bedingung, die angibt, ob ein Token über einen Konnektor übertragen werden kann. Diese wird am häufigsten für die ausgehenden Flüsse eines Entscheidungsknotens verwendet.<br /><br /> Um ein Wächter festzulegen, mit der rechten Maustaste eines Flows aus, klicken Sie auf **Eigenschaften** und legen Sie dann die **schützen** Eigenschaft.|  
|7|**Zusammenführungsknoten**|Dieser ist erforderlich, um Flüsse zusammenzuführen, die über einen Entscheidungsknoten geteilt wurden. Verfügt über zwei oder mehrere Eingaben und eine Ausgabe. Für jede Eingabe tritt bei der Ausgabe ein Token auf.|  
|8|**Kommentar**|Bietet zusätzliche Informationen zu Elementen, mit denen er verknüpft ist.|  
|9|**Aktion zum Aufrufen eines Verhaltens**|Eine Aktion, die in einem anderen Aktivitätsdiagramm ausführlicher definiert ist.<br /><br /> -   **IsSynchronous** : Wenn "true", wartet die Aktion auf die Aktivität ist beendet.<br />-   **Verhalten** : die Aktivität wurde aufgerufen.|  
|(nicht angezeigt)|**Aktion des Vorgangs zum Aufrufen eines**|Eine Aktion, die einen Vorgang für eine Instanz einer Klasse aufruft.|  
||**Aktivität**|Der Arbeitsablauf, der von einem Aktivitätsdiagramm dargestellt wird. Um die Eigenschaften einer Aktivität anzuzeigen, müssen Sie diesen in auswählen **UML-Modell-Explorer**.<br /><br /> -   **Ist schreibgeschützt.** : Wenn "true", die Aktivität den Status eines Objekts nicht ändern sollten.<br />-   **Ist die einzige Ausführung** : Wenn "true", es höchstens eine Ausführung des Diagramms zu einem Zeitpunkt gibt.|  
||**UML-Aktivitätsdiagramm**|Das Diagramm, das eine Aktivität anzeigt. Um ihre Eigenschaften anzuzeigen, klicken Sie auf einen leeren Bereich des Diagramms. **Hinweis:** den Namen des Aktivitätsdiagramms, die Datei, die das Diagramm und die im Diagramm angezeigte Aktivität enthält kann alle unterschiedlich sein.|  
  
### <a name="concurrent-flows"></a>Parallele Flüsse  
 Sie können Sequenzen von Aktionen beschreiben, die gleichzeitig ausgeführt werden. Weitere Informationen finden Sie unter „Zeichnen von parallelen Flüssen“.  
  
 ![Aktivitätsdiagramm mit gleichzeitigem Fluss](../modeling/media/uml-actovconcurrent.png "UML_ActovConcurrent")  
  
||||  
|-|-|-|  
|**Form "**|**Element**|**Beschreibung**|  
|11|**Gabelungsknoten**|Unterteilt einen einzelnen Fluss in parallele Flüsse. Jedes eingehende Token erzeugt ein Token an jedem ausgehenden Konnektor.|  
|12|**Fügen Sie Knoten**|Fasst parallele Flüsse zu einem einzelnen Fluss zusammen. Wenn für jeden eingehender Fluss ein wartendes Token vorhanden ist, wird in der Ausgabe ein Token erzeugt.|  
|13|**Aktion zum Senden**|Eine Aktion, die eine Nachricht oder ein Signal an eine andere Aktivität oder an einen parallelen Thread in der gleichen Aktivität sendet. Typ und Inhalt der Nachricht werden durch den Titel der Aktion impliziert oder in zusätzlichen Kommentaren angegeben.<br /><br /> Die Aktion kann Daten im Signal senden, die in einem Objektfluss oder Eingabepin (16) an die Aktion übergeben werden können.|  
|14|**Ereignisaktion akzeptieren**|Eine Aktion, die auf eine Nachricht oder ein Signal wartet, bevor die Aktion fortgesetzt werden kann. Der Typ der Nachricht, der von der Aktion abgerufen werden kann, wird durch den Titel der Aktion impliziert oder in zusätzlichen Kommentaren angegeben.<br /><br /> Weist die Aktion keine eingehende Ablaufsteuerung auf, erzeugt sie beim Erhalten einer Nachricht ein Token.<br /><br /> Die Aktion kann Daten im Signal empfangen, die in einem Objektfluss oder Ausgabepin (17) übergeben werden können.<br /><br /> -   **IsUnmarshall** : Wenn "true", können mehrere typisierte Ausgabepins vorhanden sein, und Daten auf diese mashallen. Bei „False“ werden alle Daten auf einem Pin angezeigt.|  
  
###  <a name="DataFlow"></a> Datenflüsse  
 Sie können den Fluss der Daten von einer Aktion zu einer anderen beschreiben. Weitere Informationen zu den in diesem Abschnitt verwendeten Elementen finden Sie im Abschnitt „Zeichnen von Datenflüssen“ des Themas „Richtlinien zum Zeichnen eines Aktivitätsdiagramms“.  
  
 ![Aktivitätsdiagramm mit Datenfluss](../modeling/media/uml-actovdata.png "UML_ActOvData")  
  
||||  
|-|-|-|  
|**Form "**|**Element**|**Beschreibung**|  
|15|**Objektknoten**|Stellt die Daten dar, die in einem Fluss übertragen werden.<br /><br /> -   **Sortierung** – Speichern mehrerer Token.<br />-   **Auswahl** -Ruft einen Prozess, der in einem anderen Diagramm definiert werden kann, die die Daten filtert.<br />-   **Obere Grenze** -0 bedeutet, dass Daten direkt im Fluss übergeben werden müssen \* gibt an, dass die Daten im Fluss gespeichert werden können.<br />-   **Typ** -Objekttypen gespeichert und übertragen.|  
|16|**Eingabepin**|Stellt die Daten dar, die eine Aktion bei ihrer Ausführung empfangen kann.<br /><br /> -   **Typ** – der Typ der übertragenen Objekte.|  
|17|**Ausgabepin**|Stellt Daten dar, die eine Aktion bei ihrer Ausführung erzeugt.<br /><br /> -   **Typ** – der Typ der übertragenen Objekte.|  
|18|**Aktivitätsparameterknoten**|Ein Objektknoten, über den Daten von der Aktivität empfangen oder erzeugt werden können.<br /><br /> Dieser wird verwendet, wenn die vom Diagramm dargestellte Aktivität von einer anderen Aktivität aufgerufen wird, oder wenn das Diagramm einen Vorgang oder eine Funktion beschreibt.<br /><br /> -   **Typ** – der Typ der übertragenen Objekte.|  
|(nicht angezeigt)|**Objektfluss**|Ein Konnektor, der den Datenfluss zwischen Aktionen und Objektknoten darstellt.<br /><br /> Verwenden Sie zum Erstellen eines Objektflusses das **Connector** Tool, um einen Eingabe- oder Ausgabepin bzw. einen Objektknoten auf ein anderes Element zu verknüpfen.<br /><br /> -   **Auswahl** -Ruft einen Prozess, der in einem anderen Diagramm definiert werden kann, die die Daten filtert.<br />-   **Transformation** -Ruft einen Prozess, der in einem anderen Diagramm definiert werden kann, die die Daten transformiert.<br />-   **IsMulticast** – gibt an, dass mehrere Empfängerobjekte oder-Komponenten vorhanden sein kann.<br />-   **IsMultiReceive** – gibt an, dass die Eingaben aus mehreren Objekten oder Komponenten empfangen werden können.|  
  
## <a name="see-also"></a>Siehe auch  
 [Bearbeiten von UML-Modellen und-Diagrammen](../modeling/edit-uml-models-and-diagrams.md)   
 [UML-Aktivitätsdiagramme: Richtlinien](../modeling/uml-activity-diagrams-guidelines.md)



