---
title: ReceiveAndSendReply-Vorlagen-Designer | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.ReceiveAndSendReply.UI
- System.ServiceModel.Activities.SendReply.UI
ms.assetid: d1d9a058-df7e-48f5-a2e7-3caeeba7eaa6
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4c00eed244867cfd38b20f6a8f065fc6da006801
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395389"
---
# <a name="receiveandsendreply-template-designer"></a>ReceiveAndSendReply-Vorlagendesigner
Die **Vorlage ReceiveAndSendReply** wird verwendet, um ein <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> Paar vorkonfigurierter und Aktivitäten innerhalb einer <xref:System.Activities.Statements.Sequence> Aktivität zu erstellen, die als Teil eines Anforderungs-Antwort-Nachrichtenaustauschmusters auf dem Server korreliert sind.

## <a name="the-receiveandsendreply-template"></a>Die ReceiveAndSendReply-Vorlage
 Das Hinzufügen der **ReceiveAndSendReply-Vorlage** <xref:System.ServiceModel.Activities.SendReply> führt neben <xref:System.Activities.Statements.Sequence> dem Erstellen der <xref:System.ServiceModel.Activities.Receive> und Aktivitäten mit einer Aktivität drei Dinge aus:

1. Die Eigenschaften <xref:System.ServiceModel.Activities.Receive.OperationName%2A> und <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> der <xref:System.ServiceModel.Activities.Receive>-Aktivität werden konfiguriert.

2. Die Eigenschaft <xref:System.ServiceModel.Activities.SendReply.Request%2A> der <xref:System.ServiceModel.Activities.Receive>-Aktivität wird an die <xref:System.ServiceModel.Activities.Send>-Aktivität gebunden.

3. Ein <xref:System.ServiceModel.Activities.CorrelationHandle> wird in der übergeordneten Aktivität als Variable erstellt.

### <a name="using-the-receiveandsendreply-template-designer"></a>Verwenden der ReceiveAndSendReply-Vorlage im Designer
 Der Aktivitäts-Designer **ReceiveAndSendReply** befindet sich in der **Kategorie Messaging** der **Toolbox** [!INCLUDE[wfd2](../includes/wfd2-md.md)] , auf die zugegriffen wird, indem Sie auf die Registerkarte **Toolbox** in (Alternativ, **Werkzeugleiste** im Menü **Ansicht** oder STRG+ALT+X) klicken.

 Der Aktivitäts-Designer **ReceiveAndSendReply** kann **Toolbox** aus der Toolbox [!INCLUDE[wfd2](../includes/wfd2-md.md)] gezogen und überall dort an die Oberfläche gesetzt werden, wo normalerweise Aktivitäten platziert werden. Dadurch wird <xref:System.ServiceModel.Activities.Receive> eine Aktivität erstellt, die mit dem Aktivitäts-Designer **Senden** konfiguriert werden kann, und eine korrelierte <xref:System.ServiceModel.Activities.SendReply> Aktivität, die mit dem SendReplyToReceive-Designer konfiguriert werden kann.

 [!INCLUDE[crabout](../includes/crabout-md.md)]Informationen **Receive** zum Konfigurieren der <xref:System.ServiceModel.Activities.Receive> Aktivität finden Sie im [Thema Empfangen.](../workflow-designer/receive-activity-designer.md)

 [!INCLUDE[crabout](../includes/crabout-md.md)]Verwenden des **SendReplyToReceive-Designers** zum Konfigurieren der <xref:System.ServiceModel.Activities.SendReply> Aktivität finden Sie im folgenden Abschnitt.

### <a name="properties-of-sendreply"></a>Eigenschaften von SendReply
 In der folgenden Tabelle werden die <xref:System.ServiceModel.Activities.SendReply>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaftenraster bearbeitet werden, einige davon auf der [!INCLUDE[wfd2](../includes/wfd2-md.md)]-Designeroberfläche.

