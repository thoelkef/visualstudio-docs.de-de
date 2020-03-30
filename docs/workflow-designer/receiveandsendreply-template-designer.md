---
title: Workflow-Designer - ReceiveAndSendReply-Vorlagen-Designer
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.ReceiveAndSendReply.UI
- System.ServiceModel.Activities.SendReply.UI
ms.assetid: d1d9a058-df7e-48f5-a2e7-3caeeba7eaa6
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 042032efe745a9cb38bbf4e362cb5ad8440129ba
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395297"
---
# <a name="receiveandsendreply-template-designer"></a>ReceiveAndSendReply-Vorlagendesigner

Die **Vorlage ReceiveAndSendReply** wird verwendet, um ein <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> Paar vorkonfigurierter und Aktivitäten zu erstellen. Die Aktivitäten sind <xref:System.Activities.Statements.Sequence> Teil einer Aktivität und werden als Teil eines Anforderungs-Antwort-Nachrichtenaustauschmusters auf dem Server korreliert.

## <a name="the-receiveandsendreply-template"></a>Die Vorlage ReceiveAndSendReply

Das Hinzufügen einer **ReceiveAndSendReply-Vorlage** <xref:System.ServiceModel.Activities.Receive> führt <xref:System.ServiceModel.Activities.SendReply> neben <xref:System.Activities.Statements.Sequence> dem Erstellen der und Aktivitäten mit einer Aktivität drei Dinge aus:

- Konfiguriert die <xref:System.ServiceModel.Activities.Receive.OperationName%2A> <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> und Eigenschaften <xref:System.ServiceModel.Activities.Receive> der Aktivität.

- Die Eigenschaft <xref:System.ServiceModel.Activities.SendReply.Request%2A> der <xref:System.ServiceModel.Activities.Receive>-Aktivität wird an die <xref:System.ServiceModel.Activities.Send>-Aktivität gebunden.

- Ein <xref:System.ServiceModel.Activities.CorrelationHandle> wird in der übergeordneten Aktivität als Variable erstellt.

### <a name="use-the-receiveandsendreply-template-designer"></a>Verwenden des Vorlage-Designers ReceiveAndSendReply

Greifen Sie auf den Aktivitäts-Designer **ReceiveAndSendReply** in der Kategorie **Messaging** der **Toolbox**zu. Der Aktivitäts-Designer **ReceiveAndSendReply** kann aus der **Toolbox** gezogen und überall dort auf die Workflow-Designer-Oberfläche abgelegt werden, wo normalerweise Aktivitäten platziert werden. Wenn Sie den <xref:System.ServiceModel.Activities.Receive> Aktivitäts-Designer löschen, wird eine Aktivität erstellt, die mit dem Aktivitäts-Designer **senden** konfiguriert werden kann, und eine korrelierte <xref:System.ServiceModel.Activities.SendReply> Aktivität, die mit dem SendReplyToReceive-Designer konfiguriert werden kann.

Weitere Informationen zur Verwendung des **Empfangs-Designers** zum Konfigurieren der <xref:System.ServiceModel.Activities.Receive> Aktivität finden Sie unter Receive Activity [Designer](../workflow-designer/receive-activity-designer.md).

### <a name="properties-of-sendreply"></a>Eigenschaften von SendReply

In der folgenden Tabelle werden die <xref:System.ServiceModel.Activities.SendReply>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaftenraster und einige auf der Workflow-Designer-Oberfläche bearbeitet werden.

| Eigenschaftenname | Erforderlich | Verwendung |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | Der optionale Anzeigename der <xref:System.ServiceModel.Activities.SendReply>-Aktivität. Der Standardname lautet SendReplyToReceive.<br /><br /> Obwohl die Verwendung eines nicht standardmäßigen <xref:System.Activities.Activity.DisplayName%2A> Werts für die Anzeigenicht unbedingt erforderlich ist, ist es am besten, einen solchen Wert zu verwenden. |
| <xref:System.ServiceModel.Activities.SendReply.Request%2A> | True | Verweis auf die dieser <xref:System.ServiceModel.Activities.Receive>-Aktivität zugeordnete <xref:System.ServiceModel.Activities.SendReply>-Aktivität. Diese Eigenschaft darf nicht **null**sein. <xref:System.ServiceModel.Activities.Receive>und <xref:System.ServiceModel.Activities.SendReply> Aktivitäten werden zusammen auf dem Server verwendet, um ein Anforderungs-/Antwort-Messagingmuster zu modellieren. Diese Eigenschaft gibt an, welche <xref:System.ServiceModel.Activities.Send>-Aktivität zugeordnet wird. Im Designer können Sie diese Eigenschaft nicht bearbeiten, da <xref:System.ServiceModel.Activities.Send> sie automatisch an <xref:System.ServiceModel.Activities.SendReply> die Aktivität gebunden ist, aus der Sie die Aktivität erstellt haben. |
| <xref:System.ServiceModel.Activities.SendReply.Content%2A> | False | Gibt die zu empfangende Nachricht oder den zu empfangenden Parameterinhalt an. Dies kann entweder eine <xref:System.ServiceModel.Activities.ReceiveMessageContent>-Aktivität oder eine <xref:System.ServiceModel.Activities.ReceiveParametersContent>-Aktivität sein. Bearbeiten Sie diese Eigenschaft, indem Sie auf die Schaltfläche "Auslassung" neben dem Feld **Inhalt** im Eigenschaftenraster klicken oder auf die Schaltfläche **Definieren** neben der **Inhaltsbeschriftung** auf der Designeroberfläche **"Aktivität empfangen"** klicken. Beide zeigen das Dialogfeld **Inhaltsdefinition** an. Weitere Informationen zur Verwendung dieses Felds finden Sie im Thema [Dialogfeld Inhaltsdefinition.](../workflow-designer/content-definition-dialog-box.md) |
| <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> | False | Gibt die Auflistung von <xref:System.ServiceModel.Activities.CorrelationInitializer>-Objekten an, die mehrere <xref:System.ServiceModel.Activities.CorrelationHandle>-Objekte initialisiert, die diese <xref:System.ServiceModel.Activities.Receive>-Aktivität im Workflow konfigurieren. Klicken Sie auf die Schaltfläche <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> Auslassung neben der Eigenschaft im Eigenschaftenraster, um das Dialogfeld **Korrelationsinitialisierer hinzufügen** zu öffnen. Weitere Informationen zur Verwendung dieses Felds finden Sie im Thema [Dialogfeld "Korrelationinitialisierer hinzufügen".](../workflow-designer/add-correlationinitializers-dialog-box.md) |
| <xref:System.ServiceModel.Activities.SendReply.Action%2A> | False | Gibt den Aktionsheader der Nachricht an. Wenn er nicht explizit festgelegt ist, wird der Wert standardmäßig auf:<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}` |
| <xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A> | False | Gibt an, ob die Workflowinstanz beibehalten werden soll, bevor die Antwortnachricht gesendet wird. Der Standardwert ist **false**. |

## <a name="see-also"></a>Siehe auch

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Empfangen](../workflow-designer/receive-activity-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)