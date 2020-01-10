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
ms.openlocfilehash: 7546f752ef7ee1053d1b0b785334a8da814720c6
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851479"
---
# <a name="activity-views-legacy"></a>Aktivitätsansichten (Vorgängerversion)
In vielen der Aktivitäten, die von [!INCLUDE[wf](../includes/wf-md.md)] bereitgestellt werden, und aus denen Workflows bestehen, stehen mehrere Entwurfsansichten in der Vorgängerversion von [!INCLUDE[wfd1](../includes/wfd1-md.md)] zur Verfügung. Wenn Sie einen Aktivitäts Designer aus der **Toolbox** auf die Entwurfs Oberfläche ziehen und anschließend bei der Auswahl der Aktivität, können Sie zwischen den verschiedenen Entwurfs Ansichten wechseln, indem Sie entweder das Menü " **Workflow** " verwenden oder mit der rechten Maustaste auf die ausgewählte Aktivität klicken. Und wenn Sie den Mauszeiger auf den Namen einer ausgewählten Aktivität verschieben, wird ein Dropdownsatz mit Registerkarten aufgerufen, mit denen Sie zwischen den verschiedenen Ansichten wechseln können.

 Jede Aktivität verfügt über mindestens eine Ansicht. Dies ist die Standardansicht, die angezeigt wird, wenn Sie einen Aktivitäts Designer aus der **Toolbox** auf die Entwurfs Oberfläche ziehen. Diese Aktivitäts Standardansicht ist als Sicht Option **[Aktivitätstyp]** in den Menüs und Registerkarten verfügbar, z. b. **parallele anzeigen**. Die meisten der Aktivitäten weisen zusätzliche Ansichten auf, und verschiedene Aktivitäten können über verschiedene Ansichten verfügen. Die [transaktionscopeactivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.transactionscopeactivity.aspx) -Aktivität verfügt beispielsweise über die Kompensierungs Ansicht und die [EventHandlingScopeActivity](https://msdn2.microsoft.com/library/system.workflow.activities.eventhandlingscopeactivity.aspx) -Aktivität über eine Ereignisansicht. Viele der Aktivitäten, die Windows Workflow Foundation enthalten, verfügen über die Entwurfs Sichten " **View Cancel** " und " **View** Fault", um [CancellationHandlerActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.cancellationhandleractivity.aspx) und eine [FaultHandlersActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.faulthandlersactivity.aspx) anzuzeigen.

 In der folgenden Tabelle werden die Namen und Beschreibungen der einzelnen Ansichten aufgeführt.

|Menü-/Registerkartenoption|Beschreibung|
|----------------------|-----------------|
|**Sicht [Aktivitätstyp]**|Wählen Sie diese Menü- oder Registerkartenoption aus, um die grafische Standarddarstellung der ausgewählten Aktivität anzuzeigen.|
|**Abbruch Handler anzeigen**|Wählen Sie diese Menü-oder Registerkarten Options Ansicht aus, um die der ausgewählten Aktivität zugeordnete [CancellationHandlerActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.cancellationhandleractivity.aspx) anzuzeigen.|
|**Fehler Handler anzeigen**|Wählen Sie diese Menü-oder Registerkarten Options Ansicht aus, um die der ausgewählten Aktivität zugeordnete [FaultHandlersActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.faulthandlersactivity.aspx) anzuzeigen.|
|**Kompensierungs Handler anzeigen**|Wählen Sie diese Menü-oder Registerkarten Options Ansicht aus, um die [CompensationHandlerActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.compensationhandleractivity.aspx) anzuzeigen, die mit der ausgewählten [transaktionscopeactivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.transactionscopeactivity.aspx)verknüpft ist.|
|**Ereignis Handler anzeigen**|Wählen Sie diese Menü-oder Registerkarten Options Ansicht aus, um die [EventHandlersActivity](https://msdn2.microsoft.com/library/system.workflow.activities.eventhandlersactivity.aspx) anzuzeigen, die der ausgewählten [EventHandlingScopeActivity](https://msdn2.microsoft.com/library/system.workflow.activities.eventhandlingscopeactivity.aspx)-Aktivität zugeordnet ist.|

 Weitere Informationen zu ähnlichen Sichten finden Sie unter [sequenzielle Workflow Sichten (Legacy)](../workflow-designer/sequential-workflow-views-legacy.md).

## <a name="see-also"></a>Siehe auch
 [Sequenzielle Workflow Sichten](../workflow-designer/sequential-workflow-views-legacy.md) der [Legacy Workflow Aktivitäten](../workflow-designer/legacy-workflow-activities.md) (Legacy)
