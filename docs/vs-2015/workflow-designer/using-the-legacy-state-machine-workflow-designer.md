---
title: Using the Legacy State Machine Workflow Designer | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- StateFinalizationActivity activity
- StateActivity activity
- SetStateActivity activity
- EventDrivenActivity activity
- state machine workflow designer
- state machine workflows, designer
- state machine workflows, activities
- StateInitializationActivity activity
ms.assetid: 2cd21123-35c2-4eaf-82f6-86fce7a8f04d
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5bab07b8ba0b71bd880135518ff9ff5fc697d54c
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302816"
---
# <a name="using-the-legacy-state-machine-workflow-designer"></a>Verwenden des Zustandsautomatworkflow-Designers der Vorgängerversion
When you are creating a new state machine workflow project in [!INCLUDE[vs2010](../includes/vs2010-md.md)] that targets either the [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] or the [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)], you can choose to use either the **State Machine Workflow Console Application** or the **State Machine Workflow Library** legacy project template. Bei Auswahl einer der Zustandsautomatprojektvorlagen wird der Zustandsautomatdesigner als Workflow-Designer-Benutzeroberfläche der Vorgängerversion angezeigt. For information about the legacy state machine project templates, see [How to: Create State Machine Workflow Console Applications (Legacy)](../workflow-designer/how-to-create-state-machine-workflow-console-applications-legacy.md) and [How to: Create a State Machine Workflow Library (Legacy)](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md).

 Ein Zustandsautomatworkflow besteht aus einem Statusset. Ein Status wird als der Ausgangsstatus bezeichnet. Jeder Zustand kann einen bestimmten Satz Ereignisse erhalten. Auf Grundlage eines Ereignisses kann ein Übergang zu einem anderen Zustand erfolgen. Der Zustandsautomatworkflow kann über einen Endzustand verfügen. Beim Übergang zum Endstatus wird der Workflow abgeschlossen.

## <a name="state-machine-designer-views"></a>Zustandsautomaten-Designeransichten
 Der Zustandsautomaten-Designer ist ein Freihand-Designer, das heißt, die Aktivitäten können frei auf der Entwurfsoberfläche verschoben werden. The state machine designer has two views: *state* view and *event-driven* view.

 In der Statusansicht werden die Statusaktivitäten und die ereignisgesteuerten Aktivitäten, die in einer Statusaktivität enthalten sein können, angezeigt. In dieser Ansicht werden die Übergänge von einem Status in den anderen mit Linien dargestellt, die sich von der ereignisgesteuerten Aktivität in einem Status zum anderen Status erstrecken. Sie können auch Übergänge erstellen, indem Sie die Linie selbst ziehen. Zum Zeichnen des Übergangs wählen Sie die ereignisgesteuerte Aktivität aus und wählen dann einen Handle an der Aktivität aus und ziehen ihn. Mit dieser Aktion wird eine Linie gezeichnet. Diese Linie wird dann an den Zielstatus angefügt und gibt einen Übergang zwischen dem einen und dem anderen Status an.

 Für den Zugriff auf die ereignisgesteuerte Ansicht doppelklicken Sie auf eine ereignisgesteuerte Aktivität. Der angezeigte Designer unterscheidet sich nur geringfügig vom sequenziellen Workflow-Designer. Oben im Designer wird in einer Navigationsleiste die Hierarchie der Aktivitäten bis zur angezeigten ereignisgesteuerten Aktivität angezeigt. Sie können zur Statusansicht zurück navigieren, indem Sie auf ein beliebiges Element in der angezeigten Hierarchie klicken. Haben Sie in der Statusansicht einen Übergang von einem Status zum anderen gezeichnet und haben Sie die ereignisgesteuerte Ansicht dieser Aktivität aufgerufen, wird der ereignisgesteuerten Aktivität eine festgelegte Statusaktivität hinzugefügt. Ändern Sie die Eigenschaften der festgelegten Statusaktivität, spiegelt sich dies in der Statusansicht wieder.

## <a name="state-machine-workflow-activities"></a>Zustandsautomatenworkflowaktivitäten
 In der folgenden Tabelle werden die Hauptaktivitäten beschrieben, die im Zustandsautomatenworkflow-Designer verwendet werden.

