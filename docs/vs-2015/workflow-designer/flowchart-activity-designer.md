---
title: Flussdiagramm-Aktivitätsdesigner | Microsoft-Dokumentation
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3e89caded1b7388b79ea3232dc0a2809dc7b8222
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62943473"
---
# <a name="flowchart-activity-designer"></a>Flussdiagramm-Aktivitätsdesigner
Die <xref:System.Activities.Statements.Flowchart>-Aktivität wird verwendet, um Workflows zu erstellen, die komplexe Flusssteuerungen definieren und verwalten. Ein <xref:System.Activities.Statements.Flowchart> kann entweder im Code oder mit [!INCLUDE[wfd2](../includes/wfd2-md.md)] erstellt werden. Dieses Thema zeigt die Verwendung von [!INCLUDE[wfd2](../includes/wfd2-md.md)]. Der [!INCLUDE[wfd1](../includes/wfd1-md.md)]-Workflowaktivitätsdesigner ermöglicht es Entwicklern, Workflows auf eine natürliche Weise zu erstellen.  
  
## <a name="the-flowchart-activity"></a>Die Flowchart-Aktivität  
 Die <xref:System.Activities.Statements.Flowchart>-Aktivität gibt einen eindeutigen <xref:System.Activities.Statements.Flowchart.StartNode%2A> an, der ausgeführt wird, wenn der Workflow startet und ein Netzwerk miteinander verknüpfter <xref:System.Activities.Statements.Flowchart.Nodes%2A> verwendet, um beliebige Schleifen zu erstellen oder zu einem bestimmten Zeitpunkt den Ausführungsfluss anderswohin im Workflow umzuleiten.  
  
### <a name="using-the-flowchart-activity-designer"></a>Verwenden des Flussdiagramm-Aktivitätsdesigners  
 Die **Flussdiagramm** Aktivitäts-Designer finden Sie in der **Flussdiagramm** Kategorie der **Toolbox**, die erfolgt durch Klicken auf die **Toolbox**Registerkarte die [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Wählen Sie alternativ **Symbolleiste** aus der **Ansicht** Menü- oder STRG + ALT + X.)  
  
 Die **Flussdiagramm** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** und auf die [!INCLUDE[wfd2](../includes/wfd2-md.md)] -Oberfläche ganz egal, wo Aktivitätsdesigner normalerweise platziert werden, entweder als eine Stammaktivität oder als untergeordnetes Element von einer anderen ablaufsteuerungsaktivität. Wenn die **Flussdiagramm** Aktivitäts-Designer wird gelöscht, auf einer leeren [!INCLUDE[wfd2](../includes/wfd2-md.md)] Entwurfsoberfläche erstellt eine <xref:System.Activities.Statements.Flowchart> -Aktivität, die standardmäßig selbst in einer erweiterten Ansicht präsentiert, in dem der Startknoten, die Ausführung startet ist, als grüner Ball dargestellt. Wenn die **Flussdiagramm** Aktivitäts-Designer in einer anderen ablaufsteuerungsaktivität abgelegt wurde, präsentiert er sich in einer minimierten Ansicht, die durch Doppelklicken auf erweitert werden kann, die **Flussdiagramm** Aktivitäts-Designer. Alle Aktivitäten in der **Toolbox** gezogen werden können, direkt auf die **Flussdiagramm** Aktivitäts-Designer, einschließlich Weitere Aktivitäten der ablaufsteuerung.  
  
 Nachdem Sie die verschiedenen Aktivitätsdesigner auf den [!INCLUDE[wfd2](../includes/wfd2-md.md)]-Canvas gezogen haben, können die durch sie dargestellten <xref:System.Activities.Activity>-Objekte miteinander verknüpft werden, um die Reihenfolge der Ausführung anzugeben. Sie erstellen einen Link zwischen einer Quellaktivität und einer Zielaktivität, indem Sie die Maus über den Designer der Quellaktivität bewegen, an dessen beiden Seiten dann quadratische Ziehpunkte angezeigt werden. Klicken Sie auf einen der quadratischen Ziehpunkte, und ziehen Sie ihn bei gedrückter Maustaste auf einen der Ziehpunkte, die um die Zielaktivität angezeigt werden, sobald Sie die Maus über diese Aktivität bewegen. Lassen Sie die Maustaste los, und zwischen beiden Aktivitäten wird ein Link erstellt, der als vom Quelldesigner zum Zieldesigner zeigender Pfeil dargestellt wird.  
  
### <a name="flowchart-activity-properties"></a>Flussdiagrammaktivitätseigenschaften  
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.Flowchart>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaftenraster oder auf der Designeroberfläche bearbeitet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Gibt den Anzeigenamen des Aktivitätsdesigners im Header an. Der Standardwert lautet Flussdiagramm. Der Wert kann bearbeitet werden, der **Eigenschaften** Fenster oder direkt im Header Aktivitätsdesigners.<br /><br /> Obwohl der <xref:System.Activities.Activity.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|  
|<xref:System.Activities.Statements.Flowchart.Variables%2A>|False|Die Auflistung der innerhalb dieses <xref:System.Activities.Statements.Flowchart> gültigen Variablen, mittels derer der Zustand gemeinsam mit seinen untergeordneten Aktivitäten verwendet wird.|  
|<xref:System.Activities.Statements.Flowchart.StartNode%2A>|False|Der <xref:System.Activities.Statements.FlowNode>, der ausgeführt wird, wenn <xref:System.Activities.Statements.Flowchart> startet.|  
|<xref:System.Activities.Statements.Flowchart.Nodes%2A>|False|Enthält die Auflistung der <xref:System.Activities.Statements.FlowNode>-Objekte im <xref:System.Activities.Statements.Flowchart>.|  
  
## <a name="see-also"></a>Siehe auch  
 [Flussdiagramm](../workflow-designer/flowchart-activity-designers.md)   
 [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)   
 [FlowSwitch\<T>](../workflow-designer/flowswitch-t-activity-designer.md)