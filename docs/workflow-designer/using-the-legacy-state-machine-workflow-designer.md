---
title: Mithilfe der Vorgängerversion des Zustandsautomatworkflow-Designers | Microsoft Docs
ms.date: 11/04/2016
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 16178d2f83ef9cc45ef7007350e30d2b36d6993a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="using-the-legacy-state-machine-workflow-designer"></a>Verwenden des Zustandsautomatworkflow-Designers der Vorgängerversion
Wenn Sie erstellen ein neues Zustandsautomat-Workflowprojekt in [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] abzielt die [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] oder die [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)], Sie könne beide verwenden die **Konsolenanwendung für Zustandsautomatenworkflows Status** oder die  **Workflowbibliothek Status** legacy-Projektvorlage. Bei Auswahl einer der Zustandsautomatprojektvorlagen wird der Zustandsautomatdesigner als Workflow-Designer-Benutzeroberfläche der Vorgängerversion angezeigt. Informationen zu den Projektvorlagen für legacy-Status-Computer finden Sie unter [Vorgehensweise: Erstellen Zustand Konsolenanwendungen für Zustandsautomatworkflows (Vorgängerversion)](../workflow-designer/how-to-create-state-machine-workflow-console-applications-legacy.md) und [Vorgehensweise: Erstellen einer Zustandsautomatworkflowbibliothek (Vorgängerversion)](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md).

 Ein Zustandsautomatworkflow besteht aus einem Statusset. Ein Status wird als der Ausgangsstatus bezeichnet. Jeder Zustand kann einen bestimmten Satz Ereignisse erhalten. Auf Grundlage eines Ereignisses kann ein Übergang zu einem anderen Zustand erfolgen. Der Zustandsautomatworkflow kann über einen Endzustand verfügen. Beim Übergang zum Endstatus wird der Workflow abgeschlossen.

## <a name="state-machine-designer-views"></a>Zustandsautomaten-Designeransichten
 Der Zustandsautomaten-Designer ist ein Freihand-Designer, das heißt, die Aktivitäten können frei auf der Entwurfsoberfläche verschoben werden. Der Zustandsautomaten-Designer verfügt über zwei Ansichten: *Status* anzeigen und *ereignisgesteuerte* anzeigen.

 In der Statusansicht werden die Statusaktivitäten und die ereignisgesteuerten Aktivitäten, die in einer Statusaktivität enthalten sein können, angezeigt. In dieser Ansicht werden die Übergänge von einem Status in den anderen mit Linien dargestellt, die sich von der ereignisgesteuerten Aktivität in einem Status zum anderen Status erstrecken. Sie können auch Übergänge erstellen, indem Sie die Linie selbst ziehen. Zum Zeichnen des Übergangs wählen Sie die ereignisgesteuerte Aktivität aus und wählen dann einen Handle an der Aktivität aus und ziehen ihn. Mit dieser Aktion wird eine Linie gezeichnet. Diese Linie wird dann an den Zielstatus angefügt und gibt einen Übergang zwischen dem einen und dem anderen Status an.

 Für den Zugriff auf die ereignisgesteuerte Ansicht doppelklicken Sie auf eine ereignisgesteuerte Aktivität. Der angezeigte Designer unterscheidet sich nur geringfügig vom sequenziellen Workflow-Designer. Oben im Designer wird in einer Navigationsleiste die Hierarchie der Aktivitäten bis zur angezeigten ereignisgesteuerten Aktivität angezeigt. Sie können zur Statusansicht zurück navigieren, indem Sie auf ein beliebiges Element in der angezeigten Hierarchie klicken. Haben Sie in der Statusansicht einen Übergang von einem Status zum anderen gezeichnet und haben Sie die ereignisgesteuerte Ansicht dieser Aktivität aufgerufen, wird der ereignisgesteuerten Aktivität eine festgelegte Statusaktivität hinzugefügt. Ändern Sie die Eigenschaften der festgelegten Statusaktivität, spiegelt sich dies in der Statusansicht wieder.

