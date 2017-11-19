---
title: "Legacyworkflowaktivitäten | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- workflows, activities
- activities
- workflow activities
ms.assetid: 4af7a06b-1e82-43c8-aec8-0dc5fb63d08a
caps.latest.revision: "8"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8a5c35fb036c1d9a94bd42c5ceabe17ae65e7b7c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="legacy-workflow-activities"></a>Legacyworkflowaktivitäten
[!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] enthält einen Standardsatz von Aktivitäten, die Funktionen für Ablaufsteuerung, Bedingungen, Ereignisbehandlung, Zustandsverwaltung und Kommunikation mit Anwendungen und Diensten bereitstellen. Beim Entwurf von Workflows können Sie die vom System bereitgestellten Aktivitäten verwenden, die von [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] bereitgestellt werden, oder eigene benutzerdefinierte Aktivitäten erstellen.  
  
 In der folgenden Tabelle ist der vordefinierte Aktivitätssatz des [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)]-Framework aufgeführt. Viele, aber nicht alle dieser Aktivitäten werden dargestellte Aktivitäts-Designer aus zugegriffen werden können die **Toolbox** von der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. Um eine Aktivität zu erstellen, ziehen Sie ihren Designer aus der **Toolbox** und legen Sie sie auf der Entwurfsoberfläche angezeigt.  
  
