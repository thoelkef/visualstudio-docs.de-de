---
title: "CancellationScope-Aktivit&#228;tsdesigner | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.CancellationScope.UI"
ms.assetid: 2c85d663-b219-4142-9866-7693ffd46379
caps.latest.revision: 8
caps.handback.revision: 8
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# CancellationScope-Aktivit&#228;tsdesigner
Der **CancellationScope**\-Aktivitätsdesigner wird verwendet, um eine <xref:System.Activities.Statements.CancellationScope>\-Aktivität zu erstellen und zu konfigurieren.  
  
## Die CancellationScope\-Aktivität  
 Mit der <xref:System.Activities.Statements.CancellationScope>\-Aktivität können Sie für eine Aktivität für die Ausführungs\- und Abbruchlogik dieser Aktivität angeben.  
  
### Verwenden des CancellationScope\-Aktivitätsdesigners  
 Der **CancellationScope**\-Aktivitätsdesigner befindet sich in der Kategorie **Transaction** der **Toolbox**, auf die Sie zugreifen können, indem Sie in [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] auf die Registerkarte **Toolbox** klicken. \(Sie können auch im Menü **Ansicht** den Befehl **Toolbox** auswählen oder STRG\+ALT\+X drücken.\)  
  
 Der **CancellationScope**\-Aktivitätsdesigner kann aus der **Toolbox** gezogen und auf der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]\-Oberfläche dort abgelegt werden, wo Aktivitätsdesigner normalerweise platziert werden, z. B. in einer <xref:System.Activities.Statements.Sequence>.Dies erstellt eine <xref:System.Activities.Statements.CancellationScope>\-Aktivität mit dem <xref:System.Activities.Activity.DisplayName%2A>\-Standardwert CancellationScope.Der <xref:System.Activities.Activity.DisplayName%2A>\-Wert kann im Header des **CancellationScope**\-Aktivitätsdesigners oder im Feld **DisplayName** des Eigenschaftenrasters bearbeitet werden.  
  
### Die CancellationScope\-Eigenschaften  
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.CancellationScope>\-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.Die <xref:System.Activities.Activity.DisplayName%2A>\-Eigenschaften kann im Eigenschaftenraster bearbeitet werden, die anderen Eigenschaften müssen jedoch auf der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]\-Oberfläche bearbeitet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-----------------------|------------------|----------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Der optionale Anzeigename der <xref:System.Activities.Statements.CancellationScope>\-Aktivität.Der Standardwert lautet CancellationScope.Obwohl der <xref:System.Activities.Activity.DisplayName%2A>\-Wert nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|  
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|True|Gibt die Aktivität an, für die Abbruchlogik bereitgestellt wird.Sie fügen die <xref:System.Activities.Statements.CancellationScope.Body%2A>\-Aktivität hinzu, indem Sie eine Aktivität aus der **Toolbox** in das Feld **Body** mit dem Hinweistext "Aktivität hier ablegen" des **CancellationScope**\-Aktivitätsdesigners ziehen.|  
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|True|Gibt die Aktivität an, die im Fall eines Abbruchs ausgeführt wird.Sie fügen die <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>\-Aktivität hinzu, indem Sie eine Aktivität aus der **Toolbox** in das Feld **CancellationHandler** mit dem Hinweistext "Aktivität hier ablegen" des **CancellationScope**\-Aktivitätsdesigners ziehen.|  
  
## Siehe auch  
 [Transaktion](../workflow-designer/transaction-activity-designers.md)   
 [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)   
 [Compensate](../workflow-designer/compensate-activity-designer.md)   
 [Confirm](../workflow-designer/confirm-activity-designer.md)   
 [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)