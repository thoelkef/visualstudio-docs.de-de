---
title: Workflow-Designer - Pick-Aktivitätsdesigner
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Statements.Pick.UI
ms.assetid: 642c0a47-1b47-45de-a19a-ca0606cedd7a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3afd20b75bdb2c00317f9acf6ec6adcd12f6f949
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/26/2019
ms.locfileid: "55069780"
---
# <a name="pick-activity-designer"></a>Pick-Aktivitätsdesigner

Die <xref:System.Activities.Statements.Pick>-Aktivität stellt eine ereignisbasierte Ablaufsteuerung bereit. Die Aktivität führt eine von mehreren Verzweigungen als Reaktion auf die Auslösung eines Ereignisses aus.

## <a name="the-pick-activity"></a>Die Pick-Aktivität

Eine <xref:System.Activities.Statements.Pick>-Aktivität enthält eine Auflistung von <xref:System.Activities.Statements.PickBranch>-Objekten, von denen die <xref:System.Activities.Statements.Pick>-Aktivität eines ausführen kann, wenn sie ein Ereignis empfängt, das als Trigger dient. Auf diese Weise stellt die Workflow-Designer das ereignisbasierte ablaufsteuerungsmodellierung bereit. Jede <xref:System.Activities.Statements.PickBranch> enthält einen <xref:System.Activities.Statements.PickBranch.Trigger%2A> und eine <xref:System.Activities.Statements.PickBranch.Action%2A>. Am Anfang einer <xref:System.Activities.Statements.Pick> aktivitätsausführung, sämtliche triggeraktivitäten der der <xref:System.Activities.Statements.PickBranch> -Elementen geplant. Wenn die erste Aktivität abgeschlossen wird, wird die entsprechende Aktionsaktivität geplant, und alle anderen Triggeraktivitäten werden abgebrochen.

### <a name="how-to-use-the-pick-activity-designer"></a>So verwenden Sie den Pick-Aktivitätsdesigner

Zugriff die **auswählen** Aktivitäts-Designer in der **Ablaufsteuerung** Kategorie der **Toolbox**. Die **auswählen** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** und sich der Workflow-Designer-Oberfläche gelöscht werden, wo Aktivitätsdesigner normalerweise, z. B. innerhalb eines platziert werden eine  **Sequenz** Aktivitäts-Designer. Nach dem Ablegen in Workflow-Designer, erstellt er eine <xref:System.Activities.Statements.Pick> -Aktivität, die standardmäßig zwei leere enthält <xref:System.Activities.Statements.PickBranch> Aktivitäten als Elemente mit den Anzeigenamen von Branch1 und Branch2. Die jeweiligen <xref:System.Activities.Statements.PickBranch.DisplayName%2A> Eigenschaftswerte können bearbeitet werden, der **PickBranch** Aktivitäts-Designer-Header oder in der **Eigenschaften** für jeden Branch.

Es gibt zwei Möglichkeiten zum Hinzufügen von <xref:System.Activities.Statements.PickBranch> -Aktivitäten der Auflistung eine <xref:System.Activities.Statements.Pick> Objekt: Ziehen und Ablegen der **PickBranch** -Designer aus der **Toolbox** oder mit der rechten Maustaste innerhalb der **auswählen** Entwurfsoberfläche. Weitere Informationen finden Sie unter den [PickBranch](../workflow-designer/pickbranch-activity-designer.md) Thema. Beachten Sie, dass als einziges Element platziert werden kann eine **auswählen** Aktivitäts-Designer eine **PickBranch** Aktivitäts-Designer.

### <a name="pick-activity-properties-in-the-workflow-designer"></a>Eigenschaften für Pick-Aktivitäten im Workflow-Designer

In der folgenden Tabelle werden die <xref:System.Activities.Statements.Pick>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaftenraster oder auf der Designeroberfläche bearbeitet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Gibt den benutzerfreundlichen Namen der <xref:System.Activities.Statements.Pick>Aktivität im Header an. Der Standardwert lautet Pick. Der Wert kann im Eigenschaftenraster oder direkt im Header des Aktivitätsdesigners bearbeitet werden.<br /><br /> Obwohl der <xref:System.Activities.Activity.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|

## <a name="see-also"></a>Siehe auch

- [Ablaufsteuerung](../workflow-designer/control-flow-activity-designers.md)
- [Auswahlaktivität](/dotnet/framework/windows-workflow-foundation/pick-activity)
- [Verwenden der Pick-Aktivität](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)