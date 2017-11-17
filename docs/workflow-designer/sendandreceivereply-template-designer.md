---
title: SendAndReceiveReply-Vorlagendesigner | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.SendAndReceiveReply.UI
- System.ServiceModel.Activities.ReceiveReply.UI
ms.assetid: 818a8c84-6593-416d-b016-1d91b85ffb68
caps.latest.revision: "6"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: be208d526fdc9f1d6f434425e3931b0f0a6510f5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="sendandreceivereply-template-designer"></a>SendAndReceiveReply-Vorlagendesigner
Die **SendAndReceiveReply** Vorlage dient dazu, erstellen Sie ein Paar von vorkonfiguriert, dass <xref:System.ServiceModel.Activities.Send> und <xref:System.ServiceModel.Activities.ReceiveReply> Aktivitäten innerhalb einer <xref:System.Activities.Statements.Sequence> Aktivität, die als Teil eines Anforderungs-/Antwort-Nachrichtenaustauschs korreliert werden Muster auf dem Client.  
  
## <a name="the-sendandreceivereply-template"></a>Die SendAndReceiveReply-Vorlage  
 Hinzufügen von **SendAndReceiveReply** -Vorlage bewirkt drei Dinge neben der Erstellung der <xref:System.ServiceModel.Activities.Send> und <xref:System.ServiceModel.Activities.ReceiveReply> Aktivitäten innerhalb einer <xref:System.Activities.Statements.Sequence> Aktivität:  
  
1.  Die Eigenschaften <xref:System.ServiceModel.Activities.Send.OperationName%2A> und <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> der <xref:System.ServiceModel.Activities.Send>-Aktivität werden konfiguriert.  
  
2.  Die Eigenschaft <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> der <xref:System.ServiceModel.Activities.ReceiveReply>-Aktivität wird an die <xref:System.ServiceModel.Activities.Send>-Aktivität gebunden.  
  
3.  Ein <xref:System.ServiceModel.Activities.CorrelationHandle> wird in der übergeordneten Aktivität als Variable erstellt.  
  
### <a name="using-the-sendandreceivereply-template-designer"></a>Verwenden des SendAndReceiveReply-Vorlagen-Designers  
 Die **SendAndReceiveReply** Aktivitäts-Designer finden Sie in der **Messaging** Kategorie der **Toolbox**, die erfolgt durch Klicken auf die **Toolbox**  Registerkarte [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (Wählen Sie alternativ **Symbolleiste** aus der **Ansicht** Menüs oder STRG + ALT + X drücken.)  
  
 Die **SendAndReceiveReply** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** gezogen und auf die [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] -Oberfläche ablegen, wo Aktivitäten normalerweise platziert werden. Dies erstellt eine <xref:System.ServiceModel.Activities.Send> Aktivität, die mit konfiguriert werden kann die **senden** Aktivitäts-Designer und korrelierte <xref:System.ServiceModel.Activities.ReceiveReply> , die konfiguriert werden können, mit der **ReceiveReplyForSend** Designer.  
  
 [!INCLUDE[crabout](../test/includes/crabout_md.md)]Mithilfe der **senden** -Designers zur Konfiguration der <xref:System.ServiceModel.Activities.Send> Aktivität, finden Sie unter der [senden](../workflow-designer/send-activity-designer.md) Thema.  
  
 [!INCLUDE[crabout](../test/includes/crabout_md.md)]Mithilfe der **ReceiveReplyForSend** -Designers zur Konfiguration der <xref:System.ServiceModel.Activities.ReceiveReply> Aktivität, finden Sie im folgenden Abschnitt.  
  
### <a name="properties-of-receivereply"></a>Eigenschaften von ReceiveReply  
 In der folgenden Tabelle werden die <xref:System.ServiceModel.Activities.ReceiveReply>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaftenraster bearbeitet werden, einige davon auf der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]-Designeroberfläche.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Der optionale Anzeigename der <xref:System.ServiceModel.Activities.ReceiveReply>-Aktivität. Der Standardwert lautet ReceiveReplyForSend.<br /><br /> Obwohl die Verwendung eines nicht standardmäßigen Werts für den benutzerfreundlichen <xref:System.Activities.Activity.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen solchen Wert zu verwenden.|  
|<xref:System.ServiceModel.Activities.ReceiveReply.Request%2A>|True|Verweis auf die dieser <xref:System.ServiceModel.Activities.Send>-Aktivität zugeordnete <xref:System.ServiceModel.Activities.ReceiveReply>-Aktivität. Diese Eigenschaft muss nicht **null**. Die <xref:System.ServiceModel.Activities.Send>-Aktivität und die <xref:System.ServiceModel.Activities.ReceiveReply>-Aktivität werden zusammen verwendet, um auf dem Client ein Anforderungs-/Antwort-Messagingmuster zu modellieren. Diese Eigenschaft gibt an, welche <xref:System.ServiceModel.Activities.Send>-Aktivität zugeordnet wird. Im Designer können Sie diese Eigenschaft nicht bearbeiten, da sie automatisch an die <xref:System.ServiceModel.Activities.Send>-Aktivität gebunden wird, anhand der Sie die <xref:System.ServiceModel.Activities.ReceiveReply>-Aktivität erstellt haben.|  
|<xref:System.ServiceModel.Activities.ReceiveReply.Content%2A>|False|Gibt die zu empfangende Nachricht oder den zu empfangenden Parameterinhalt an. Dies kann entweder eine <xref:System.ServiceModel.Activities.ReceiveMessageContent>-Aktivität oder eine <xref:System.ServiceModel.Activities.ReceiveParametersContent>-Aktivität sein. Diese Eigenschaft bearbeiten, indem Sie auf die Schaltfläche mit den Auslassungspunkten neben der **Content** Feld im Eigenschaftenraster oder indem Sie auf die **definieren...**  neben der **Content** auf bezeichnen die **Receive** aktivitätsdesigneroberfläche. Beides anzeigen der **Inhaltsdefinition** Dialogfeld. [!INCLUDE[crabout](../test/includes/crabout_md.md)]zum Verwenden Sie dieses Feld finden Sie unter der [Content Vorgangsdefinition (Dialogfeld)](../workflow-designer/content-definition-dialog-box.md) Thema.|  
|<xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A>|False|Gibt die Auflistung von <xref:System.ServiceModel.Activities.CorrelationInitializer>-Objekten an, die mehrere <xref:System.ServiceModel.Activities.CorrelationHandle>-Objekte initialisiert, die diese <xref:System.ServiceModel.Activities.Receive>-Aktivität im Workflow konfigurieren. Klicken Sie auf die Schaltfläche mit den Auslassungszeichen neben der <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> Eigenschaft im Eigenschaftenraster So öffnen die **Korrelationsinitialisierer hinzufügen** (Dialogfeld). [!INCLUDE[crabout](../test/includes/crabout_md.md)]Verwenden dieses Kontrollkästchen, finden Sie unter der [CorrelationInitializers-Dialogfeld hinzufügen](../workflow-designer/add-correlationinitializers-dialog-box.md) Thema.|  
|<xref:System.ServiceModel.Activities.ReceiveReply.Action%2A>|False|Gibt den Aktionsheader der Nachricht an. Ist er nicht explizit festgelegt, lautet sein Standardwert:<br /><br /> **https://tempuri.org/ {Dienstvertragsnamespace} / {Dienstvertragsname} / {Vorgangsname}.**|  
  
## <a name="see-also"></a>Siehe auch  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [Empfangen](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Senden](../workflow-designer/send-activity-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)