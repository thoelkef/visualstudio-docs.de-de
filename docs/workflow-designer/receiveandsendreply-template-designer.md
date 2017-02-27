---
title: "ReceiveAndSendReply-Vorlagendesigner | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.ServiceModel.Activities.ReceiveAndSendReply.UI"
  - "System.ServiceModel.Activities.SendReply.UI"
ms.assetid: d1d9a058-df7e-48f5-a2e7-3caeeba7eaa6
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# ReceiveAndSendReply-Vorlagendesigner
Die **ReceiveAndSendReply**\-Vorlage wird verwendet, um ein Paar vorkonfigurierter <xref:System.ServiceModel.Activities.Receive>\- und <xref:System.ServiceModel.Activities.SendReply>\-Aktivitäten innerhalb einer <xref:System.Activities.Statements.Sequence>\-Aktivität zu erstellen. Diese Aktivitäten sind sich einander entsprechende Teile eines Anforderungs\-\/Antwort\-Nachrichtenaustauschmusters auf dem Server.  
  
## Die ReceiveAndSendReply\-Vorlage  
 Das Hinzufügen der **ReceiveAndSendReply**\-Vorlage bewirkt neben der Erstellung der beiden Aktivitäten <xref:System.ServiceModel.Activities.Receive> und <xref:System.ServiceModel.Activities.SendReply> mit einer <xref:System.Activities.Statements.Sequence>\-Aktivität drei Dinge:  
  
1.  Die Eigenschaften <xref:System.ServiceModel.Activities.Receive.OperationName%2A> und <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> der <xref:System.ServiceModel.Activities.Receive>\-Aktivität werden konfiguriert.  
  
2.  Die Eigenschaft <xref:System.ServiceModel.Activities.SendReply.Request%2A> der <xref:System.ServiceModel.Activities.Receive>\-Aktivität wird an die <xref:System.ServiceModel.Activities.Send>\-Aktivität gebunden.  
  
3.  Ein <xref:System.ServiceModel.Activities.CorrelationHandle> wird in der übergeordneten Aktivität als Variable erstellt.  
  
### Verwenden der ReceiveAndSendReply\-Vorlage im Designer  
 Der **ReceiveAndSendReply**\-Aktivitätsdesigner befindet sich in der Kategorie **Messaging** der **Toolbox**, auf die Sie zugreifen können, indem Sie in [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] auf die Registerkarte **Toolbox** klicken \(Sie können auch im Menü **Ansicht** den Befehl **Symbolleiste** auswählen oder STRG\+ALT\+X drücken\).  
  
 Der **ReceiveAndSendReply**\-Aktivitätsdesigner kann aus der **Toolbox** gezogen und auf der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]\-Oberfläche dort abgelegt werden, wo Aktivitäten normalerweise platziert werden.Dadurch wird eine <xref:System.ServiceModel.Activities.Receive>\-Aktivität erstellt, die mit dem **Send**\-Aktivitätsdesigner konfiguriert werden kann, während die mit dieser Aktivität korrelierte <xref:System.ServiceModel.Activities.SendReply>\-Aktivität mit dem SendReplyToReceive\-Designer konfiguriert wird.  
  
 [!INCLUDE[crabout](../test/includes/crabout_md.md)] der Verwendung des **Receive**\-Designers bei der Konfiguration der <xref:System.ServiceModel.Activities.Receive>\-Aktivität, finden Sie im Thema [Receive](../workflow-designer/receive-activity-designer.md).  
  
 [!INCLUDE[crabout](../test/includes/crabout_md.md)] der Verwendung des **SendReplyToReceive**\-Designers bei der Konfiguration der <xref:System.ServiceModel.Activities.SendReply>\-Aktivität, finden Sie im folgenden Abschnitt.  
  
