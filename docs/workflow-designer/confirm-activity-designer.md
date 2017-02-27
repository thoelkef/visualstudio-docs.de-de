---
title: "Confirm-Aktivit&#228;tsdesigner | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Confirm.UI"
ms.assetid: c753b67b-b0e7-462a-bb4e-ba8db04a078d
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Confirm-Aktivit&#228;tsdesigner
Der **Confirm**\-Aktivitätsdesigner wird verwendet, um eine <xref:System.Activities.Statements.Confirm>\-Aktivität zu erstellen und zu konfigurieren.  
  
## Die Confirm\-Aktivität  
 Die <xref:System.Activities.Statements.Confirm>\-Aktivität ruft den <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> explizit für eine in einem <xref:System.Activities.Statements.CompensableActivity>\-Objekt enthaltene Aktivität auf.Wenn die <xref:System.Activities.Statements.Confirm>\-Aktivität nicht innerhalb des <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> oder <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> einer <xref:System.Activities.Statements.CompensableActivity>\-Instanz verwendet wird, dann müssen Sie die <xref:System.Activities.Statements.Confirm.Target%2A>\-Eigenschaft angeben.  
  
 Das vom <xref:System.Activities.Statements.Compensate.Target%2A> angegebene <xref:System.Activities.Statements.CompensationToken>\-Token stellt eine Möglichkeit dar, eine <xref:System.Activities.Statements.CompensableActivity>\-Instanz explizit zu bestätigen oder zu kompensieren, nachdem der <xref:System.Activities.Statements.CompensableActivity.Body%2A>\-Teil der <xref:System.Activities.Statements.CompensableActivity>\-Instanz erfolgreich beendet wurde.  
  
### Verwenden des Confirm\-Aktivitätsdesigners  
 Der **Confirm**\-Aktivitätsdesigner befindet sich in der Kategorie **Transaktion** der **Toolbox**, auf die Sie zugreifen können, indem Sie auf der linken Seite von [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] auf die Registerkarte **Toolbox** klicken \(Sie können auch im Menü **Ansicht** den Befehl **Symbolleiste** auswählen oder STRG\+ALT\+X drücken\).  
  
 Der **Confirm**\-Aktivitätsdesigner kann aus der **Toolbox** gezogen und auf der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]\-Oberfläche dort abgelegt werden, wo Aktivitäten normalerweise platziert werden, etwa innerhalb einer <xref:System.Activities.Statements.Sequence>.Dadurch wird eine <xref:System.Activities.Statements.Confirm>\-Aktivität mit dem <xref:System.Activities.Activity.DisplayName%2A>\-Standardwert Confirm erstellt.Der <xref:System.Activities.Activity.DisplayName%2A>\-Wert kann im Header des **Confirm**\-Aktivitätsdesigners oder im Feld **DisplayName** des Eigenschaftenrasters bearbeitet werden.  
  
### Die Confirm\-Eigenschaften  
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.Confirm>\-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.Die <xref:System.Activities.Activity.DisplayName%2A>\-Eigenschaften kann im Eigenschaftenraster und auf der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]\-Oberfläche bearbeitet werden, die <xref:System.Activities.Statements.Confirm.Target%2A>\- Eigenschaften muss jedoch im Eigenschaftenraster bearbeitet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-----------------------|------------------|----------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Gibt den optionalen Anzeigenamen der <xref:System.Activities.Statements.CancellationScope>\-Aktivität an.Der Standardwert lautet Confirm.|  
|<xref:System.Activities.Statements.Confirm.Target%2A>|True|Gibt das <xref:System.Activities.InArgument%601>\-Argument an, welches das <xref:System.Activities.Statements.CompensationToken>\-Token für diese <xref:System.Activities.Statements.Confirm>\-Aktivität enthält.|  
  
## Siehe auch  
 [Transaktion](../workflow-designer/transaction-activity-designers.md)   
 [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)   
 [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)   
 [Compensate](../workflow-designer/compensate-activity-designer.md)   
 [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)