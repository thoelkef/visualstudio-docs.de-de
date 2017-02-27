---
title: "TransactionScope-Aktivit&#228;tsdesigner | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.TransactionScope.UI"
ms.assetid: 8d7ebfc6-7478-4888-b3b0-b14f296096af
caps.latest.revision: 8
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# TransactionScope-Aktivit&#228;tsdesigner
Der **TransactionScope**\-Aktivitätsdesigner wird verwendet, um eine <xref:System.Activities.Statements.TransactionScope>\-Aktivität zu erstellen und zu konfigurieren.  
  
## Die TransactionScope\-Aktivität  
 Die <xref:System.Activities.Statements.TransactionScope>\-Aktivität führt die in ihr enthaltene Aktivität in einer einzelnen Transaktion aus.Der Commit\-Vorgang der Transaktion wird ausgeführt, sobald die <xref:System.Activities.Statements.TransactionScope.Body%2A>\-Aktivität und alle anderen Teilnehmer der Transaktion erfolgreich abgeschlossen wurden.  
  
### Verwenden des TransactionScope\-Aktivitätsdesigners  
 Der **TransactionScope**\-Aktivitätsdesigner befindet sich in der Kategorie **Transaction** der **Toolbox**, auf die Sie zugreifen können, indem Sie in [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] auf die Registerkarte **Toolbox** klicken. \(Sie können auch im Menü **Ansicht** den Befehl **Toolbox** auswählen oder STRG\+ALT\+X drücken.\)  
  
 Der **TransactionScope**\-Aktivitätsdesigner kann aus der **Toolbox** gezogen und auf der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]\-Oberfläche dort abgelegt werden, wo Aktivitäten normalerweise platziert werden, etwa innerhalb einer <xref:System.Activities.Statements.Sequence>.Daraufhin wird eine <xref:System.Activities.Statements.TransactionScope>\-Aktivität mit dem <xref:System.Activities.Activity.DisplayName%2A>\-Standardwert TransactionScope erstellt.Der <xref:System.Activities.Activity.DisplayName%2A>\-Wert kann im Header des **TransactionScope**\-Aktivitätsdesigners oder im Feld **DisplayName** des Eigenschaftenrasters bearbeitet werden.  
  
### Die TransactionScope\-Eigenschaften  
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.TransactionScope>\-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.Die <xref:System.Activities.Activity.DisplayName%2A>\-Eigenschaft und die <xref:System.Activities.Statements.TransactionScope.Body%2A>\-Eigenschaft können in der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]\-Oberfläche bearbeitet werden.Die anderen Eigenschaften müssen jedoch im Eigenschaftenraster bearbeitet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-----------------------|------------------|----------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Der optionale Anzeigename der <xref:System.Activities.Statements.TransactionScope>\-Aktivität.Der Standardwert lautet TransactionScope.Obwohl der <xref:System.Activities.Activity.DisplayName%2A>\-Wert nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|  
|<xref:System.Activities.Statements.TransactionScope.Body%2A>|True|Gibt die Aktivität an, die in einer einzelnen Transaktion ausgeführt werden soll.Sie fügen die <xref:System.Activities.Statements.TransactionScope.Body%2A>\-Aktivität hinzu, indem Sie eine Aktivität aus der **Toolbox** in das Feld **Body** mit dem Hinweistext "Aktivität hier ablegen" des **TransactionScope**\-Aktivitätsdesigners ziehen.|  
|<xref:System.Activities.Statements.TransactionScope.IsolationLevel%2A>|True|Gibt die <xref:System.Transactions.IsolationLevel>\-Ebene für diesen <xref:System.Activities.Statements.TransactionScope>\-Bereich an.|  
|<xref:System.Activities.Statements.TransactionScope.Timeout%2A>|False|Gibt das Zeitintervall \(im Format 00:00:00 für Stunden:Minuten:Sekunden\) an, in dem die Transaktion abgeschlossen werden muss.Der Standardwert beträgt 1 Minute \(00:01:00\).|  
|<xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure%2A>|True|Gibt den Wert an, der angibt, ob der Workflow abgebrochen werden soll, wenn die Transaktion abbricht.|  
  
## Siehe auch  
 [Transaktion](../workflow-designer/transaction-activity-designers.md)   
 [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)   
 [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)   
 [Compensate](../workflow-designer/compensate-activity-designer.md)   
 [Confirm](../workflow-designer/confirm-activity-designer.md)