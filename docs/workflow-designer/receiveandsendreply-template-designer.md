---
title: Workflow-Designer-receiveandsendreply-Vorlagen-Designer
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
ms.openlocfilehash: a816013f4eceb390a16e76a06814043aa0adaeb8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650020"
---
# <a name="receiveandsendreply-template-designer"></a>ReceiveAndSendReply-Vorlagendesigner

Die **receiveandsendreply** -Vorlage wird verwendet, um ein paar vorkonfigurierter <xref:System.ServiceModel.Activities.Receive>-und <xref:System.ServiceModel.Activities.SendReply> Aktivitäten zu erstellen. Die Aktivitäten sind Teil einer <xref:System.Activities.Statements.Sequence>-Aktivität und werden als Teil eines Anforderungs-/Antwort-Nachrichtenaustauschmusters auf dem Server korreliert.

## <a name="the-receiveandsendreply-template"></a>Die receiveandsendreply-Vorlage

Durch das Hinzufügen einer **receiveandsendreply** -Vorlage werden neben dem Erstellen der <xref:System.ServiceModel.Activities.Receive>-und <xref:System.ServiceModel.Activities.SendReply> Aktivitäten mit einer <xref:System.Activities.Statements.Sequence> Aktivität drei Schritte ausgeführt:

- Konfiguriert die Eigenschaften <xref:System.ServiceModel.Activities.Receive.OperationName%2A> und <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> der <xref:System.ServiceModel.Activities.Receive> Aktivität.

- Die Eigenschaft <xref:System.ServiceModel.Activities.SendReply.Request%2A> der <xref:System.ServiceModel.Activities.Receive>-Aktivität wird an die <xref:System.ServiceModel.Activities.Send>-Aktivität gebunden.

- Ein <xref:System.ServiceModel.Activities.CorrelationHandle> wird in der übergeordneten Aktivität als Variable erstellt.

### <a name="use-the-receiveandsendreply-template-designer"></a>Verwenden des receiveandsendreply-Vorlagen-Designers

Greifen Sie in der Kategorie **Messaging** der **Toolbox**auf den **receiveandsendreply** -Aktivitäts Designer zu. Der **receiveandsendreply** -Aktivitäts Designer kann aus der **Toolbox** gezogen und auf der Workflow-Designer-Oberfläche dort abgelegt werden, wo Aktivitäten normalerweise platziert werden. Durch das Löschen des Aktivitäts Designers wird eine <xref:System.ServiceModel.Activities.Receive> Aktivität erstellt, die mit dem **Send** -Aktivitäts Designer konfiguriert werden kann, sowie eine korrelierte <xref:System.ServiceModel.Activities.SendReply>, die mit dem sendreplytor eceive-Designer konfiguriert werden kann.

Weitere Informationen zum Konfigurieren der <xref:System.ServiceModel.Activities.Receive> Aktivität mithilfe des **Empfangs** -Designers finden Sie unter [Receive Activity Designer](../workflow-designer/receive-activity-designer.md).

### <a name="properties-of-sendreply"></a>Eigenschaften von SendReply

In der folgenden Tabelle werden die <xref:System.ServiceModel.Activities.SendReply>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaften Raster bearbeitet werden, und einige können auf der Workflow-Designer Oberfläche bearbeitet werden.

| Eigenschaftenname | Erforderlich | Verwendung |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | Der optionale Anzeigename der <xref:System.ServiceModel.Activities.SendReply>-Aktivität. Der Standardname lautet SendReplyToReceive.<br /><br /> Obwohl die Verwendung eines nicht standardmäßigen Werts für den freundlichen <xref:System.Activities.Activity.DisplayName%2A> nicht unbedingt erforderlich ist, empfiehlt es sich, einen solchen Wert zu verwenden. |
| <xref:System.ServiceModel.Activities.SendReply.Request%2A> | True | Verweis auf die dieser <xref:System.ServiceModel.Activities.Receive>-Aktivität zugeordnete <xref:System.ServiceModel.Activities.SendReply>-Aktivität. Diese Eigenschaft darf nicht **null**sein. Die <xref:System.ServiceModel.Activities.Receive>-Aktivität und die <xref:System.ServiceModel.Activities.SendReply>-Aktivität werden verwendet, um zusammen ein Anforderungs-/Antwort-Messaging-Muster auf dem Server zu modellieren. Diese Eigenschaft gibt an, welche <xref:System.ServiceModel.Activities.Send>-Aktivität zugeordnet wird. Im Designer können Sie diese Eigenschaft nicht bearbeiten, da Sie automatisch an die <xref:System.ServiceModel.Activities.Send> Aktivität gebunden ist, aus der Sie die <xref:System.ServiceModel.Activities.SendReply> Aktivität erstellt haben. |
| <xref:System.ServiceModel.Activities.SendReply.Content%2A> | False | Gibt die zu empfangende Nachricht oder den zu empfangenden Parameterinhalt an. Dies kann entweder eine <xref:System.ServiceModel.Activities.ReceiveMessageContent>-Aktivität oder eine <xref:System.ServiceModel.Activities.ReceiveParametersContent>-Aktivität sein. Bearbeiten Sie diese Eigenschaft, indem Sie auf die Schaltfläche mit den Auslassungs Punkten neben dem Feld **Inhalt** im Eigenschaften Raster klicken, oder indem Sie auf der Oberfläche des **Empfangs** Aktivitäts Designers neben der **Inhalts** Bezeichnung auf die Schaltfläche **definieren** klicken. Beide zeigen das Dialogfeld **Inhalts Definition** an. Weitere Informationen zur Verwendung dieses Felds finden Sie im Thema [Inhalts Definition (Dialog Feld](../workflow-designer/content-definition-dialog-box.md) ). |
| <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> | False | Gibt die Auflistung von <xref:System.ServiceModel.Activities.CorrelationInitializer>-Objekten an, die mehrere <xref:System.ServiceModel.Activities.CorrelationHandle>-Objekte initialisiert, die diese <xref:System.ServiceModel.Activities.Receive>-Aktivität im Workflow konfigurieren. Klicken Sie im Eigenschaften Raster neben der Eigenschaft <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> auf die Schaltfläche mit den Auslassungs Punkten, um das Dialogfeld **korrelationsinitialisierer hinzufügen** zu öffnen. Weitere Informationen zur Verwendung dieses Felds finden Sie im Thema [Dialog Feld "correlationinitializers hinzufügen](../workflow-designer/add-correlationinitializers-dialog-box.md) ". |
| <xref:System.ServiceModel.Activities.SendReply.Action%2A> | False | Gibt den Aktionsheader der Nachricht an. Wenn Sie nicht explizit festgelegt ist, wird der Wert standardmäßig auf Folgendes festgelegt:<br /><br /> <strong>https://tempuri.org/{service Vertrags Namespace}/Vertrags Name}/{Vorgangs Name}</strong> |
| <xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A> | False | Gibt an, ob die Workflowinstanz beibehalten werden soll, bevor die Antwortnachricht gesendet wird. Der Standardwert ist **FALSE**. |

## <a name="see-also"></a>Siehe auch

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)