---
title: Aktivitäts Ansichten (Legacy) | Microsoft-Dokumentation
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
In vielen der Aktivitäten, die von [!INCLUDE[wf](../includes/wf-md.md)] bereitgestellt werden, und aus denen Workflows bestehen, stehen mehrere Entwurfsansichten in der Vorgängerversion von [!INCLUDE[wfd1](../includes/wfd1-md.md)] zur Verfügung. Wenn Sie einen Aktivitäts Designer aus der **Toolbox** auf die Entwurfs Oberfläche ziehen und anschließend bei der Auswahl der Aktivität, können Sie zwischen den verschiedenen Entwurfs Ansichten wechseln, indem Sie entweder das Menü " **Workflow** " verwenden oder mit der rechten Maustaste auf die ausgewählte Aktivität klicken. Und wenn Sie den Mauszeiger auf den Namen einer ausgewählten Aktivität verschieben, wird ein Dropdownsatz mit Registerkarten aufgerufen, mit denen Sie zwischen den verschiedenen Ansichten wechseln können.

 Jede Aktivität verfügt über mindestens eine Ansicht. Dies ist die Standardansicht, die angezeigt wird, wenn Sie einen Aktivitäts Designer aus der **Toolbox** auf die Entwurfs Oberfläche ziehen. Diese Aktivitäts Standardansicht ist als Sicht Option **[Aktivitätstyp]** in den Menüs und Registerkarten verfügbar, z. b. **parallele anzeigen**. Die meisten der Aktivitäten weisen zusätzliche Ansichten auf, und verschiedene Aktivitäten können über verschiedene Ansichten verfügen. Die [transaktionscopeactivity](https://go.microsoft.com/fwlink?LinkID=65093) -Aktivität verfügt beispielsweise über die Kompensierungs Ansicht und die [EventHandlingScopeActivity](https://go.microsoft.com/fwlink?LinkID=65030) -Aktivität über eine Ereignisansicht. Viele der Aktivitäten, die Windows Workflow Foundation enthalten, verfügen über die Entwurfs Sichten " **View Cancel** " und " **View** Fault", um [CancellationHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65050) und eine [FaultHandlersActivity](https://go.microsoft.com/fwlink?LinkID=65055) anzuzeigen.

 In der folgenden Tabelle werden die Namen und Beschreibungen der einzelnen Ansichten aufgeführt.

|Menü-/Registerkartenoption|Beschreibung|
|----------------------|-----------------|
|**Sicht [Aktivitätstyp]**|Wählen Sie diese Menü- oder Registerkartenoption aus, um die grafische Standarddarstellung der ausgewählten Aktivität anzuzeigen.|
|**Abbruch Handler anzeigen**|Wählen Sie diese Menü-oder Registerkarten Options Ansicht aus, um die der ausgewählten Aktivität zugeordnete [CancellationHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65050) anzuzeigen.|
|**Fehler Handler anzeigen**|Wählen Sie diese Menü-oder Registerkarten Options Ansicht aus, um die der ausgewählten Aktivität zugeordnete [FaultHandlersActivity](https://go.microsoft.com/fwlink?LinkID=65055) anzuzeigen.|
|**Kompensierungs Handler anzeigen**|Wählen Sie diese Menü-oder Registerkarten Options Ansicht aus, um die [CompensationHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65053) anzuzeigen, die mit der ausgewählten [transaktionscopeactivity](https://go.microsoft.com/fwlink?LinkID=65093)verknüpft ist.|
|**Ereignis Handler anzeigen**|Wählen Sie diese Menü-oder Registerkarten Options Ansicht aus, um die [EventHandlersActivity](https://go.microsoft.com/fwlink?LinkID=65018) anzuzeigen, die der ausgewählten [EventHandlingScopeActivity](https://go.microsoft.com/fwlink?LinkID=65030)-Aktivität zugeordnet ist.|

 Weitere Informationen zu ähnlichen Sichten finden Sie unter [sequenzielle Workflow Sichten (Legacy)](../workflow-designer/sequential-workflow-views-legacy.md).

## <a name="see-also"></a>Siehe auch
 [Sequenzielle Workflow Sichten](../workflow-designer/sequential-workflow-views-legacy.md) der [Legacy Workflow Aktivitäten](../workflow-designer/legacy-workflow-activities.md) (Legacy)