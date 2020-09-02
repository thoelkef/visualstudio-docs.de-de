---
title: Flussdiagramm-Aktivitäts Designer | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Flowchart.UI
- System.Activities.Statements.FlowStep.UI
- System.Activities.Core.Presentation.FlowStart.UI
ms.assetid: d5af2276-5215-4138-880a-cf2b90bbf3a0
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8a85efea49d641fa54774c1428d15f7d8218ca53
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656707"
---
# <a name="flowchart-activity-designer"></a>Flussdiagramm-Aktivitätsdesigner
Die <xref:System.Activities.Statements.Flowchart>-Aktivität wird verwendet, um Workflows zu erstellen, die komplexe Flusssteuerungen definieren und verwalten. Ein <xref:System.Activities.Statements.Flowchart> kann entweder im Code oder mit [!INCLUDE[wfd2](../includes/wfd2-md.md)] erstellt werden. Dieses Thema zeigt die Verwendung von [!INCLUDE[wfd2](../includes/wfd2-md.md)]. Der [!INCLUDE[wfd1](../includes/wfd1-md.md)]-Workflowaktivitätsdesigner ermöglicht es Entwicklern, Workflows auf eine natürliche Weise zu erstellen.

## <a name="the-flowchart-activity"></a>Die Flowchart-Aktivität
 Die <xref:System.Activities.Statements.Flowchart>-Aktivität gibt einen eindeutigen <xref:System.Activities.Statements.Flowchart.StartNode%2A> an, der ausgeführt wird, wenn der Workflow startet und ein Netzwerk miteinander verknüpfter <xref:System.Activities.Statements.Flowchart.Nodes%2A> verwendet, um beliebige Schleifen zu erstellen oder zu einem bestimmten Zeitpunkt den Ausführungsfluss anderswohin im Workflow umzuleiten.

### <a name="using-the-flowchart-activity-designer"></a>Verwenden des Flussdiagramm-Aktivitätsdesigners
 Der **Flussdiagramm** -Aktivitäts Designer befindet sich in der Kategorie **Flussdiagramm** der **Toolbox**, auf die Sie zugreifen können, indem Sie in auf die Registerkarte **Toolbox** klicken (Sie können auch im [!INCLUDE[wfd2](../includes/wfd2-md.md)] Menü **Ansicht** den Befehl **Symbolleiste** auswählen oder STRG + ALT + X drücken).

 Der **Flussdiagramm** -Aktivitäts Designer kann aus der **Toolbox** gezogen und auf der- [!INCLUDE[wfd2](../includes/wfd2-md.md)] Oberfläche dort abgelegt werden, wo Aktivitäts Designer normalerweise platziert werden, entweder als Stamm Aktivität oder als untergeordnetes Element einer anderen Ablauf Steuerungs Aktivität. Wenn der **Flussdiagramm** -Aktivitäts Designer auf einer leeren [!INCLUDE[wfd2](../includes/wfd2-md.md)] Oberfläche abgelegt wird, erstellt er eine- <xref:System.Activities.Statements.Flowchart> Aktivität, die sich standardmäßig in einer erweiterten Ansicht präsentiert, in der der Startknoten, der die Ausführung initiiert, als grüner Ball dargestellt wird. Wenn der **Flussdiagramm** -Aktivitäts Designer in einer anderen Ablauf Steuerungs Aktivität abgelegt wird, stellt er sich in einer minimierten Ansicht vor, die durch Doppelklicken auf den **Flussdiagramm** -Aktivitäts Designer erweitert werden kann. Alle Aktivitäten in der **Toolbox** können direkt auf den **Flussdiagramm** -Aktivitäts Designer, einschließlich anderer Ablauf Steuerungsaktivitäten, gezogen werden.

 Nachdem Sie die verschiedenen Aktivitätsdesigner auf den [!INCLUDE[wfd2](../includes/wfd2-md.md)]-Canvas gezogen haben, können die durch sie dargestellten <xref:System.Activities.Activity>-Objekte miteinander verknüpft werden, um die Reihenfolge der Ausführung anzugeben. Sie erstellen einen Link zwischen einer Quellaktivität und einer Zielaktivität, indem Sie die Maus über den Designer der Quellaktivität bewegen, an dessen beiden Seiten dann quadratische Ziehpunkte angezeigt werden. Klicken Sie auf einen der quadratischen Ziehpunkte, und ziehen Sie ihn bei gedrückter Maustaste auf einen der Ziehpunkte, die um die Zielaktivität angezeigt werden, sobald Sie die Maus über diese Aktivität bewegen. Lassen Sie die Maustaste los, und zwischen beiden Aktivitäten wird ein Link erstellt, der als vom Quelldesigner zum Zieldesigner zeigender Pfeil dargestellt wird.

### <a name="flowchart-activity-properties"></a>Flussdiagrammaktivitätseigenschaften
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.Flowchart>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaftenraster oder auf der Designeroberfläche bearbeitet werden.

|Eigenschaftenname|Erforderlich|Verbrauch|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Falsch|Gibt den Anzeigenamen des Aktivitätsdesigners im Header an. Der Standardwert lautet Flussdiagramm. Der Wert kann im **Eigenschaften** Fenster oder direkt im Header des Aktivitäts Designers bearbeitet werden.<br /><br /> Obwohl der <xref:System.Activities.Activity.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|
|<xref:System.Activities.Statements.Flowchart.Variables%2A>|Falsch|Die Auflistung der innerhalb dieses <xref:System.Activities.Statements.Flowchart> gültigen Variablen, mittels derer der Zustand gemeinsam mit seinen untergeordneten Aktivitäten verwendet wird.|
|<xref:System.Activities.Statements.Flowchart.StartNode%2A>|Falsch|Der <xref:System.Activities.Statements.FlowNode>, der ausgeführt wird, wenn <xref:System.Activities.Statements.Flowchart> startet.|
|<xref:System.Activities.Statements.Flowchart.Nodes%2A>|Falsch|Enthält die Auflistung der <xref:System.Activities.Statements.FlowNode>-Objekte im <xref:System.Activities.Statements.Flowchart>.|

## <a name="see-also"></a>Weitere Informationen
 Fluss [Diagramm](../workflow-designer/flowchart-activity-designers.md) [FlowDecision](../workflow-designer/flowdecision-activity-designer.md) - [FlowSwitch \<T> ](../workflow-designer/flowswitch-t-activity-designer.md)