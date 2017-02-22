---
title: "CompensableActivity-Aktivit&#228;tsdesigner | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.CompensableActivity.UI"
ms.assetid: e0340d89-d39e-4a52-8557-13e27040d7b5
caps.latest.revision: 6
caps.handback.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# CompensableActivity-Aktivit&#228;tsdesigner
Der **CompensableActivity**\-Aktivitätsdesigner wird verwendet, um eine <xref:System.Activities.Statements.CompensableActivity>\-Aktivität zu erstellen und zu konfigurieren.  
  
## Die CompensableActivity\-Aktivität  
 Die <xref:System.Activities.Statements.CompensableActivity> definiert eine Arbeitseinheit, die nach erfolgreichem Abschluss bestätigt oder kompensiert werden kann.  
  
### Verwenden des CompensableActivity\-Aktivitätsdesigners  
 Der **CompensableActivity**\-Aktivitätsdesigner befindet sich in der Kategorie **Transaktion** der **Toolbox**, auf die Sie zugreifen können, indem Sie auf der linken Seite von [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] auf die Registerkarte **Toolbox** klicken \(Sie können auch im Menü **Ansicht** den Befehl **Symbolleiste** auswählen oder STRG\+ALT\+X drücken\).  
  
 Der **CompensableActivity**\-Aktivitätsdesigner kann aus der **Toolbox** gezogen und auf der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]\-Oberfläche dort abgelegt werden, wo Aktivitätsdesigner normalerweise platziert werden z. B. in einer <xref:System.Activities.Statements.Sequence>.Dadurch wird eine <xref:System.Activities.Statements.CompensableActivity>\-Aktivität mit dem standardmäßigen <xref:System.Activities.Activity.DisplayName%2A> CompensableActivity erstellt.Der <xref:System.Activities.Activity.DisplayName%2A>\-Wert kann im Header des **CompensableActivity**\-Aktivitätsdesigners oder im Feld **DisplayName** des Eigenschaftenrasters bearbeitet werden.  
  
### Die CompensableActivity\-Eigenschaften  
 Die folgende Tabelle enthält die <xref:System.Activities.Statements.CompensableActivity>\-Eigenschaften und eine Beschreibung zu deren Verwendung im Designer.Die Eigenschaften <xref:System.Activities.Activity.DisplayName%2A> und <xref:System.Activities.Activity%601.Result%2A> können im Eigenschaftenraster bearbeitet werden, die anderen Eigenschaften müssen jedoch auf der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]\-Oberfläche bearbeitet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-----------------------|------------------|----------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Der optionale Anzeigename der <xref:System.Activities.Statements.CompensableActivity>\-Aktivität.Der Standardwert lautet CompensableActivity.|  
|<xref:System.Activities.Activity%601.Result%2A>|False|Gibt den Rückgabewert der <xref:System.Activities.Statements.CompensableActivity> an.Diese Eigenschaft muss im Eigenschaftenraster bearbeitet werden.|  
|<xref:System.Activities.Statements.CompensableActivity.Body%2A>|True|Gibt die Aktivität an, für die Kompensations\-, Abbruch\- und Bestätigungslogik bereitgestellt wurde.Sie fügen die <xref:System.Activities.Statements.CompensableActivity.Body%2A>\-Aktivität hinzu, indem Sie eine Aktivität aus der **Toolbox** in das Feld **Body** mit dem Hinweistext "Aktivität hier ablegen" des **CompensableActivity**\-Aktivitätsdesigners ziehen.|  
|<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>|False|Gibt die Aktivität an, die im Fall eines Abbruchs ausgeführt wird.Sie fügen die Aktivität hinzu, indem Sie ihren Designer aus der **Toolbox** in das Feld **CancellationHandler** mit dem Hinweistext "Aktivität hier ablegen" des **CompensableActivity**\-Aktivitätsdesigners ziehen.|  
|<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>|False|Gibt die Aktivität an, die beim Kompensieren der <xref:System.Activities.Statements.CompensableActivity.Body%2A>\-Aktivität ausgeführt werden soll.Dieser Handler kann explizit mithilfe der <xref:System.Activities.Statements.Compensate>\-Aktivität aufgerufen werden.<br /><br /> Sie fügen die Aktivität hinzu, indem Sie ihren Aktivitätsdesigner aus der **Toolbox** in das Feld **CompensationHandler** mit dem Hinweistext "Aktivität hier ablegen" des **CompensableActivity**\-Aktivitätsdesigners ziehen.|  
|<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>|False|Gibt die Aktivität an, die beim Bestätigen der <xref:System.Activities.Statements.CompensableActivity.Body%2A>\-Aktivität ausgeführt werden soll.Dieser Handler kann explizit mithilfe der <xref:System.Activities.Statements.Confirm>\-Aktivität aufgerufen werden.<br /><br /> Sie fügen die Aktivität hinzu, indem Sie ihren Aktivitätsdesigner aus der **Toolbox** in das Feld **ConfirmationHandler** mit dem Hinweistext "Aktivität hier ablegen" des **CompensableActivity**\-Aktivitätsdesigners ziehen.|  
  
## Siehe auch  
 [Transaktion](../workflow-designer/transaction-activity-designers.md)   
 [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)   
 [Compensate](../workflow-designer/compensate-activity-designer.md)   
 [Confirm](../workflow-designer/confirm-activity-designer.md)   
 [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)