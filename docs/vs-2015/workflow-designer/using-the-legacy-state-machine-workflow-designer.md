---
title: Verwenden des Legacy Zustands Automaten-Workflow-Designer | Microsoft-Dokumentation
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
ms.openlocfilehash: 77bb2c7abb49dbf6fe973ebc80f8340000e4afbd
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2020
ms.locfileid: "75846005"
---
# <a name="using-the-legacy-state-machine-workflow-designer"></a>Verwenden des Zustandsautomatworkflow-Designers der Vorgängerversion
Wenn Sie ein neues zustandsautomatworkflowprojekt in [!INCLUDE[vs2010](../includes/vs2010-md.md)] erstellen, das entweder die [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] oder die [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]als Ziel hat, können Sie entweder die **Konsolenanwendung des Zustands Automaten Workflows** oder die Legacy-Projektvorlage für die **Zustands Automat-Workflow Bibliothek** verwenden. Bei Auswahl einer der Zustandsautomatprojektvorlagen wird der Zustandsautomatdesigner als Workflow-Designer-Benutzeroberfläche der Vorgängerversion angezeigt. Informationen zu den Legacy-zustandsautomatprojektvorlagen finden Sie unter Gewusst [wie: Erstellen von Konsolen Anwendungen für Zustandsautomatworkflows (Legacy)](../workflow-designer/how-to-create-state-machine-workflow-console-applications-legacy.md) und Vorgehensweise: Erstellen einer zustandsautomatworkflowbibliothek [(Legacy)](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md).

 Ein Zustandsautomatworkflow besteht aus einem Statusset. Ein Status wird als der Ausgangsstatus bezeichnet. Jeder Zustand kann einen bestimmten Satz Ereignisse erhalten. Auf Grundlage eines Ereignisses kann ein Übergang zu einem anderen Zustand erfolgen. Der Zustandsautomatworkflow kann über einen Endzustand verfügen. Beim Übergang zum Endstatus wird der Workflow abgeschlossen.

## <a name="state-machine-designer-views"></a>Zustandsautomaten-Designeransichten
 Der Zustandsautomaten-Designer ist ein Freihand-Designer, das heißt, die Aktivitäten können frei auf der Entwurfsoberfläche verschoben werden. Der Zustands Automaten-Designer verfügt über zwei Ansichten: *Status* Ansicht und *ereignisgesteuerte* Ansicht.

 In der Statusansicht werden die Statusaktivitäten und die ereignisgesteuerten Aktivitäten, die in einer Statusaktivität enthalten sein können, angezeigt. In dieser Ansicht werden die Übergänge von einem Status in den anderen mit Linien dargestellt, die sich von der ereignisgesteuerten Aktivität in einem Status zum anderen Status erstrecken. Sie können auch Übergänge erstellen, indem Sie die Linie selbst ziehen. Zum Zeichnen des Übergangs wählen Sie die ereignisgesteuerte Aktivität aus und wählen dann einen Handle an der Aktivität aus und ziehen ihn. Mit dieser Aktion wird eine Linie gezeichnet. Diese Linie wird dann an den Zielstatus angefügt und gibt einen Übergang zwischen dem einen und dem anderen Status an.

 Für den Zugriff auf die ereignisgesteuerte Ansicht doppelklicken Sie auf eine ereignisgesteuerte Aktivität. Der angezeigte Designer unterscheidet sich nur geringfügig vom sequenziellen Workflow-Designer. Oben im Designer wird in einer Navigationsleiste die Hierarchie der Aktivitäten bis zur angezeigten ereignisgesteuerten Aktivität angezeigt. Sie können zur Statusansicht zurück navigieren, indem Sie auf ein beliebiges Element in der angezeigten Hierarchie klicken. Haben Sie in der Statusansicht einen Übergang von einem Status zum anderen gezeichnet und haben Sie die ereignisgesteuerte Ansicht dieser Aktivität aufgerufen, wird der ereignisgesteuerten Aktivität eine festgelegte Statusaktivität hinzugefügt. Ändern Sie die Eigenschaften der festgelegten Statusaktivität, spiegelt sich dies in der Statusansicht wieder.

## <a name="state-machine-workflow-activities"></a>Zustandsautomatenworkflowaktivitäten
 In der folgenden Tabelle werden die Hauptaktivitäten beschrieben, die im Zustandsautomatenworkflow-Designer verwendet werden.

