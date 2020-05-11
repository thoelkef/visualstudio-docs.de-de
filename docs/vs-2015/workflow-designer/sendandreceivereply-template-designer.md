---
title: SendAndReceiveReply-Vorlagen-Designer | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.SendAndReceiveReply.UI
- System.ServiceModel.Activities.ReceiveReply.UI
ms.assetid: 818a8c84-6593-416d-b016-1d91b85ffb68
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1bfe43f410709a924b0ebdb0cf6afbb8d30a8fcf
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395351"
---
# <a name="sendandreceivereply-template-designer"></a>SendAndReceiveReply-Vorlagendesigner
Die **SendAndReceiveReply-Vorlage** wird verwendet, um ein <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> Paar von <xref:System.Activities.Statements.Sequence> vorkonfigurierten und Aktivitäten innerhalb einer Aktivität zu erstellen, die als Teil eines Anforderungs-Antwort-Nachrichtenaustauschmusters auf dem Client korreliert sind.

## <a name="the-sendandreceivereply-template"></a>Die SendAndReceiveReply-Vorlage
 Das Hinzufügen der **SendAndReceiveReply-Vorlage** <xref:System.ServiceModel.Activities.ReceiveReply> führt neben <xref:System.Activities.Statements.Sequence> dem Erstellen der <xref:System.ServiceModel.Activities.Send> und Aktivitäten innerhalb einer Aktivität drei Dinge aus:

1. Die Eigenschaften <xref:System.ServiceModel.Activities.Send.OperationName%2A> und <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> der <xref:System.ServiceModel.Activities.Send>-Aktivität werden konfiguriert.

2. Die Eigenschaft <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> der <xref:System.ServiceModel.Activities.ReceiveReply>-Aktivität wird an die <xref:System.ServiceModel.Activities.Send>-Aktivität gebunden.

3. Ein <xref:System.ServiceModel.Activities.CorrelationHandle> wird in der übergeordneten Aktivität als Variable erstellt.

### <a name="using-the-sendandreceivereply-template-designer"></a>Verwenden des SendAndReceiveReply-Vorlagen-Designers
 Der Aktivitäts-Designer **SendAndReceiveReply** befindet sich in der **Kategorie Messaging** der **Toolbox**, auf die zugegriffen wird, indem Sie auf die Registerkarte **Toolbox** auf klicken [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Alternativ wählen Sie **Toolbar** im **Menü Ansicht** oder STRG+ALT+X aus.)

 Der **SendAndReceiveReply-Aktivitäts-Designer** kann aus der **Toolbox** gezogen und überall dort an die [!INCLUDE[wfd2](../includes/wfd2-md.md)] Oberfläche gesetzt werden, wo aktivitäten normalerweise platziert werden. Dadurch wird <xref:System.ServiceModel.Activities.Send> eine Aktivität erstellt, die mit dem Aktivitäts-Designer **Senden** konfiguriert werden kann, und eine korrelierte <xref:System.ServiceModel.Activities.ReceiveReply> Aktivität, die mit dem **ReceiveReplyForSend-Designer** konfiguriert werden kann.

 [!INCLUDE[crabout](../includes/crabout-md.md)]Informationen **Send** zum Konfigurieren der <xref:System.ServiceModel.Activities.Send> Aktivität finden Sie [unter](../workflow-designer/send-activity-designer.md) Senden.

 [!INCLUDE[crabout](../includes/crabout-md.md)]Verwenden des **ReceiveReplyForSend-Designers** zum Konfigurieren der <xref:System.ServiceModel.Activities.ReceiveReply> Aktivität finden Sie im folgenden Abschnitt.

### <a name="properties-of-receivereply"></a>Eigenschaften von ReceiveReply
 In der folgenden Tabelle werden die <xref:System.ServiceModel.Activities.ReceiveReply>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaftenraster bearbeitet werden, einige davon auf der [!INCLUDE[wfd2](../includes/wfd2-md.md)]-Designeroberfläche.

