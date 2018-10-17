---
title: ReceiveAndSendReply-Vorlagendesigner | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.ReceiveAndSendReply.UI
- System.ServiceModel.Activities.SendReply.UI
ms.assetid: d1d9a058-df7e-48f5-a2e7-3caeeba7eaa6
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 6536ea4053e889e45fa85d2230a73c446bd1feea
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49302990"
---
# <a name="receiveandsendreply-template-designer"></a>ReceiveAndSendReply-Vorlagendesigner
Die **ReceiveAndSendReply** Vorlage wird verwendet, um ein paar vorkonfiguriert, dass <xref:System.ServiceModel.Activities.Receive> und <xref:System.ServiceModel.Activities.SendReply> Aktivitäten innerhalb einer <xref:System.Activities.Statements.Sequence> Aktivität, die als Teil eines Anforderungs-/Antwort-Nachrichtenaustauschs korreliert werden Muster auf dem Server.  
  
## <a name="the-receiveandsendreply-template"></a>Die ReceiveAndSendReply-Vorlage  
 Hinzufügen von **ReceiveAndSendReply** Vorlage bewirkt drei Dinge, neben der Erstellung der <xref:System.ServiceModel.Activities.Receive> und <xref:System.ServiceModel.Activities.SendReply> Aktivitäten mit einer <xref:System.Activities.Statements.Sequence> Aktivität:  
  
1.  Die Eigenschaften <xref:System.ServiceModel.Activities.Receive.OperationName%2A> und <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> der <xref:System.ServiceModel.Activities.Receive>-Aktivität werden konfiguriert.  
  
2.  Die Eigenschaft <xref:System.ServiceModel.Activities.SendReply.Request%2A> der <xref:System.ServiceModel.Activities.Receive>-Aktivität wird an die <xref:System.ServiceModel.Activities.Send>-Aktivität gebunden.  
  
3.  Ein <xref:System.ServiceModel.Activities.CorrelationHandle> wird in der übergeordneten Aktivität als Variable erstellt.  
  
### <a name="using-the-receiveandsendreply-template-designer"></a>Verwenden der ReceiveAndSendReply-Vorlage im Designer  
 Die **ReceiveAndSendReply** Aktivitäts-Designer finden Sie in der **Messaging** Kategorie der **Toolbox**, die erfolgt durch Klicken auf die **Toolbox**  Registerkarte [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Wählen Sie alternativ **Symbolleiste** aus der **Ansicht** Menü oder STRG + ALT + X.)  
  
 Die **ReceiveAndSendReply** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** und auf die [!INCLUDE[wfd2](../includes/wfd2-md.md)] -Oberfläche ganz egal, wo Aktivitäten normalerweise platziert werden. Erstellt eine <xref:System.ServiceModel.Activities.Receive> Aktivität, die konfiguriert werden kann die **senden** Aktivitäts-Designer und korrelierte <xref:System.ServiceModel.Activities.SendReply> , die mit dem SendReplyToReceive-Designer konfiguriert werden kann.  
  
 [!INCLUDE[crabout](../includes/crabout-md.md)] Mithilfe der **Receive** -Designers bei der Konfiguration der <xref:System.ServiceModel.Activities.Receive> -Aktivität, finden Sie unter der [Receive](../workflow-designer/receive-activity-designer.md) Thema.  
  
 [!INCLUDE[crabout](../includes/crabout-md.md)] Mithilfe der **SendReplyToReceive** -Designers bei der Konfiguration der <xref:System.ServiceModel.Activities.SendReply> -Aktivität, finden Sie im folgenden Abschnitt.  
  
