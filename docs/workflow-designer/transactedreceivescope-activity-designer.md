---
title: "TransactedReceiveScope-Aktivit&#228;tsdesigner | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.ServiceModel.Activities.TransactedReceiveScope.UI"
ms.assetid: 7ca93aad-4e83-4d81-90f4-998ee114d9b6
caps.latest.revision: 4
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# TransactedReceiveScope-Aktivit&#228;tsdesigner
Der **TransactedReceiveScope**\-Designer wird verwendet, um eine <xref:System.ServiceModel.Activities.TransactedReceiveScope>\-Aktivität zu erstellen und zu konfigurieren.  
  
## Die TransactedReceiveScope\-Aktivität  
 Die <xref:System.ServiceModel.Activities.TransactedReceiveScope>\-Aktivität ermöglicht es Ihnen, eine Transaktion in Servertransaktionen einzubinden, die von einem Workflow oder einem Verteiler erstellt werden.  
  
### Verwenden des TransactedReceiveScope\-Aktivitätsdesigners  
 Der **TransactedReceiveScope**\-Aktivitätsdesigner befindet sich in der Kategorie **Messaging** der **Toolbox**, auf die Sie zugreifen können, indem Sie in [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] auf die Registerkarte **Toolbox** klicken. \(Sie können auch im Menü **Ansicht** den Befehl **Toolbox** auswählen oder STRG\+ALT\+X drücken.\)  
  
 Der **TransactedReceiveScope**\-Aktivitätsdesigner kann aus der **Toolbox** gezogen und auf der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]\-Oberfläche dort abgelegt werden, wo Aktivitäten normalerweise platziert werden.Daraufhin wird eine <xref:System.ServiceModel.Activities.TransactedReceiveScope>\-Aktivität mit dem **DisplayName**\-Standardwert TransactedReceiveScope erstellt.Der <xref:System.Activities.Activity.DisplayName%2A>\-Wert kann im Header des **TransactedReceiveScope**\-Aktivitätsdesigners oder im Feld **DisplayName** des Eigenschaftenrasters bearbeitet werden.  
  
 Der **TransactedReceiveScope**\-Designer enthält die Felder **Request** und **Body**.Diese werden verwendet, um die <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>\-Eigenschaft, die eine <xref:System.ServiceModel.Activities.Receive>\-Aktivität angibt, und die <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>\-Eigenschaft zu konfigurieren, die eine andere <xref:System.Activities.Activity>\-Instanz angibt.<xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> erstellt eine Transaktion.Die Transaktion wird dann dem Geltungsbereich der <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>\-Instanz zugeordnet, damit jede Aktivität in diesem Bereich in dieser Transaktion ausgeführt wird.  
  
### Die TransactedReceiveScope\-Eigenschaften  
 In der folgenden Tabelle werden die <xref:System.ServiceModel.Activities.TransactedReceiveScope>\-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.Diese <xref:System.Activities.Activity.DisplayName%2A>\-Eigenschaft kann im Eigenschaftenraster oder in der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]\-Oberfläche bearbeitet werden, die anderen Eigenschaften müssen jedoch in der Entwurfsoberfläche bearbeitet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-----------------------|------------------|----------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Der optionale Anzeigename der <xref:System.ServiceModel.Activities.TransactedReceiveScope>\-Aktivität.Der Standardwert lautet TransactedReceiveScope.<br /><br /> Obwohl der <xref:System.Activities.Activity.DisplayName%2A>\-Name nicht unbedingt erforderlich ist, wird als Best Practice empfohlen, einen Anzeigenamen zu verwenden.|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>|True|Legt eine <xref:System.ServiceModel.Activities.Receive>\-Aktivität im **Request**\-Block auf der Aktivitätsdesigneroberfläche ab.|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>|False|Legt eine <xref:System.Activities.Activity>\-Instanz im **Body**\-Block auf der Aktivitätsdesigneroberfläche ab.|  
  
## Siehe auch  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [Receive](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Senden](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)