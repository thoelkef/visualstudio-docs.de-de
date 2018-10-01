---
title: Aktivitätsansichten (Vorgängerversion) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- activities, activity views
- views, activity
- activity views
ms.assetid: 83dc68cd-2cb2-45c2-9a6e-10d82053171a
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: ef7aaa042ea358ecdf3d45b6ee75dd14cf117a01
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47515110"
---
# <a name="activity-views-legacy"></a>Aktivitätsansichten (Vorgängerversion)
In vielen der Aktivitäten, die von [!INCLUDE[wf](../includes/wf-md.md)] bereitgestellt werden, und aus denen Workflows bestehen, stehen mehrere Entwurfsansichten in der Vorgängerversion von [!INCLUDE[wfd1](../includes/wfd1-md.md)] zur Verfügung. Beim Ziehen von eines Aktivitätsdesigners aus der **Toolbox** auf die Entwurfsoberfläche, und anschließend, wenn Sie die Aktivität auswählen, können Sie zwischen den verschiedenen Entwurfsansichten entweder wechseln die **Workflow**Menü oder per Rechtsklick auf die ausgewählte Aktivität. Und wenn Sie den Mauszeiger auf den Namen einer ausgewählten Aktivität verschieben, wird ein Dropdownsatz mit Registerkarten aufgerufen, mit denen Sie zwischen den verschiedenen Ansichten wechseln können.  
  
 Jede Aktivität verfügt über mindestens eine Ansicht; Dies ist die Standardansicht, die angezeigt wird, beim Ziehen von eines Aktivitätsdesigners aus der **Toolbox** auf die Entwurfsoberfläche. Diese Standardansicht für Aktivitäten steht als die **anzeigen [Aktivitätstyp]** Option in den Menüs und die Registerkarte ", z. B. **Ansicht Parallel**. Die meisten der Aktivitäten weisen zusätzliche Ansichten auf, und verschiedene Aktivitäten können über verschiedene Ansichten verfügen. Z. B. die [TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093) Aktivität verfügt über die kompensierungsansicht und die [EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030) Aktivität verfügt über eine Ereignisansicht anzeigen. Viele der Aktivitäten, die die im Lieferumfang von Windows Workflow Foundation **Abbruchhandler anzeigen** und **Fehler anzeigen** Entwerfen von Sichten zur Ansicht der [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050) und ein [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) zugeordnet werden.  
  
 In der folgenden Tabelle werden die Namen und Beschreibungen der einzelnen Ansichten aufgeführt.  
  
|Menü-/Registerkartenoption|Beschreibung|  
|----------------------|-----------------|  
|**Ansicht [Aktivitätstyp]**|Wählen Sie diese Menü- oder Registerkartenoption aus, um die grafische Standarddarstellung der ausgewählten Aktivität anzuzeigen.|  
|**Abbruchhandler anzeigen**|Wählen Sie diese Menü- oder die Option Ansicht zum Anzeigen der [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050) der ausgewählten Aktivität zugeordnet.|  
|**Fehlerhandler anzeigen**|Wählen Sie diese Menü- oder die Option Ansicht zum Anzeigen der [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) der ausgewählten Aktivität zugeordnet.|  
|**Anzeigen von Kompensierungshandlern**|Wählen Sie diese Menü- oder die Option Ansicht zum Anzeigen der [CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65053) zugeordnet [TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093).|  
|**Anzeigen von Ereignisse-Handler**|Wählen Sie diese Menü- oder die Option Ansicht zum Anzeigen der [EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018) zugeordnet der [EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030).|  
  
 Weitere Informationen zu ähnlichen Ansichten finden Sie unter [sequenzielle Workflowansichten (Vorgängerversion)](../workflow-designer/sequential-workflow-views-legacy.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Legacyworkflowaktivitäten](../workflow-designer/legacy-workflow-activities.md)   
 [Sequenzielle Workflowansichten (Vorgängerversion)](../workflow-designer/sequential-workflow-views-legacy.md)