### Eigenschaften von SendReply  
 In der folgenden Tabelle werden die Eigenschaften von <xref:System.ServiceModel.Activities.SendReply> gezeigt, und es wird beschrieben, wie sie im Designer verwendet werden.Diese Eigenschaften können im Eigenschaftenraster bearbeitet werden, einige davon auf der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]\-Designeroberfläche.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-----------------------|------------------|----------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Der optionale Anzeigename der <xref:System.ServiceModel.Activities.SendReply>\-Aktivität.Der Standardname lautet SendReplyToReceive.<br /><br /> Obwohl die Verwendung eines nicht standardmäßigen Werts für den benutzerfreundlichen <xref:System.Activities.Activity.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen solchen Wert zu verwenden.|  
|<xref:System.ServiceModel.Activities.SendReply.Request%2A>|True|Verweis auf die dieser <xref:System.ServiceModel.Activities.SendReply>\-Aktivität zugeordnete <xref:System.ServiceModel.Activities.Receive>\-Aktivität.Diese Eigenschaft darf nicht **null** sein.Die <xref:System.ServiceModel.Activities.Receive>\-Aktivität und die <xref:System.ServiceModel.Activities.SendReply>\-Aktivität werden zusammen verwendet, um ein Anforderungs\-\/Antwort\-Messagingmuster auf dem Server zu modellieren.Diese Eigenschaft gibt an, welche <xref:System.ServiceModel.Activities.Send>\-Aktivität zugeordnet wird.Im Designer können Sie diese Eigenschaft nicht bearbeiten, da sie automatisch an die <xref:System.ServiceModel.Activities.Send>\-Aktivität gebunden wird, anhand der Sie die <xref:System.ServiceModel.Activities.SendReply>\-Aktivität erstellt haben.|  
|<xref:System.ServiceModel.Activities.SendReply.Content%2A>|False|Gibt die zu empfangende Nachricht oder den zu empfangenden Parameterinhalt an.Dies kann entweder eine <xref:System.ServiceModel.Activities.ReceiveMessageContent>\-Aktivität oder eine <xref:System.ServiceModel.Activities.ReceiveParametersContent>\-Aktivität sein.Bearbeiten Sie diese Eigenschaft, indem Sie im Eigenschaftenraster neben dem **Content**\-Feld auf die Schaltfläche mit den Auslassungspunkten klicken. Oder klicken Sie neben der Bezeichnung **Inhalt** auf der Designer\-Oberfläche der **Receive**\-Aktivität auf die Schaltfläche **Definieren…**.Durch beide wird das Dialogfeld **Inhaltsdefinition** eingeblendet.[!INCLUDE[crabout](../test/includes/crabout_md.md)] zur Verwendung dieses Dialogfelds finden Sie im Thema [Inhaltsdefinition \(Dialogfeld\)](../workflow-designer/content-definition-dialog-box.md).|  
|<xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A>|False|Gibt die Auflistung von <xref:System.ServiceModel.Activities.CorrelationInitializer>\-Objekten an, die mehrere <xref:System.ServiceModel.Activities.CorrelationHandle>\-Objekte initialisiert, die diese <xref:System.ServiceModel.Activities.Receive>\-Aktivität im Workflow konfigurieren.Klicken Sie im Eigenschaftenraster auf die Schaltfläche mit den Auslassungspunkten neben der <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A>\-Eigenschaft, um das Dialogfeld **Korrelationsinitialisierer hinzufügen** zu öffnen.[!INCLUDE[crabout](../test/includes/crabout_md.md)] zur Verwendung dieses Dialogfelds finden Sie im Thema [CorrelationInitializers hinzufügen \(Dialogfeld\)](../workflow-designer/add-correlationinitializers-dialog-box.md).|  
|<xref:System.ServiceModel.Activities.SendReply.Action%2A>|False|Gibt den Aktionsheader der Nachricht an.Ist er nicht explizit festgelegt, lautet sein Standardwert:<br /><br /> **https:\/\/tempuri.org\/{Dienstvertragsnamespace}\/{Dienstvertragsname}\/{Vorgangsname}**|  
|<xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A>|False|Gibt an, ob die Workflowinstanz beibehalten werden soll, bevor die Antwortnachricht gesendet wird.Der Standardwert ist **false**.|  
  
## Siehe auch  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [Receive](../workflow-designer/receive-activity-designer.md)   
 [Senden](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)