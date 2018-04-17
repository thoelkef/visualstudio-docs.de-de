---
title: Sequenzielle Workflowansichten (Vorgängerversion) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- sequential workflow views
- sequential workflows, views
ms.assetid: 135f24b9-1b37-442b-9ef8-f0f2108a3212
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a6b42ba9c1c9f7dbe2beb4a741501967e4968508
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="sequential-workflow-views-legacy"></a>Sequenzielle Workflowansichten (Vorgängerversion)
[!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] Stellt eine ältere Windows-Workflow-Designer, die verwendet werden kann, Ziel der [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] oder die [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] bietet eine Möglichkeit, [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)]-Anwendungen mithilfe der vertrauten [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Benutzeroberfläche grafisch zu erstellen. [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)]-Anwendungen bestehen aus Workflowprozessschritten, den so genannten Aktivitäten. Um einen Workflow zu erstellen, erstellen Sie Aktivitäten auf der Entwurfsoberfläche ziehen Sie die jeweiligen Aktivitätsdesigner aus **Toolbox** auf die Entwurfsoberfläche.

 Einen sequenziellen Workflow, also beim Erstellen einer [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040), stehen drei Ansichten des Workflows zur Verfügung. Diese Ansichten sind über die **Workflow** Menü und im Kontextmenü auf der Entwurfsoberfläche angezeigt.

 In der folgenden Tabelle werden die Namen und Beschreibungen der einzelnen Ansichten aufgeführt.

|Menü-/Registerkartenoption|Beschreibung|
|----------------------|-----------------|
|**Sequenziellen Workflow anzeigen**|Mit der rechten Maustaste in des Entwurfs, die Entwurfsoberfläche, und wählen die **sequenziellen Workflow anzeigen** Option im Kontextmenü zum Anzeigen der **sequenzieller Workflow** Ansicht, in der die aktivitätsbasierte zeigt grafische Darstellung des sequenziellen Workflows. Oder wählen Sie **sequenziellen Workflow anzeigen** aus der **Workflow** Menü.|
|**Abbruchhandler anzeigen**|Mit der rechten Maustaste in des Entwurfs, die Entwurfsoberfläche, und wählen die **Abbruchhandler anzeigen** Option im Kontextmenü zum Anzeigen der **sequenzieller Workflow** anzuzeigen, der angezeigt wird der [CancellationHandlerActivity ](http://go.microsoft.com/fwlink?LinkID=65050) mit dem Workflow zugeordneten Aktivität. Oder wählen Sie **Abbruchhandler anzeigen** aus der **Workflow** Menü.|
|**Fehlerhandler anzeigen**|Mit der rechten Maustaste in des Entwurfs, die Entwurfsoberfläche, und wählen die **Fehlerhandler anzeigen** Option im Kontextmenü zum Anzeigen der **Fehler** anzuzeigen, der angezeigt wird der [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) die Aktivität dem Workflow zugeordnet. Oder wählen Sie **Fehlerhandler anzeigen** aus der **Workflow** Menü.|

 Weitere Informationen zu ähnlichen Sichten, finden Sie unter [Aktivitätsansichten (Vorgängerversion)](../workflow-designer/activity-views-legacy.md).

## <a name="see-also"></a>Siehe auch

- [Aktivitätsansichten (Vorgängerversion)](../workflow-designer/activity-views-legacy.md)
- [Erstellen von Legacyworkflowprojekten](../workflow-designer/creating-legacy-workflow-projects.md)
- [Workflow Authoring Modi](http://go.microsoft.com/fwlink?LinkID=65014)