---
title: "CorrelatesOn-Definition (Dialogfeld) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CorrelatesOnDefinition.UI"
ms.assetid: 8b2b627a-f236-4479-aa09-525df65e3413
caps.latest.revision: 6
caps.handback.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# CorrelatesOn-Definition (Dialogfeld)
Das Dialogfeld **CorrelatesOn** wird in [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] verwendet, um die <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>\-Eigenschaft einer <xref:System.ServiceModel.Activities.Receive>\-Aktivität zu bearbeiten.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)] dem folgenden Thema: [Receive](../workflow-designer/receive-activity-designer.md).  
  
 Die Korrelation zwischen <xref:System.ServiceModel.Activities.Receive>\-Aktivitäten gibt an, in welcher Beziehung verschiedene Dienstvorgänge in einem Workflow miteinander stehen.  
  
 In der folgenden Tabelle werden die Benutzeroberflächenelemente des Dialogfelds **CorrelatesOn** beschrieben.  
  
|Benutzeroberflächenelement|Beschreibung|  
|--------------------------------|------------------|  
|**CorrelatesWith**|Die <xref:System.ServiceModel.Activities.CorrelationHandle>\-Instanz, die verwendet wird, um die Nachricht an die entsprechende Workflowinstanz weiterzuleiten.|  
|**XPath\-Abfragen**|Ein Schlüssel\-Wert\-Paar, das die Abfragen enthält, mit denen Korrelationsdaten aus eingehenden Nachrichten extrahiert werden.Dies entspricht der <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>\-Eigenschaft.Die XPath\-Abfragen sind in einem <xref:System.ServiceModel.MessageQuerySet>\-Objekt enthalten.|  
  
## So öffnen Sie das Dialogfeld CorrelatesOn  
 Der **Receive**\-Aktivitätsdesigner kann aus der **Toolbox** gezogen und auf der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]\-Oberfläche dort abgelegt werden, wo Aktivitäten normalerweise platziert werden.Dadurch wird eine <xref:System.ServiceModel.Activities.Receive>\-Aktivität mit dem standardmäßigen <xref:System.Activities.Activity.DisplayName%2A> Receive erstellt.Wählen Sie den **Receive**\-Aktivitätsdesigner aus, und klicken Sie im Eigenschaftenraster neben dem \(Collection\) Text für die **CorrelatesOn**\-Eigenschaft auf die Schaltfläche mit den Auslassungspunkten, damit das Dialogfeld **CorrelatesOn Definition** angezeigt wird.  
  
## Siehe auch  
 <xref:System.ServiceModel.Activities.Receive>   
 [CorrelationInitializers hinzufügen \(Dialogfeld\)](../workflow-designer/add-correlationinitializers-dialog-box.md)   
 [Add Correlation Dialog Box](http://msdn.microsoft.com/de-de/9e41a149-e8ab-41b1-8886-ea06a63041b6)   
 [ Korrelation initialisieren \(Dialogfeld\)](../workflow-designer/initialize-correlation-dialog-box.md)