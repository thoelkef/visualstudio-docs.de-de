---
title: "CorrelationScope-Aktivitätsdesigner | Microsoft Docs"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.CorrelationScope.UI
ms.assetid: 75f20664-9042-464d-8e2b-148d365a2286
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 3a8798e653148e07baff5f0fb70c2ff56f7d4a16
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2018
---
# <a name="correlationscope-activity-designer"></a>CorrelationScope-Aktivitätsdesigner
Die **CorrelationScope** Aktivitäts-Designer dient zum Erstellen und Konfigurieren einer <xref:System.ServiceModel.Activities.CorrelationScope> Aktivität, die implizite Verwaltung untergeordneter messagingaktivitäten mithilfe einer <xref:System.ServiceModel.Activities.CorrelationHandle> Objekt.

## <a name="the-correlationscope-activity"></a>Die CorrelationScope-Aktivität
 Die <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>-Eigenschaft gibt das <xref:System.ServiceModel.Activities.CorrelationHandle>-Handle an, das zum Verwalten der untergeordneten Messagingaktivitäten verwendet wird. Die <xref:System.ServiceModel.Activities.Send>-Aktivität und die <xref:System.ServiceModel.Activities.Receive>-Aktivität, die im <xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>-Objekt enthalten sind, werden so konfiguriert, dass sie die <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>-Eigenschaft der übergeordneten <xref:System.ServiceModel.Activities.CorrelationScope>-Aktivität verwenden, um die Korrelation auszuführen.

### <a name="using-the-correlationscope-activity-designer"></a>Verwenden des CorrelationScope-Aktivitätsdesigners
 Die **CorrelationScope** Aktivitäts-Designer finden Sie in der **Messaging** Kategorie der **Toolbox**, die erfolgt durch Klicken auf die **Toolbox** auf der linken Seite der Registerkarte die [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (Wählen Sie alternativ **Symbolleiste** aus der **Ansicht** Menüs oder STRG + ALT + X drücken.)

 Die **CorrelationScope** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** gezogen und auf die [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] Oberfläche. Dies erstellt eine <xref:System.ServiceModel.Activities.CorrelationScope> -Aktivität mit dem standardmäßigen **DisplayName** des CorrelationScope. Die <xref:System.Activities.Activity.DisplayName%2A> kann im Header des bearbeitet werden die **CorrelationScope** Aktivitäts-Designer oder in der **DisplayName** im Feld der **Eigenschaften** Fenster.

 Angeben der <xref:System.ServiceModel.Activities.CorrelationHandle> von untergeordneten messagingaktivitäten verwendet, und klicken Sie auf die Schaltfläche mit den Auslassungspunkten neben der **CorrelatesWith** Feld **Eigenschaften** Fenster zum Anzeigen der **Ausdrucks-Editor**  (Dialogfeld). Diese Eigenschaft kann auch in der Aktivitätsdesigneroberfläche festgelegt werden.

 Die Aktivitäten, die innerhalb der Korrelation werden angegeben, indem ihre Designer innerhalb der **Text** Feld innerhalb der **CorrelationScope** Designer.

### <a name="the-correlationscope-properties"></a>Die CorrelationScope-Eigenschaften
 In der folgenden Tabelle werden die <xref:System.ServiceModel.Activities.CorrelationScope>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können werden bearbeitet, entweder in **Eigenschaften** Fenster oder auf [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] -Designeroberfläche und oft in beiden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Der optionale Anzeigename der <xref:System.ServiceModel.Activities.InitializeCorrelation>-Aktivität.|
|<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>|False|Gibt das <xref:System.ServiceModel.Activities.CorrelationHandle>-Handle an, das zum Verwalten der untergeordneten Messagingaktivitäten verwendet wird. Wenn Sie diese Eigenschaft nicht festlegen, erstellt <xref:System.ServiceModel.Activities.CorrelationScope> automatisch einen impliziten <xref:System.ServiceModel.Activities.CorrelationHandle>.|
|<xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>|False|Gibt die Aktivitäten im Bereich der Korrelation an.|

## <a name="see-also"></a>Siehe auch

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Empfangen](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Senden](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)