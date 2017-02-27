---
title: "Verwenden des Zustandsautomatworkflow-Designers der Vorg&#228;ngerversion | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "EventDrivenActivity-Aktivität"
  - "SetStateActivity-Aktivität"
  - "Zustandsautomatenworkflow-Designer"
  - "Zustandsautomatenworkflows, Aktivitäten"
  - "Zustandsautomatenworkflows, Designer"
  - "StateActivity-Aktivität"
  - "StateFinalizationActivity-Aktivität"
  - "StateInitializationActivity-Aktivität"
ms.assetid: 2cd21123-35c2-4eaf-82f6-86fce7a8f04d
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Verwenden des Zustandsautomatworkflow-Designers der Vorg&#228;ngerversion
Wenn Sie ein neues Zustandsautomat\-Workflowprojekt in [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] erstellen, das auf [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] oder [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] abzielt, können Sie die Projektvorlage des Zustandsautomatworkflowprojekt erstellen, können Sie wählen, entweder die **Konsolenanwendung für Zustandsautomatworkflows** oder die Projektvorlage aus der Vorgängerversion **Zustandsautomat\-Workflowbibliothek** verwenden.Bei Auswahl einer der Zustandsautomatprojektvorlagen wird der Zustandsautomatdesigner als Workflow\-Designer\-Benutzeroberfläche der Vorgängerversion angezeigt.Weitere Informationen zu den Zustandsautomatprojektvorlagen der Vorgängerversion finden Sie unter [Vorgehensweise: Erstellen von Konsolenanwendungen für Zustandsautomatworkflows \(Vorgängerversion\)](../workflow-designer/how-to-create-state-machine-workflow-console-applications-legacy.md) und [Vorgehensweise: Erstellen einer Zustandsautomatworkflowbibliothek \(Vorgängerversion\)](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md).  
  
 Ein Zustandsautomatworkflow besteht aus einer Reihe von Status.Ein Status wird als der Ausgangsstatus bezeichnet.Jeder Status kann einen bestimmten Satz Ereignisse erhalten.Auf Grundlage eines Ereignisses kann ein Übergang zu einem anderen Status erfolgen.Der Zustandsautomatenworkflow kann über einen Endstatus verfügen.Beim Übergang zum Endstatus wird der Workflow abgeschlossen.  
  
## Zustandsautomaten\-Designeransichten  
 Der Zustandsautomaten\-Designer ist ein Freihand\-Designer, das heißt, die Aktivitäten können frei auf der Entwurfsoberfläche verschoben werden.Der Zustandsautomaten\-Designer verfügt über zwei Ansichten: *Statusansicht* und *ereignisgesteuerte* Ansicht.  
  
 In der Statusansicht werden die Statusaktivitäten und die ereignisgesteuerten Aktivitäten, die in einer Statusaktivität enthalten sein können, angezeigt.In dieser Ansicht werden die Übergänge von einem Status in den anderen mit Linien dargestellt, die sich von der ereignisgesteuerten Aktivität in einem Status zum anderen Status erstrecken.Sie können auch Übergänge erstellen, indem Sie die Linie selbst ziehen.Zum Zeichnen des Übergangs wählen Sie die ereignisgesteuerte Aktivität aus und wählen dann einen Handle an der Aktivität aus und ziehen ihn.Mit dieser Aktion wird eine Linie gezeichnet.Diese Linie wird dann an den Zielstatus angefügt und gibt einen Übergang zwischen dem einen und dem anderen Status an.  
  
 Für den Zugriff auf die ereignisgesteuerte Ansicht doppelklicken Sie auf eine ereignisgesteuerte Aktivität.Der angezeigte Designer unterscheidet sich nur geringfügig vom sequenziellen Workflow\-Designer.Oben im Designer wird in einer Navigationsleiste die Hierarchie der Aktivitäten bis zur angezeigten ereignisgesteuerten Aktivität angezeigt.Sie können zur Statusansicht zurück navigieren, indem Sie auf ein beliebiges Element in der angezeigten Hierarchie klicken.Haben Sie in der Statusansicht einen Übergang von einem Status zum anderen gezeichnet und haben Sie die ereignisgesteuerte Ansicht dieser Aktivität aufgerufen, wird der ereignisgesteuerten Aktivität eine festgelegte Statusaktivität hinzugefügt.Ändern Sie die Eigenschaften der festgelegten Statusaktivität, spiegelt sich dies in der Statusansicht wieder.  
  
## Zustandsautomatenworkflowaktivitäten  
 In der folgenden Tabelle werden die Hauptaktivitäten beschrieben, die im Zustandsautomatenworkflow\-Designer verwendet werden.  
  
