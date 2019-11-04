---
title: Terminateworkflow-Aktivitäts Designer | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TerminateWorkflow.UI
ms.assetid: 08e632ed-0724-4fb4-9df1-f8d443eaf0ac
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c204c14818a9c6e6fb0a46e6234b550838f3b1a4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72607094"
---
# <a name="terminateworkflow-activity-designer"></a>TerminateWorkflow-Aktivitätsdesigner
Der **terminateworkflow** -Aktivitäts Designer wird verwendet, um eine <xref:System.Activities.Statements.TerminateWorkflow>-Aktivität zu erstellen und zu konfigurieren.

## <a name="the-terminateworkflow-activity"></a>Die TerminateWorkflow-Aktivität
 Mit der <xref:System.Activities.Statements.TerminateWorkflow>-Aktivität können Sie die Ausführung eines Workflows beenden.

### <a name="using-the-terminateworkflow-activity-designer"></a>Verwenden des TerminateWorkflow-Aktivitätsdesigners
 Der **terminateworkflow** -Aktivitäts Designer befindet sich in der Kategorie **Laufzeit** der **Toolbox**, auf die Sie zugreifen können, indem Sie auf die Registerkarte **Toolbox** klicken (Sie können auch im Menü **Ansicht** die Option **Toolbox** auswählen oder STRG + ALT + X.)

 Der **terminateworkflow** -Aktivitäts Designer kann aus der **Toolbox** gezogen und auf der [!INCLUDE[wfd2](../includes/wfd2-md.md)]-Oberfläche dort abgelegt werden, wo Aktivitäten normalerweise platziert werden, z. b. innerhalb eines <xref:System.Activities.Statements.Sequence>. Dadurch wird eine <xref:System.Activities.Statements.TerminateWorkflow>-Aktivität mit dem standardmäßigen **Display Name** terminateworkflow erstellt. Der <xref:System.Activities.Activity.DisplayName%2A> kann in der Kopfzeile des **terminateworkflow** -Aktivitäts Designers oder im Feld **Display Name** des Eigenschaften Rasters bearbeitet werden.

### <a name="the-terminateworkflow-properties"></a>Die TerminateWorkflow-Eigenschaften
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.TerminateWorkflow>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaftenraster bearbeitet werden, einige davon können auch auf der [!INCLUDE[wfd2](../includes/wfd2-md.md)]-Oberfläche bearbeitet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Der Anzeigename der <xref:System.Activities.Statements.TerminateWorkflow>-Aktivität. Der Standardwert ist TerminateWorkflow. Obwohl der Anzeigename nicht unbedingt erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|
|<xref:System.Activities.Statements.TerminateWorkflow.Exception%2A>|False|Die Ausnahme, die beim Beenden des Workflows ausgelöst werden soll. Legen Sie diese Eigenschaft im Eigenschaftenraster fest.|
|<xref:System.Activities.Statements.TerminateWorkflow.Reason%2A>|False|Die Ursache für das Beenden des Workflows. Legen Sie diese Eigenschaft im Eigenschaftenraster fest.|

## <a name="see-also"></a>Siehe auch
 [Laufzeit](../workflow-designer/runtime-activity-designers.md) [beibehalten](../workflow-designer/persist-activity-designer.md)