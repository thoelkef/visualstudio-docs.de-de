---
title: "Aktivitätsansichten (Vorgängerversion) | Microsoft Docs"
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- activities, activity views
- views, activity
- activity views
ms.assetid: 83dc68cd-2cb2-45c2-9a6e-10d82053171a
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 10661aa3f12b83a383defaa204b5bba0b93e236a
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2018
---
# <a name="activity-views-legacy"></a>Aktivitätsansichten (Vorgängerversion)
Viele der bereitgestellten Aktivitäten [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)], aus denen Workflows bestehen, stehen mehrere Entwurfsansichten, die in älteren Windows Workflow-Designer verfügbar. Beim Ziehen Sie eines Aktivitätsdesigners aus der **Toolbox** auf die Entwurfsoberfläche, und anschließend die Aktivität ausgewählt wird, wechseln Sie zwischen den verschiedenen Entwurfsansichten mithilfe einer der **Workflow**Menü oder über das Kontextmenü der ausgewählten Aktivität. Und wenn Sie den Mauszeiger auf den Namen einer ausgewählten Aktivität verschieben, wird ein Dropdownsatz mit Registerkarten aufgerufen, mit denen Sie zwischen den verschiedenen Ansichten wechseln können.

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

- [Legacyworkflowaktivitäten](../workflow-designer/legacy-workflow-activities.md)
- [Sequenzielle Workflowansichten (Vorgängerversion)](../workflow-designer/sequential-workflow-views-legacy.md)