### <a name="properties-of-sendreply"></a>Eigenschaften von SendReply  
 In der folgenden Tabelle werden die <xref:System.ServiceModel.Activities.SendReply>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaftenraster bearbeitet werden, einige davon auf der [!INCLUDE[wfd2](../includes/wfd2-md.md)]-Designeroberfläche.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Der optionale Anzeigename der <xref:System.ServiceModel.Activities.SendReply>-Aktivität. Der Standardname lautet SendReplyToReceive.<br /><br /> Obwohl die Verwendung eines nicht standardmäßigen Werts für den benutzerfreundlichen <xref:System.Activities.Activity.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen solchen Wert zu verwenden.|  
|<xref:System.ServiceModel.Activities.SendReply.Request%2A>|True|Verweis auf die dieser <xref:System.ServiceModel.Activities.Receive>-Aktivität zugeordnete <xref:System.ServiceModel.Activities.SendReply>-Aktivität. Diese Eigenschaft darf nicht sein **null**. Die <xref:System.ServiceModel.Activities.Receive>-Aktivität und die <xref:System.ServiceModel.Activities.SendReply>-Aktivität werden verwendet, um zusammen ein Anforderungs-/Antwort-Messaging-Muster auf dem Server zu modellieren. Diese Eigenschaft gibt an, welche <xref:System.ServiceModel.Activities.Send>-Aktivität zugeordnet wird. Im Designer können Sie diese Eigenschaft nicht bearbeiten, da sie automatisch an die <xref:System.ServiceModel.Activities.Send>-Aktivität gebunden wird, anhand der Sie die <xref:System.ServiceModel.Activities.SendReply>-Aktivität erstellt haben.|  
|<xref:System.ServiceModel.Activities.SendReply.Content%2A>|False|Gibt die zu empfangende Nachricht oder den zu empfangenden Parameterinhalt an. Dies kann entweder eine <xref:System.ServiceModel.Activities.ReceiveMessageContent>-Aktivität oder eine <xref:System.ServiceModel.Activities.ReceiveParametersContent>-Aktivität sein. Diese Eigenschaft bearbeiten, indem Sie auf die Schaltfläche mit den Auslassungspunkten neben der **Content** Feld im Eigenschaftenraster oder indem Sie auf die **definieren...** neben der **Content** Bezeichnung auf die **Receive** aktivitätsdesigneroberfläche. Anzeigen der **Inhaltsdefinition** Dialogfeld. [!INCLUDE[crabout](../includes/crabout-md.md)] zur Verwendung dieses Dialogfelds finden Sie unter den [Content Definition (Dialogfeld)](../workflow-designer/content-definition-dialog-box.md) Thema.|  
|<xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A>|False|Gibt die Auflistung von <xref:System.ServiceModel.Activities.CorrelationInitializer>-Objekten an, die mehrere <xref:System.ServiceModel.Activities.CorrelationHandle>-Objekte initialisiert, die diese <xref:System.ServiceModel.Activities.Receive>-Aktivität im Workflow konfigurieren. Klicken Sie auf die Schaltfläche mit den Auslassungspunkten neben der <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> Eigenschaft im Eigenschaftenraster, öffnen Sie die **Korrelationsinitialisierer hinzufügen** im Dialogfeld. [!INCLUDE[crabout](../includes/crabout-md.md)] Verwenden dieses Dialogfeld finden Sie unter den [CorrelationInitializers-Dialogfeld hinzufügen](../workflow-designer/add-correlationinitializers-dialog-box.md) Thema.|  
|<xref:System.ServiceModel.Activities.SendReply.Action%2A>|False|Gibt den Aktionsheader der Nachricht an. Ist er nicht explizit festgelegt, lautet sein Standardwert:<br /><br /> **https://tempuri.org/{service Vertrag Namespace} / {Dienstvertragsname} / {Vorgangsname}**|  
|<xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A>|False|Gibt an, ob die Workflowinstanz beibehalten werden soll, bevor die Antwortnachricht gesendet wird. Der Standardwert ist **FALSE**.|  
  
## <a name="see-also"></a>Siehe auch  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [Empfangen](../workflow-designer/receive-activity-designer.md)   
 [Senden](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)