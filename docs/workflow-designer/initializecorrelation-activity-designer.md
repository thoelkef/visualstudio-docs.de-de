---
title: Workflow-Designer-InitializeCorrelation-Aktivitäts Designer
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.InitializeCorrelation.UI
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 98a9a6bccb6eab2c4565a717daa897f93dbe8f53
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650222"
---
# <a name="initializecorrelation-activity-designer"></a>InitializeCorrelation-Aktivitätsdesigner

Der **InitializeCorrelation** -Aktivitäts Designer wird verwendet, um eine <xref:System.ServiceModel.Activities.InitializeCorrelation>-Aktivität zu erstellen und zu konfigurieren. Die <xref:System.ServiceModel.Activities.InitializeCorrelation>-Aktivität stellt vor dem Senden oder empfangen eine Korrelation zwischen den Nachrichten her.

## <a name="the-initializecorrelation-activity"></a>Die InitializeCorrelation-Aktivität

Eine <xref:System.ServiceModel.Activities.InitializeCorrelation>-Aktivität wird verwendet, um Korrelationen zu initialisieren, ohne eine Nachricht zu senden oder zu empfangen. In der Regel wird die Korrelation durch das Senden oder Empfangen einer Nachricht initialisiert. Wenn eine Korrelation festgelegt werden muss, bevor eine Nachricht gesendet oder empfangen wird, verwenden Sie <xref:System.ServiceModel.Activities.InitializeCorrelation>, um die Korrelation zu initialisieren.

### <a name="using-the-initializecorrelation-activity-designer"></a>Verwenden des InitializeCorrelation-Aktivitätsdesigners

Greifen Sie in der Kategorie **Messaging** der **Toolbox**auf den **InitializeCorrelation** -Aktivitäts Designer zu.

Der **InitializeCorrelation** -Aktivitäts Designer kann aus der **Toolbox** gezogen und auf der Workflow-Designer Oberfläche abgelegt werden. Beim Löschen des Aktivitäts Designers wird eine <xref:System.ServiceModel.Activities.InitializeCorrelation>-Aktivität mit einem Standard <xref:System.Activities.Activity.DisplayName%2A> von "InitializeCorrelation" erstellt. Der <xref:System.Activities.Activity.DisplayName%2A> kann in der Kopfzeile des **InitializeCorrelation** -Aktivitäts Designers oder im Feld **Display Name** des **Eigenschaften** Fensters bearbeitet werden.

Der <xref:System.ServiceModel.Activities.CorrelationHandle> kann im Feld **Korrelation** im Fenster **Eigenschaften** auf der **InitializeCorrelation** -Aktivitäts Designer Oberfläche angegeben werden.

Um das Dialogfeld **Korrelation initialisieren** anzuzeigen, in dem Sie das Korrelations Handle und die Schlüssel-Wert-Paare angeben können, die zur Initialisierung verwendet werden, wählen Sie im **Eigenschaften** Fenster neben dem Feld **correlationdata** die Schaltfläche mit den Auslassungs Zeichen aus. Oder wählen Sie die Ansicht "anzeigen..." aus. der Hinweis Text auf der **InitializeCorrelation** -Aktivitäts Designer Oberfläche. Weitere Informationen zur Verwendung dieses Dialog Felds finden Sie im Artikel [typauflistungs-Editor-Dialogfeld](../workflow-designer/type-collection-editor-dialog-box.md) .

### <a name="the-initializecorrelation-properties"></a>Die InitializeCorrelation-Eigenschaften

In der folgenden Tabelle sind die <xref:System.ServiceModel.Activities.InitializeCorrelation> Eigenschaften aufgeführt, und es wird beschrieben, wie Sie im Designer verwendet werden. Diese Eigenschaften können im **Eigenschaften** Fenster oder auf Workflow-Designer-Oberfläche bearbeitet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Der Anzeigename der <xref:System.ServiceModel.Activities.InitializeCorrelation>-Aktivität. Der Standardwert lautet InitializeCorrelation.<br /><br /> Obwohl die Verwendung eines nicht standardmäßigen Werts für den freundlichen <xref:System.Activities.Activity.DisplayName%2A> nicht unbedingt erforderlich ist, wird empfohlen.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|False|Das <xref:System.ServiceModel.Activities.CorrelationHandle>-Objekt, das verwendet wurde, um Workflowaktivitäten in der Korrelation zuzuordnen.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|False|Ein Wörterbuch von Korrelationsdaten, die Nachrichten mit der Workflowinstanz verknüpft.<br /><br /> Verwenden Sie das Dialogfeld **Korrelation initialisieren** , um die <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> zu konfigurieren. Weitere Informationen zum Dialogfeld dieses Dialogfeld verwenden finden Sie im Artikel typauflistungs- [Editor](../workflow-designer/type-collection-editor-dialog-box.md) .|

## <a name="see-also"></a>Siehe auch

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)