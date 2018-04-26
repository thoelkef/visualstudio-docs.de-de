---
title: Workflow-Designer - Flussdiagramm-Aktivitätsdesigner
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Flowchart.UI
- System.Activities.Statements.FlowStep.UI
- System.Activities.Core.Presentation.FlowStart.UI
ms.assetid: d5af2276-5215-4138-880a-cf2b90bbf3a0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 81af4a51da2bb15bafd17fc7ba98d676f7b0decc
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="flowchart-activity-designer"></a>Flussdiagramm-Aktivitätsdesigner

Die <xref:System.Activities.Statements.Flowchart>-Aktivität wird verwendet, um Workflows zu erstellen, die komplexe Flusssteuerungen definieren und verwalten. Ein <xref:System.Activities.Statements.Flowchart> können entweder im Code oder mithilfe des Workflow-Designers erstellt werden. In diesem Thema werden die Workflow-Designer-Umgebung. Windows Workflow-Designer-workflowaktivitätsdesigner ermöglicht Entwicklern das Erstellen von Workflows auf natürliche Weise.

## <a name="the-flowchart-activity"></a>Die Flowchart-Aktivität

Die <xref:System.Activities.Statements.Flowchart>-Aktivität gibt einen eindeutigen <xref:System.Activities.Statements.Flowchart.StartNode%2A> an, der ausgeführt wird, wenn der Workflow startet und ein Netzwerk miteinander verknüpfter <xref:System.Activities.Statements.Flowchart.Nodes%2A> verwendet, um beliebige Schleifen zu erstellen oder zu einem bestimmten Zeitpunkt den Ausführungsfluss anderswohin im Workflow umzuleiten.

### <a name="using-the-flowchart-activity-designer"></a>Verwenden des Flussdiagramm-Aktivitätsdesigners

Die **Flussdiagramm** Aktivitäts-Designer finden Sie in der **Flussdiagramm** Kategorie der **Toolbox**, die erfolgt durch Klicken auf die **Toolbox**Registerkarte im Workflow-Designer (Wählen Sie alternativ **Symbolleiste** aus der **Ansicht** Menüs oder STRG + ALT + X drücken.)

Die **Flussdiagramm** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** und sich der Workflow-Designer-Oberfläche gelöscht wird, wo Aktivitätsdesigner normalerweise, als eine Stammaktivität oder als platziert werden die untergeordnetes Element von einer anderen ablaufsteuerungsaktivität. Wenn die **Flussdiagramm** Aktivitäts-Designer auf eine leere Oberfläche des Workflow-Designer abgelegt wird, erstellt er eine <xref:System.Activities.Statements.Flowchart> Aktivität, die standardmäßig sich in einer erweiterten Ansicht präsentiert, in der der Startknoten, der die Ausführung initiiert wird. als grüner Ball dargestellt. Wenn die **Flussdiagramm** Aktivitäts-Designer in einer anderen ablaufsteuerungsaktivität abgelegt wird, präsentiert er sich in einer minimierten Ansicht, die durch Doppelklicken auf erweitert werden kann, die **Flussdiagramm** Aktivitäts-Designer. Jede Aktivität in der **Toolbox** gezogen werden können, direkt auf die **Flussdiagramm** Aktivitäts-Designer, wie andere ablaufsteuerungsaktivitäten.

Nach dem Ziehen von verschiedenen Aktivitätsdesigner auf der Zeichenfläche Workflow-Designer die <xref:System.Activities.Activity> Objekte, die sie darstellen können verknüpft werden zusammen, um die Reihenfolge der Ausführung anzugeben. Sie erstellen einen Link zwischen einer Quellaktivität und einer Zielaktivität, indem Sie die Maus über den Designer der Quellaktivität bewegen, an dessen beiden Seiten dann quadratische Ziehpunkte angezeigt werden. Klicken Sie auf einen der quadratischen Ziehpunkte, und ziehen Sie ihn bei gedrückter Maustaste auf einen der Ziehpunkte, die um die Zielaktivität angezeigt werden, sobald Sie die Maus über diese Aktivität bewegen. Lassen Sie die Maustaste los, und zwischen beiden Aktivitäten wird ein Link erstellt, der als vom Quelldesigner zum Zieldesigner zeigender Pfeil dargestellt wird.

### <a name="flowchart-activity-properties"></a>Flussdiagrammaktivitätseigenschaften

In der folgenden Tabelle werden die <xref:System.Activities.Statements.Flowchart>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaftenraster oder auf der Designeroberfläche bearbeitet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Gibt den Anzeigenamen des Aktivitätsdesigners im Header an. Der Standardwert lautet Flussdiagramm. Der Wert kann bearbeitet werden, der **Eigenschaften** Fenster oder direkt im Header Aktivitätsdesigners.<br /><br /> Obwohl der <xref:System.Activities.Activity.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|
|<xref:System.Activities.Statements.Flowchart.Variables%2A>|False|Die Auflistung der innerhalb dieses <xref:System.Activities.Statements.Flowchart> gültigen Variablen, mittels derer der Zustand gemeinsam mit seinen untergeordneten Aktivitäten verwendet wird.|
|<xref:System.Activities.Statements.Flowchart.StartNode%2A>|False|Der <xref:System.Activities.Statements.FlowNode>, der ausgeführt wird, wenn <xref:System.Activities.Statements.Flowchart> startet.|
|<xref:System.Activities.Statements.Flowchart.Nodes%2A>|False|Enthält die Auflistung der <xref:System.Activities.Statements.FlowNode>-Objekte im <xref:System.Activities.Statements.Flowchart>.|

## <a name="see-also"></a>Siehe auch

- [Flussdiagramm](../workflow-designer/flowchart-activity-designers.md)
- [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)
- [FlowSwitch\<T>](../workflow-designer/flowswitch-t-activity-designer.md)