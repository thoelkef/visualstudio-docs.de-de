---
title: "Sequenzieren der Aktivitäts-Designer | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.Sequence.UI
ms.assetid: 51c8d3cb-4d43-458f-9631-b63755f9ac94
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 51f138d17c2b0f8d8a483ef09c298d1dbbf9345c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="sequence-activity-designer"></a>Sequence-Aktivitätsdesigner
Die <xref:System.Activities.Statements.Sequence>-Aktivität enthält eine geordnete Auflistung von untergeordneten Aktivitäten, die in der angegebenen Reihenfolge ausgeführt werden.  
  
 Eine andere Möglichkeit, eine Gruppe von Aktivitäten in einer bestimmten Reihenfolge auszuführen, besteht in der Verwendung einer <xref:System.Activities.Statements.Flowchart>-Aktivität. Erwägen Sie die [Flussdiagramm](../workflow-designer/flowchart-activity-designer.md) Wenn stehen Ihnen eine einfache Verzweigen oder Schleifen Programmfluss, die Sie Sternmuster modellieren möchten.  
  
## <a name="using-the-sequence-activity-designer"></a>Verwenden des Sequence-Aktivitätsdesigners  
 Hinzufügen einer <xref:System.Activities.Statements.Sequence> Aktivität, ziehen Sie die **Sequenz** Aktivitäts-Designer aus der **Toolbox** und legen ihn auf die [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] Oberfläche. Hinzufügen eine untergeordneten Aktivität <xref:System.Activities.Statements.Sequence> Aktivität, ziehen Sie eine andere Aktivität aus der **Toolbox** und legen ihn auf dem Dreieck im Feld mit dem Hinweistext "Aktivität hier ablegen".  
  
### <a name="sequence-activity-properties-in-the-workflow-designer"></a>Eigenschaften der Sequence-Aktivität im Workflow-Designer  
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.Sequence>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaftenraster oder auf der Designeroberfläche bearbeitet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Gibt den benutzerfreundlichen Namen der <xref:System.Activities.Statements.Sequence>Aktivität im Header an. Der Standardwert ist Sequence. Der Wert kann im Eigenschaftenraster oder direkt im Header des Aktivitätsdesigners bearbeitet werden.<br /><br /> Obwohl der <xref:System.Activities.Activity.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|  
  
## <a name="see-also"></a>Siehe auch  
 [Flussdiagramm](../workflow-designer/flowchart-activity-designer.md)   
 [Ablaufsteuerung](../workflow-designer/control-flow-activity-designers.md)