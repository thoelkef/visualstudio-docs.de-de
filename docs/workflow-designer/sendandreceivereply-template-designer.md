---
title: "SendAndReceiveReply-Vorlagendesigner | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.ServiceModel.Activities.SendAndReceiveReply.UI"
  - "System.ServiceModel.Activities.ReceiveReply.UI"
ms.assetid: 818a8c84-6593-416d-b016-1d91b85ffb68
caps.latest.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# SendAndReceiveReply-Vorlagendesigner
Die **SendAndReceiveReply**\-Vorlage wird verwendet, um ein Paar vorkonfigurierter <xref:System.ServiceModel.Activities.Send>\- und <xref:System.ServiceModel.Activities.ReceiveReply>\-Aktivitäten innerhalb einer <xref:System.Activities.Statements.Sequence>\-Aktivität zu erstellen. Diese Aktivitäten sind sich einander entsprechende Teile eines Anforderungs\-\/Antwort\-Nachrichtenaustauschmusters auf dem Client.  
  
## Die SendAndReceiveReply\-Vorlage  
 Das Hinzufügen der **SendAndReceiveReply**\-Vorlage bewirkt neben der Erstellung der beiden Aktivitäten <xref:System.ServiceModel.Activities.Send> und <xref:System.ServiceModel.Activities.ReceiveReply> innerhalb einer <xref:System.Activities.Statements.Sequence>\-Aktivität drei Dinge:  
  
1.  Die Eigenschaften <xref:System.ServiceModel.Activities.Send.OperationName%2A> und <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> der <xref:System.ServiceModel.Activities.Send>\-Aktivität werden konfiguriert.  
  
2.  Die Eigenschaft <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> der <xref:System.ServiceModel.Activities.ReceiveReply>\-Aktivität wird an die <xref:System.ServiceModel.Activities.Send>\-Aktivität gebunden.  
  
3.  In der übergeordneten Aktivität wird ein <xref:System.ServiceModel.Activities.CorrelationHandle> als Variable erstellt.  
  
### Verwenden des SendAndReceiveReply\-Vorlagen\-Designers  
 Der **SendAndReceiveReply**\-Aktivitätsdesigner befindet sich in der Kategorie **Messaging** der **Toolbox**, auf die Sie zugreifen können, indem Sie in [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] auf die Registerkarte **Toolbox** klicken. \(Sie können auch im Menü **Ansicht** den Befehl **Toolbox** auswählen oder STRG\+ALT\+X drücken.\)  
  
 Der **SendAndReceiveReply**\-Aktivitätsdesigner kann aus der **Toolbox** gezogen und auf der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]\-Oberfläche dort abgelegt werden, wo Aktivitäten normalerweise platziert werden.Dadurch wird eine <xref:System.ServiceModel.Activities.Send>\-Aktivität erstellt, die mit dem **Send**\-Aktivitätsdesigner konfiguriert werden kann, während die mit dieser Aktivität korrelierte <xref:System.ServiceModel.Activities.ReceiveReply>\-Aktivität mit dem **ReceiveReplyForSend**\-Designer konfiguriert wird.  
  
 [!INCLUDE[crabout](../test/includes/crabout_md.md)] der Verwendung des **Send**\-Designers bei der Konfiguration der <xref:System.ServiceModel.Activities.Send>\-Aktivität, finden Sie im Thema [Senden](../workflow-designer/send-activity-designer.md).  
  
 [!INCLUDE[crabout](../test/includes/crabout_md.md)] zur Verwendung des **ReceiveReplyForSend**\-Designers zur Konfiguration der <xref:System.ServiceModel.Activities.ReceiveReply>\-Aktivität, finden Sie im folgenden Abschnitt.  
  
