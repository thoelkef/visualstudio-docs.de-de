---
title: Activity Views (Legacy) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- activities, activity views
- views, activity
- activity views
ms.assetid: 83dc68cd-2cb2-45c2-9a6e-10d82053171a
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9b65a46d5d0061eeaf3ad707affea1423e5fca5d
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297535"
---
# <a name="activity-views-legacy"></a>Aktivitätsansichten (Vorgängerversion)
In vielen der Aktivitäten, die von [!INCLUDE[wf](../includes/wf-md.md)] bereitgestellt werden, und aus denen Workflows bestehen, stehen mehrere Entwurfsansichten in der Vorgängerversion von [!INCLUDE[wfd1](../includes/wfd1-md.md)] zur Verfügung. When you drag an activity designer from the **Toolbox** onto the design surface, and thereafter whenever you select the activity, you can switch between the different design views by using either the **Workflow** menu or by right-clicking the selected activity. Und wenn Sie den Mauszeiger auf den Namen einer ausgewählten Aktivität verschieben, wird ein Dropdownsatz mit Registerkarten aufgerufen, mit denen Sie zwischen den verschiedenen Ansichten wechseln können.

 Every activity has at least one view; this is the default view shown when you drag an activity designer from the **Toolbox** onto the design surface. This activity default view is available as the **View [activity type]** option on the menus and tab, for example, **View Parallel**. Die meisten der Aktivitäten weisen zusätzliche Ansichten auf, und verschiedene Aktivitäten können über verschiedene Ansichten verfügen. For example, the [TransactionScopeActivity](https://go.microsoft.com/fwlink?LinkID=65093) activity has the compensation view and the [EventHandlingScopeActivity](https://go.microsoft.com/fwlink?LinkID=65030) activity has an events view. Many of the activities that come with Windows Workflow Foundation have **View Cancel Handler** and **View Faults** design views to view the [CancellationHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65050) and a [FaultHandlersActivity](https://go.microsoft.com/fwlink?LinkID=65055) associated with them.

 In der folgenden Tabelle werden die Namen und Beschreibungen der einzelnen Ansichten aufgeführt.

|Menü-/Registerkartenoption|Beschreibung|
|----------------------|-----------------|
|**View [activity type]**|Wählen Sie diese Menü- oder Registerkartenoption aus, um die grafische Standarddarstellung der ausgewählten Aktivität anzuzeigen.|
|**View Cancel Handler**|Select this menu or tab option view to view the [CancellationHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65050) associated with the selected activity.|
|**View Fault Handler**|Select this menu or tab option view to view the [FaultHandlersActivity](https://go.microsoft.com/fwlink?LinkID=65055) associated with the selected activity.|
|**View Compensation Handler**|Select this menu or tab option view to view the [CompensationHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65053) associated with the selected [TransactionScopeActivity](https://go.microsoft.com/fwlink?LinkID=65093).|
|**View Events Handler**|Select this menu or tab option view to view the [EventHandlersActivity](https://go.microsoft.com/fwlink?LinkID=65018) associated with the selected the [EventHandlingScopeActivity](https://go.microsoft.com/fwlink?LinkID=65030).|

 For information about similar views, see [Sequential Workflow Views (Legacy)](../workflow-designer/sequential-workflow-views-legacy.md).

## <a name="see-also"></a>Siehe auch
 [Legacy Workflow Activities](../workflow-designer/legacy-workflow-activities.md) [Sequential Workflow Views (Legacy)](../workflow-designer/sequential-workflow-views-legacy.md)