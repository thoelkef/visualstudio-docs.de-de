---
title: Workflow-Designer - Legacy-Workflowaktivitäten
ms.date: 01/18/2017
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- workflows, activities
- activities
- workflow activities
ms.assetid: 4af7a06b-1e82-43c8-aec8-0dc5fb63d08a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 45c24c0be518e58ce87af11a38486818ca4a3ac7
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31979476"
---
# <a name="legacy-workflow-activities"></a>Legacyworkflowaktivitäten

Windows Workflow Foundation (WF) umfasst eine Reihe von Aktivitäten, die Funktionen für ablaufsteuerung, Bedingungen, Ereignisbehandlung, Zustandsverwaltung und Kommunikation mit Anwendungen und Dienste bereitzustellen. Beim Entwurf von Workflows können Sie die vom System bereitgestellte Aktivitäten, die von der Windows-Workflow-Designer bereitgestellt werden, oder Sie können eigene benutzerdefinierten Aktivitäten erstellen.

In der folgenden Tabelle ist der vordefinierte Aktivitätssatz des Windows Workflow Foundation-Framework aufgeführt. Viele, aber nicht alle dieser Aktivitäten werden dargestellte Aktivitäts-Designer aus zugegriffen werden können die **Toolbox** im Workflow-Designer. Um eine Aktivität zu erstellen, ziehen Sie ihren Designer aus der **Toolbox** und legen Sie sie auf der Entwurfsoberfläche angezeigt.

