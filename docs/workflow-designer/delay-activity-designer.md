---
title: "Verzögern der Aktivitäts-Designer | Microsoft Docs"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Delay.UI
ms.assetid: f51742a8-2c9a-47d1-8a23-18459d03ae19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: cddf4be42d05ebfc3c2df3e64f011b93673eead6
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2018
---
# <a name="delay-activity-designer"></a>Delay-Aktivitätsdesigner
Die **Verzögerung** Aktivitäts-Designer dient zum Erstellen und Konfigurieren einer <xref:System.Activities.Statements.Delay> Aktivität.

## <a name="the-delay-activity"></a>Die Delay-Aktivität
 Die <xref:System.Activities.Statements.Delay>-Aktivität verzögert die Ausführung eines Workflows während einer bestimmten Zeitspanne.

### <a name="using-the-delay-activity-designer"></a>Verwenden des Delay-Aktivitätsdesigners
 Die **Verzögerung** Aktivitäts-Designer finden Sie in der **primitive** Kategorie der **Toolbox**, die erfolgt durch Klicken auf die **Toolbox**auf der Registerkarte die [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (Wählen Sie alternativ **Symbolleiste** aus der **Ansicht** Menüs oder STRG + ALT + X drücken.)

 Die **Verzögerung** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** gezogen und auf die [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] -Oberfläche ablegen, wo Aktivitäten normalerweise platziert werden, z. B. in einem <xref:System.Activities.Statements.Sequence>. Dadurch wird eine <xref:System.Activities.Statements.Delay>-Aktivität mit dem standardmäßigen <xref:System.Activities.Activity.DisplayName%2A> Delay erstellt. Die <xref:System.Activities.Activity.DisplayName%2A> kann im Header des bearbeitet werden die **Verzögerung** Aktivitäts-Designer oder in der **DisplayName** Feld des Eigenschaftenrasters.

### <a name="the-delay-properties"></a>Die Delay-Eigenschaften
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.Delay>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaftenraster, einige davon auf der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]-Designeroberfläche bearbeitet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Der Anzeigename der <xref:System.Activities.Statements.Delay>-Aktivität. Der Standardwert lautet Delay. Obwohl der <xref:System.Activities.Activity.DisplayName%2A>-Wert nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|
|<xref:System.Activities.Statements.Delay.Duration%2A>|True|Die Zeitspanne, um die der Workflow verzögert werden soll. Diese Eigenschaft wird im Eigenschaftenraster festgelegt. Geben Sie in entweder einen literalen <xref:System.TimeSpan>-Wert im Format 00:00:00 oder einem Visual Basic-Ausdruck ein, um die Zeitspanne anzugeben.|

## <a name="see-also"></a>Siehe auch

- [Primitive](../workflow-designer/primitives-activity-designers.md)
- [Zuweisen](../workflow-designer/assign-activity-designer.md)
- [Delay-Aktivitätsdesigner](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)