### Eigenschaften von ReceiveReply  
 In der folgenden Tabelle werden die <xref:System.ServiceModel.Activities.ReceiveReply>\-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.Diese Eigenschaften können im Eigenschaftenraster bearbeitet werden, einige davon können auch in der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]\-Designeroberfläche bearbeitet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-----------------------|------------------|----------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Der optionale Anzeigename der <xref:System.ServiceModel.Activities.ReceiveReply>\-Aktivität.Der Standardwert lautet ReceiveReplyForSend.<br /><br /> Obwohl die Verwendung eines nicht standardmäßigen Werts für den benutzerfreundlichen <xref:System.Activities.Activity.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen solchen Wert zu verwenden.|  
|<xref:System.ServiceModel.Activities.ReceiveReply.Request%2A>|True|Verweis auf die dieser <xref:System.ServiceModel.Activities.ReceiveReply>\-Aktivität zugeordnete <xref:System.ServiceModel.Activities.Send>\-Aktivität.Diese Eigenschaft darf nicht **null** sein.Die <xref:System.ServiceModel.Activities.Send>\-Aktivität und die <xref:System.ServiceModel.Activities.ReceiveReply>\-Aktivität werden zusammen verwendet, um auf dem Client ein Anforderungs\-\/Antwort\-Messagingmuster zu modellieren.Diese Eigenschaft gibt an, welche <xref:System.ServiceModel.Activities.Send>\-Aktivität zugeordnet wird.Im Designer können Sie diese Eigenschaft nicht bearbeiten, da sie automatisch an die <xref:System.ServiceModel.Activities.Send>\-Aktivität gebunden wird, anhand der Sie die <xref:System.ServiceModel.Activities.ReceiveReply>\-Aktivität erstellt haben.|  
|<xref:System.ServiceModel.Activities.ReceiveReply.Content%2A>|False|Gibt die zu empfangende Nachricht oder den zu empfangenden Parameterinhalt an.Dies kann entweder eine <xref:System.ServiceModel.Activities.ReceiveMessageContent>\-Aktivität oder eine <xref:System.ServiceModel.Activities.ReceiveParametersContent>\-Aktivität sein.Bearbeiten Sie diese Eigenschaft, indem Sie im Eigenschaftenraster neben dem **Content**\-Feld auf die Schaltfläche mit den Auslassungspunkten klicken. Oder klicken Sie neben der Bezeichnung **Inhalt** auf der Designer\-Oberfläche der **Receive**\-Aktivität auf die Schaltfläche **Definieren…**.Durch beide wird das Dialogfeld **Inhaltsdefinition** eingeblendet.[!INCLUDE[crabout](../test/includes/crabout_md.md)] zur Verwendung dieses Dialogfelds finden Sie im Thema [Inhaltsdefinition \(Dialogfeld\)](../workflow-designer/content-definition-dialog-box.md).|  
|<xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A>|False|Gibt die Auflistung von <xref:System.ServiceModel.Activities.CorrelationInitializer>\-Objekten an, die mehrere <xref:System.ServiceModel.Activities.CorrelationHandle>\-Objekte initialisiert, die diese <xref:System.ServiceModel.Activities.Receive>\-Aktivität im Workflow konfigurieren.Klicken Sie im Eigenschaftenraster auf die Schaltfläche mit den Auslassungspunkten neben der <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A>\-Eigenschaft, um das Dialogfeld **Korrelationsinitialisierer hinzufügen** zu öffnen.[!INCLUDE[crabout](../test/includes/crabout_md.md)] zur Verwendung dieses Dialogfelds finden Sie im Thema [CorrelationInitializers hinzufügen \(Dialogfeld\)](../workflow-designer/add-correlationinitializers-dialog-box.md).|  
|<xref:System.ServiceModel.Activities.ReceiveReply.Action%2A>|False|Gibt den Aktionsheader der Nachricht an.Ist er nicht explizit festgelegt, lautet sein Standardwert:<br /><br /> **https:\/\/tempuri.org\/{Dienstvertragsnamespace}\/{Dienstvertragsname}\/{Vorgangsname}.**|  
  
## Siehe auch  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [Receive](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Senden](../workflow-designer/send-activity-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)