|Aktivität|Beschreibung|
|--------------|-----------------|
|<xref:System.Workflow.Activities.CallExternalMethodActivity>|Verwendet die **HandleExternalEventActivity** -Aktivität für Eingabe- und ausgabekommunikation mit einem lokalen Dienst. Weitere Informationen finden Sie unter [mithilfe der Aktivität CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65060).|
|**System.Workflow.Activities.CancellationHandlerActivity**|Wird zur Speicherung der Bereinigungslogik für eine zusammengesetzte Aktivität verwendet, die abgebrochen wurde, bevor alle untergeordneten Elemente der zusammengesetzten Aktivität ausgeführt werden konnten. Weitere Informationen finden Sie unter [mithilfe der Aktivität CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65061).|
|<xref:System.Workflow.Activities.CodeActivity>|Ermöglicht das Hinzufügen von Visual Basic- oder C#-Code zu Ihrem Workflow. Weitere Informationen finden Sie unter [mithilfe der Aktivität CodeActivity](http://go.microsoft.com/fwlink?LinkID=65062).|
|<xref:System.Workflow.Activities.CompensatableSequenceActivity>|Eine kompensierbare Version von <xref:System.Workflow.Activities.SequenceActivity>. Weitere Informationen finden Sie unter [mithilfe der Aktivität CompensatableSequenceActivity](http://go.microsoft.com/fwlink?LinkID=65002).|
|**System.Workflow.Activities.CompensatableTransactionScopeActivity**|Eine kompensierbare Version der **TransactionScopeActivity**. Weitere Informationen finden Sie unter [mithilfe der Aktivität CompensatableTransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65063).|
|**System.Workflow.Activities.CompensateActivity**|Hiermit können Sie den Code aufrufen oder Vorgänge kompensieren, die zum Zeitpunkt des Auftretens des Fehlers bereits vom Workflow ausgeführt wurden. Weitere Informationen finden Sie unter [mithilfe der Aktivität "CompensateActivity"](http://go.microsoft.com/fwlink?LinkID=65064).|
|**System.Workflow.Activities.CompensationHandlerActivity**|Ein Wrapper für eine oder mehrere Aktivitäten, eine abgeschlossene TransactionScopeActivity-Aktivität für Weitere Informationen finden Sie unter [verwenden der CompensationHandlerActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65065).|
|<xref:System.Workflow.Activities.ConditionedActivityGroup>|Führt untergeordnete Aktivitäten auf Grundlage einer Bedingung aus, die für die <xref:System.Workflow.Activities.ConditionedActivityGroup>-Aktivität selbst gilt, sowie auf Grundlage von Bedingungen, die gesondert für jede untergeordnete Aktivität gelten. Weitere Informationen finden Sie unter [mithilfe der Aktivität ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65066).|
|<xref:System.Workflow.Activities.DelayActivity>|Ermöglicht das Erstellen von auf einem Timeoutintervall basierenden Verzögerungen in Ihrem Workflow. Weitere Informationen finden Sie unter [mithilfe der Aktivität DelayActivity](http://go.microsoft.com/fwlink?LinkID=65067).|
|<xref:System.Workflow.Activities.EventDrivenActivity>|Umschließt eine oder mehrere Aktivitäten, die ausgeführt werden, wenn ein bestimmtes Ereignis eintritt. Weitere Informationen finden Sie unter [verwenden der EventDrivenActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65068).|
|<xref:System.Workflow.Activities.EventHandlersActivity>|Stellt ein Framework für das Zuweisen von Ereignissen zu einer Aktivität bereit. Weitere Informationen finden Sie unter [mithilfe der Aktivität EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65069).|
|<xref:System.Workflow.Activities.EventHandlingScopeActivity>|Führt die wichtigste untergeordnete Aktivität gleichzeitig mit einer <xref:System.Workflow.Activities.EventHandlersActivity>. Weitere Informationen finden Sie unter [mithilfe der Aktivität EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65070).|
|**System.Workflow.Activities.FaultHandlerActivity**|Wird zur Behandlung einer Ausnahme des von Ihnen angegebenen Typs verwendet. Weitere Informationen finden Sie unter [mithilfe der Aktivität FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65071).|
|**System.Workflow.Activities.FaultHandlersActivity**|Stellt eine zusammengesetzte Aktivität, die eine geordnete Liste untergeordneter Aktivitäten vom Typ hat **System.Workflow.Activities.FaultHandlerActivity**. Weitere Informationen finden Sie unter [mithilfe der Aktivität FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65072).|
|<xref:System.Workflow.Activities.HandleExternalEventActivity>|Wird in Verbindung mit der <xref:System.Workflow.Activities.CallExternalMethodActivity> -Aktivität für Eingabe- und ausgabekommunikation mit einem lokalen Dienst. Weitere Informationen finden Sie unter [mithilfe der Aktivität HandleExternalEventActivity](http://go.microsoft.com/fwlink?LinkID=65073).|
|<xref:System.Workflow.Activities.IfElseActivity>|Testet eine Bedingung für jede Verzweigung und führt Aktivitäten für die erste Verzweigung, die für die die Bedingung **"true"**. Weitere Informationen finden Sie unter [mithilfe der Aktivität IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65074).|
|<xref:System.Workflow.Activities.IfElseBranchActivity>|Stellt eine Verzweigung von <xref:System.Workflow.Activities.IfElseActivity> dar. Weitere Informationen finden Sie unter [mithilfe der Aktivität "IfElseBranchActivity"](http://go.microsoft.com/fwlink?LinkID=65075).|
|<xref:System.Workflow.Activities.InvokeWebServiceActivity>|Unterstützt das Aufrufen eines Webdienstes durch Ihren Workflow. Weitere Informationen finden Sie unter [mithilfe der Aktivität InvokeWebServiceActivity](http://go.microsoft.com/fwlink?LinkID=65076).|
|<xref:System.Workflow.Activities.InvokeWorkflowActivity>|Unterstützt das Aufrufen eines anderen Webdienstes durch Ihren Workflow. Weitere Informationen finden Sie unter [mithilfe der Aktivität "InvokeWorkflowActivity"](http://go.microsoft.com/fwlink?LinkID=65077).|
|<xref:System.Workflow.Activities.ListenActivity>|Eine zusammengesetzte Aktivität, die nur untergeordnete <xref:System.Workflow.Activities.EventDrivenActivity>-Aktivitäten enthält. Weitere Informationen finden Sie unter [mithilfe der Aktivität "ListenActivity"](http://go.microsoft.com/fwlink?LinkID=65078).|
|<xref:System.Workflow.Activities.ParallelActivity>|Bietet eine Möglichkeit, Planung von zwei oder mehr untergeordneten **SequenceActivity** -aktivitätsverzweigungen für die gleichzeitige Verarbeitung. Weitere Informationen finden Sie unter [mithilfe der Aktivität ParallelActivity](http://go.microsoft.com/fwlink?LinkID=65079).|
|<xref:System.Workflow.Activities.PolicyActivity>|Verwendung zur Darstellung einer Auflistung von Regeln. Eine Regel besteht aus Bedingungen und daraus resultierenden Aktionen. Weitere Informationen finden Sie unter [verwenden der PolicyActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65004).|
|<xref:System.Workflow.Activities.ReplicatorActivity>|Erstellt mehrere Instanzen einer einzelnen untergeordneten Aktivität. Weitere Informationen finden Sie unter [mithilfe der Aktivität ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65080).|
|<xref:System.Workflow.Activities.SequenceActivity>|Bietet eine einfache Möglichkeit zur Verknüpfung mehrerer Aktivitäten für die sequenzielle Ausführung. Weitere Informationen finden Sie unter [mithilfe der Aktivität SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65081).|
|<xref:System.Workflow.Activities.SetStateActivity>|Gibt einen Übergang zu einem neuen Zustand an. Weitere Informationen finden Sie unter [verwenden der SetStateActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65082).|
|<xref:System.Workflow.Activities.StateActivity>|Stellt einen Zustand in einem Zustandsautomatworkflow dar. Weitere Informationen finden Sie unter [verwenden der StateActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65083).|
|<xref:System.Workflow.Activities.StateFinalizationActivity>|Verwendet eine <xref:System.Workflow.Activities.StateActivity> -Aktivität als Container für untergeordnete Aktivitäten, die ausgeführt werden, beim Verlassen der **StateActivity** Aktivität. Weitere Informationen finden Sie unter [verwenden der StateFinalizationActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65008).|
|<xref:System.Workflow.Activities.StateInitializationActivity>|Verwendet eine <xref:System.Workflow.Activities.StateActivity> -Aktivität als Container für untergeordnete Aktivitäten, die ausgeführt werden, bei der Eingabe der **StateActivity** Aktivität. Weitere Informationen finden Sie unter [StateInitializationActivity-Aktivität mit](http://go.microsoft.com/fwlink?LinkID=65006).|
|**System.Workflow.Activities.SuspendActivity**|Unterbricht den Vorgang des Workflows, um bei einer besonders zu beachtenden Fehlerbedingung Eingriffe zu ermöglichen. Weitere Informationen finden Sie unter [mithilfe der Aktivität SuspendActivity](http://go.microsoft.com/fwlink?LinkID=65084).|
|**System.Workflow.Activities.SynchronizationScopeActivity**|Führt enthaltene Aktivitäten in einer synchronisierten Domäne sequenziell aus. Weitere Informationen finden Sie unter [mithilfe der Aktivität SynchronizationScopeActivity](http://go.microsoft.com/fwlink?LinkID=65085).|
|**System.Workflow.Activities.TerminateActivity**|Unterstützt die sofortige Beendigung der Ausführung Ihres Workflows für den Fall, dass eine Fehlerbedingung vorliegt. Weitere Informationen finden Sie unter [mithilfe der Aktivität TerminateActivity](http://go.microsoft.com/fwlink?LinkID=65086).|
|**System.Workflow.Activities.ThrowActivity**|Unterstützt die Erfassung von Geschäftsausnahmen, die als Bestandteil der Prozessmetadaten für einen Workflow ausgelöst werden. Weitere Informationen finden Sie unter [mithilfe der Aktivität ThrowActivity](http://go.microsoft.com/fwlink?LinkID=65087).|
|**System.Workflow.Activities.TransactionScopeActivity**|Stellt ein Framework für Transaktionen und Ausnahmebehandlung bereit. Weitere Informationen finden Sie unter [verwenden der TransactionScopeActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65088).|
|<xref:System.Workflow.Activities.WebServiceFaultActivity>|Unterstützt die Erstellung des Auftretens eines Webdienstfehlers. Weitere Informationen finden Sie unter [mithilfe der Aktivität "WebServiceFaultActivity"](http://go.microsoft.com/fwlink?LinkID=65089).|
|<xref:System.Workflow.Activities.WebServiceInputActivity>|Empfängt Daten von einem Webdienst. Weitere Informationen finden Sie unter [mithilfe der Aktivität WebServiceInputActivity](http://go.microsoft.com/fwlink?LinkID=65090).|
|<xref:System.Workflow.Activities.WebServiceOutputActivity>|Antwortet auf eine an einen Workflow ausgegebene Webdienstanforderung. Weitere Informationen finden Sie unter [mithilfe der Aktivität "WebServiceOutputActivity"](http://go.microsoft.com/fwlink?LinkID=65092).|
|<xref:System.Workflow.Activities.WhileActivity>|Unterstützt das Durchlaufen Ihres Workflows, bis eine Bedingung erfüllt ist. Weitere Informationen finden Sie unter [mithilfe der Aktivität WhileActivity](http://go.microsoft.com/fwlink?LinkID=65091).|

Weitere Informationen zum Erstellen von benutzerdefinierter Aktivitäten finden Sie unter [Entwickeln von benutzerdefinierten Aktivitäten](http://go.microsoft.com/fwlink?LinkID=65023) und [Aktivitätsdesigners der Vorgängerversion mit](../workflow-designer/using-the-legacy-activity-designer.md).

## <a name="see-also"></a>Siehe auch

- [Windows Workflow Foundation-Aktivitäten](http://go.microsoft.com/fwlink?LinkID=65005)
- [Entwickeln von Workflows](http://go.microsoft.com/fwlink?LinkID=65010)
- [Entwickeln von Workflowaktivitäten](http://go.microsoft.com/fwlink?LinkID=65023)