## <a name="state-machine-workflow-activities"></a>Zustandsautomatenworkflowaktivitäten
 In der folgenden Tabelle werden die Hauptaktivitäten beschrieben, die im Zustandsautomatenworkflow-Designer verwendet werden.

|Toolboxname|Aktivität|Beschreibung|
|------------------|--------------|-----------------|
|**Zustand**|[StateActivity](http://go.microsoft.com/fwlink?LinkID=65042)|Stellt einen Zustand in einem Zustandsautomaten dar; enthält möglicherweise zusätzliche **StateActivity** Aktivitäten. Weitere Informationen finden Sie unter [verwenden der StateActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65083).|
|**SetState**|[SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041)|Gibt einen Übergang zu einem neuen Zustand an. Weitere Informationen finden Sie unter [verwenden der SetStateActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65082).|
|**StateInitialization**|[StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044)|Wird ausgeführt, wenn ein Zustand eintritt. Enthält möglicherweise andere Aktivitäten. Weitere Informationen finden Sie unter [verwenden der StateInitialization-Aktivität](http://go.microsoft.com/fwlink?LinkID=65006).|
|**StateFinalization**|[StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043)|Führt enthaltene Aktivitäten beim Verlassen einer [StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) Aktivität. Weitere Informationen finden Sie unter [verwenden der StateFinalizationActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65008).|
|**EventDriven**|[EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029)|Wird für Zustände verwendet, die für die Ausführung ein externes Ereignis benötigen. Die **EventDrivenActivity** Aktivität benötigen eine Aktivität, die implementiert die [IEventActivity](http://go.microsoft.com/fwlink?LinkID=65032) Schnittstelle als die erste untergeordnete Aktivität. Weitere Informationen finden Sie unter [verwenden der EventDrivenActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65068).|

 Die Hauptkomponente in einem zustandsautomatenworkflow ist die [StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) Aktivität. Da Ereignisse an verschiedenen Punkten in einem Zustandsautomatenworkflow erfasst werden, werden verschiedene Zustände zur Handhabung der den Ereignissen zugewiesenen Aufgaben angenommen. Während der Workflowlebensdauer kann der Workflow verschiedene Status verlassen und annehmen. Diese Zustände miteinander verbinden, mithilfe der [SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041) Aktivität.

 Wenn Sie ein neues ziehen **StateActivity** Sie können auf der Workflowentwurfsoberfläche hinzufügen [EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029), [StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044), [ StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043), oder zusätzliche **StateActivity** Aktivitäten als untergeordnete Aktivitäten.

> [!CAUTION]
> Wenn Sie die Zustandsautomatworkflow-Designers verwenden, um Workflows zu erstellen, müssen Sie die Struktur des Workflows, die Sie entwerfen mit überwachen die **Dokumentgliederung** Fenster "anzeigen". Die Ansicht der Struktur des zustandsautomatenworkflows in der **Dokumentgliederung** spiegelt die logische Struktur der Aktivitäten in der Workflowmarkupdatei anzeigen. Die physische Struktur der Workflowaktivitäten gemäß Darstellung auf der Entwurfsoberfläche spiegelt möglicherweise nicht die logische Struktur der Aktivitäten in der Workflowmarkupdatei wider.
>
> So öffnen die **Dokumentgliederung** Fenster auf die **Ansicht** Startmenü nacheinander auf **Weitere Fenster**, und wählen Sie dann **Dokumentgliederung**.

## <a name="see-also"></a>Siehe auch

- [Vorgehensweise: Erstellen von Konsolenanwendungen für Zustandsautomatworkflows (Vorgängerversion)](../workflow-designer/how-to-create-state-machine-workflow-console-applications-legacy.md)
- [Vorgehensweise: Erstellen einer Zustandsautomatworkflowbibliothek (Vorgängerversion)](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md)
- [Zustandsautomatworkflows](http://go.microsoft.com/fwlink?LinkID=65016)
- [Verwenden der StateActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65083)
- [Verwenden der StateInitializationActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65006)
- [Verwenden der StateFinalizationActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65008)
- [Verwenden der SetStateActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65082)
- [Verwenden der EventDrivenActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65068)