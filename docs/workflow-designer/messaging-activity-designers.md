---
title: "Messaging-Aktivit&#228;tsdesigner | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 897e63cf-a42f-4edd-876f-c4ccfffaf6d6
caps.latest.revision: 7
caps.handback.revision: 7
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Messaging-Aktivit&#228;tsdesigner
Messaging\-Aktivitätsdesigner werden verwendet, um Messaging\-Aktivitäten zu erstellen und zu konfigurieren, die [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)]\-Nachrichten in einer [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)]\-Anwendung senden und empfangen.Der [!INCLUDE[netfx40_long](../workflow-designer/includes/netfx40_long_md.md)] führt fünf Messaging\-Aktivitäten ein, und der [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] stellt zwei neue Vorlagen\-Designer bereit, die Ihnen ermöglichen, das Messaging innerhalb eines Workflows zu verwalten.Die Themen, die in diesem Abschnitt enthalten und in der folgenden Tabelle aufgeführt sind, enthalten Anleitungen dazu, wie die [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]\-Aktivitäts\- und Vorlagen\-Designer verwendet werden.  
  
## In diesem Abschnitt  
  
|Messagingaktivität|Beschreibung|  
|------------------------|------------------|  
|[CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)|Erstellt und konfiguriert eine <xref:System.ServiceModel.Activities.CorrelationScope>\-Aktivität, die die implizite Verwaltung von untergeordneten Messagingaktivitäten mit einem <xref:System.ServiceModel.Activities.CorrelationHandle>\-Objekt bereitstellt.|  
|[InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)|Erstellt und konfiguriert eine <xref:System.ServiceModel.Activities.InitializeCorrelation>\-Aktivität, die verwendet wird, um eine Korrelation zu initialisieren, ohne eine Nachricht zu senden oder zu empfangen.|  
|[Receive](../workflow-designer/receive-activity-designer.md)|Erstellt und konfiguriert eine <xref:System.ServiceModel.Activities.Receive>\-Aktivität, die eine Nachricht von einem Dienst empfängt.|  
|[ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)|Erstellt innerhalb einer <xref:System.Activities.Statements.Sequence>\-Aktivität ein vorkonfiguriertes Paar von <xref:System.ServiceModel.Activities.Send>\-Aktivität und <xref:System.ServiceModel.Activities.ReceiveReply>\-Aktivität.|  
|[Senden](../workflow-designer/send-activity-designer.md)|Erstellt und konfiguriert eine <xref:System.ServiceModel.Activities.Send>\-Aktivität, die eine Nachricht an einen Dienst sendet.|  
|[SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)|Erstellt innerhalb einer <xref:System.Activities.Statements.Sequence>\-Aktivität ein vorkonfiguriertes Paar von <xref:System.ServiceModel.Activities.Receive>\-Aktivität und <xref:System.ServiceModel.Activities.SendReply>\-Aktivität.|  
|[TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)|Erstellt und konfiguriert eine <xref:System.ServiceModel.Activities.TransactedReceiveScope>\-Aktivität, welche den Transaktionsfluss in einen Workflow ermöglicht.|  
  
## Referenz  
 <xref:System.Activities.Activity>  
  
 <xref:System.ServiceModel.Activities.CorrelationScope>  
  
 <xref:System.ServiceModel.Activities.Receive>  
  
 <xref:System.ServiceModel.Activities.Send>  
  
 <xref:System.ServiceModel.Activities.ReceiveReply>  
  
 <xref:System.ServiceModel.Activities.SendReply>  
  
 <xref:System.ServiceModel.Activities.TransactedReceiveScope>  
  
## Verwandte Abschnitte  
 Andere Typen von Aktivitätsdesignern werden in den folgenden Themen behandelt.  
  
 [Ablaufsteuerung](../workflow-designer/control-flow-activity-designers.md)  
  
 [Verwenden der Aktivitätsdesigner](../workflow-designer/using-the-activity-designers.md)  
  
 [Flussdiagramm](../workflow-designer/flowchart-activity-designers.md)  
  
 [Laufzeit](../workflow-designer/runtime-activity-designers.md)  
  
 [Primitive](../workflow-designer/primitives-activity-designers.md)  
  
 [Transaktion](../workflow-designer/transaction-activity-designers.md)  
  
 [Auflistung](../workflow-designer/collection-activity-designers.md)  
  
 [Fehlerbehandlung](../workflow-designer/error-handling-activity-designers.md)  
  
## Externe Ressourcen  
 [Verwenden der Aktivitätsdesigner](../workflow-designer/using-the-activity-designers.md)