|Toolboxname|Aktivität|Beschreibung|  
|-----------------|---------------|------------------|  
|**Zustand**|[StateActivity](http://go.microsoft.com/fwlink?LinkID=65042)|Stellt einen Status auf einem Zustandsautomaten dar; enthält möglicherweise zusätzliche **StateActivity**\-Aktivitäten.Weitere Informationen finden Sie unter [Verwenden der StateActivity\-Aktivität](http://go.microsoft.com/fwlink?LinkID=65083).|  
|**SetState**|[SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041)|Gibt einen Übergang zu einem neuen Status an.Weitere Informationen finden Sie unter [Verwenden der SetStateActivity\-Aktivität](http://go.microsoft.com/fwlink?LinkID=65082).|  
|**StateInitialization**|[StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044)|Wird ausgeführt, wenn ein Status eintritt. Enthält möglicherweise andere Aktivitäten.Weitere Informationen finden Sie unter [Verwenden der StateInitialization\-Aktivität](http://go.microsoft.com/fwlink?LinkID=65006).|  
|**StateFinalization**|[StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043)|Führt beim Verlassen einer [StateActivity](http://go.microsoft.com/fwlink?LinkID=65042)\-Aktivität enthaltene Aktivitäten aus.Weitere Informationen finden Sie unter [Verwenden der StateFinalizationActivity\-Aktivität](http://go.microsoft.com/fwlink?LinkID=65008).|  
|**EventDriven**|[EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029)|Wird für jeden Status verwendet, der für die Ausführung ein externes Ereignis benötigt.Die **EventDrivenActivity**\-Aktivität muss über eine Aktivität verfügen, die die [IEventActivity](http://go.microsoft.com/fwlink?LinkID=65032)\-Schnittstelle als erste untergeordnete Aktivität implementiert.Weitere Informationen finden Sie unter [Verwenden der EventDrivenActivity\-Aktivität](http://go.microsoft.com/fwlink?LinkID=65068).|  
  
 Die Hauptkomponente in einem Zustandsautomatenworkflow ist die [StateActivity](http://go.microsoft.com/fwlink?LinkID=65042)\-Aktivität.Da Ereignisse an verschiedenen Punkten in einem Zustandsautomatenworkflow erfasst werden, werden verschiedene Zustände zur Handhabung der den Ereignissen zugewiesenen Aufgaben angenommen.Während der Workflowlebensdauer kann der Workflow verschiedene Status verlassen und annehmen.Diese Status werden mit der [SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041)\-Aktivität miteinander verbunden.  
  
 Wenn Sie eine neue **StateActivity** auf die Workflowentwurfsoberfläche ziehen, können Sie die [EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029)\-Aktivität, die [StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044)\-Aktivität, die [StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043)\-Aktivität oder zusätzliche **StateActivity**\-Aktivitäten als untergeordnete Aktivitäten hinzufügen.  
  
> [!CAUTION]
>  Bei Verwendung des Zustandsautomaten\-Designers zur Erstellung von Workflows müssen Sie die Struktur des Workflows überwachen, den Sie mit dem Ansichtsfenster **Dokumentgliederung** entwerfen.Die Ansicht der Struktur des Zustandsautomatenworkflows in der Ansicht **Dokumentgliederung** spiegelt die logische Struktur der in der Workflowmarkupdatei enthaltenen Aktivitäten wider.Die physische Struktur der Workflowaktivitäten gemäß Darstellung auf der Entwurfsoberfläche spiegelt möglicherweise nicht die logische Struktur der Aktivitäten in der Workflowmarkupdatei wider.  
>   
>  Zeigen Sie zum Öffnen des Fensters **Dokumentgliederung** im Menü **Ansicht** auf **Weitere Fenster**, und klicken Sie anschließend auf **Dokumentgliederung**.  
  
## Siehe auch  
 [Vorgehensweise: Erstellen von Konsolenanwendungen für Zustandsautomatworkflows \(Vorgängerversion\)](../workflow-designer/how-to-create-state-machine-workflow-console-applications-legacy.md)   
 [Vorgehensweise: Erstellen einer Zustandsautomatworkflowbibliothek \(Vorgängerversion\)](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md)   
 [Zustandsautomatworkflows](http://go.microsoft.com/fwlink?LinkID=65016)   
 [Verwenden der StateActivity\-Aktivität](http://go.microsoft.com/fwlink?LinkID=65083)   
 [Verwenden der StateInitializationActivity\-Aktivität](http://go.microsoft.com/fwlink?LinkID=65006)   
 [Verwenden der StateFinalizationActivity\-Aktivität](http://go.microsoft.com/fwlink?LinkID=65008)   
 [Verwenden der SetStateActivity\-Aktivität](http://go.microsoft.com/fwlink?LinkID=65082)   
 [Verwenden der EventDrivenActivity\-Aktivität](http://go.microsoft.com/fwlink?LinkID=65068)