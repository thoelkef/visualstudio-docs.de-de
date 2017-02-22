---
title: "Compensate-Aktivit&#228;tsdesigner | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Compensate.UI"
ms.assetid: 7347c947-bfff-4bad-becd-5cd23e7b24cd
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Compensate-Aktivit&#228;tsdesigner
Der **Compensate**\-Aktivitätsdesigner wird verwendet, um eine <xref:System.Activities.Statements.Compensate>\-Aktivität zu erstellen und zu konfigurieren.  
  
## Die Compensate\-Aktivität  
 Die <xref:System.Activities.Statements.Compensate>\-Aktivität ruft den <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> explizit für eine in einem <xref:System.Activities.Statements.CompensableActivity>\-Objekt enthaltene Aktivität auf.Wenn die <xref:System.Activities.Statements.Compensate>\-Aktivität nicht innerhalb des <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> oder <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> einer <xref:System.Activities.Statements.CompensableActivity>\-Instanz verwendet wird, dann müssen Sie die <xref:System.Activities.Statements.Compensate.Target%2A>\-Eigenschaft angeben.  
  
 Das vom <xref:System.Activities.Statements.Compensate.Target%2A> angegebene <xref:System.Activities.Statements.CompensationToken>\-Token stellt eine Möglichkeit dar, eine <xref:System.Activities.Statements.CompensableActivity>\-Instanz explizit zu bestätigen oder zu kompensieren, nachdem der <xref:System.Activities.Statements.CompensableActivity.Body%2A>\-Teil der <xref:System.Activities.Statements.CompensableActivity>\-Instanz erfolgreich beendet wurde.  
  
### Verwenden des Compensate\-Aktivitätsdesigners  
 Der **Compensate**\-Aktivitätsdesigner befindet sich in der Kategorie **Transaktion** der **Toolbox**, auf die Sie zugreifen können, indem Sie auf der linken Seite von [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] auf die Registerkarte **Toolbox** klicken. \(Sie können auch im Menü **Ansicht** den Befehl **Toolbox** auswählen oder STRG\+ALT\+X drücken.\)  
  
 Der **Compensate**\-Aktivitätsdesigner kann aus der **Toolbox** gezogen und auf der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]\-Oberfläche dort abgelegt werden, wo Aktivitäten normalerweise platziert werden, etwa innerhalb einer <xref:System.Activities.Statements.Sequence>.Daraufhin wird eine <xref:System.Activities.Statements.Compensate>\-Aktivität mit dem <xref:System.Activities.Activity.DisplayName%2A>\-Standardwert Compensate erstellt.Der <xref:System.Activities.Activity.DisplayName%2A>\-Wert kann im Header des **Compensate**\-Aktivitätsdesigners oder im Feld **DisplayName** des Eigenschaftenrasters bearbeitet werden.  
  
### Die Compensate\-Eigenschaften  
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.CancellationScope>\-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.Die <xref:System.Activities.Activity.DisplayName%2A>\-Eigenschaften kann im Eigenschaftenraster und auf der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]\-Oberfläche bearbeitet werden, die <xref:System.Activities.Statements.Compensate.Target%2A>\- Eigenschaften muss jedoch im Eigenschaftenraster bearbeitet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-----------------------|------------------|----------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Gibt den optionalen Anzeigenamen der <xref:System.Activities.Statements.Compensate>\-Aktivität an.Der Standardwert lautet Compensate.|  
|<xref:System.Activities.Statements.Compensate.Target%2A>|True|Gibt das <xref:System.Activities.InArgument%601>\-Argument an, welches das <xref:System.Activities.Statements.CompensationToken>\-Token für diese <xref:System.Activities.Statements.Compensate>\-Aktivität enthält.|  
  
## Siehe auch  
 [Transaktion](../workflow-designer/transaction-activity-designers.md)   
 [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)   
 [Compensate Activity Designer](../workflow-designer/compensate-activity-designer.md)   
 [Confirm](../workflow-designer/confirm-activity-designer.md)   
 [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)