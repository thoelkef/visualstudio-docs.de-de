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
ms.openlocfilehash: 8c2b1ce1f1b2c6a16b5576880904feadf37a3e7b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72606770"
---
# <a name="using-the-legacy-state-machine-workflow-designer"></a>Verwenden des Zustandsautomatworkflow-Designers der Vorgängerversion
Wenn Sie ein neues zustandsautomatworkflowprojekt in [!INCLUDE[vs2010](../includes/vs2010-md.md)] erstellen, das entweder die [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] oder die [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] als Ziel hat, können Sie entweder die **Konsolenanwendung des Zustands Automaten Workflows** oder die Vorgängerversion der **Zustands Automat-Workflow Bibliothek** verwenden. Projektvorlage. Bei Auswahl einer der Zustandsautomatprojektvorlagen wird der Zustandsautomatdesigner als Workflow-Designer-Benutzeroberfläche der Vorgängerversion angezeigt. Informationen zu den Legacy-zustandsautomatprojektvorlagen finden Sie unter Gewusst [wie: Erstellen von Konsolen Anwendungen für Zustandsautomatworkflows (Legacy)](../workflow-designer/how-to-create-state-machine-workflow-console-applications-legacy.md) und Vorgehensweise: Erstellen einer zustandsautomatworkflowbibliothek [(Legacy)](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md).

 Ein Zustandsautomatworkflow besteht aus einem Statusset. Ein Status wird als der Ausgangsstatus bezeichnet. Jeder Zustand kann einen bestimmten Satz Ereignisse erhalten. Auf Grundlage eines Ereignisses kann ein Übergang zu einem anderen Zustand erfolgen. Der Zustandsautomatworkflow kann über einen Endzustand verfügen. Beim Übergang zum Endstatus wird der Workflow abgeschlossen.

## <a name="state-machine-designer-views"></a>Zustandsautomaten-Designeransichten
 Der Zustandsautomaten-Designer ist ein Freihand-Designer, das heißt, die Aktivitäten können frei auf der Entwurfsoberfläche verschoben werden. Der Zustands Automaten-Designer verfügt über zwei Ansichten: *Status* Ansicht und *ereignisgesteuerte* Ansicht.

 In der Statusansicht werden die Statusaktivitäten und die ereignisgesteuerten Aktivitäten, die in einer Statusaktivität enthalten sein können, angezeigt. In dieser Ansicht werden die Übergänge von einem Status in den anderen mit Linien dargestellt, die sich von der ereignisgesteuerten Aktivität in einem Status zum anderen Status erstrecken. Sie können auch Übergänge erstellen, indem Sie die Linie selbst ziehen. Zum Zeichnen des Übergangs wählen Sie die ereignisgesteuerte Aktivität aus und wählen dann einen Handle an der Aktivität aus und ziehen ihn. Mit dieser Aktion wird eine Linie gezeichnet. Diese Linie wird dann an den Zielstatus angefügt und gibt einen Übergang zwischen dem einen und dem anderen Status an.

 Für den Zugriff auf die ereignisgesteuerte Ansicht doppelklicken Sie auf eine ereignisgesteuerte Aktivität. Der angezeigte Designer unterscheidet sich nur geringfügig vom sequenziellen Workflow-Designer. Oben im Designer wird in einer Navigationsleiste die Hierarchie der Aktivitäten bis zur angezeigten ereignisgesteuerten Aktivität angezeigt. Sie können zur Statusansicht zurück navigieren, indem Sie auf ein beliebiges Element in der angezeigten Hierarchie klicken. Haben Sie in der Statusansicht einen Übergang von einem Status zum anderen gezeichnet und haben Sie die ereignisgesteuerte Ansicht dieser Aktivität aufgerufen, wird der ereignisgesteuerten Aktivität eine festgelegte Statusaktivität hinzugefügt. Ändern Sie die Eigenschaften der festgelegten Statusaktivität, spiegelt sich dies in der Statusansicht wieder.

