---
title: 'UML-Sequenzdiagramme: Referenz | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.sequencediagram.diagram
- vs.teamarch.UMLModelExplorer.sequencediagram
- vs.teamarch.sequencediagram.toolbox
helpviewer_keywords:
- diagrams - modeling, sequence
- sequence diagrams
- UML diagrams, sequence
- diagrams - modeling, UML sequence
- UML, sequence diagrams
ms.assetid: 366fc324-aeeb-4894-bd13-ec2e40754b8e
caps.latest.revision: 43
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7f9b02bbad4fa897404f6c20e12b1705a3ae9ac8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661712"
---
# <a name="uml-sequence-diagrams-reference"></a>UML-Sequenzdiagramme: Referenz
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio zeigt ein *Sequenzdiagramm* eine Interaktion, die die Reihenfolge der Nachrichten zwischen Instanzen von Klassen, Komponenten, Subsystemen oder Akteuren darstellt. Zeit verläuft im Diagramm abwärts und zeigt die Ablaufsteuerung von einem Teilnehmer zu einem anderen. Verwenden Sie Sequenzdiagramme, um Instanzen und Ereignisse zu visualisieren, anstatt Klassen und Methoden. Mehr als eine Instanz des gleichen Typs kann im Diagramm angezeigt werden. Auch kann mehr als ein Vorkommen der gleichen Meldung angezeigt werden.

 UML-Sequenzdiagramme sind Teil eines UML-Modells und nur innerhalb von UML-Modellierungsprojekten vorhanden. Um ein UML-Sequenzdiagramm zu erstellen, klicken Sie im Menü **Architektur** auf **neues UML-oder ebenendiagramm**. Erfahren Sie mehr über das Erstellen und Zeichnen von [UML-Sequenzdiagrammen](../modeling/uml-sequence-diagrams-guidelines.md) oder [UML-Modellierungs Diagrammen](../modeling/edit-uml-models-and-diagrams.md) im Allgemeinen.

 Welche Versionen von Visual Studio dieses Features unterstützen, erfahren Sie unter [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="reading-sequence-diagrams"></a>Lesen von Sequenzdiagrammen
 In der folgenden Tabelle werden die Elemente beschrieben, die in einem Sequenzdiagramm angezeigt werden. Weitere Informationen zu den [Eigenschaften dieser Elemente](../modeling/properties-of-elements-on-uml-sequence-diagrams.md)finden Sie hier.

 ![Teile eines Sequenz Diagramms](../modeling/media/uml-sequence.png "UML_Sequence")

|**Gebildet**|**Element**|**Beschreibung**|
|---------------|-----------------|---------------------|
|1|**Lebens**|Eine vertikale Linie, die die Sequenz von Ereignissen darstellt, die während einer Interaktion in einem Teilnehmer vorkommen,während die Zeit abwärts entlang der Linie verläuft. Dieser Teilnehmer kann eine Instanz einer Klasse, einer Komponente oder eines Akteurs sein.|
|2|**Teurs**|Ein Teilnehmer, der sich außerhalb des Systems befindet, das Sie entwickeln.<br /><br /> Sie können ein Actor-Symbol am oberen Rand einer Lebenslinie durch Festlegen der **Actor** -Eigenschaft anzeigen.|
|3|**Synchrone Meldung**|Der Absender wartet auf eine Antwort auf eine synchrone Meldung, bevor er fortfährt. Das Diagramm zeigt den Aufruf und die Rückgabe. Synchrone Meldungen werden verwendet, um gewöhnliche Funktionsaufrufe innerhalb eines Programms sowie andere Arten von Meldungen darzustellen, die das gleiche Verhalten aufweisen.|
|4|**Asynchrone Nachricht**|Eine Meldung, die keine Antwort erfordert, bevor der Absender fortfährt. Eine asynchrone Meldung zeigt nur einen Aufruf vom Absender. Verwenden Sie diese, um die Kommunikation zwischen separaten Threads oder die Erstellung eines neuen Threads darzustellen.|
|5|**Vorkommnisausführung**|Ein vertikal schattiertes Rechteck, das auf der Lebenslinie eines Teilnehmers angezeigt wird und den Zeitraum darstellt, in dem der Teilnehmer eine Operation ausführt.<br /><br /> Die Ausführung beginnt, wenn der Teilnehmer eine Meldung empfängt. Wenn die initiierende Meldung eine synchrone Meldung war, endet die Ausführung mit einem „Rückgabepfeil“ zurück an den Absender.|
|6|**Rückruf Meldung**|Eine Meldung, die an einen Teilnehmer zurückgeht, der auf die Rückgabe von einem früheren Aufruf wartet. Die daraus resultierende Vorkommnisausführung wird über der vorhandenen angezeigt.|
|7|**Selbst Meldung**|Eine Meldung von einem Teilnehmer an sich selbst. Die daraus resultierende Vorkommnisausführung wird über der sendenden Ausführung angezeigt.|
|8|**Nachricht erstellen**|Eine Meldung, die einen Teilnehmer erstellt. Empfängt ein Teilnehmer eine Create-Meldung, sollte sie die erste sein, die er erhält.|
|9|**Meldung gefunden**|Eine asynchrone Meldung von einem unbekannten oder einem nicht angegebenen Teilnehmer.|
|10|**Verlorene Nachricht**|Eine asynchrone Meldung an einen unbekannten oder einen nicht angegebenen Teilnehmer.|
|11|**Kommentar**|Ein Kommentar kann an einen beliebigen Punkt auf einer Lebenslinie angefügt werden.|
|12|**Interaktions Verwendung**|Umschließt eine Sequenz von Meldungen, die in einem anderen Diagramm definiert sind.<br /><br /> Klicken Sie zum Erstellen einer **Interaktions Verwendung**auf das Tool, und ziehen Sie es dann über die Lebenslinien, die Sie einschließen möchten.|
|13|**Kombiniertes Fragment**|Eine Auflistung von Fragmenten. Jedes Fragment kann eine oder mehrere Meldungen einschließen. Es gibt verschiedene Arten von kombinierten Fragmenten. Weitere Informationen finden Sie unter [beschreiben der Ablauf Steuerung mit Fragmenten in UML-Sequenzdiagrammen](../modeling/describe-control-flow-with-fragments-on-uml-sequence-diagrams.md).<br /><br /> Zum Erstellen eines Fragments klicken Sie mit der rechten Maustaste auf eine Meldung, zeigen Sie auf **Umschließen mit**, und klicken Sie dann auf einen fragmenttyp.|
|14|**Fragmentwächter**|Kann verwendet werden, um eine Bedingung anzugeben, die entscheidet, ob das Fragment auftritt.<br /><br /> Um den Wächter festzulegen, wählen Sie ein Fragment, wählen Sie dann den Wächter, und geben Sie einen Wert ein.|
|**X**|**Zerstörungs Ereignis**|Gibt den Punkt an, an dem das Objekt gelöscht wird oder nicht mehr verfügbar ist. Wird am unteren Rand jeder Lebenslinie angezeigt.|
||**Interaktion**|Die Auflistung der Meldungen und Lebenslinien, die im Sequenzdiagramm angezeigt wird. Um die Eigenschaften einer Interaktion anzuzeigen, müssen Sie Sie im UML- **Modell-Explorer**auswählen.|
||**Sequenzdiagramm**|Das Diagramm, das eine Interaktion anzeigt. Um seine Eigenschaften anzuzeigen, klicken Sie auf einen leeren Bereich des Diagramms. **Hinweis:**  Die Namen des Sequenz Diagramms, die von ihm angezeigten Interaktionen und die Datei, die das Diagramm enthält, können unterschiedlich sein.|

## <a name="see-also"></a>Siehe auch
 [UML-Sequenzdiagramme: Richtlinien](../modeling/uml-sequence-diagrams-guidelines.md) [Bearbeiten von UML-Modellen und-Diagrammen UML-](../modeling/edit-uml-models-and-diagrams.md) [Anwendungsfall Diagramme: Referenz](../modeling/uml-use-case-diagrams-reference.md) für [UML-Klassendiagramme: Referenz](../modeling/uml-class-diagrams-reference.md) für UML- [Komponenten Diagramme:](../modeling/uml-component-diagrams-reference.md) [Referenz](../modeling/uml-component-diagrams-reference.md)
