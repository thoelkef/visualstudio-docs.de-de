---
title: Workflow-Designer - SendAndReceiveReply-Vorlagendesigner
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.ServiceModel.Activities.SendAndReceiveReply.UI
- System.ServiceModel.Activities.ReceiveReply.UI
ms.assetid: 818a8c84-6593-416d-b016-1d91b85ffb68
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 469e8ca3c325b04684e9481957c2e6bf9e14cffb
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54940413"
---
# <a name="sendandreceivereply-template-designer"></a>SendAndReceiveReply-Vorlagendesigner

Die **SendAndReceiveReply** Vorlage wird verwendet, um ein paar vorkonfigurierter <xref:System.ServiceModel.Activities.Send> und <xref:System.ServiceModel.Activities.ReceiveReply> Aktivitäten. Die Aktivitäten sind Teil einer <xref:System.Activities.Statements.Sequence> Aktivität und sind als Teil einer Anforderung/Antwort-nachrichtenaustauschmusters auf dem Client zu korrelieren.

## <a name="the-sendandreceivereply-template"></a>Die SendAndReceiveReply-Vorlage

Hinzufügen der **SendAndReceiveReply** Vorlage bewirkt drei Dinge, neben der Erstellung der <xref:System.ServiceModel.Activities.Send> und <xref:System.ServiceModel.Activities.ReceiveReply> Aktivitäten innerhalb einer <xref:System.Activities.Statements.Sequence> Aktivität:

- Konfiguriert die <xref:System.ServiceModel.Activities.Send.OperationName%2A> und <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> Eigenschaften der <xref:System.ServiceModel.Activities.Send> Aktivität.

- Die Eigenschaft <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> der <xref:System.ServiceModel.Activities.ReceiveReply>-Aktivität wird an die <xref:System.ServiceModel.Activities.Send>-Aktivität gebunden.

- Ein <xref:System.ServiceModel.Activities.CorrelationHandle> wird in der übergeordneten Aktivität als Variable erstellt.

### <a name="use-the-sendandreceivereply-template-designer"></a>Verwenden Sie die SendAndReceiveReply-Vorlagendesigner

Zugriff die **SendAndReceiveReply** Aktivitäts-Designer in der **Messaging** Kategorie der **Toolbox**. Die **SendAndReceiveReply** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** und sich der Workflow-Designer-Oberfläche gelöscht werden, wo Aktivitäten normalerweise platziert werden. Löschen die Aktivitäts-Designer erstellt eine <xref:System.ServiceModel.Activities.Send> Aktivität, die konfiguriert werden kann die **senden** Aktivitäts-Designer und korrelierte <xref:System.ServiceModel.Activities.ReceiveReply> , die konfiguriert werden kann, mit der **ReceiveReplyForSend** Designer.

Weitere Informationen zur Verwendung der **senden** -Designers bei der Konfiguration der <xref:System.ServiceModel.Activities.Send> -Aktivität, finden Sie unter [senden](../workflow-designer/send-activity-designer.md).

### <a name="properties-of-receivereply"></a>Eigenschaften von ReceiveReply

Die folgende Tabelle zeigt die <xref:System.ServiceModel.Activities.ReceiveReply> Eigenschaften und beschreibt, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaftenraster bearbeitet werden, und einige auf der Oberfläche des Workflow-Designer bearbeitet werden kann.


| Eigenschaftenname | Erforderlich | Verwendung |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | Der optionale Anzeigename der <xref:System.ServiceModel.Activities.ReceiveReply>-Aktivität. Der Standardwert lautet ReceiveReplyForSend.<br /><br /> Obwohl die Verwendung von einem nicht standardmäßigen Wert für den Anzeigenamen <xref:System.Activities.Activity.DisplayName%2A> ist nicht zwingend erforderlich, es wird empfohlen, einen solchen Wert zu verwenden. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> | True | Verweis auf die dieser <xref:System.ServiceModel.Activities.Send>-Aktivität zugeordnete <xref:System.ServiceModel.Activities.ReceiveReply>-Aktivität. Diese Eigenschaft darf nicht sein **null**. Die <xref:System.ServiceModel.Activities.Send>-Aktivität und die <xref:System.ServiceModel.Activities.ReceiveReply>-Aktivität werden zusammen verwendet, um auf dem Client ein Anforderungs-/Antwort-Messagingmuster zu modellieren. Diese Eigenschaft gibt an, welche <xref:System.ServiceModel.Activities.Send>-Aktivität zugeordnet wird. Im Designer können Sie diese Eigenschaft bearbeiten, da er automatisch an gebunden ist die <xref:System.ServiceModel.Activities.Send> Aktivität aus der Sie erstellt die <xref:System.ServiceModel.Activities.ReceiveReply> Aktivität. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A> | False | Gibt die zu empfangende Nachricht oder den zu empfangenden Parameterinhalt an. Dies kann entweder eine <xref:System.ServiceModel.Activities.ReceiveMessageContent>-Aktivität oder eine <xref:System.ServiceModel.Activities.ReceiveParametersContent>-Aktivität sein. Diese Eigenschaft bearbeiten, indem Sie auf die Schaltfläche mit den Auslassungspunkten neben der **Inhalt** Feld im Eigenschaftenraster oder auf die **definieren** neben der **Inhalt** Bezeichnung auf der **Receive** aktivitätsdesigneroberfläche. Anzeigen der **Inhaltsdefinition** Dialogfeld. Weitere Informationen dazu, wie Sie dieses Feld verwenden, finden Sie unter [Content Definition (Dialogfeld)](../workflow-designer/content-definition-dialog-box.md). |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> | False | Gibt die Auflistung von <xref:System.ServiceModel.Activities.CorrelationInitializer>-Objekten an, die mehrere <xref:System.ServiceModel.Activities.CorrelationHandle>-Objekte initialisiert, die diese <xref:System.ServiceModel.Activities.Receive>-Aktivität im Workflow konfigurieren. Klicken Sie auf die Schaltfläche mit den Auslassungspunkten neben der <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> Eigenschaft im Eigenschaftenraster, öffnen Sie die **Korrelationsinitialisierer hinzufügen** im Dialogfeld. Weitere Informationen zur Verwendung dieses Dialogfelds finden Sie unter [CorrelationInitializers-Dialogfeld hinzufügen](../workflow-designer/add-correlationinitializers-dialog-box.md). |
| <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A> | False | Gibt den Aktionsheader der Nachricht an. Wenn sie nicht explizit festgelegt ist, lautet sein Standardwert:<br /><br /> <strong>https://tempuri.org/{service Vertrag Namespace} / {Dienstvertragsname} / {Vorgangsname}.</strong> |

## <a name="see-also"></a>Siehe auch

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)