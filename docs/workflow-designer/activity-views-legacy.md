---
title: "Aktivitätsansichten (Vorgängerversion) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- activities, activity views
- views, activity
- activity views
ms.assetid: 83dc68cd-2cb2-45c2-9a6e-10d82053171a
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 0a6658bdf0f1df76e585236497ba4ba19525b199
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="activity-views-legacy"></a>Aktivitätsansichten (Vorgängerversion)
In vielen der Aktivitäten, die von [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] bereitgestellt werden, und aus denen Workflows bestehen, stehen mehrere Entwurfsansichten in der Vorgängerversion von [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] zur Verfügung. Beim Ziehen Sie eines Aktivitätsdesigners aus der **Toolbox** auf die Entwurfsoberfläche, und anschließend die Aktivität ausgewählt wird, wechseln Sie zwischen den verschiedenen Entwurfsansichten mithilfe einer der **Workflow**Menü oder über das Kontextmenü der ausgewählten Aktivität. Und wenn Sie den Mauszeiger auf den Namen einer ausgewählten Aktivität verschieben, wird ein Dropdownsatz mit Registerkarten aufgerufen, mit denen Sie zwischen den verschiedenen Ansichten wechseln können.  
  
 Jede Aktivität verfügt über mindestens eine Ansicht; Dies ist die Standardansicht angezeigt, wenn Sie einen Aktivitätsdesigner aus ziehen die **Toolbox** auf die Entwurfsoberfläche. Diese Standardansicht für Aktivitäten steht als die **anzeigen [Aktivitätstyp]** Option auf der Registerkarte, z. B. "und" Menüs **Ansicht Parallel**. Die meisten der Aktivitäten weisen zusätzliche Ansichten auf, und verschiedene Aktivitäten können über verschiedene Ansichten verfügen. Z. B. die [TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093) -Aktivität verfügt über die kompensierungsansicht und die [EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030) -Aktivität verfügt über eine Ereignisansicht anzeigen. Viele der Aktivitäten, die die im Lieferumfang von Windows Workflow Foundation **Abbruchhandler anzeigen** und **Fehler anzeigen** Entwerfen von Sichten zur Ansicht der [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050) und ein [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) zugeordnet.  
  
 In der folgenden Tabelle werden die Namen und Beschreibungen der einzelnen Ansichten aufgeführt.  
  
|Menü-/Registerkartenoption|Beschreibung|  
|----------------------|-----------------|  
|**Ansicht [Aktivitätstyp]**|Wählen Sie diese Menü- oder Registerkartenoption aus, um die grafische Standarddarstellung der ausgewählten Aktivität anzuzeigen.|  
|**Abbruchhandler anzeigen**|Wählen Sie diese Menü- oder die Option Ansicht zum Anzeigen der [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050) der ausgewählten Aktivität zugeordnet.|  
|**Fehlerhandler anzeigen**|Wählen Sie diese Menü- oder die Option Ansicht zum Anzeigen der [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) der ausgewählten Aktivität zugeordnet.|  
|**Anzeigen von Kompensierungshandlern**|Wählen Sie diese Menü- oder die Option Ansicht zum Anzeigen der [CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65053) verknüpft sind, mit dem ausgewählten [TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093).|  
|**Anzeigen von Ereignisse-Handler**|Wählen Sie diese Menü- oder die Option Ansicht zum Anzeigen der [EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018) verknüpft sind, mit dem ausgewählten der [EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030).|  
  
 Informationen über ähnliche Sichten finden Sie unter [sequenzielle Workflowansichten (Vorgängerversion)](../workflow-designer/sequential-workflow-views-legacy.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Legacyworkflowaktivitäten](../workflow-designer/legacy-workflow-activities.md)   
 [Sequenzielle Workflowansichten (Vorgängerversion)](../workflow-designer/sequential-workflow-views-legacy.md)