|Toolboxname|Activity|Beschreibung|
|------------------|--------------|-----------------|
|**Zustand**|[StateActivity](https://msdn2.microsoft.com/library/system.workflow.activities.stateactivity.aspx)|Stellt einen Zustand in einem Zustands Automaten dar. kann weitere **StateActivity** -Aktivitäten enthalten. Weitere Informationen finden Sie unter [Verwenden der StateActivity-Aktivität](https://msdn2.microsoft.com/library/bb628612.aspx).|
|**SetState**|[SetStateActivity](https://msdn2.microsoft.com/library/system.workflow.activities.setstateactivity.aspx)|Gibt einen Übergang zu einem neuen Zustand an. Weitere Informationen finden Sie unter [Verwenden der SetStateActivity-Aktivität](https://msdn2.microsoft.com/library/bb628469.aspx).|
|**StateInitialization**|[StateInitializationActivity](https://msdn2.microsoft.com/library/system.workflow.activities.stateinitializationactivity.aspx)|Wird ausgeführt, wenn ein Zustand eintritt. Enthält möglicherweise andere Aktivitäten. Weitere Informationen finden Sie unter [Verwenden der "Status-tialization](https://msdn2.microsoft.com/library/bb675253.aspx)"-Aktivität.|
|**StateFinalization**|[StateFinalizationActivity](https://msdn2.microsoft.com/library/system.workflow.activities.statefinalizationactivity.aspx)|Führt enthaltene Aktivitäten aus, wenn eine [StateActivity](https://msdn2.microsoft.com/library/system.workflow.activities.stateactivity.aspx) -Aktivität beendet wird. Weitere Informationen finden Sie unter [Verwenden der StateFinalizationActivity-Aktivität](https://msdn2.microsoft.com/library/bb675278.aspx).|
|**EventDriven**|[EventDrivenActivity](https://msdn2.microsoft.com/library/system.workflow.activities.eventdrivenactivity.aspx)|Wird für Zustände verwendet, die für die Ausführung ein externes Ereignis benötigen. Die **EventDrivenActivity** -Aktivität muss über eine Aktivität verfügen, die die [IEventActivity](https://msdn2.microsoft.com/library/system.workflow.activities.ieventactivity.aspx) -Schnittstelle als erste untergeordnete Aktivität implementiert. Weitere Informationen finden Sie unter [Verwenden der EventDrivenActivity-Aktivität](https://msdn2.microsoft.com/library/bb628466.aspx).|

 Die Hauptkomponente in einem Zustands Automaten Workflow ist die [StateActivity](https://msdn2.microsoft.com/library/system.workflow.activities.stateactivity.aspx) -Aktivität. Da Ereignisse an verschiedenen Punkten in einem Zustandsautomatenworkflow erfasst werden, werden verschiedene Zustände zur Handhabung der den Ereignissen zugewiesenen Aufgaben angenommen. Während der Workflowlebensdauer kann der Workflow verschiedene Status verlassen und annehmen. Diese Zustände werden mithilfe der [SetStateActivity](https://msdn2.microsoft.com/library/system.workflow.activities.setstateactivity.aspx) -Aktivität miteinander verbunden.

 Wenn Sie eine neue **StateActivity** auf die Workflow Entwurfs Oberfläche ziehen, können Sie [EventDrivenActivity](https://msdn2.microsoft.com/library/system.workflow.activities.eventdrivenactivity.aspx)-, [StateInitializationActivity](https://msdn2.microsoft.com/library/system.workflow.activities.stateinitializationactivity.aspx)-, [StateFinalizationActivity](https://msdn2.microsoft.com/library/system.workflow.activities.statefinalizationactivity.aspx)-oder zusätzliche **StateActivity** -Aktivitäten als untergeordnete Aktivitäten hinzufügen.

> [!CAUTION]
> Wenn Sie den Zustandsautomatworkflow-Designer verwenden, um Workflows zu erstellen, müssen Sie die Struktur des Workflows überwachen, den Sie mit dem **Dokument** Gliederungs Ansichts Fenster entwerfen. Die Ansicht der Struktur des Zustands Automaten Workflows im Fenster " **Dokument** Gliederungs Ansicht" spiegelt das logische Layout der Aktivitäten in der Workflow Markup Datei wider. Die physische Struktur der Workflowaktivitäten gemäß Darstellung auf der Entwurfsoberfläche spiegelt möglicherweise nicht die logische Struktur der Aktivitäten in der Workflowmarkupdatei wider.
>
> Zeigen Sie zum Öffnen des Fensters **Dokument** Gliederung im Menü **Ansicht** auf **Weitere Fenster**, und klicken Sie dann auf **Dokument**Gliederung.

## <a name="see-also"></a>Siehe auch
 Gewusst [wie: Erstellen von Konsolen Anwendungen für Zustandsautomatworkflows (](../workflow-designer/how-to-create-state-machine-workflow-console-applications-legacy.md) Vorgängerversion) Gewusst [wie: Erstellen eines](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md) Zustands Automaten [Workflows](https://msdn2.microsoft.com/library/bb628601.aspx) für Zustands Automaten Workflows [mithilfe der StateActivity](https://msdn2.microsoft.com/library/bb628612.aspx) -Aktivität mithilfe der [StateInitializationActivity](https://msdn2.microsoft.com/library/bb675253.aspx) -Aktivität mithilfe der Aktivität " [StateFinalizationActivity](https://msdn2.microsoft.com/library/bb675278.aspx) " mithilfe der Aktivität " [SetStateActivity](https://msdn2.microsoft.com/library/bb628469.aspx) " mithilfe der [EventDrivenActivity](https://msdn2.microsoft.com/library/bb628466.aspx) -Aktivität
