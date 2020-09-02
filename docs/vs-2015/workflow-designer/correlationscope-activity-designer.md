---
title: CorrelationScope-Aktivitäts Designer | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.CorrelationScope.UI
ms.assetid: 75f20664-9042-464d-8e2b-148d365a2286
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b6ffcfd63d60ab6f085b5cb2a793e8bf17a50d8e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656909"
---
# <a name="correlationscope-activity-designer"></a>CorrelationScope-Aktivitätsdesigner
Der **CorrelationScope** -Aktivitäts Designer wird verwendet, um eine-Aktivität zu erstellen und zu konfigurieren <xref:System.ServiceModel.Activities.CorrelationScope> , die die implizite Verwaltung von untergeordneten Messaging Aktivitäten mithilfe eines- <xref:System.ServiceModel.Activities.CorrelationHandle> Objekts ermöglicht.

## <a name="the-correlationscope-activity"></a>Die CorrelationScope-Aktivität
 Die <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>-Eigenschaft gibt das <xref:System.ServiceModel.Activities.CorrelationHandle>-Handle an, das zum Verwalten der untergeordneten Messagingaktivitäten verwendet wird. Die <xref:System.ServiceModel.Activities.Send>-Aktivität und die <xref:System.ServiceModel.Activities.Receive>-Aktivität, die im <xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>-Objekt enthalten sind, werden so konfiguriert, dass sie die <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>-Eigenschaft der übergeordneten <xref:System.ServiceModel.Activities.CorrelationScope>-Aktivität verwenden, um die Korrelation auszuführen.

### <a name="using-the-correlationscope-activity-designer"></a>Verwenden des CorrelationScope-Aktivitätsdesigners
 Der **CorrelationScope** -Aktivitäts Designer befindet sich in der Kategorie **Messaging** der **Toolbox**, auf die Sie zugreifen können, indem Sie auf der linken Seite von auf die Registerkarte **Toolbox** klicken (Sie können auch im [!INCLUDE[wfd2](../includes/wfd2-md.md)] Menü **Ansicht** den Befehl **Symbolleiste** auswählen oder STRG + ALT + X drücken).

 Der **CorrelationScope** -Aktivitäts Designer kann aus der **Toolbox** gezogen und auf der- [!INCLUDE[wfd2](../includes/wfd2-md.md)] Oberfläche abgelegt werden. Dadurch wird eine- <xref:System.ServiceModel.Activities.CorrelationScope> Aktivität mit dem **Display Name** -Standardwert von CorrelationScope erstellt. Der <xref:System.Activities.Activity.DisplayName%2A> kann im Header des **CorrelationScope** -Aktivitäts Designers oder im Feld **Display Name** des **Eigenschaften** Fensters bearbeitet werden.

 Um die von untergeordneten <xref:System.ServiceModel.Activities.CorrelationHandle> Messaging Aktivitäten verwendete anzugeben, klicken Sie im **Eigenschaften** Fenster neben dem Feld **correlateswith** auf die Schaltfläche Ellipse, um das Dialogfeld **Ausdrucks-Editor** anzuzeigen. Diese Eigenschaft kann auch in der Aktivitätsdesigneroberfläche festgelegt werden.

 Die innerhalb der Korrelation enthaltenen Aktivitäten werden durch Löschen Ihrer Designer innerhalb des Felds **Body** innerhalb des **CorrelationScope** -Designers angegeben.

### <a name="the-correlationscope-properties"></a>Die CorrelationScope-Eigenschaften
 In der folgenden Tabelle werden die <xref:System.ServiceModel.Activities.CorrelationScope>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können entweder im **Eigenschaften** Fenster oder auf der [!INCLUDE[wfd2](../includes/wfd2-md.md)] Designer Oberfläche und häufig in beidem bearbeitet werden.

|Eigenschaftenname|Erforderlich|Verbrauch|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Falsch|Der optionale Anzeigename der <xref:System.ServiceModel.Activities.InitializeCorrelation>-Aktivität.|
|<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>|Falsch|Gibt das <xref:System.ServiceModel.Activities.CorrelationHandle>-Handle an, das zum Verwalten der untergeordneten Messagingaktivitäten verwendet wird. Wenn Sie diese Eigenschaft nicht festlegen, erstellt <xref:System.ServiceModel.Activities.CorrelationScope> automatisch einen impliziten <xref:System.ServiceModel.Activities.CorrelationHandle>.|
|<xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>|Falsch|Gibt die Aktivitäten im Bereich der Korrelation an.|

## <a name="see-also"></a>Weitere Informationen
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) [Receive](../workflow-designer/receive-activity-designer.md) [receiveandsendreply](../workflow-designer/receiveandsendreply-template-designer.md) [Send](../workflow-designer/send-activity-designer.md) [sendandreceivereply](../workflow-designer/sendandreceivereply-template-designer.md) [transactedreceivescope](../workflow-designer/transactedreceivescope-activity-designer.md)