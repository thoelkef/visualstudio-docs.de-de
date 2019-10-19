---
title: Delay-Aktivitäts Designer | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Delay.UI
ms.assetid: f51742a8-2c9a-47d1-8a23-18459d03ae19
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a47279bc68503ba645fea3ef23a04ce9d5ef4c41
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656799"
---
# <a name="delay-activity-designer"></a>Delay-Aktivitätsdesigner
Der **Delay** -Aktivitäts Designer wird verwendet, um eine <xref:System.Activities.Statements.Delay>-Aktivität zu erstellen und zu konfigurieren.

## <a name="the-delay-activity"></a>Die Delay-Aktivität
 Die <xref:System.Activities.Statements.Delay>-Aktivität verzögert die Ausführung eines Workflows während einer bestimmten Zeitspanne.

### <a name="using-the-delay-activity-designer"></a>Verwenden des Delay-Aktivitätsdesigners
 Der **Verzögerungs** Aktivitäts Designer befindet sich in der Kategorie **Primitives** der **Toolbox**, auf die Sie zugreifen können, indem Sie im [!INCLUDE[wfd2](../includes/wfd2-md.md)] auf die Registerkarte **Toolbox** klicken (Sie können auch im Menü **Ansicht** den Befehl **Symbolleiste** auswählen oder STRG + ALT + X.)

 Der **Verzögerungs** Aktivitäts Designer kann aus der **Toolbox** gezogen und auf der [!INCLUDE[wfd2](../includes/wfd2-md.md)]-Oberfläche dort abgelegt werden, wo Aktivitäten normalerweise platziert werden, z. b. innerhalb eines <xref:System.Activities.Statements.Sequence>. Dadurch wird eine <xref:System.Activities.Statements.Delay>-Aktivität mit dem standardmäßigen <xref:System.Activities.Activity.DisplayName%2A> Delay erstellt. Der <xref:System.Activities.Activity.DisplayName%2A> kann im Header des **Delay** -Aktivitäts Designers oder im Feld **Display Name** des Eigenschaften Rasters bearbeitet werden.

### <a name="the-delay-properties"></a>Die Delay-Eigenschaften
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.Delay>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaftenraster, einige davon auf der [!INCLUDE[wfd2](../includes/wfd2-md.md)]-Designeroberfläche bearbeitet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Der Anzeigename der <xref:System.Activities.Statements.Delay>-Aktivität. Der Standardwert lautet Delay. Obwohl der <xref:System.Activities.Activity.DisplayName%2A>-Wert nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|
|<xref:System.Activities.Statements.Delay.Duration%2A>|True|Die Zeitspanne, um die der Workflow verzögert werden soll. Diese Eigenschaft wird im Eigenschaftenraster festgelegt. Geben Sie in entweder einen literalen <xref:System.TimeSpan>-Wert im Format 00:00:00 oder einem Visual Basic-Ausdruck ein, um die Zeitspanne anzugeben.|

## <a name="see-also"></a>Siehe auch
 [Primitives](../workflow-designer/primitives-activity-designers.md) [assign](../workflow-designer/assign-activity-designer.md) - [Aktivitäts Designer](../workflow-designer/delay-activity-designer.md) [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md) [Write teline](../workflow-designer/writeline-activity-designer.md)