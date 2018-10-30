---
title: Workflow-Designer - Sequence-Aktivitätsdesigner
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Sequence.UI
ms.assetid: 51c8d3cb-4d43-458f-9631-b63755f9ac94
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 288e184f2ae2b4df74860a2cd8066d00e02a44c2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49950588"
---
# <a name="sequence-activity-designer"></a>Sequence-Aktivitätsdesigner

Die <xref:System.Activities.Statements.Sequence>-Aktivität enthält eine geordnete Auflistung von untergeordneten Aktivitäten, die in der angegebenen Reihenfolge ausgeführt werden.

Eine andere Möglichkeit, eine Gruppe von Aktivitäten in einer bestimmten Reihenfolge auszuführen, besteht in der Verwendung einer <xref:System.Activities.Statements.Flowchart>-Aktivität. Erwägen Sie die Verwendung der [Flussdiagramm](../workflow-designer/flowchart-activity-designer.md) , wenn Sie haben eine einfache Verzweigung oder Programmablauf an, die Sie einer Schleife graphisch modellieren möchten.

## <a name="using-the-sequence-activity-designer"></a>Verwenden des Sequence-Aktivitätsdesigners

Hinzufügen einer <xref:System.Activities.Statements.Sequence> -Aktivität ziehen Sie die **Sequenz** Aktivitäts-Designer aus der **Toolbox** und legen Sie sie an der Oberfläche des Workflow-Designer. Zum Hinzufügen einer untergeordneten Aktivität <xref:System.Activities.Statements.Sequence> -Aktivität, ziehen Sie eine andere Aktivität aus der **Toolbox** und legen Sie es auf dem Dreieck im Feld mit dem Hinweistext "Aktivität hier ablegen".

### <a name="sequence-activity-properties-in-the-workflow-designer"></a>Eigenschaften der Sequence-Aktivität im Workflow-Designer

In der folgenden Tabelle werden die <xref:System.Activities.Statements.Sequence>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaftenraster oder auf der Designeroberfläche bearbeitet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Gibt den benutzerfreundlichen Namen der <xref:System.Activities.Statements.Sequence>Aktivität im Header an. Der Standardwert ist Sequence. Der Wert kann im Eigenschaftenraster oder direkt im Header des Aktivitätsdesigners bearbeitet werden.<br /><br /> Obwohl der <xref:System.Activities.Activity.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|

## <a name="see-also"></a>Siehe auch

- [Flussdiagramm](../workflow-designer/flowchart-activity-designer.md)
- [Ablaufsteuerung](../workflow-designer/control-flow-activity-designers.md)