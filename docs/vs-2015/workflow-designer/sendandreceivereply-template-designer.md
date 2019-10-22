---
title: Sendandreceivereply-Vorlagen-Designer | Microsoft-Dokumentation
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
ms.openlocfilehash: 4ecb0e201c4351a8a117d1e35aca97866b2beb89
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663270"
---
# <a name="sendandreceivereply-template-designer"></a>SendAndReceiveReply-Vorlagendesigner
Die **sendandreceivereply** -Vorlage wird verwendet, um ein paar vorkonfigurierter <xref:System.ServiceModel.Activities.Send>-und <xref:System.ServiceModel.Activities.ReceiveReply> Aktivitäten innerhalb einer <xref:System.Activities.Statements.Sequence> Aktivität zu erstellen, die als Teil eines Anforderungs-/Antwort-Nachrichtenaustauschmusters auf dem Client korreliert werden.

## <a name="the-sendandreceivereply-template"></a>Die SendAndReceiveReply-Vorlage
 Durch das Hinzufügen der **sendandreceivereply** -Vorlage werden neben dem Erstellen der <xref:System.ServiceModel.Activities.Send>-und <xref:System.ServiceModel.Activities.ReceiveReply> Aktivitäten innerhalb einer <xref:System.Activities.Statements.Sequence> Aktivität drei Schritte ausgeführt:

1. Die Eigenschaften <xref:System.ServiceModel.Activities.Send.OperationName%2A> und <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> der <xref:System.ServiceModel.Activities.Send>-Aktivität werden konfiguriert.

2. Die Eigenschaft <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> der <xref:System.ServiceModel.Activities.ReceiveReply>-Aktivität wird an die <xref:System.ServiceModel.Activities.Send>-Aktivität gebunden.

3. Ein <xref:System.ServiceModel.Activities.CorrelationHandle> wird in der übergeordneten Aktivität als Variable erstellt.

### <a name="using-the-sendandreceivereply-template-designer"></a>Verwenden des SendAndReceiveReply-Vorlagen-Designers
 Der **sendandreceivereply** -Aktivitäts Designer befindet sich in der Kategorie **Messaging** der **Toolbox**, auf die Sie zugreifen können, indem Sie auf [!INCLUDE[wfd2](../includes/wfd2-md.md)] auf die Registerkarte **Toolbox** klicken (Sie können auch **Symbolleiste** aus der **Ansicht** auswählen. Menü oder STRG + ALT + X.)

 Der **sendandreceivereply** -Aktivitäts Designer kann aus der **Toolbox** gezogen und auf der [!INCLUDE[wfd2](../includes/wfd2-md.md)]-Oberfläche dort abgelegt werden, wo Aktivitäten normalerweise platziert werden. Dadurch wird eine <xref:System.ServiceModel.Activities.Send> Aktivität erstellt, die mit dem **Send** -Aktivitäts Designer konfiguriert werden kann, sowie eine korrelierte <xref:System.ServiceModel.Activities.ReceiveReply>, die mit dem **receivereplyforsend** -Designer konfiguriert werden kann.

 [!INCLUDE[crabout](../includes/crabout-md.md)] zum Konfigurieren der <xref:System.ServiceModel.Activities.Send> Aktivität mithilfe des **Send** -Designers finden Sie im Thema [senden](../workflow-designer/send-activity-designer.md) .

 [!INCLUDE[crabout](../includes/crabout-md.md)] Verwenden des **receivereplyforsend** -Designers, um die <xref:System.ServiceModel.Activities.ReceiveReply>-Aktivität zu konfigurieren, finden Sie im folgenden Abschnitt.

### <a name="properties-of-receivereply"></a>Eigenschaften von ReceiveReply
 In der folgenden Tabelle werden die <xref:System.ServiceModel.Activities.ReceiveReply>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaftenraster bearbeitet werden, einige davon auf der [!INCLUDE[wfd2](../includes/wfd2-md.md)]-Designeroberfläche.

