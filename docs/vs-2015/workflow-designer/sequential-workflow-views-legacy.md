---
title: Sequenzielle Workflow Sichten (Legacy) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- sequential workflow views
- sequential workflows, views
ms.assetid: 135f24b9-1b37-442b-9ef8-f0f2108a3212
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 76d357c1f6ebc770d0e625e60bae237e37e0a6aa
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2020
ms.locfileid: "75846212"
---
# <a name="sequential-workflow-views-legacy"></a>Sequenzielle Workflowansichten (Vorgängerversion)
[!INCLUDE[vs2010](../includes/vs2010-md.md)] stellt eine Legacy [!INCLUDE[wfd1](../includes/wfd1-md.md)] bereit, die verwendet werden kann, um die [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] oder die [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]als Ziel festzustellen.

 [!INCLUDE[wfd2](../includes/wfd2-md.md)] bietet eine Möglichkeit, [!INCLUDE[wf](../includes/wf-md.md)]-Anwendungen mithilfe der vertrauten [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Benutzeroberfläche grafisch zu erstellen. [!INCLUDE[wf](../includes/wf-md.md)]-Anwendungen bestehen aus Workflowprozessschritten, den so genannten Aktivitäten. Um einen Workflow zu erstellen, verfassen Sie Aktivitäten auf der Entwurfs Oberfläche, indem Sie die entsprechenden Aktivitäts Designer aus der **Toolbox** auf die Entwurfs Oberfläche ziehen.

 Wenn Sie einen sequenziellen Workflow erstellen, bei dem es sich um eine [SequentialWorkflowActivity](https://msdn2.microsoft.com/library/system.workflow.activities.sequentialworkflowactivity.aspx)handelt, stehen drei Ansichten des Workflows zur Verfügung. Diese Sichten sind über das Menü **Workflow** und über das Kontextmenü der Entwurfs Oberfläche zugänglich.

 In der folgenden Tabelle werden die Namen und Beschreibungen der einzelnen Ansichten aufgeführt.

|Menü-/Registerkartenoption|Beschreibung|
|----------------------|-----------------|
|**SequentialWorkflow anzeigen**|Klicken Sie mit der rechten Maustaste auf die Entwurfs Oberfläche, und wählen Sie im Kontextmenü die Option **SequentialWorkflow anzeigen** aus, um die Ansicht **sequenzieller Workflow** anzuzeigen, in der die aktivitätsbasierte grafische Darstellung des sequenziellen Workflows angezeigt wird. Oder wählen Sie im Menü **Workflow** die Option **SequentialWorkflow anzeigen** aus.|
|**Abbruch Handler anzeigen**|Klicken Sie mit der rechten Maustaste auf die Entwurfs Oberfläche, und wählen Sie die Option **Abbruch Handler anzeigen** im Kontextmenü aus, um die Ansicht **sequenzieller Workflow** anzuzeigen, die die dem Workflow zugeordnete [CancellationHandlerActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.cancellationhandleractivity.aspx) -Aktivität anzeigt. Oder wählen Sie im Menü **Workflow** die Option **Abbruch Handler anzeigen** aus.|
|**Fehler Handler anzeigen**|Klicken Sie mit der rechten Maustaste auf die Entwurfs Oberfläche, und wählen Sie die Option **Fehler Handler anzeigen** im Kontextmenü aus, um die Ansicht **Fehler** anzuzeigen, die die dem Workflow zugeordnete [FaultHandlersActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.faulthandlersactivity.aspx) -Aktivität anzeigt. Oder wählen Sie im Menü **Workflow** die Option **Fehler Handler anzeigen** aus.|

 Weitere Informationen zu ähnlichen Sichten finden Sie unter [Aktivitäts Ansichten (Legacy)](../workflow-designer/activity-views-legacy.md).

## <a name="see-also"></a>Siehe auch
 [Aktivitäts Sichten (Legacy)](../workflow-designer/activity-views-legacy.md) Erstellen von [Workflow-Erstellungs Modi](https://msdn2.microsoft.com/library/bb628440.aspx) für [Legacy Workflow Projekte](../workflow-designer/creating-legacy-workflow-projects.md)
