---
title: "Inhaltsdefinition (Dialogfeld) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "MessageContent.UI"
ms.assetid: 7e4237c3-90a1-4149-bd8a-3643d1dde0df
caps.latest.revision: 3
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# Inhaltsdefinition (Dialogfeld)
Das Dialogfeld **Inhaltsdefinition** wird in [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] verwendet, um die **Content**\-Eigenschaften der Aktivitäten <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply> und <xref:System.ServiceModel.Activities.ReceiveReply> zu konfigurieren.[!INCLUDE[crabout](../test/includes/crabout_md.md)] zu den Aktivitätsdesignern, die dieses Dialogfeld verwenden, finden Sie in den Themen [Senden](../workflow-designer/send-activity-designer.md), [Receive](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) und [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md).  
  
 In der folgenden Tabelle werden die Benutzeroberflächenelemente des Dialogfelds **Korrelation initialisieren** beschrieben.  
  
|Benutzeroberflächenelement|Beschreibung|  
|--------------------------------|------------------|  
|**Nachricht**|Gibt den Nachrichteninhalt mit dem Ausdruckstextfeld **Nachrichtendaten** und den Typ mit dem Dropdownlistenfeld **Nachrichtentyp** an.Standardmäßig wird in der **Inhaltsdefinition** der <xref:System.ServiceModel.Activities.ReceiveMessageContent>\-Typ verwendet, der einen <xref:System.ServiceModel.Channels.Message>\-Typ oder einen Nachrichtenvertragstyp in der Workflowdienstdefinition erwartet.|  
|**Parameter**|Klicken Sie auf das Optionsfeld **Parameter**, um den <xref:System.ServiceModel.Activities.ReceiveParametersContent>\-Typ zu verwenden, der einen Datenvertrag erwartet.Legen Sie mithilfe des Datenrasters eine generische Auflistung von <xref:System.Activities.OutArgument>\-Schlüssel\-Wert\-Paaren fest, deren Werte variablen Parametern im aktuellen Workflow zugewiesen werden.|  
  
 Das Dialogfeld **Inhaltsdefinition** wird von den Aktivitätsdesignern für **Send**, **Receive**, **ReceiveAndSendReply** und **SendAndReceiveReply** verwendet.Auf diese Designer wird auf ähnliche Weise zugegriffen. Zur Veranschaulichung des Verfahrens wird hier der Receive\-Fall verwendet.  
  
 Der **Receive**\-Aktivitätsdesigner kann aus der **Toolbox** gezogen und auf der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]\-Oberfläche dort abgelegt werden, wo Aktivitäten normalerweise platziert werden.Dadurch wird eine <xref:System.ServiceModel.Activities.Receive>\-Aktivität mit dem standardmäßigen <xref:System.Activities.Activity.DisplayName%2A> Receive erstellt.Wählen Sie den **Receive**\-Aktivitätsdesigner aus, und klicken Sie im Eigenschaftenraster neben dem \(Inhalt\) Text für die **Content**\-Eigenschaft auf die Schaltfläche mit den Auslassungspunkten, damit das Dialogfeld **Inhaltsdefinition** angezeigt wird.  
  
 Der Inhalt kann innerhalb des Abschnitts **Nachricht** für eine <xref:System.ServiceModel.Activities.ReceiveMessageContent>\-Aktivität oder innerhalb des Abschnitts **Parameter** für eine <xref:System.ServiceModel.Activities.ReceiveParametersContent>\-Aktivität angegeben werden.  
  
## Siehe auch  
 [Workflow\-Designer\-Benutzeroberflächenhilfe](../workflow-designer/workflow-designer-ui-help.md)