|                                 Eigenschaftenname                                 | Erforderlich |                                                                                                                                                                                                                                                                                                                                                        Verwendung                                                                                                                                                                                                                                                                                                                                                        |
|-------------------------------------------------------------------------------|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|               <xref:System.Activities.Activity.DisplayName%2A>                |  False   |                                                                                                                                                                                            Der optionale Anzeigename der <xref:System.ServiceModel.Activities.ReceiveReply>-Aktivität. Der Standardwert lautet ReceiveReplyForSend.<br /><br /> Obwohl die Verwendung eines nicht standardmäßigen Werts für den benutzerfreundlichen <xref:System.Activities.Activity.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen solchen Wert zu verwenden.                                                                                                                                                                                            |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A>         |   True   | Verweis auf die dieser <xref:System.ServiceModel.Activities.Send>-Aktivität zugeordnete <xref:System.ServiceModel.Activities.ReceiveReply>-Aktivität. Diese Eigenschaft darf nicht **null**sein. Die <xref:System.ServiceModel.Activities.Send>-Aktivität und die <xref:System.ServiceModel.Activities.ReceiveReply>-Aktivität werden zusammen verwendet, um auf dem Client ein Anforderungs-/Antwort-Messagingmuster zu modellieren. Diese Eigenschaft gibt an, welche <xref:System.ServiceModel.Activities.Send>-Aktivität zugeordnet wird. Im Designer können Sie diese Eigenschaft nicht bearbeiten, da sie automatisch an die <xref:System.ServiceModel.Activities.Send>-Aktivität gebunden wird, anhand der Sie die <xref:System.ServiceModel.Activities.ReceiveReply>-Aktivität erstellt haben. |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A>         |  False   |                        Gibt die zu empfangende Nachricht oder den zu empfangenden Parameterinhalt an. Dies kann entweder eine <xref:System.ServiceModel.Activities.ReceiveMessageContent>-Aktivität oder eine <xref:System.ServiceModel.Activities.ReceiveParametersContent>-Aktivität sein. Bearbeiten Sie diese Eigenschaft, indem Sie auf die Schaltfläche mit den Auslassungs Punkten neben dem Feld **Inhalt** im Eigenschaften Raster oder auf die Schaltfläche **definieren...** Schaltfläche neben der **Inhalts** Bezeichnung auf der **Empfangs** Aktivitäts Designer Oberfläche. Beide zeigen das Dialogfeld **Inhalts Definition** an. [!INCLUDE[crabout](../includes/crabout-md.md)], wie Sie dieses Feld verwenden, finden Sie im Thema [Inhalts Definition (Dialog Feld](../workflow-designer/content-definition-dialog-box.md) ).                         |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> |  False   |              Gibt die Auflistung von <xref:System.ServiceModel.Activities.CorrelationInitializer>-Objekten an, die mehrere <xref:System.ServiceModel.Activities.CorrelationHandle>-Objekte initialisiert, die diese <xref:System.ServiceModel.Activities.Receive>-Aktivität im Workflow konfigurieren. Klicken Sie im Eigenschaften Raster neben der Eigenschaft <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> auf die Schaltfläche mit den Auslassungs Punkten, um das Dialogfeld **korrelationsinitialisierer hinzufügen** zu öffnen. [!INCLUDE[crabout](../includes/crabout-md.md)] dieses Kontrollkästchen finden Sie im Thema [Dialog Feld "correlationinitializers hinzufügen](../workflow-designer/add-correlationinitializers-dialog-box.md) ".               |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A>          |  False   |                                                                                                                                                                                                                                               Gibt den Aktionsheader der Nachricht an. Ist er nicht explizit festgelegt, lautet sein Standardwert:<br /><br /> <strong>https://tempuri.org/{service Vertrags Namespace}/Vertrags Name}/{Vorgangs Name}.</strong>                                                                                                                                                                                                                                               |

## <a name="see-also"></a>Siehe auch
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md) [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) [Receive](../workflow-designer/receive-activity-designer.md) [receiveandsendreply](../workflow-designer/receiveandsendreply-template-designer.md) [Send](../workflow-designer/send-activity-designer.md) [transactedreceivescope](../workflow-designer/transactedreceivescope-activity-designer.md)