|Aktivität|Beschreibung|  
|--------------|-----------------|  
|[CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65025)|Verwendet die **HandleExternalEventActivity** -Aktivität für Eingabe- und ausgabekommunikation mit einem lokalen Dienst. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der Aktivität CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65060).|  
|[CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050)|Wird zur Speicherung der Bereinigungslogik für eine zusammengesetzte Aktivität verwendet, die abgebrochen wurde, bevor alle untergeordneten Elemente der zusammengesetzten Aktivität ausgeführt werden konnten. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der Aktivität CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65061).|  
|[CodeActivity](http://go.microsoft.com/fwlink?LinkID=65026)|Ermöglicht das Hinzufügen von Visual Basic- oder C#-Code zu Ihrem Workflow. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der CodeActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65062).|  
|[CompensatableSequenceActivity](http://go.microsoft.com/fwlink?LinkID=65027)|Eine kompensierbare Version der [SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020). [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der Aktivität CompensatableSequenceActivity](http://go.microsoft.com/fwlink?LinkID=65002).|  
|[CompensatableTransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65051)|Eine kompensierbare Version der **TransactionScopeActivity**. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der Aktivität CompensatableTransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65063).|  
|["CompensateActivity"](http://go.microsoft.com/fwlink?LinkID=65052)|Hiermit können Sie den Code aufrufen oder Vorgänge kompensieren, die zum Zeitpunkt des Auftretens des Fehlers bereits vom Workflow ausgeführt wurden. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der Aktivität "CompensateActivity"](http://go.microsoft.com/fwlink?LinkID=65064).|  
|[CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65053)|Ein Wrapper für eine oder mehrere Aktivitäten, eine abgeschlossene TransactionScopeActivity-Aktivität [!INCLUDE[crdefault](../test/includes/crdefault_md.md)] [verwenden der CompensationHandlerActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65065).|  
|[ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)|Führt untergeordnete Aktivitäten auf Grundlage einer Bedingung, die für gilt die [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017) Aktivität selbst und basierend auf Bedingungen, die separat für jedes untergeordnete Element gelten. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der Aktivität ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65066).|  
|[DelayActivity](http://go.microsoft.com/fwlink?LinkID=65028)|Ermöglicht das Erstellen von auf einem Timeoutintervall basierenden Verzögerungen in Ihrem Workflow. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der Aktivität DelayActivity](http://go.microsoft.com/fwlink?LinkID=65067).|  
|[EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029)|Umschließt eine oder mehrere Aktivitäten, die ausgeführt werden, wenn ein bestimmtes Ereignis eintritt. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der EventDrivenActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65068).|  
|[EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018)|Stellt ein Framework für das Zuweisen von Ereignissen zu einer Aktivität bereit. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der Aktivität EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65069).|  
|[EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030)|Führt die wichtigste untergeordnete Aktivität gleichzeitig mit einer [EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018). [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der Aktivität EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65070).|  
|[FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65054)|Wird zur Behandlung einer Ausnahme des von Ihnen angegebenen Typs verwendet. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der Aktivität FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65071).|  
|[FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055)|Stellt eine zusammengesetzte Aktivität, die eine geordnete Liste untergeordneter Aktivitäten vom Typ hat [FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65054). [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der Aktivität FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65072).|  
|[HandleExternalEventActivity](http://go.microsoft.com/fwlink?LinkID=65031)|Wird in Verbindung mit der [CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65025) -Aktivität für Eingabe- und ausgabekommunikation mit einem lokalen Dienst. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der Aktivität HandleExternalEventActivity](http://go.microsoft.com/fwlink?LinkID=65073).|  
|[IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033)|Testet eine Bedingung für jede Verzweigung und führt Aktivitäten für die erste Verzweigung, die für die die Bedingung **"true"**. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der Aktivität IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65074).|  
|["IfElseBranchActivity"](http://go.microsoft.com/fwlink?LinkID=65034)|Stellt eine Verzweigung einer [IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033). [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der Aktivität "IfElseBranchActivity"](http://go.microsoft.com/fwlink?LinkID=65075).|  
|[InvokeWebServiceActivity](http://go.microsoft.com/fwlink?LinkID=65035)|Unterstützt das Aufrufen eines Webdienstes durch Ihren Workflow. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der Aktivität InvokeWebServiceActivity](http://go.microsoft.com/fwlink?LinkID=65076).|  
|["InvokeWorkflowActivity"](http://go.microsoft.com/fwlink?LinkID=65036)|Unterstützt das Aufrufen eines anderen Webdienstes durch Ihren Workflow. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der Aktivität "InvokeWorkflowActivity"](http://go.microsoft.com/fwlink?LinkID=65077).|  
|["ListenActivity"](http://go.microsoft.com/fwlink?LinkID=65037)|Eine zusammengesetzte Aktivität, die nur enthält [EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029) untergeordneten Aktivitäten. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der Aktivität "ListenActivity"](http://go.microsoft.com/fwlink?LinkID=65078).|  
|[ParallelActivity](http://go.microsoft.com/fwlink?LinkID=65038)|Bietet eine Möglichkeit, Planung von zwei oder mehr untergeordneten **SequenceActivity** -aktivitätsverzweigungen für die gleichzeitige Verarbeitung. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der Aktivität ParallelActivity](http://go.microsoft.com/fwlink?LinkID=65079).|  
|[PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)|Verwendung zur Darstellung einer Auflistung von Regeln. Eine Regel besteht aus Bedingungen und daraus resultierenden Aktionen. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der PolicyActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65004).|  
|[ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)|Erstellt mehrere Instanzen einer einzelnen untergeordneten Aktivität. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der Aktivität ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65080).|  
|[SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020)|Bietet eine einfache Möglichkeit zur Verknüpfung mehrerer Aktivitäten für die sequenzielle Ausführung. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der Aktivität SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65081).|  
|[SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041)|Gibt einen Übergang zu einem neuen Zustand an. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der SetStateActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65082).|  
|[StateActivity](http://go.microsoft.com/fwlink?LinkID=65042)|Stellt einen Zustand in einem Zustandsautomatworkflow dar. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der StateActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65083).|  
|[StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043)|Verwendet eine [StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) -Aktivität als Container für untergeordnete Aktivitäten, die ausgeführt werden, beim Verlassen der **StateActivity** Aktivität. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der StateFinalizationActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65008).|  
|[StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044)|Verwendet eine [StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) -Aktivität als Container für untergeordnete Aktivitäten, die ausgeführt werden, bei der Eingabe der **StateActivity** Aktivität. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der StateInitializationActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65006).|  
|[SuspendActivity](http://go.microsoft.com/fwlink?LinkID=65056)|Unterbricht den Vorgang des Workflows, um bei einer besonders zu beachtenden Fehlerbedingung Eingriffe zu ermöglichen. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der Aktivität SuspendActivity](http://go.microsoft.com/fwlink?LinkID=65084).|  
|[SynchronizationScopeActivity](http://go.microsoft.com/fwlink?LinkID=65057)|Führt enthaltene Aktivitäten in einer synchronisierten Domäne sequenziell aus. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der Aktivität SynchronizationScopeActivity](http://go.microsoft.com/fwlink?LinkID=65085).|  
|[TerminateActivity](http://go.microsoft.com/fwlink?LinkID=65058)|Unterstützt die sofortige Beendigung der Ausführung Ihres Workflows für den Fall, dass eine Fehlerbedingung vorliegt. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der Aktivität TerminateActivity](http://go.microsoft.com/fwlink?LinkID=65086).|  
|[ThrowActivity](http://go.microsoft.com/fwlink?LinkID=65059)|Unterstützt die Erfassung von Geschäftsausnahmen, die als Bestandteil der Prozessmetadaten für einen Workflow ausgelöst werden. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der Aktivität ThrowActivity](http://go.microsoft.com/fwlink?LinkID=65087).|  
|[TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093)|Stellt ein Framework für Transaktionen und Ausnahmebehandlung bereit. Weitere Informationen finden Sie unter [verwenden der TransactionScopeActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65088).|  
|["WebServiceFaultActivity"](http://go.microsoft.com/fwlink?LinkID=65046)|Unterstützt die Erstellung des Auftretens eines Webdienstfehlers. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der Aktivität "WebServiceFaultActivity"](http://go.microsoft.com/fwlink?LinkID=65089).|  
|[WebServiceInputActivity](http://go.microsoft.com/fwlink?LinkID=65047)|Empfängt Daten von einem Webdienst. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der Aktivität WebServiceInputActivity](http://go.microsoft.com/fwlink?LinkID=65090).|  
|["WebServiceOutputActivity"](http://go.microsoft.com/fwlink?LinkID=65048)|Antwortet auf eine an einen Workflow ausgegebene Webdienstanforderung. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der Aktivität "WebServiceOutputActivity"](http://go.microsoft.com/fwlink?LinkID=65092).|  
|[WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)|Unterstützt das Durchlaufen Ihres Workflows, bis eine Bedingung erfüllt ist. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der Aktivität WhileActivity](http://go.microsoft.com/fwlink?LinkID=65091).|  
  
 [!INCLUDE[crabout](../test/includes/crabout_md.md)]zum Erstellen von benutzerdefinierten Aktivitäten finden Sie unter [Entwickeln von benutzerdefinierten Aktivitäten](http://go.microsoft.com/fwlink?LinkID=65023) und [Aktivitätsdesigners der Vorgängerversion mit](../workflow-designer/using-the-legacy-activity-designer.md).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Aktivitätsansichten (Vorgängerversion)](../workflow-designer/activity-views-legacy.md)  
 Beschreibt die verschiedenen Entwurfsansichten von Aktivitäten.  
  
 [Vorgehensweise: Hinzufügen von Aktivitäten zur Toolbox (Vorgängerversion)](../workflow-designer/how-to-add-activities-to-the-toolbox-legacy.md)  
 Veranschaulicht das Hinzufügen von Aktivitäten zur Toolbox.  
  
 [Vorgehensweise: Erstellen einer deklarativen Regelbedingung (Vorgängerversion)](../workflow-designer/how-to-create-a-declarative-rule-condition-legacy.md)  
 Zeigt die Schritte zum Erstellen einer deklarativen Regelbedingung.  
  
 [Vorgehensweise: Erstellen eines PolicyActivity-Regelsatzes (Vorgängerversion)](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md)  
 Zeigt die Schritte zum Erstellen eines PolicyActivity-Regelsatzes.  
  
 [Vorgehensweise: implementieren ein WCF-Vertragsvorgangs (Vorgängerversion)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)  
 Zeigt die Schritte zum Implementieren eines [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)]-Vertragsvorgang.  
  
 [Vorgehensweise: Aufrufen ein WCF-Vertragsvorgangs (Vorgängerversion)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)  
 Zeigt die Schritte zum Aufrufen eines [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)]-Vertragsvorgang.  
  
## <a name="see-also"></a>Siehe auch  
 [Windows Workflow Foundation-Aktivitäten](http://go.microsoft.com/fwlink?LinkID=65005)   
 [Entwickeln von Workflows](http://go.microsoft.com/fwlink?LinkID=65010)   
 [Entwickeln von Workflowaktivitäten](http://go.microsoft.com/fwlink?LinkID=65023)