|                               Eigenschaftenname                                | Erforderlich |                                                                                                                                                                                                                                                                                                                                                      Verwendung                                                                                                                                                                                                                                                                                                                                                       |
|----------------------------------------------------------------------------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|              <xref:System.Activities.Activity.DisplayName%2A>              |  False   |                                                                                                                                                                                            Der optionale Anzeigename der <xref:System.ServiceModel.Activities.SendReply>-Aktivität. Der Standardname lautet SendReplyToReceive.<br /><br /> Obwohl die Verwendung eines nicht standardmäßigen Werts für den benutzerfreundlichen <xref:System.Activities.Activity.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen solchen Wert zu verwenden.                                                                                                                                                                                             |
|         <xref:System.ServiceModel.Activities.SendReply.Request%2A>         |   True   | Verweis auf die dieser <xref:System.ServiceModel.Activities.Receive>-Aktivität zugeordnete <xref:System.ServiceModel.Activities.SendReply>-Aktivität. Diese Eigenschaft darf nicht **null**sein. <xref:System.ServiceModel.Activities.Receive>und <xref:System.ServiceModel.Activities.SendReply> Aktivitäten werden zusammen auf dem Server verwendet, um ein Anforderungs-/Antwort-Messagingmuster zu modellieren. Diese Eigenschaft gibt an, welche <xref:System.ServiceModel.Activities.Send>-Aktivität zugeordnet wird. Im Designer können Sie diese Eigenschaft nicht bearbeiten, da sie automatisch an die <xref:System.ServiceModel.Activities.Send>-Aktivität gebunden wird, anhand der Sie die <xref:System.ServiceModel.Activities.SendReply>-Aktivität erstellt haben. |
|         <xref:System.ServiceModel.Activities.SendReply.Content%2A>         |  False   |                       Gibt die zu empfangende Nachricht oder den zu empfangenden Parameterinhalt an. Dies kann entweder eine <xref:System.ServiceModel.Activities.ReceiveMessageContent>-Aktivität oder eine <xref:System.ServiceModel.Activities.ReceiveParametersContent>-Aktivität sein. Bearbeiten Sie diese Eigenschaft, indem Sie auf die Ellipsenschaltfläche neben dem Feld **Inhalt** im Eigenschaftenraster klicken oder auf die **Definition...** Neben der **Inhaltsbeschriftung** auf der Oberfläche **des Aktivitäts-Designers empfangen.** Beide zeigen das Dialogfeld **Inhaltsdefinition** an. [!INCLUDE[crabout](../includes/crabout-md.md)]Wie Sie dieses Feld verwenden, finden Sie im Thema [Dialogfeld Inhaltsdefinition.](../workflow-designer/content-definition-dialog-box.md)                       |
| <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> |  False   |            Gibt die Auflistung von <xref:System.ServiceModel.Activities.CorrelationInitializer>-Objekten an, die mehrere <xref:System.ServiceModel.Activities.CorrelationHandle>-Objekte initialisiert, die diese <xref:System.ServiceModel.Activities.Receive>-Aktivität im Workflow konfigurieren. Klicken Sie auf die Schaltfläche <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> Auslassung neben der Eigenschaft im Eigenschaftenraster, um das Dialogfeld **Korrelationsinitialisierer hinzufügen** zu öffnen. [!INCLUDE[crabout](../includes/crabout-md.md)]In diesem Feld finden Sie weitere Informationen zum [Dialogfeld "Hinzufügen von CorrelationInitializers".](../workflow-designer/add-correlationinitializers-dialog-box.md)            |
|         <xref:System.ServiceModel.Activities.SendReply.Action%2A>          |  False   |                                                                                                                                                                                                                                              Gibt den Aktionsheader der Nachricht an. Ist er nicht explizit festgelegt, lautet sein Standardwert:<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`                                                                                                                                                                                                                                              |
|    <xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A>    |  False   |                                                                                                                                                                                                                                                                                          Gibt an, ob die Workflowinstanz beibehalten werden soll, bevor die Antwortnachricht gesendet wird. Der Standardwert ist **false**.                                                                                                                                                                                                                                                                                           |

## <a name="see-also"></a>Siehe auch
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md) [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) [Receive](../workflow-designer/receive-activity-designer.md) [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md) [Send](../workflow-designer/send-activity-designer.md)