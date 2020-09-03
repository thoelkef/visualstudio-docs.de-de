---
title: Sequence-Aktivitäts Designer | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Sequence.UI
ms.assetid: 51c8d3cb-4d43-458f-9631-b63755f9ac94
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3acf02ab478eee244557e04f19f78ba2d5f0b950
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663260"
---
# <a name="sequence-activity-designer"></a>Sequence-Aktivitätsdesigner
Die <xref:System.Activities.Statements.Sequence>-Aktivität enthält eine geordnete Auflistung von untergeordneten Aktivitäten, die in der angegebenen Reihenfolge ausgeführt werden.

 Eine andere Möglichkeit, eine Gruppe von Aktivitäten in einer bestimmten Reihenfolge auszuführen, besteht in der Verwendung einer <xref:System.Activities.Statements.Flowchart>-Aktivität. Verwenden Sie ggf. das Flussdiagramm, wenn ein einfacher Verzweigungs-oder Schleifen Programmfluss vorhanden ist, den Sie [Diagramms](../workflow-designer/flowchart-activity-designer.md) modellieren möchten.

## <a name="using-the-sequence-activity-designer"></a>Verwenden des Sequence-Aktivitätsdesigners
 Ziehen Sie zum Hinzufügen einer- <xref:System.Activities.Statements.Sequence> Aktivität den **Sequence** -Aktivitäts Designer aus der **Toolbox** , und legen Sie ihn auf der- [!INCLUDE[wfd1](../includes/wfd1-md.md)] Oberfläche ab. Um dieser Aktivität eine untergeordnete Aktivität hinzuzufügen <xref:System.Activities.Statements.Sequence> , ziehen Sie eine andere Aktivität aus der **Toolbox** , und legen Sie Sie auf dem Dreieck im Feld mit dem Hinweis Text "Aktivität hier ablegen" ab.

### <a name="sequence-activity-properties-in-the-workflow-designer"></a>Eigenschaften der Sequence-Aktivität im Workflow-Designer
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.Sequence>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaftenraster oder auf der Designeroberfläche bearbeitet werden.

|Eigenschaftenname|Erforderlich|Verbrauch|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Falsch|Gibt den benutzerfreundlichen Namen der <xref:System.Activities.Statements.Sequence>Aktivität im Header an. Der Standardwert ist Sequence. Der Wert kann im Eigenschaftenraster oder direkt im Header des Aktivitätsdesigners bearbeitet werden.<br /><br /> Obwohl der <xref:System.Activities.Activity.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|

## <a name="see-also"></a>Weitere Informationen
 Fluss [Diagramm](../workflow-designer/flowchart-activity-designer.md) - [Ablauf Steuerung](../workflow-designer/control-flow-activity-designers.md)