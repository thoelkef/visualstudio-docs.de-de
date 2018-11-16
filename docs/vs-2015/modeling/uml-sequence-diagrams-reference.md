---
title: 'UML-Sequenzdiagramme: Referenz | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 5c92d9eb8ee7858a036fdbb8dfb621c269e3ed4c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51797025"
---
# <a name="uml-sequence-diagrams-reference"></a>UML-Sequenzdiagramme: Referenz
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio eine *Sequenzdiagramm* zeigt eine Interaktion, die die Sequenz von Meldungen zwischen Instanzen von Klassen, Komponenten, Subsystemen oder Akteuren darstellt. Zeit verläuft im Diagramm abwärts und zeigt die Ablaufsteuerung von einem Teilnehmer zu einem anderen. Verwenden Sie Sequenzdiagramme, um Instanzen und Ereignisse zu visualisieren, anstatt Klassen und Methoden. Mehr als eine Instanz des gleichen Typs kann im Diagramm angezeigt werden. Auch kann mehr als ein Vorkommen der gleichen Meldung angezeigt werden.  
  
 UML-Sequenzdiagramme sind Teil eines UML-Modells und nur innerhalb von UML-Modellierungsprojekten vorhanden. Erstellen Sie ein UML-Sequenzdiagramm können auf die **Architektur** Menü klicken Sie auf **neues UML- oder Ebenendiagramm**. Erfahren Sie mehr über das Erstellen und zeichnen [UML-Sequenzdiagramme](../modeling/uml-sequence-diagrams-guidelines.md) oder [UML-Modellierungsdiagrammen](../modeling/edit-uml-models-and-diagrams.md) im Allgemeinen.  
  
 Welche Versionen von Visual Studio dieses Feature unterstützen, erfahren Sie unter [Versionsunterstützung für Architektur- und Modellierungstools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="reading-sequence-diagrams"></a>Lesen von Sequenzdiagrammen  
 In der folgenden Tabelle werden die Elemente beschrieben, die in einem Sequenzdiagramm angezeigt werden. Erfahren Sie mehr über diese [Eigenschaften Elemente](../modeling/properties-of-elements-on-uml-sequence-diagrams.md).  
  
 ![Teile eines Sequenzdiagramms](../modeling/media/uml-sequence.png "UML_Sequence")  
  
|**Form "**|**Element**|**Beschreibung**|  
|---------------|-----------------|---------------------|  
|1|**Lebenslinie**|Eine vertikale Linie, die die Sequenz von Ereignissen darstellt, die während einer Interaktion in einem Teilnehmer vorkommen,während die Zeit abwärts entlang der Linie verläuft. Dieser Teilnehmer kann eine Instanz einer Klasse, einer Komponente oder eines Akteurs sein.|  
|2|**Actor**|Ein Teilnehmer, der sich außerhalb des Systems befindet, das Sie entwickeln.<br /><br /> Sie können ein Akteursymbol am Anfang einer Lebenslinie angezeigt werden, indem Sie die Einstellung machen die **Actor** Eigenschaft.|  
|3|**Synchrone Meldung**|Der Absender wartet auf eine Antwort auf eine synchrone Meldung, bevor er fortfährt. Das Diagramm zeigt den Aufruf und die Rückgabe. Synchrone Meldungen werden verwendet, um gewöhnliche Funktionsaufrufe innerhalb eines Programms sowie andere Arten von Meldungen darzustellen, die das gleiche Verhalten aufweisen.|  
|4|**Asynchrone Meldung**|Eine Meldung, die keine Antwort erfordert, bevor der Absender fortfährt. Eine asynchrone Meldung zeigt nur einen Aufruf vom Absender. Verwenden Sie diese, um die Kommunikation zwischen separaten Threads oder die Erstellung eines neuen Threads darzustellen.|  
|5|**Vorkommnisausführung**|Ein vertikal schattiertes Rechteck, das auf der Lebenslinie eines Teilnehmers angezeigt wird und den Zeitraum darstellt, in dem der Teilnehmer eine Operation ausführt.<br /><br /> Die Ausführung beginnt, wenn der Teilnehmer eine Meldung empfängt. Wenn die initiierende Meldung eine synchrone Meldung war, endet die Ausführung mit einem „Rückgabepfeil“ zurück an den Absender.|  
|6|**Callback-Nachricht**|Eine Meldung, die an einen Teilnehmer zurückgeht, der auf die Rückgabe von einem früheren Aufruf wartet. Die daraus resultierende Vorkommnisausführung wird über der vorhandenen angezeigt.|  
|7|**Self-Meldung**|Eine Meldung von einem Teilnehmer an sich selbst. Die daraus resultierende Vorkommnisausführung wird über der sendenden Ausführung angezeigt.|  
|8|**Nachricht erstellen**|Eine Meldung, die einen Teilnehmer erstellt. Empfängt ein Teilnehmer eine Create-Meldung, sollte sie die erste sein, die er erhält.|  
|9|**Gefundene Meldung**|Eine asynchrone Meldung von einem unbekannten oder einem nicht angegebenen Teilnehmer.|  
|10|**Verlorene Meldung**|Eine asynchrone Meldung an einen unbekannten oder einen nicht angegebenen Teilnehmer.|  
|11|**Kommentar**|Ein Kommentar kann an einen beliebigen Punkt auf einer Lebenslinie angefügt werden.|  
|12|**Interaktionsverwendung**|Umschließt eine Sequenz von Meldungen, die in einem anderen Diagramm definiert sind.<br /><br /> Zum Erstellen einer **Interaktionsverwendung**, klicken Sie auf das Tool, und ziehen Sie dann über die Lebenslinien, die Sie einschließen möchten.|  
|13|**Kombiniertes Fragment**|Eine Auflistung von Fragmenten. Jedes Fragment kann eine oder mehrere Meldungen einschließen. Es gibt verschiedene Arten von kombinierten Fragmenten. Weitere Informationen finden Sie unter [Beschreiben des Kontrollflusses mit Fragmenten in UML-Sequenzdiagrammen](../modeling/describe-control-flow-with-fragments-on-uml-sequence-diagrams.md).<br /><br /> Um ein Fragment zu erstellen, mit der rechten Maustaste einer Meldung, zeigen Sie auf **Umschließen mit**, und klicken Sie dann auf einen Fragmenttyp.|  
|14|**Fragmentwächter**|Kann verwendet werden, um eine Bedingung anzugeben, die entscheidet, ob das Fragment auftritt.<br /><br /> Um den Wächter festzulegen, wählen Sie ein Fragment, wählen Sie dann den Wächter, und geben Sie einen Wert ein.|  
|**X**|**Zerstörungsereignis**|Gibt den Punkt an, an dem das Objekt gelöscht wird oder nicht mehr verfügbar ist. Wird am unteren Rand jeder Lebenslinie angezeigt.|  
||**Interaktion**|Die Auflistung der Meldungen und Lebenslinien, die im Sequenzdiagramm angezeigt wird. Um die Eigenschaften einer Interaktion anzuzeigen, müssen Sie diesen in auswählen **UML-Modell-Explorer**.|  
||**Sequenzdiagramm**|Das Diagramm, das eine Interaktion anzeigt. Um seine Eigenschaften anzuzeigen, klicken Sie auf einen leeren Bereich des Diagramms. **Hinweis:** die Namen der im Sequenzdiagramm die Interaktion, die angezeigt wird, und die Datei, die das Diagramm enthält kann alle unterschiedlich sein.|  
  
## <a name="see-also"></a>Siehe auch  
 [UML-Sequenzdiagramme: Richtlinien](../modeling/uml-sequence-diagrams-guidelines.md)   
 [Bearbeiten von UML-Modellen und-Diagrammen](../modeling/edit-uml-models-and-diagrams.md)   
 [UML-Anwendungsfalldiagramme: Referenz](../modeling/uml-use-case-diagrams-reference.md)   
 [UML-Klassendiagramme: Referenz](../modeling/uml-class-diagrams-reference.md)   
 [UML-Komponentendiagramme: Referenz](../modeling/uml-component-diagrams-reference.md)   
 [UML-Komponentendiagramme: Referenz](../modeling/uml-component-diagrams-reference.md)



