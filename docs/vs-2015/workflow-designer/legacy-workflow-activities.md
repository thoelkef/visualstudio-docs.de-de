---
title: Legacyworkflowaktivitäten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- workflows, activities
- activities
- workflow activities
ms.assetid: 4af7a06b-1e82-43c8-aec8-0dc5fb63d08a
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 6ff21a431e380a281ce1261215367b89c4ecf1a3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49205400"
---
# <a name="legacy-workflow-activities"></a>Legacyworkflowaktivitäten
[!INCLUDE[wf](../includes/wf-md.md)] enthält einen Standardsatz von Aktivitäten, die Funktionen für Ablaufsteuerung, Bedingungen, Ereignisbehandlung, Zustandsverwaltung und Kommunikation mit Anwendungen und Diensten bereitstellen. Beim Entwurf von Workflows können Sie die vom System bereitgestellten Aktivitäten verwenden, die von [!INCLUDE[wfd1](../includes/wfd1-md.md)] bereitgestellt werden, oder eigene benutzerdefinierte Aktivitäten erstellen.  
  
 In der folgenden Tabelle ist der vordefinierte Aktivitätssatz des [!INCLUDE[wf2](../includes/wf2-md.md)]-Framework aufgeführt. Viele, aber nicht alle dieser Aktivitäten werden von den Aktivitätsdesignern, die aus zugegriffen werden können dargestellt die **Toolbox** von der [!INCLUDE[wfd2](../includes/wfd2-md.md)]. Um eine Aktivität zu erstellen, ziehen Sie ihren Designer aus der **Toolbox** und legen Sie sie auf der Entwurfsoberfläche angezeigt.  
  
