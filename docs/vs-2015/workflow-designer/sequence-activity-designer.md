---
title: Sequence-Aktivitätsdesigner | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Sequence.UI
ms.assetid: 51c8d3cb-4d43-458f-9631-b63755f9ac94
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: d3f005ba61ad93eb2b1dd2663831b33a133b64e7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47524677"
---
# <a name="sequence-activity-designer"></a>Sequence-Aktivitätsdesigner
Die <xref:System.Activities.Statements.Sequence>-Aktivität enthält eine geordnete Auflistung von untergeordneten Aktivitäten, die in der angegebenen Reihenfolge ausgeführt werden.  
  
 Eine andere Möglichkeit, eine Gruppe von Aktivitäten in einer bestimmten Reihenfolge auszuführen, besteht in der Verwendung einer <xref:System.Activities.Statements.Flowchart>-Aktivität. Erwägen Sie die Verwendung der [Flussdiagramm](../workflow-designer/flowchart-activity-designer.md) , wenn Sie haben eine einfache Verzweigung oder Programmablauf an, die Sie einer Schleife graphisch modellieren möchten.  
  
## <a name="using-the-sequence-activity-designer"></a>Verwenden des Sequence-Aktivitätsdesigners  
 Hinzufügen einer <xref:System.Activities.Statements.Sequence> -Aktivität ziehen Sie die **Sequenz** Aktivitäts-Designer aus der **Toolbox** und legen ihn auf die [!INCLUDE[wfd1](../includes/wfd1-md.md)] Oberfläche. Zum Hinzufügen einer untergeordneten Aktivität <xref:System.Activities.Statements.Sequence> -Aktivität, ziehen Sie eine andere Aktivität aus der **Toolbox** und legen Sie es auf dem Dreieck im Feld mit dem Hinweistext "Aktivität hier ablegen".  
  
### <a name="sequence-activity-properties-in-the-workflow-designer"></a>Eigenschaften der Sequence-Aktivität im Workflow-Designer  
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.Sequence>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaftenraster oder auf der Designeroberfläche bearbeitet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Gibt den benutzerfreundlichen Namen der <xref:System.Activities.Statements.Sequence>Aktivität im Header an. Der Standardwert ist Sequence. Der Wert kann im Eigenschaftenraster oder direkt im Header des Aktivitätsdesigners bearbeitet werden.<br /><br /> Obwohl der <xref:System.Activities.Activity.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|  
  
## <a name="see-also"></a>Siehe auch  
 [Flussdiagramm](../workflow-designer/flowchart-activity-designer.md)   
 [Ablaufsteuerung](../workflow-designer/control-flow-activity-designers.md)