---
title: "Aktivit&#228;tsansichten (Vorg&#228;ngerversion) | Microsoft Docs"
ms.custom: ""
ms.date: "11/23/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Aktivitäten, Aktivitätsansichten"
  - "Aktivitätsansichten"
  - "Ansichten, Aktivität"
ms.assetid: 83dc68cd-2cb2-45c2-9a6e-10d82053171a
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Aktivit&#228;tsansichten (Vorg&#228;ngerversion)
In vielen der Aktivitäten, die von [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] bereitgestellt werden, und aus denen Workflows bestehen, stehen mehrere Entwurfsansichten in der Vorgängerversion von [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] zur Verfügung.Wird ein Aktivitätsdesigner aus der **Toolbox** in die Entwurfsoberfläche gezogen und wird die Aktivität später ausgewählt, können Sie mit dem Menü **Workflow** oder mit einen Rechtsklick auf die ausgewählte Aktivität zwischen den verschiedenen Entwurfsansichten wechseln.Und wenn Sie den Mauszeiger auf den Namen einer ausgewählten Aktivität verschieben, wird ein Dropdownsatz mit Registerkarten aufgerufen, mit denen Sie zwischen den verschiedenen Ansichten wechseln können.  
  
 Jede Aktivität verfügt über mindestens eine Ansicht. Dies ist die Standardansicht, die angezeigt wird, wenn Sie einen Aktivitätsdesigner aus der **Toolbox** in die Entwurfsoberfläche ziehen.Diese Standardansicht für Aktivitäten ist als Option **Ansicht \[Aktivitätstyp\]** in den Menüs und auf den Registerkarten verfügbar, zum Beispiel **Ansicht Parallel**.Die meisten der Aktivitäten weisen zusätzliche Ansichten auf, und verschiedene Aktivitäten können über verschiedene Ansichten verfügen.So verfügt die [TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093)\-Aktivität \(Seite ist möglicherweise nur in englischer Sprache verfügbar.\) beispielsweise über die Kompensierungsansicht und die [EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030)\-Aktivität \(Seite ist möglicherweise nur in englischer Sprache verfügbar.\) über eine Ereignisansicht.Viele der in Windows Workflow Foundation enthaltenen Ansichten verfügen über **Abbruchhandler anzeigen**\- und **Fehler anzeigen**\-Entwurfsansichten zur Anzeige der [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050) \(Seite ist möglicherweise nur in englischer Sprache verfügbar.\) und einer diesen zugewiesenen [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) \(Seite ist möglicherweise nur in englischer Sprache verfügbar.\).  
  
 In der folgenden Tabelle werden die Namen und Beschreibungen der einzelnen Ansichten aufgeführt.  
  
|Menü\-\/Registerkartenoption|Beschreibung|  
|----------------------------------|------------------|  
|**Ansicht \[Aktivitätstyp\]**|Wählen Sie diese Menü\- oder Registerkartenoption aus, um die grafische Standarddarstellung der ausgewählten Aktivität anzuzeigen.|  
|**Abbruchhandler anzeigen**|Wählen Sie diese Menü\- oder Registerkartenoptionsansicht aus, um die der ausgewählten Aktivität zugewiesene [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050) \(Seite ist möglicherweise nur in englischer Sprache verfügbar.\) anzuzeigen.|  
|**Fehlerhandler anzeigen**|Wählen Sie diese Menü\- oder Registerkartenoptionsansicht aus, um die der ausgewählten Aktivität zugewiesene [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) \(Seite ist möglicherweise nur in englischer Sprache verfügbar.\) anzuzeigen.|  
|**Anzeigen von Kompensierungshandlern**|Wählen Sie diese Menü\- oder Registerkartenoptionsansicht aus, um die der ausgewählten [TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093) \(Seite ist möglicherweise nur in englischer Sprache verfügbar.\) zugewiesene [CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65053) \(Seite ist möglicherweise nur in englischer Sprache verfügbar.\) anzuzeigen.|  
|**Anzeigen von Ereignisse\-Handler**|Wählen Sie diese Menü\- oder Registerkartenoptionsansicht aus, um die der ausgewählten [TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030) \(Seite ist möglicherweise nur in englischer Sprache verfügbar.\) zugewiesene [EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018) \(Seite ist möglicherweise nur in englischer Sprache verfügbar.\) anzuzeigen.|  
  
 Weitere Informationen zu ähnlichen Ansichten finden Sie unter [Sequenzielle Workflowansichten \(Vorgängerversion\)](../workflow-designer/sequential-workflow-views-legacy.md).  
  
## Siehe auch  
 [Legacyworkflowaktivitäten](../workflow-designer/legacy-workflow-activities.md)   
 [Sequenzielle Workflowansichten \(Vorgängerversion\)](../workflow-designer/sequential-workflow-views-legacy.md)