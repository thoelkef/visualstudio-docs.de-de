---
title: Workflow-Designer-terminateworkflow-Aktivitäts Designer
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TerminateWorkflow.UI
ms.assetid: 08e632ed-0724-4fb4-9df1-f8d443eaf0ac
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 078dfb43b5960580327448627a30eec20297d9f3
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2020
ms.locfileid: "76111781"
---
# <a name="terminateworkflow-activity-designer"></a>TerminateWorkflow-Aktivitätsdesigner

Der **terminateworkflow** -Aktivitäts Designer wird verwendet, um eine <xref:System.Activities.Statements.TerminateWorkflow>-Aktivität zu erstellen und zu konfigurieren.

## <a name="the-terminateworkflow-activity"></a>Die TerminateWorkflow-Aktivität

Mit der <xref:System.Activities.Statements.TerminateWorkflow>-Aktivität können Sie die Ausführung eines Workflows beenden.

### <a name="using-the-terminateworkflow-activity-designer"></a>Verwenden des TerminateWorkflow-Aktivitätsdesigners

Der **terminateworkflow** -Aktivitäts Designer befindet sich in der Kategorie **Laufzeit** der **Toolbox**, auf die Sie zugreifen können, indem Sie auf die Registerkarte **Toolbox** klicken (Sie können auch im Menü **Ansicht** die Option **Toolbox** auswählen oder STRG + ALT + X drücken).

Der **terminateworkflow** -Aktivitäts Designer kann aus der **Toolbox** gezogen und auf der Workflow-Designer-Oberfläche dort abgelegt werden, wo Aktivitäten normalerweise platziert werden, z. b. innerhalb eines <xref:System.Activities.Statements.Sequence>. Dadurch wird eine <xref:System.Activities.Statements.TerminateWorkflow>-Aktivität mit dem standardmäßigen **Display Name** terminateworkflow erstellt. Der <xref:System.Activities.Activity.DisplayName%2A> kann in der Kopfzeile des **terminateworkflow** -Aktivitäts Designers oder im Feld **Display Name** des Eigenschaften Rasters bearbeitet werden.

### <a name="the-terminateworkflow-properties"></a>Die TerminateWorkflow-Eigenschaften

In der folgenden Tabelle werden die <xref:System.Activities.Statements.TerminateWorkflow>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaften Raster bearbeitet werden, und einige von Ihnen können auf Workflow-Designer Oberfläche bearbeitet werden.

|Eigenschaftsname|Erforderlich|Verwendungs-|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falsch|Der Anzeigename der <xref:System.Activities.Statements.TerminateWorkflow>-Aktivität. Der Standardwert ist TerminateWorkflow. Obwohl der Anzeigename nicht unbedingt erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|
|<xref:System.Activities.Statements.TerminateWorkflow.Exception%2A>|Falsch|Die Ausnahme, die beim Beenden des Workflows ausgelöst werden soll. Legen Sie diese Eigenschaft im Eigenschaftenraster fest.|
|<xref:System.Activities.Statements.TerminateWorkflow.Reason%2A>|Falsch|Die Ursache für das Beenden des Workflows. Legen Sie diese Eigenschaft im Eigenschaftenraster fest.|

## <a name="see-also"></a>Siehe auch

- [Laufzeit](../workflow-designer/runtime-activity-designers.md)
- [Persist](../workflow-designer/persist-activity-designer.md)
