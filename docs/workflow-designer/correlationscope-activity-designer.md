---
title: "CorrelationScope-Aktivit&#228;tsdesigner | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.ServiceModel.Activities.CorrelationScope.UI"
ms.assetid: 75f20664-9042-464d-8e2b-148d365a2286
caps.latest.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# CorrelationScope-Aktivit&#228;tsdesigner
Der **CorrelationScope**\-Aktivitätsdesigner wird verwendet, um eine <xref:System.ServiceModel.Activities.CorrelationScope>\-Aktivität zu erstellen und zu konfigurieren, die die implizite Verwaltung untergeordneter Messagingaktivitäten mithilfe eines <xref:System.ServiceModel.Activities.CorrelationHandle>\-Objekts bereitstellt.  
  
## Die CorrelationScope\-Aktivität  
 Die <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>\-Eigenschaft gibt das <xref:System.ServiceModel.Activities.CorrelationHandle>\-Handle an, das zum Verwalten der untergeordneten Messagingaktivitäten verwendet wird.Die <xref:System.ServiceModel.Activities.Send>\-Aktivität und die <xref:System.ServiceModel.Activities.Receive>\-Aktivität, die im <xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>\-Objekt enthalten sind, werden so konfiguriert, dass sie die <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>\-Eigenschaft der übergeordneten <xref:System.ServiceModel.Activities.CorrelationScope>\-Aktivität verwenden, um die Korrelation auszuführen.  
  
### Verwenden des CorrelationScope\-Aktivitätsdesigners  
 Der **CorrelationScope**\-Aktivitätsdesigner befindet sich in der Kategorie **Messaging** der **Toolbox**, auf die Sie zugreifen können, indem Sie auf der linken Seite von [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] auf die Registerkarte **Toolbox** klicken. \(Sie können auch im Menü **Ansicht** den Befehl **Toolbox** auswählen oder STRG\+ALT\+X drücken.\)  
  
 Der **CorrelationScope**\-Aktivitätsdesigner kann aus der **Toolbox** gezogen werden und auf der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]\-Oberfläche abgelegt werden.Daraufhin wird eine <xref:System.ServiceModel.Activities.CorrelationScope>\-Aktivität mit einem **DisplayName**\-Standardwert CorrelationScope erstellt.Der <xref:System.Activities.Activity.DisplayName%2A>\-'Wert kann im Header des **CorrelationScope**\-Aktivitätsdesigners oder dem Feld **DisplayName** des **Eigenschaftenfensters** bearbeitet werden.  
  
 Um den von untergeordneten Messagingaktivitäten verwendeten <xref:System.ServiceModel.Activities.CorrelationHandle>\-Handle anzugeben, klicken Sie im **Eigenschaftenfenster** auf die Schaltfläche mit den Auslassungspunkten neben dem Feld **CorrelatesWith**, um das Dialogfeld **Ausdrucks\-Editor** anzuzeigen.Diese Eigenschaft kann auch in der Aktivitätsdesigneroberfläche festgelegt werden.  
  
 Die innerhalb der Korrelation geltenden Aktivitäten werden angegeben, indem ihre Designer innerhalb des **CorrelationScope**\-Designers im Feld **Body** abgelegt werden.  
  
### Die CorrelationScope\-Eigenschaften  
 In der folgenden Tabelle werden die <xref:System.ServiceModel.Activities.CorrelationScope>\-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.Diese Eigenschaften können entweder im **Eigenschaftenfenster** oder in der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]\-Designeroberfläche und oft in beiden Umgebungen bearbeitet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-----------------------|------------------|----------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Der optionale Anzeigename der <xref:System.ServiceModel.Activities.InitializeCorrelation>\-Aktivität.|  
|<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>|False|Gibt das <xref:System.ServiceModel.Activities.CorrelationHandle>\-Handle an, das zum Verwalten der untergeordneten Messagingaktivitäten verwendet wird.Wenn Sie diese Eigenschaft nicht festlegen, erstellt <xref:System.ServiceModel.Activities.CorrelationScope> automatisch einen impliziten <xref:System.ServiceModel.Activities.CorrelationHandle>.|  
|<xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>|False|Gibt die Aktivitäten im Bereich der Korrelation an.|  
  
## Siehe auch  
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [Receive](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Senden](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)