---
title: Workflow-Designer - Pick-Aktivitätsdesigner
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Pick.UI
ms.assetid: 642c0a47-1b47-45de-a19a-ca0606cedd7a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f664ac3a22b91780d392e0fef3224cd80b1e7919
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31975431"
---
# <a name="pick-activity-designer"></a>Pick-Aktivitätsdesigner

Die <xref:System.Activities.Statements.Pick>-Aktivität stellt eine ereignisbasierte Ablaufsteuerung bereit. Die Aktivität führt eine von mehreren Verzweigungen als Reaktion auf die Auslösung eines Ereignisses aus.

## <a name="the-pick-activity"></a>Die Pick-Aktivität

Eine <xref:System.Activities.Statements.Pick>-Aktivität enthält eine Auflistung von <xref:System.Activities.Statements.PickBranch>-Objekten, von denen die <xref:System.Activities.Statements.Pick>-Aktivität eines ausführen kann, wenn sie ein Ereignis empfängt, das als Trigger dient. Auf diese Weise stellt Windows Workflow-Designer das ereignisbasierte flusssteuerungsmodellierung bereit. Jede <xref:System.Activities.Statements.PickBranch> enthält einen <xref:System.Activities.Statements.PickBranch.Trigger%2A> und eine <xref:System.Activities.Statements.PickBranch.Action%2A>. Am Anfang einer <xref:System.Activities.Statements.Pick> aktivitätsausführung, sämtliche triggeraktivitäten der der <xref:System.Activities.Statements.PickBranch> -Elementen geplant. Wenn die erste Aktivität abgeschlossen wird, wird die entsprechende Aktionsaktivität geplant, und alle anderen Triggeraktivitäten werden abgebrochen.

### <a name="how-to-use-the-pick-activity-designer"></a>So verwenden Sie den Pick-Aktivitätsdesigner

Die **auswählen** Aktivitäts-Designer finden Sie in der **Control Flow** Kategorie der **Toolbox**, die erfolgt durch Klicken auf die **Toolbox**Registerkarte Workflow-Designer (Wählen Sie alternativ **Symbolleiste** aus der **Ansicht** Menüs oder STRG + ALT + X.)

Die **auswählen** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** und sich der Workflow-Designer-Oberfläche gelöscht wird, wo Aktivitätsdesigner normalerweise, z. B. innerhalb eines platziert werden eine  **Sequenz** Aktivitäts-Designer. Nach dem in den Workflow-Designer ablegen, erstellt er eine <xref:System.Activities.Statements.Pick> -Aktivität, die standardmäßig zwei leere <xref:System.Activities.Statements.PickBranch> Aktivitäten als Elemente mit den Anzeigenamen von Branch1 und branch2 enthält. Die jeweiligen <xref:System.Activities.Statements.PickBranch.DisplayName%2A> Eigenschaftswerte können bearbeitet werden, der **PickBranch** Aktivitäts-Designer-Header oder innerhalb der **Eigenschaften** für jede Verzweigung.

Es gibt zwei Möglichkeiten zum Hinzufügen von <xref:System.Activities.Statements.PickBranch> auf die Auflistung von Aktivitäten eine <xref:System.Activities.Statements.Pick> Objekt: Drag & Drop die **PickBranch** -Designer aus der **Toolbox** oder indem Sie im Kontextmenü den Befehl aus innerhalb der **Pick** Entwurfsoberfläche angezeigt. Einzelheiten finden Sie in der [PickBranch](../workflow-designer/pickbranch-activity-designer.md) Thema. Beachten Sie, dass als einziges Element platziert werden eine **auswählen** Aktivitäts-Designer ist ein **PickBranch** Aktivitäts-Designer.

### <a name="pick-activity-properties-in-the-workflow-designer"></a>Eigenschaften für Pick-Aktivitäten im Workflow-Designer

In der folgenden Tabelle werden die <xref:System.Activities.Statements.Pick>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaftenraster oder auf der Designeroberfläche bearbeitet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Gibt den benutzerfreundlichen Namen der <xref:System.Activities.Statements.Pick>Aktivität im Header an. Der Standardwert lautet Pick. Der Wert kann im Eigenschaftenraster oder direkt im Header des Aktivitätsdesigners bearbeitet werden.<br /><br /> Obwohl der <xref:System.Activities.Activity.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|

## <a name="see-also"></a>Siehe auch

- [Ablaufsteuerung](../workflow-designer/control-flow-activity-designers.md)
- [Auswahlaktivität](/dotnet/framework/windows-workflow-foundation/pick-activity)
- [Verwenden der Pick-Aktivität](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)