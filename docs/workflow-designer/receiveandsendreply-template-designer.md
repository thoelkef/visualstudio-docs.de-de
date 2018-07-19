---
title: Workflow-Designer - ReceiveAndSendReply-Vorlagendesigner
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.ServiceModel.Activities.ReceiveAndSendReply.UI
- System.ServiceModel.Activities.SendReply.UI
ms.assetid: d1d9a058-df7e-48f5-a2e7-3caeeba7eaa6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: acfe9f80a5125ef13996e7cd8ec88a35cfb83211
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2018
ms.locfileid: "36756385"
---
# <a name="receiveandsendreply-template-designer"></a>ReceiveAndSendReply-Vorlagendesigner

Die **ReceiveAndSendReply** Vorlage wird verwendet, um ein paar vorkonfigurierter <xref:System.ServiceModel.Activities.Receive> und <xref:System.ServiceModel.Activities.SendReply> Aktivitäten. Die Aktivitäten sind Teil einer <xref:System.Activities.Statements.Sequence> Aktivität und sind als Teil einer Anforderung/Antwort-nachrichtenaustauschmusters auf dem Server zu korrelieren.

## <a name="the-receiveandsendreply-template"></a>Die ReceiveAndSendReply-Vorlage

Hinzufügen einer **ReceiveAndSendReply** Vorlage bewirkt drei Dinge, neben der Erstellung der <xref:System.ServiceModel.Activities.Receive> und <xref:System.ServiceModel.Activities.SendReply> Aktivitäten mit einem <xref:System.Activities.Statements.Sequence> Aktivität:

- Konfiguriert die <xref:System.ServiceModel.Activities.Receive.OperationName%2A> und <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> Eigenschaften der <xref:System.ServiceModel.Activities.Receive> Aktivität.

- Die Eigenschaft <xref:System.ServiceModel.Activities.SendReply.Request%2A> der <xref:System.ServiceModel.Activities.Receive>-Aktivität wird an die <xref:System.ServiceModel.Activities.Send>-Aktivität gebunden.

- Ein <xref:System.ServiceModel.Activities.CorrelationHandle> wird in der übergeordneten Aktivität als Variable erstellt.

### <a name="use-the-receiveandsendreply-template-designer"></a>Verwenden der ReceiveAndSendReply-Vorlagendesigner

Zugriff die **ReceiveAndSendReply** Aktivitäts-Designer in der **Messaging** Kategorie der **Toolbox**. Die **ReceiveAndSendReply** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** und sich der Workflow-Designer-Oberfläche gelöscht werden, wo Aktivitäten normalerweise platziert werden. Löschen der Aktivitäts-Designer erstellt eine <xref:System.ServiceModel.Activities.Receive> Aktivität, die konfiguriert werden kann die **senden** Aktivitäts-Designer und korrelierte <xref:System.ServiceModel.Activities.SendReply> , die mit dem SendReplyToReceive-Designer konfiguriert werden kann.

Weitere Informationen zur Verwendung der **empfangen** -Designers bei der Konfiguration der <xref:System.ServiceModel.Activities.Receive> -Aktivität, finden Sie unter [Aktivitäts-Designer erhalten](../workflow-designer/receive-activity-designer.md).

### <a name="properties-of-sendreply"></a>Eigenschaften von SendReply

In der folgenden Tabelle werden die <xref:System.ServiceModel.Activities.SendReply>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaftenraster bearbeitet werden, und einige auf der Oberfläche des Workflow-Designer bearbeitet werden kann.

|Eigenschaftenname|Erforderlich|Verwendung|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Der optionale Anzeigename der <xref:System.ServiceModel.Activities.SendReply>-Aktivität. Der Standardname lautet SendReplyToReceive.<br /><br /> Obwohl die Verwendung von einem nicht standardmäßigen Wert für den Anzeigenamen <xref:System.Activities.Activity.DisplayName%2A> ist nicht zwingend erforderlich, es wird empfohlen, einen solchen Wert zu verwenden.|
|<xref:System.ServiceModel.Activities.SendReply.Request%2A>|True|Verweis auf die dieser <xref:System.ServiceModel.Activities.Receive>-Aktivität zugeordnete <xref:System.ServiceModel.Activities.SendReply>-Aktivität. Diese Eigenschaft darf nicht sein **null**. Die <xref:System.ServiceModel.Activities.Receive>-Aktivität und die <xref:System.ServiceModel.Activities.SendReply>-Aktivität werden verwendet, um zusammen ein Anforderungs-/Antwort-Messaging-Muster auf dem Server zu modellieren. Diese Eigenschaft gibt an, welche <xref:System.ServiceModel.Activities.Send>-Aktivität zugeordnet wird. Im Designer können Sie diese Eigenschaft bearbeiten, da er automatisch an gebunden ist die <xref:System.ServiceModel.Activities.Send> Aktivität aus der Sie erstellt die <xref:System.ServiceModel.Activities.SendReply> Aktivität.|
|<xref:System.ServiceModel.Activities.SendReply.Content%2A>|False|Gibt die zu empfangende Nachricht oder den zu empfangenden Parameterinhalt an. Dies kann entweder eine <xref:System.ServiceModel.Activities.ReceiveMessageContent>-Aktivität oder eine <xref:System.ServiceModel.Activities.ReceiveParametersContent>-Aktivität sein. Diese Eigenschaft bearbeiten, indem Sie auf die Schaltfläche mit den Auslassungspunkten neben der **Content** Feld im Eigenschaftenraster oder durch Klicken auf die **definieren** neben der **Inhalt** Bezeichnung auf die  **Empfangen von** aktivitätsdesigneroberfläche. Anzeigen der **Inhaltsdefinition** Dialogfeld. Weitere Informationen dazu, wie Sie dieses Feld verwenden, finden Sie unter den [Content Definition (Dialogfeld)](../workflow-designer/content-definition-dialog-box.md) Thema.|
|<xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A>|False|Gibt die Auflistung von <xref:System.ServiceModel.Activities.CorrelationInitializer>-Objekten an, die mehrere <xref:System.ServiceModel.Activities.CorrelationHandle>-Objekte initialisiert, die diese <xref:System.ServiceModel.Activities.Receive>-Aktivität im Workflow konfigurieren. Klicken Sie auf die Schaltfläche mit den Auslassungspunkten neben der <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> Eigenschaft im Eigenschaftenraster, öffnen Sie die **Korrelationsinitialisierer hinzufügen** im Dialogfeld. Weitere Informationen zur Verwendung dieses Dialogfelds finden Sie unter den [CorrelationInitializers-Dialogfeld hinzufügen](../workflow-designer/add-correlationinitializers-dialog-box.md) Thema.|
|<xref:System.ServiceModel.Activities.SendReply.Action%2A>|False|Gibt den Aktionsheader der Nachricht an. Wenn sie nicht explizit festgelegt ist, lautet sein Standardwert:<br /><br /> **https://tempuri.org/{service Vertrag Namespace} / {Dienstvertragsname} / {Vorgangsname}**|
|<xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A>|False|Gibt an, ob die Workflowinstanz beibehalten werden soll, bevor die Antwortnachricht gesendet wird. Der Standardwert ist **FALSE**.|

## <a name="see-also"></a>Siehe auch

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Empfangen](../workflow-designer/receive-activity-designer.md)
- [Senden](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)