|                                 Eigenschaftenname                                 | Erforderlich |                                                                                                                                                                                                                                                                                                                                                        Verwendung                                                                                                                                                                                                                                                                                                                                                        |
|-------------------------------------------------------------------------------|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|               <xref:System.Activities.Activity.DisplayName%2A>                |  False   |                                                                                                                                                                                            Der optionale Anzeigename der <xref:System.ServiceModel.Activities.ReceiveReply>-Aktivität. Der Standardwert lautet ReceiveReplyForSend.<br /><br /> Obwohl die Verwendung eines nicht standardmäßigen Werts für den benutzerfreundlichen <xref:System.Activities.Activity.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen solchen Wert zu verwenden.                                                                                                                                                                                            |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A>         |   True   | Verweis auf die dieser <xref:System.ServiceModel.Activities.Send>-Aktivität zugeordnete <xref:System.ServiceModel.Activities.ReceiveReply>-Aktivität. Diese Eigenschaft darf nicht **null**sein. <xref:System.ServiceModel.Activities.Send>und <xref:System.ServiceModel.Activities.ReceiveReply> Aktivitäten werden zusammen auf dem Client verwendet, um ein Anforderungs-/Antwort-Messagingmuster zu modellieren. Diese Eigenschaft gibt an, welche <xref:System.ServiceModel.Activities.Send>-Aktivität zugeordnet wird. Im Designer können Sie diese Eigenschaft nicht bearbeiten, da sie automatisch an die <xref:System.ServiceModel.Activities.Send>-Aktivität gebunden wird, anhand der Sie die <xref:System.ServiceModel.Activities.ReceiveReply>-Aktivität erstellt haben. |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A>         |  False   |                        Gibt die zu empfangende Nachricht oder den zu empfangenden Parameterinhalt an. Dies kann entweder eine <xref:System.ServiceModel.Activities.ReceiveMessageContent>-Aktivität oder eine <xref:System.ServiceModel.Activities.ReceiveParametersContent>-Aktivität sein. Bearbeiten Sie diese Eigenschaft, indem Sie auf die Ellipsenschaltfläche neben dem Feld **Inhalt** im Eigenschaftenraster klicken oder auf die **Definition...** Neben der **Inhaltsbeschriftung** auf der Oberfläche **des Aktivitäts-Designers empfangen.** Beide zeigen das Dialogfeld **Inhaltsdefinition** an. [!INCLUDE[crabout](../includes/crabout-md.md)]Wie Sie dieses Feld verwenden, finden Sie im Thema [Dialogfeld Inhaltsdefinition.](../workflow-designer/content-definition-dialog-box.md)                         |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> |  False   |              Gibt die Auflistung von <xref:System.ServiceModel.Activities.CorrelationInitializer>-Objekten an, die mehrere <xref:System.ServiceModel.Activities.CorrelationHandle>-Objekte initialisiert, die diese <xref:System.ServiceModel.Activities.Receive>-Aktivität im Workflow konfigurieren. Klicken Sie auf die Schaltfläche <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> Auslassung neben der Eigenschaft im Eigenschaftenraster, um das Dialogfeld **Korrelationsinitialisierer hinzufügen** zu öffnen. [!INCLUDE[crabout](../includes/crabout-md.md)]In diesem Feld finden Sie weitere Informationen zum [Dialogfeld "Hinzufügen von CorrelationInitializers".](../workflow-designer/add-correlationinitializers-dialog-box.md)               |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A>          |  False   |                                                                                                                                                                                                                                               Gibt den Aktionsheader der Nachricht an. Ist er nicht explizit festgelegt, lautet sein Standardwert:<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`.                                                                                                                                                                                                                                              |

## <a name="see-also"></a>Siehe auch
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md) [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) [Receive](../workflow-designer/receive-activity-designer.md) [AndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) [Send](../workflow-designer/send-activity-designer.md) [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)