|Toolboxname|Aktivität|Beschreibung|
|------------------|--------------|-----------------|
|**Zustand**|[StateActivity](https://go.microsoft.com/fwlink?LinkID=65042)|Represents a state in a state machine; may contain additional **StateActivity** activities. For more information, see [Using the StateActivity Activity](https://go.microsoft.com/fwlink?LinkID=65083).|
|**SetState**|[SetStateActivity](https://go.microsoft.com/fwlink?LinkID=65041)|Gibt einen Übergang zu einem neuen Zustand an. For more information, see [Using the SetStateActivity Activity](https://go.microsoft.com/fwlink?LinkID=65082).|
|**StateInitialization**|[StateInitializationActivity](https://go.microsoft.com/fwlink?LinkID=65044)|Wird ausgeführt, wenn ein Zustand eintritt. Enthält möglicherweise andere Aktivitäten. For more information, see [Using the StateInitialization Activity](https://go.microsoft.com/fwlink?LinkID=65006).|
|**StateFinalization**|[StateFinalizationActivity](https://go.microsoft.com/fwlink?LinkID=65043)|Executes contained activities when leaving a [StateActivity](https://go.microsoft.com/fwlink?LinkID=65042) activity. For more information, see [Using the StateFinalizationActivity Activity](https://go.microsoft.com/fwlink?LinkID=65008).|
|**EventDriven**|[EventDrivenActivity](https://go.microsoft.com/fwlink?LinkID=65029)|Wird für Zustände verwendet, die für die Ausführung ein externes Ereignis benötigen. The **EventDrivenActivity** activity must have an activity that implements the [IEventActivity](https://go.microsoft.com/fwlink?LinkID=65032) interface as the first child activity. For more information, see [Using the EventDrivenActivity Activity](https://go.microsoft.com/fwlink?LinkID=65068).|

 The main component in a state machine workflow is the [StateActivity](https://go.microsoft.com/fwlink?LinkID=65042) activity. Da Ereignisse an verschiedenen Punkten in einem Zustandsautomatenworkflow erfasst werden, werden verschiedene Zustände zur Handhabung der den Ereignissen zugewiesenen Aufgaben angenommen. Während der Workflowlebensdauer kann der Workflow verschiedene Status verlassen und annehmen. These states connect to each other by using the [SetStateActivity](https://go.microsoft.com/fwlink?LinkID=65041) activity.

 When you drag a new **StateActivity** onto the workflow design surface, you can add [EventDrivenActivity](https://go.microsoft.com/fwlink?LinkID=65029), [StateInitializationActivity](https://go.microsoft.com/fwlink?LinkID=65044), [StateFinalizationActivity](https://go.microsoft.com/fwlink?LinkID=65043), or additional **StateActivity** activities as child activities.

> [!CAUTION]
> When you use the state machine workflow designer to create workflows, you must monitor the structure of the workflow you are designing with the **Document Outline** view window. The view of the structure of the state machine workflow in the **Document Outline** view window mirrors the logical layout of the activities in the workflow markup file. Die physische Struktur der Workflowaktivitäten gemäß Darstellung auf der Entwurfsoberfläche spiegelt möglicherweise nicht die logische Struktur der Aktivitäten in der Workflowmarkupdatei wider.
>
> To open the **Document Outline** window, on the **View** menu, point to **Other Windows**, and then select **Document Outline**.

## <a name="see-also"></a>Siehe auch
 [How to: Create State Machine Workflow Console Applications (Legacy)](../workflow-designer/how-to-create-state-machine-workflow-console-applications-legacy.md) [How to: Create a State Machine Workflow Library (Legacy)](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md) [State Machine Workflows](https://go.microsoft.com/fwlink?LinkID=65016) [Using the StateActivity Activity](https://go.microsoft.com/fwlink?LinkID=65083) [Using the StateInitializationActivity Activity](https://go.microsoft.com/fwlink?LinkID=65006) [Using the StateFinalizationActivity Activity](https://go.microsoft.com/fwlink?LinkID=65008) [Using the SetStateActivity Activity](https://go.microsoft.com/fwlink?LinkID=65082) [Using the EventDrivenActivity Activity](https://go.microsoft.com/fwlink?LinkID=65068)