## <a name="state-machine-workflow-activities"></a>Zustandsautomatenworkflowaktivitäten
 In der folgenden Tabelle werden die Hauptaktivitäten beschrieben, die im Zustandsautomatenworkflow-Designer verwendet werden.

|Toolboxname|Aktivität|Beschreibung|
|------------------|--------------|-----------------|
|**Zustand**|[StateActivity](http://go.microsoft.com/fwlink?LinkID=65042)|Stellt einen Zustand in einem Zustands Automaten dar. kann weitere **StateActivity** -Aktivitäten enthalten. Weitere Informationen finden Sie unter [Verwenden der StateActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65083).|
|**SetState**|[SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041)|Gibt einen Übergang zu einem neuen Zustand an. Weitere Informationen finden Sie unter [Verwenden der SetStateActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65082).|
|**StateInitialization**|[StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044)|Wird ausgeführt, wenn ein Zustand eintritt. Enthält möglicherweise andere Aktivitäten. Weitere Informationen finden Sie unter [Verwenden der "Status-tialization](http://go.microsoft.com/fwlink?LinkID=65006)"-Aktivität.|
|**StateFinalization**|[StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043)|Führt enthaltene Aktivitäten aus, wenn eine [StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) -Aktivität beendet wird. Weitere Informationen finden Sie unter [Verwenden der StateFinalizationActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65008).|
|**EventDriven**|[EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029)|Wird für Zustände verwendet, die für die Ausführung ein externes Ereignis benötigen. Die **EventDrivenActivity** -Aktivität muss über eine Aktivität verfügen, die die [IEventActivity](http://go.microsoft.com/fwlink?LinkID=65032) -Schnittstelle als erste untergeordnete Aktivität implementiert. Weitere Informationen finden Sie unter [Verwenden der EventDrivenActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65068).|

 Die Hauptkomponente in einem Zustands Automaten Workflow ist die [StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) -Aktivität. Da Ereignisse an verschiedenen Punkten in einem Zustandsautomatenworkflow erfasst werden, werden verschiedene Zustände zur Handhabung der den Ereignissen zugewiesenen Aufgaben angenommen. Während der Workflowlebensdauer kann der Workflow verschiedene Status verlassen und annehmen. Diese Zustände werden mithilfe der [SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041) -Aktivität miteinander verbunden.

 Wenn Sie eine neue **StateActivity** auf die Workflow Entwurfs Oberfläche ziehen, können Sie [EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029)-, [StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044)-, [StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043)-oder zusätzliche **StateActivity** -Aktivitäten als untergeordnete Aktivitäten.

> [!CAUTION]
> Wenn Sie den Zustandsautomatworkflow-Designer verwenden, um Workflows zu erstellen, müssen Sie die Struktur des Workflows überwachen, den Sie mit dem **Dokument** Gliederungs Ansichts Fenster entwerfen. Die Ansicht der Struktur des Zustands Automaten Workflows im Fenster " **Dokument** Gliederungs Ansicht" spiegelt das logische Layout der Aktivitäten in der Workflow Markup Datei wider. Die physische Struktur der Workflowaktivitäten gemäß Darstellung auf der Entwurfsoberfläche spiegelt möglicherweise nicht die logische Struktur der Aktivitäten in der Workflowmarkupdatei wider.
>
> Zeigen Sie zum Öffnen des Fensters **Dokument** Gliederung im Menü **Ansicht** auf **Weitere Fenster**, und klicken Sie dann auf **Dokument**Gliederung.

## <a name="see-also"></a>Siehe auch
 Gewusst [wie: Erstellen von Konsolen Anwendungen für Zustandsautomatworkflows (](../workflow-designer/how-to-create-state-machine-workflow-console-applications-legacy.md) Vorgängerversion) Gewusst [wie: Erstellen eines](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md) Zustands Automaten [Workflows](http://go.microsoft.com/fwlink?LinkID=65016) für Zustands Automaten Workflows [mithilfe der StateActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65083) mithilfe [der StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65006) -Aktivität, [die die StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65008) -Aktivität mithilfe der [SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65082) -Aktivität mithilfe [der EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65068) -Aktivität verwendet.