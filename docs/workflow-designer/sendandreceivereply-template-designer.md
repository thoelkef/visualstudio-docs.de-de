---
title: Workflow-Designer - SendAndReceiveReply-Vorlagen-Designer
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.SendAndReceiveReply.UI
- System.ServiceModel.Activities.ReceiveReply.UI
ms.assetid: 818a8c84-6593-416d-b016-1d91b85ffb68
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2067ee92883d0c4ad3003f23032a88f5da3fa710
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395243"
---
# <a name="sendandreceivereply-template-designer"></a>SendAndReceiveReply-Vorlagendesigner

Die **SendAndReceiveReply-Vorlage** wird verwendet, um ein <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> Paar vorkonfigurierter und Aktivitäten zu erstellen. Die Aktivitäten sind <xref:System.Activities.Statements.Sequence> Teil einer Aktivität und werden als Teil eines Anforderungs-Antwort-Nachrichtenaustauschmusters auf dem Client korreliert.

## <a name="the-sendandreceivereply-template"></a>Die SendAndReceiveReply-Vorlage

Das Hinzufügen der **SendAndReceiveReply-Vorlage** <xref:System.ServiceModel.Activities.Send> führt <xref:System.ServiceModel.Activities.ReceiveReply> neben <xref:System.Activities.Statements.Sequence> dem Erstellen der und Aktivitäten innerhalb einer Aktivität drei Dinge aus:

- Konfiguriert die <xref:System.ServiceModel.Activities.Send.OperationName%2A> <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> und Eigenschaften <xref:System.ServiceModel.Activities.Send> der Aktivität.

- Die Eigenschaft <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> der <xref:System.ServiceModel.Activities.ReceiveReply>-Aktivität wird an die <xref:System.ServiceModel.Activities.Send>-Aktivität gebunden.

- Ein <xref:System.ServiceModel.Activities.CorrelationHandle> wird in der übergeordneten Aktivität als Variable erstellt.

### <a name="use-the-sendandreceivereply-template-designer"></a>Verwenden des SendAndReceiveReply-Vorlagen-Designers

Greifen Sie auf den Aktivitäts-Designer **SendAndReceiveReply** in der Kategorie **Messaging** der **Toolbox**zu. Der **SendAndReceiveReply-Aktivitäts-Designer** kann aus der **Toolbox** gezogen und auf die Workflow-Designer-Oberfläche dort abgelegt werden, wo normalerweise Aktivitäten platziert werden. Wenn Sie den <xref:System.ServiceModel.Activities.Send> Aktivitäts-Designer löschen, wird eine Aktivität erstellt, die mit dem Aktivitäts-Designer **Senden** konfiguriert werden kann, und eine korrelierte <xref:System.ServiceModel.Activities.ReceiveReply> Aktivität, die mit dem **ReceiveReplyForSend-Designer** konfiguriert werden kann.

Weitere Informationen zur Verwendung des **Sende-Designers** zum Konfigurieren der <xref:System.ServiceModel.Activities.Send> Aktivität finden Sie unter [Senden](../workflow-designer/send-activity-designer.md).

### <a name="properties-of-receivereply"></a>Eigenschaften von ReceiveReply

Die folgende Tabelle <xref:System.ServiceModel.Activities.ReceiveReply> zeigt die Eigenschaften und beschreibt, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaftenraster und einige auf der Workflow-Designer-Oberfläche bearbeitet werden.

| Eigenschaftenname | Erforderlich | Verwendung |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | Der optionale Anzeigename der <xref:System.ServiceModel.Activities.ReceiveReply>-Aktivität. Der Standardwert lautet ReceiveReplyForSend.<br /><br /> Obwohl die Verwendung eines nicht standardmäßigen <xref:System.Activities.Activity.DisplayName%2A> Werts für die Anzeigenicht unbedingt erforderlich ist, ist es am besten, einen solchen Wert zu verwenden. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> | True | Verweis auf die dieser <xref:System.ServiceModel.Activities.Send>-Aktivität zugeordnete <xref:System.ServiceModel.Activities.ReceiveReply>-Aktivität. Diese Eigenschaft darf nicht **null**sein. <xref:System.ServiceModel.Activities.Send>und <xref:System.ServiceModel.Activities.ReceiveReply> Aktivitäten werden zusammen auf dem Client verwendet, um ein Anforderungs-/Antwort-Messagingmuster zu modellieren. Diese Eigenschaft gibt an, welche <xref:System.ServiceModel.Activities.Send>-Aktivität zugeordnet wird. Im Designer können Sie diese Eigenschaft nicht bearbeiten, da <xref:System.ServiceModel.Activities.Send> sie automatisch an <xref:System.ServiceModel.Activities.ReceiveReply> die Aktivität gebunden ist, aus der Sie die Aktivität erstellt haben. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A> | False | Gibt die zu empfangende Nachricht oder den zu empfangenden Parameterinhalt an. Dies kann entweder eine <xref:System.ServiceModel.Activities.ReceiveMessageContent>-Aktivität oder eine <xref:System.ServiceModel.Activities.ReceiveParametersContent>-Aktivität sein. Bearbeiten Sie diese Eigenschaft, indem Sie auf die Schaltfläche "Auslassung" neben dem Feld **Inhalt** im Eigenschaftenraster klicken oder auf die Schaltfläche **Definieren** neben der **Inhaltsbeschriftung** auf der Designeroberfläche **"Aktivität empfangen"** klicken. Beide zeigen das Dialogfeld **Inhaltsdefinition** an. Weitere Informationen zur Verwendung dieses Felds finden Sie im [Dialogfeld Inhaltsdefinition](../workflow-designer/content-definition-dialog-box.md). |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> | False | Gibt die Auflistung von <xref:System.ServiceModel.Activities.CorrelationInitializer>-Objekten an, die mehrere <xref:System.ServiceModel.Activities.CorrelationHandle>-Objekte initialisiert, die diese <xref:System.ServiceModel.Activities.Receive>-Aktivität im Workflow konfigurieren. Klicken Sie auf die Schaltfläche <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> Auslassung neben der Eigenschaft im Eigenschaftenraster, um das Dialogfeld **Korrelationsinitialisierer hinzufügen** zu öffnen. Weitere Informationen zur Verwendung dieses Felds finden Sie im [Dialogfeld "CorrelationInitializers hinzufügen "Weitere](../workflow-designer/add-correlationinitializers-dialog-box.md)Informationen. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A> | False | Gibt den Aktionsheader der Nachricht an. Wenn er nicht explizit festgelegt ist, wird der Wert standardmäßig auf:<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`. |

## <a name="see-also"></a>Siehe auch

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Empfangen](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)