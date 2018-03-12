---
title: ReceiveAndSendReply-Vorlagendesigner | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.ReceiveAndSendReply.UI
- System.ServiceModel.Activities.SendReply.UI
ms.assetid: d1d9a058-df7e-48f5-a2e7-3caeeba7eaa6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 4c1236f8c3f86362ba49aa4b985dcc601a66c476
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2018
---
# <a name="receiveandsendreply-template-designer"></a>ReceiveAndSendReply-Vorlagendesigner

Die **ReceiveAndSendReply** Vorlage dient dazu, erstellen Sie ein Paar von vorkonfiguriert, dass <xref:System.ServiceModel.Activities.Receive> und <xref:System.ServiceModel.Activities.SendReply> Aktivitäten innerhalb einer <xref:System.Activities.Statements.Sequence> Aktivität, die als Teil eines Anforderungs-/Antwort-Nachrichtenaustauschs korreliert werden Muster auf dem Server.

## <a name="the-receiveandsendreply-template"></a>Die ReceiveAndSendReply-Vorlage
 Hinzufügen von **ReceiveAndSendReply** -Vorlage bewirkt drei Dinge neben der Erstellung der <xref:System.ServiceModel.Activities.Receive> und <xref:System.ServiceModel.Activities.SendReply> Aktivitäten mit einer <xref:System.Activities.Statements.Sequence> Aktivität:

1.  Die Eigenschaften <xref:System.ServiceModel.Activities.Receive.OperationName%2A> und <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> der <xref:System.ServiceModel.Activities.Receive>-Aktivität werden konfiguriert.

2.  Die Eigenschaft <xref:System.ServiceModel.Activities.SendReply.Request%2A> der <xref:System.ServiceModel.Activities.Receive>-Aktivität wird an die <xref:System.ServiceModel.Activities.Send>-Aktivität gebunden.

3.  Ein <xref:System.ServiceModel.Activities.CorrelationHandle> wird in der übergeordneten Aktivität als Variable erstellt.

### <a name="using-the-receiveandsendreply-template-designer"></a>Verwenden der ReceiveAndSendReply-Vorlage im Designer
 Die **ReceiveAndSendReply** Aktivitäts-Designer finden Sie in der **Messaging** Kategorie der **Toolbox**, die erfolgt durch Klicken auf die **Toolbox**  Registerkarte [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (Wählen Sie alternativ **Symbolleiste** aus der **Ansicht** Menüs oder STRG + ALT + X drücken.)

 Die **ReceiveAndSendReply** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** gezogen und auf die [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] -Oberfläche ablegen, wo Aktivitäten normalerweise platziert werden. Dies erstellt eine <xref:System.ServiceModel.Activities.Receive> Aktivität, die mit konfiguriert werden kann die **senden** Aktivitäts-Designer und korrelierte <xref:System.ServiceModel.Activities.SendReply> , die mit dem SendReplyToReceive-Designer konfiguriert werden können.

 Weitere Informationen zum Verwenden der **Receive** -Designers zur Konfiguration der <xref:System.ServiceModel.Activities.Receive> Aktivität, finden Sie unter der [empfangen](../workflow-designer/receive-activity-designer.md) Thema.

 Weitere Informationen zum Verwenden der **SendReplyToReceive** -Designers zur Konfiguration der <xref:System.ServiceModel.Activities.SendReply> Aktivität, finden Sie im folgenden Abschnitt.

### <a name="properties-of-sendreply"></a>Eigenschaften von SendReply
 In der folgenden Tabelle werden die <xref:System.ServiceModel.Activities.SendReply>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaftenraster bearbeitet werden, einige davon auf der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]-Designeroberfläche.

|Eigenschaftenname|Erforderlich|Verwendung|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Der optionale Anzeigename der <xref:System.ServiceModel.Activities.SendReply>-Aktivität. Der Standardname lautet SendReplyToReceive.<br /><br /> Obwohl die Verwendung eines nicht standardmäßigen Werts für den benutzerfreundlichen <xref:System.Activities.Activity.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen solchen Wert zu verwenden.|
|<xref:System.ServiceModel.Activities.SendReply.Request%2A>|True|Verweis auf die dieser <xref:System.ServiceModel.Activities.Receive>-Aktivität zugeordnete <xref:System.ServiceModel.Activities.SendReply>-Aktivität. Diese Eigenschaft muss nicht **null**. Die <xref:System.ServiceModel.Activities.Receive>-Aktivität und die <xref:System.ServiceModel.Activities.SendReply>-Aktivität werden verwendet, um zusammen ein Anforderungs-/Antwort-Messaging-Muster auf dem Server zu modellieren. Diese Eigenschaft gibt an, welche <xref:System.ServiceModel.Activities.Send>-Aktivität zugeordnet wird. Im Designer können Sie diese Eigenschaft nicht bearbeiten, da sie automatisch an die <xref:System.ServiceModel.Activities.Send>-Aktivität gebunden wird, anhand der Sie die <xref:System.ServiceModel.Activities.SendReply>-Aktivität erstellt haben.|
|<xref:System.ServiceModel.Activities.SendReply.Content%2A>|False|Gibt die zu empfangende Nachricht oder den zu empfangenden Parameterinhalt an. Dies kann entweder eine <xref:System.ServiceModel.Activities.ReceiveMessageContent>-Aktivität oder eine <xref:System.ServiceModel.Activities.ReceiveParametersContent>-Aktivität sein. Diese Eigenschaft bearbeiten, indem Sie auf die Schaltfläche mit den Auslassungspunkten neben der **Content** Feld im Eigenschaftenraster oder indem Sie auf die **definieren...**  neben der **Content** auf bezeichnen die **Receive** aktivitätsdesigneroberfläche. Beides anzeigen der **Inhaltsdefinition** Dialogfeld. Weitere Informationen dazu, wie Sie dieses Feld verwenden, finden Sie unter der [Content Vorgangsdefinition (Dialogfeld)](../workflow-designer/content-definition-dialog-box.md) Thema.|
|<xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A>|False|Gibt die Auflistung von <xref:System.ServiceModel.Activities.CorrelationInitializer>-Objekten an, die mehrere <xref:System.ServiceModel.Activities.CorrelationHandle>-Objekte initialisiert, die diese <xref:System.ServiceModel.Activities.Receive>-Aktivität im Workflow konfigurieren. Klicken Sie auf die Schaltfläche mit den Auslassungszeichen neben der <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> Eigenschaft im Eigenschaftenraster So öffnen die **Korrelationsinitialisierer hinzufügen** (Dialogfeld). Weitere Informationen zu diesem Feld verwenden, finden Sie unter der [CorrelationInitializers-Dialogfeld hinzufügen](../workflow-designer/add-correlationinitializers-dialog-box.md) Thema.|
|<xref:System.ServiceModel.Activities.SendReply.Action%2A>|False|Gibt den Aktionsheader der Nachricht an. Ist er nicht explizit festgelegt, lautet sein Standardwert:<br /><br /> **https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}**|
|<xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A>|False|Gibt an, ob die Workflowinstanz beibehalten werden soll, bevor die Antwortnachricht gesendet wird. Der Standardwert ist **FALSE**.|

## <a name="see-also"></a>Siehe auch

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Empfangen](../workflow-designer/receive-activity-designer.md)
- [Senden](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)