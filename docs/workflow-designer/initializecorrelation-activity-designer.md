---
title: "InitializeCorrelation-Aktivit&#228;tsdesigner | Microsoft Docs"
ms.custom: ""
ms.date: "11/23/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.ServiceModel.Activities.InitializeCorrelation.UI"
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
caps.latest.revision: 6
caps.handback.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# InitializeCorrelation-Aktivit&#228;tsdesigner
Der **InitializeCorrelation**\-Aktivitätsdesigner wird verwendet, um eine <xref:System.ServiceModel.Activities.InitializeCorrelation>\-Aktivität zu erstellen, die verwendet wird, um eine Korrelation zwischen Nachrichten festzulegen und zu konfigurieren, bevor diese gesendet oder empfangen werden.  
  
## Die InitializeCorrelation\-Aktivität  
 Eine <xref:System.ServiceModel.Activities.InitializeCorrelation>\-Aktivität wird verwendet, um Korrelationen zu initialisieren, ohne eine Nachricht zu senden oder zu empfangen.In der Regel wird die Korrelation durch das Senden oder Empfangen einer Nachricht initialisiert.Wenn eine Korrelation festgelegt werden muss, bevor eine Nachricht gesendet oder empfangen wird, verwenden Sie <xref:System.ServiceModel.Activities.InitializeCorrelation>, um die Korrelation zu initialisieren.  
  
### Verwenden des InitializeCorrelation\-Aktivitätsdesigners  
 Der **InitializeCorrelation**\-Aktivitätsdesigner befindet sich in die Kategorie **Messaging** der **Toolbox**, auf die Sie zugreifen können, indem Sie in [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] auf die Registerkarte **Toolbox** klicken \(Sie können auch im Menü **Ansicht** den Befehl **Toolbox** auswählen oder STRG\+ALT\+X drücken\).  
  
 Der **InitializeCorrelation**\-Aktivitätsdesigner kann aus der **Toolbox** gezogen und auf der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]\-Oberfläche abgelegt werden.Daraufhin wird eine <xref:System.ServiceModel.Activities.InitializeCorrelation>\-Aktivität mit dem <xref:System.Activities.Activity.DisplayName%2A>\-Standardwert InitializeCorrelation erstellt.Der <xref:System.Activities.Activity.DisplayName%2A>\-'Wert kann im Header des **InitializeCorrelation**\-Aktivitätsdesigners oder dem Feld **DisplayName** des Fensters **Eigenschaften** bearbeitet werden.  
  
 Das <xref:System.ServiceModel.Activities.CorrelationHandle>\-Objekt kann im Feld **Korrelation** im Fenster **Eigenschaften** auf der **InitializeCorrelation**\-Aktivitätsdesigneroberfläche angegeben werden.  
  
 Wenn Sie auf die Schaltfläche mit den Auslassungspunkten neben dem Feld **CorrelationData** im Fenster **Eigenschaften** oder auf den Hinweistext "View …" auf der **InitializeCorrelation**\-Aktivitätsdesigneroberfläche klicken, wird das Dialogfeld **Korrelation initialisieren** angezeigt, in dem Sie das Korrelationshandle und die Schlüssel\-Wert\-Paare angeben können, die zum Initialisieren verwendet werden.[!INCLUDE[crabout](../test/includes/crabout_md.md)] zur Verwendung dieses Dialogfelds finden Sie im Thema [Typauflistungs\-Editor \(Dialogfeld\)](../workflow-designer/type-collection-editor-dialog-box.md).  
  
### Die InitializeCorrelation\-Eigenschaften  
 In der folgenden Tabelle werden die <xref:System.ServiceModel.Activities.InitializeCorrelation>\-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.Diese Eigenschaften können im Fenster **Eigenschaften** oder in der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]\-Oberfläche bearbeitet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-----------------------|------------------|----------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Gibt den Anzeigenamen der <xref:System.ServiceModel.Activities.InitializeCorrelation>\-Aktivität an.Der Standardwert lautet InitializeCorrelation.<br /><br /> Obwohl die Verwendung eines nicht standardmäßigen Werts für den benutzerfreundlichen <xref:System.Activities.Activity.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen solchen Wert zu verwenden.|  
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|False|Das <xref:System.ServiceModel.Activities.CorrelationHandle>\-Objekt, das verwendet wurde, um Workflowaktivitäten in der Korrelation zuzuordnen.|  
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|False|Ein Wörterbuch von Korrelationsdaten, die Nachrichten mit der Workflowinstanz verknüpft.<br /><br /> Verwenden Sie das Dialogfeld **Korrelation initialisieren** zum Konfigurieren von <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>.[!INCLUDE[crabout](../test/includes/crabout_md.md)] zur Verwendung dieses Dialogfelds finden Sie im Thema [Typauflistungs\-Editor \(Dialogfeld\)](../workflow-designer/type-collection-editor-dialog-box.md).|  
  
## Siehe auch  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [Receive](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Senden](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)