|Aktivität|Beschreibung|  
|--------------|-----------------|  
|[CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65025)|Verwendung der **HandleExternalEventActivity** -Aktivität für Eingabe- und ausgabekommunikation mit einem lokalen Dienst. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Verwenden der CallExternalMethodActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65060).|  
|[CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050)|Wird zur Speicherung der Bereinigungslogik für eine zusammengesetzte Aktivität verwendet, die abgebrochen wurde, bevor alle untergeordneten Elemente der zusammengesetzten Aktivität ausgeführt werden konnten. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Verwenden der CancellationHandlerActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65061).|  
|[CodeActivity](http://go.microsoft.com/fwlink?LinkID=65026)|Ermöglicht das Hinzufügen von Visual Basic- oder C#-Code zu Ihrem Workflow. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Verwenden der CodeActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65062).|  
|[CompensatableSequenceActivity](http://go.microsoft.com/fwlink?LinkID=65027)|Eine kompensierbare Version der [SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020). [!INCLUDE[crdefault](../includes/crdefault-md.md)][Verwenden der CompensatableSequenceActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65002).|  
|[CompensatableTransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65051)|Eine kompensierbare Version der **TransactionScopeActivity**. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Verwenden der CompensatableTransactionScopeActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65063).|  
|[CompensateActivity](http://go.microsoft.com/fwlink?LinkID=65052)|Hiermit können Sie den Code aufrufen oder Vorgänge kompensieren, die zum Zeitpunkt des Auftretens des Fehlers bereits vom Workflow ausgeführt wurden. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Verwenden der CompensateActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65064).|  
|[CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65053)|Ein Wrapper für eine oder mehrere Aktivitäten, die eine abgeschlossene TransactionScopeActivity-Aktivität kompensieren [!INCLUDE[crdefault](../includes/crdefault-md.md)] [verwenden der CompensationHandlerActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65065).|  
|[ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)|Führt untergeordnete Aktivitäten auf Grundlage einer Bedingung, die für gilt die [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017) Aktivität selbst und basierend auf Bedingungen, die separat für jedes untergeordnete Element gelten. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Der ConditionedActivityGroup-Aktivität mit](http://go.microsoft.com/fwlink?LinkID=65066).|  
|[DelayActivity](http://go.microsoft.com/fwlink?LinkID=65028)|Ermöglicht das Erstellen von auf einem Timeoutintervall basierenden Verzögerungen in Ihrem Workflow. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Verwenden der DelayActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65067).|  
|[EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029)|Umschließt eine oder mehrere Aktivitäten, die ausgeführt werden, wenn ein bestimmtes Ereignis eintritt. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Verwenden der EventDrivenActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65068).|  
|[EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018)|Stellt ein Framework für das Zuweisen von Ereignissen zu einer Aktivität bereit. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Verwenden der EventHandlersActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65069).|  
|[EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030)|Führt die wichtigste untergeordnete Aktivität gleichzeitig mit einer [EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018). [!INCLUDE[crdefault](../includes/crdefault-md.md)][Verwenden der EventHandlingScopeActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65070).|  
|[FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65054)|Wird zur Behandlung einer Ausnahme des von Ihnen angegebenen Typs verwendet. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Verwenden der FaultHandlerActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65071).|  
|[FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055)|Stellt eine zusammengesetzte Aktivität, die eine geordnete Liste untergeordneter Aktivitäten vom Typ [FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65054). [!INCLUDE[crdefault](../includes/crdefault-md.md)][Verwenden der FaultHandlersActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65072).|  
|[HandleExternalEventActivity](http://go.microsoft.com/fwlink?LinkID=65031)|Zusammen mit den [CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65025) -Aktivität für Eingabe- und ausgabekommunikation mit einem lokalen Dienst. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Verwenden der HandleExternalEventActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65073).|  
|[IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033)|Testet eine Bedingung für jede Verzweigung und führt Aktivitäten für die erste Verzweigung, die für die die Bedingung gleich **"true"**. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Verwenden der IfElseActivity Aktivität](http://go.microsoft.com/fwlink?LinkID=65074).|  
|[IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)|Stellt einen Branch einer [Aktivität "IfElseActivity"](http://go.microsoft.com/fwlink?LinkID=65033). [!INCLUDE[crdefault](../includes/crdefault-md.md)][Verwenden der IfElseBranchActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65075).|  
|[InvokeWebServiceActivity](http://go.microsoft.com/fwlink?LinkID=65035)|Unterstützt das Aufrufen eines Webdienstes durch Ihren Workflow. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Verwenden der InvokeWebServiceActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65076).|  
|[InvokeWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65036)|Unterstützt das Aufrufen eines anderen Webdienstes durch Ihren Workflow. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Verwenden der InvokeWorkflowActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65077).|  
|[ListenActivity](http://go.microsoft.com/fwlink?LinkID=65037)|Eine zusammengesetzte Aktivität, die nur enthält [EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029) untergeordneten Aktivitäten. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Verwenden der ListenActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65078).|  
|[ParallelActivity](http://go.microsoft.com/fwlink?LinkID=65038)|Bietet eine Möglichkeit zum Planen von zwei oder mehr untergeordnete **SequenceActivity** -aktivitätsverzweigungen für die Verarbeitung zur gleichen Zeit. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Verwenden der ParallelActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65079).|  
|[PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)|Verwendung zur Darstellung einer Auflistung von Regeln. Eine Regel besteht aus Bedingungen und daraus resultierenden Aktionen. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Verwenden der PolicyActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65004).|  
|[ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)|Erstellt mehrere Instanzen einer einzelnen untergeordneten Aktivität. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Verwenden der ReplicatorActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65080).|  
|[SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020)|Bietet eine einfache Möglichkeit zur Verknüpfung mehrerer Aktivitäten für die sequenzielle Ausführung. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Verwenden der SequenceActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65081).|  
|[SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041)|Gibt einen Übergang zu einem neuen Zustand an. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Verwenden der SetStateActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65082).|  
|[StateActivity](http://go.microsoft.com/fwlink?LinkID=65042)|Stellt einen Zustand in einem Zustandsautomatworkflow dar. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Verwenden der StateActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65083).|  
|[StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043)|Verwendet eine [StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) -Aktivität als Container für untergeordnete Aktivitäten, die ausgeführt werden, beim Verlassen der **StateActivity** Aktivität. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Verwenden der StateFinalizationActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65008).|  
|[StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044)|Verwendet eine [StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) -Aktivität als Container für untergeordnete Aktivitäten, die ausgeführt werden, bei der Eingabe der **StateActivity** Aktivität. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Verwenden der StateInitializationActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65006).|  
|[SuspendActivity](http://go.microsoft.com/fwlink?LinkID=65056)|Unterbricht den Vorgang des Workflows, um bei einer besonders zu beachtenden Fehlerbedingung Eingriffe zu ermöglichen. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Verwenden der SuspendActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65084).|  
|[SynchronizationScopeActivity](http://go.microsoft.com/fwlink?LinkID=65057)|Führt enthaltene Aktivitäten in einer synchronisierten Domäne sequenziell aus. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Verwenden der SynchronizationScopeActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65085).|  
|[TerminateActivity](http://go.microsoft.com/fwlink?LinkID=65058)|Unterstützt die sofortige Beendigung der Ausführung Ihres Workflows für den Fall, dass eine Fehlerbedingung vorliegt. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Verwenden der TerminateActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65086).|  
|[ThrowActivity](http://go.microsoft.com/fwlink?LinkID=65059)|Unterstützt die Erfassung von Geschäftsausnahmen, die als Bestandteil der Prozessmetadaten für einen Workflow ausgelöst werden. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Verwenden der ThrowActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65087).|  
|[TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093)|Stellt ein Framework für Transaktionen und Ausnahmebehandlung bereit. Weitere Informationen finden Sie unter [verwenden der TransactionScopeActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65088).|  
|[WebServiceFaultActivity](http://go.microsoft.com/fwlink?LinkID=65046)|Unterstützt die Erstellung des Auftretens eines Webdienstfehlers. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Verwenden der WebServiceFaultActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65089).|  
|[WebServiceInputActivity](http://go.microsoft.com/fwlink?LinkID=65047)|Empfängt Daten von einem Webdienst. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Verwenden der WebServiceInputActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65090).|  
|[WebServiceOutputActivity](http://go.microsoft.com/fwlink?LinkID=65048)|Antwortet auf eine an einen Workflow ausgegebene Webdienstanforderung. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Verwenden der WebServiceOutputActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65092).|  
|[WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)|Unterstützt das Durchlaufen Ihres Workflows, bis eine Bedingung erfüllt ist. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Verwenden der WhileActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65091).|  
  
 [!INCLUDE[crabout](../includes/crabout-md.md)] zum Erstellen benutzerdefinierter Aktivitäten finden Sie unter [Developing Custom Activities](http://go.microsoft.com/fwlink?LinkID=65023) und [Verwenden des Aktivitätsdesigners der Vorgängerversion](../workflow-designer/using-the-legacy-activity-designer.md).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Aktivitätsansichten (Vorgängerversion)](../workflow-designer/activity-views-legacy.md)  
 Beschreibt die verschiedenen Entwurfsansichten von Aktivitäten.  
  
 [Vorgehensweise: Hinzufügen von Aktivitäten zur Toolbox (Vorgängerversion)](../workflow-designer/how-to-add-activities-to-the-toolbox-legacy.md)  
 Veranschaulicht das Hinzufügen von Aktivitäten zur Toolbox.  
  
 [Vorgehensweise: Erstellen einer deklarativen Regelbedingung (Vorgängerversion)](../workflow-designer/how-to-create-a-declarative-rule-condition-legacy.md)  
 Zeigt die Schritte zum Erstellen einer deklarativen Regelbedingung.  
  
 [Vorgehensweise: Erstellen eines PolicyActivity-Regelsatzes (Vorgängerversion)](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md)  
 Zeigt die Schritte zum Erstellen eines PolicyActivity-Regelsatzes.  
  
 [Vorgehensweise: Implementieren eines WCF-Vertragsvorgangs (Vorgängerversion)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)  
 Zeigt die Schritte zum Implementieren eines [!INCLUDE[indigo2](../includes/indigo2-md.md)]-Vertragsvorgang.  
  
 [Vorgehensweise: Aufrufen eines WCF-Vertragsvorgangs (Vorgängerversion](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md))  
 Zeigt die Schritte zum Aufrufen eines [!INCLUDE[indigo2](../includes/indigo2-md.md)]-Vertragsvorgang.  
  
## <a name="see-also"></a>Siehe auch  
 [Windows Workflow Foundation-Aktivitäten](http://go.microsoft.com/fwlink?LinkID=65005)   
 [Entwickeln von Workflows](http://go.microsoft.com/fwlink?LinkID=65010)   
 [Entwickeln von Workflowaktivitäten](http://go.microsoft.com/fwlink?LinkID=65023)