---
title: Workflow-Designer - sequenzielle Workflowansichten (Vorgängerversion)
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- sequential workflow views
- sequential workflows, views
ms.assetid: 135f24b9-1b37-442b-9ef8-f0f2108a3212
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ce1217ea629ae0301b72b444161d61db4fe448b1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31976018"
---
# <a name="sequential-workflow-views-legacy"></a>Sequenzielle Workflowansichten (Vorgängerversion)

Visual Studio 2010 enthält eine ältere Windows-Workflow-Designer, die .NET Framework, Version 3.5 oder die WinFX als Ziel verwendet werden kann.

Workflow-Designer bietet eine Möglichkeit zum Erstellen von Windows Workflow Foundation (WF)-Anwendungen, die mithilfe der vertrauten Visual Studio-Benutzeroberfläche grafisch dargestellt. Windows Workflow Foundation (WF)-Anwendungen bestehen aus der genannten Aktivitäten. Um einen Workflow zu erstellen, erstellen Sie Aktivitäten auf der Entwurfsoberfläche ziehen Sie die jeweiligen Aktivitätsdesigner aus **Toolbox** auf die Entwurfsoberfläche.

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