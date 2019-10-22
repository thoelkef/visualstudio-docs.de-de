---
title: Legacy Workflow Aktivitäten | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflows, activities
- activities
- workflow activities
ms.assetid: 4af7a06b-1e82-43c8-aec8-0dc5fb63d08a
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f4f1110424aefc1771c0dc7600fb9996bff0e892
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658937"
---
# <a name="legacy-workflow-activities"></a>Legacyworkflowaktivitäten
[!INCLUDE[wf](../includes/wf-md.md)] enthält einen Standardsatz von Aktivitäten, die Funktionen für Ablaufsteuerung, Bedingungen, Ereignisbehandlung, Zustandsverwaltung und Kommunikation mit Anwendungen und Diensten bereitstellen. Beim Entwurf von Workflows können Sie die vom System bereitgestellten Aktivitäten verwenden, die von [!INCLUDE[wfd1](../includes/wfd1-md.md)] bereitgestellt werden, oder eigene benutzerdefinierte Aktivitäten erstellen.

 In der folgenden Tabelle ist der vordefinierte Aktivitätssatz des [!INCLUDE[wf2](../includes/wf2-md.md)]-Framework aufgeführt. Viele, aber nicht alle dieser Aktivitäten werden von Aktivitäts Designern dargestellt, auf die über die **Toolbox** der [!INCLUDE[wfd2](../includes/wfd2-md.md)] zugegriffen werden kann. Um eine Aktivität zu erstellen, ziehen Sie Ihren Designer aus der **Toolbox** , und legen Sie ihn auf der Entwurfs Oberfläche ab.

|Aktivität|Beschreibung|
|--------------|-----------------|
|[CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65025)|Wird **für die Eingabe** -und Ausgabe Kommunikation mit einem lokalen Dienst für die Eingabe-und Ausgabe Kommunikation verwendet. [!INCLUDE[crdefault](../includes/crdefault-md.md)][mithilfe der CallExternalMethodActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65060).|
|[CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050)|Wird zur Speicherung der Bereinigungslogik für eine zusammengesetzte Aktivität verwendet, die abgebrochen wurde, bevor alle untergeordneten Elemente der zusammengesetzten Aktivität ausgeführt werden konnten. [!INCLUDE[crdefault](../includes/crdefault-md.md)][mithilfe der CancellationHandlerActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65061).|
|[CodeActivity](http://go.microsoft.com/fwlink?LinkID=65026)|Ermöglicht das Hinzufügen von Visual Basic- oder C#-Code zu Ihrem Workflow. [!INCLUDE[crdefault](../includes/crdefault-md.md)][mithilfe der CodeActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65062).|
|[CompensatableSequenceActivity](http://go.microsoft.com/fwlink?LinkID=65027)|Eine kompensierbare Version von [SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020). [!INCLUDE[crdefault](../includes/crdefault-md.md)][mithilfe der CompensatableSequenceActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65002).|
|[CompensatableTransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65051)|Eine kompensierbare Version von **transaktionscopeactivity**. [!INCLUDE[crdefault](../includes/crdefault-md.md)][mithilfe der compensatabletransaktionscopeactivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65063).|
|[CompensateActivity](http://go.microsoft.com/fwlink?LinkID=65052)|Hiermit können Sie den Code aufrufen oder Vorgänge kompensieren, die zum Zeitpunkt des Auftretens des Fehlers bereits vom Workflow ausgeführt wurden. [!INCLUDE[crdefault](../includes/crdefault-md.md)][mithilfe der CompensateActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65064).|
|[CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65053)|Ein Wrapper für eine oder mehrere Aktivitäten, die eine Kompensierung für eine abgeschlossene transaktionscopeactivity-Aktivität [!INCLUDE[crdefault](../includes/crdefault-md.md)][mithilfe der CompensationHandlerActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65065)ausführen.|
|[ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)|Führt untergeordnete Aktivitäten auf der Grundlage einer Bedingung aus, die für die [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017) -Aktivität selbst gilt, sowie auf Grundlage von Bedingungen, die separat für jedes untergeordnete Element gelten. [!INCLUDE[crdefault](../includes/crdefault-md.md)][mithilfe der ConditionedActivityGroup-Aktivität](http://go.microsoft.com/fwlink?LinkID=65066).|
|[DelayActivity](http://go.microsoft.com/fwlink?LinkID=65028)|Ermöglicht das Erstellen von auf einem Timeoutintervall basierenden Verzögerungen in Ihrem Workflow. [!INCLUDE[crdefault](../includes/crdefault-md.md)][mithilfe der Delta Activity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65067).|
|[EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029)|Umschließt eine oder mehrere Aktivitäten, die ausgeführt werden, wenn ein bestimmtes Ereignis eintritt. [!INCLUDE[crdefault](../includes/crdefault-md.md)][mithilfe der EventDrivenActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65068).|
|[EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018)|Stellt ein Framework für das Zuweisen von Ereignissen zu einer Aktivität bereit. [!INCLUDE[crdefault](../includes/crdefault-md.md)][mithilfe der EventHandlersActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65069).|
|[EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030)|Führt die untergeordnete Hauptaktivität gleichzeitig mit einer [EventHandlersActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65018)aus. [!INCLUDE[crdefault](../includes/crdefault-md.md)][mithilfe der EventHandlingScopeActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65070).|
|[FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65054)|Wird zur Behandlung einer Ausnahme des von Ihnen angegebenen Typs verwendet. [!INCLUDE[crdefault](../includes/crdefault-md.md)][mithilfe der FaultHandlerActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65071).|
|[FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055)|Stellt eine zusammengesetzte Aktivität dar, die über eine geordnete Liste untergeordneter Aktivitäten vom Typ [FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65054)verfügt. [!INCLUDE[crdefault](../includes/crdefault-md.md)][mithilfe der FaultHandlersActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65072).|
|[HandleExternalEventActivity](http://go.microsoft.com/fwlink?LinkID=65031)|Wird in Verbindung mit der [CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65025) -Aktivität für die Eingabe-und Ausgabe Kommunikation mit einem lokalen Dienst verwendet. [!INCLUDE[crdefault](../includes/crdefault-md.md)][mithilfe der "Lenker externaleventactivity](http://go.microsoft.com/fwlink?LinkID=65073)"-Aktivität.|
|[IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033)|Testet eine Bedingung für jede Verzweigung und führt Aktivitäten für die erste Verzweigung aus, für die die Bedingung **true**ist. [!INCLUDE[crdefault](../includes/crdefault-md.md)][mithilfe der ifelsactivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65074).|
|[IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)|Stellt eine Verzweigung einer [IFeL* Activity](http://go.microsoft.com/fwlink?LinkID=65033)dar. [!INCLUDE[crdefault](../includes/crdefault-md.md)][mithilfe der ifelsbranchactivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65075).|
|[InvokeWebServiceActivity](http://go.microsoft.com/fwlink?LinkID=65035)|Unterstützt das Aufrufen eines Webdienstes durch Ihren Workflow. [!INCLUDE[crdefault](../includes/crdefault-md.md)][mithilfe der InvokeWebServiceActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65076).|
|[InvokeWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65036)|Unterstützt das Aufrufen eines anderen Webdienstes durch Ihren Workflow. [!INCLUDE[crdefault](../includes/crdefault-md.md)][mithilfe der InvokeWorkflowActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65077).|
|[ListenActivity](http://go.microsoft.com/fwlink?LinkID=65037)|Eine zusammengesetzte Aktivität, die nur untergeordnete [EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029) -Aktivitäten enthält. [!INCLUDE[crdefault](../includes/crdefault-md.md)][mithilfe der ListenActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65078).|
|[ParallelActivity](http://go.microsoft.com/fwlink?LinkID=65038)|Bietet eine Möglichkeit, zwei oder mehr untergeordnete **SequenceActivity** -Aktivitäts branches zur gleichen Zeit zu verarbeiten. [!INCLUDE[crdefault](../includes/crdefault-md.md)][mithilfe der ParallelActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65079).|
|[PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)|Verwendung zur Darstellung einer Auflistung von Regeln. Eine Regel besteht aus Bedingungen und daraus resultierenden Aktionen. [!INCLUDE[crdefault](../includes/crdefault-md.md)][mithilfe der PolicyActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65004).|
|[ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)|Erstellt mehrere Instanzen einer einzelnen untergeordneten Aktivität. [!INCLUDE[crdefault](../includes/crdefault-md.md)][mithilfe der Repli-Activity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65080).|
|[SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020)|Bietet eine einfache Möglichkeit zur Verknüpfung mehrerer Aktivitäten für die sequenzielle Ausführung. [!INCLUDE[crdefault](../includes/crdefault-md.md)][mithilfe der SequenceActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65081).|
|[SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041)|Gibt einen Übergang zu einem neuen Zustand an. [!INCLUDE[crdefault](../includes/crdefault-md.md)][mithilfe der SetStateActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65082).|
|[StateActivity](http://go.microsoft.com/fwlink?LinkID=65042)|Stellt einen Zustand in einem Zustandsautomatworkflow dar. [!INCLUDE[crdefault](../includes/crdefault-md.md)][mithilfe der StateActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65083).|
|[StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043)|Wird in einer [StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) -Aktivität als Container für untergeordnete Aktivitäten verwendet, die ausgeführt werden, wenn die **StateActivity** -Aktivität verlässt. [!INCLUDE[crdefault](../includes/crdefault-md.md)][mithilfe der StateFinalizationActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65008).|
|[StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044)|Wird in einer [StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) -Aktivität als Container für untergeordnete Aktivitäten verwendet, die bei der Eingabe der **StateActivity** -Aktivität ausgeführt werden. [!INCLUDE[crdefault](../includes/crdefault-md.md)][mithilfe der Aktivität "Status-Aktivität](http://go.microsoft.com/fwlink?LinkID=65006)".|
|[SuspendActivity](http://go.microsoft.com/fwlink?LinkID=65056)|Unterbricht den Vorgang des Workflows, um bei einer besonders zu beachtenden Fehlerbedingung Eingriffe zu ermöglichen. [!INCLUDE[crdefault](../includes/crdefault-md.md)][mithilfe der SuspendActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65084).|
|[SynchronizationScopeActivity](http://go.microsoft.com/fwlink?LinkID=65057)|Führt enthaltene Aktivitäten in einer synchronisierten Domäne sequenziell aus. [!INCLUDE[crdefault](../includes/crdefault-md.md)][mithilfe der SynchronizationScopeActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65085).|
|[TerminateActivity](http://go.microsoft.com/fwlink?LinkID=65058)|Unterstützt die sofortige Beendigung der Ausführung Ihres Workflows für den Fall, dass eine Fehlerbedingung vorliegt. [!INCLUDE[crdefault](../includes/crdefault-md.md)][mithilfe der TerminateActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65086).|
|[ThrowActivity](http://go.microsoft.com/fwlink?LinkID=65059)|Unterstützt die Erfassung von Geschäftsausnahmen, die als Bestandteil der Prozessmetadaten für einen Workflow ausgelöst werden. [!INCLUDE[crdefault](../includes/crdefault-md.md)][mithilfe der ThrowActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65087).|
|[TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093)|Stellt ein Framework für Transaktionen und Ausnahmebehandlung bereit. Weitere Informationen finden Sie unter [Verwenden der transaktionscopeactivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65088).|
|[WebServiceFaultActivity](http://go.microsoft.com/fwlink?LinkID=65046)|Unterstützt die Erstellung des Auftretens eines Webdienstfehlers. [!INCLUDE[crdefault](../includes/crdefault-md.md)][mithilfe der WebServiceFaultActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65089).|
|[WebServiceInputActivity](http://go.microsoft.com/fwlink?LinkID=65047)|Empfängt Daten von einem Webdienst. [!INCLUDE[crdefault](../includes/crdefault-md.md)][mithilfe der webservicinput Activity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65090).|
|[WebServiceOutputActivity](http://go.microsoft.com/fwlink?LinkID=65048)|Antwortet auf eine an einen Workflow ausgegebene Webdienstanforderung. [!INCLUDE[crdefault](../includes/crdefault-md.md)][mithilfe der WebServiceOutputActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65092).|
|[WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)|Unterstützt das Durchlaufen Ihres Workflows, bis eine Bedingung erfüllt ist. [!INCLUDE[crdefault](../includes/crdefault-md.md)][mithilfe der WhileActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65091).|

 [!INCLUDE[crabout](../includes/crabout-md.md)], wie Sie benutzerdefinierte Aktivitäten erstellen, finden Sie unter [entwickeln von benutzerdefinierten Aktivitäten](http://go.microsoft.com/fwlink?LinkID=65023) und [Verwenden des Legacy-Aktivitäts Designers](../workflow-designer/using-the-legacy-activity-designer.md).

## <a name="in-this-section"></a>In diesem Abschnitt
 [Aktivitäts Ansichten (Legacy)](../workflow-designer/activity-views-legacy.md) Beschreibt die verschiedenen Entwurfs Ansichten von Aktivitäten.

 Gewusst [wie: Hinzufügen von Aktivitäten zur Toolbox (Legacy)](../workflow-designer/how-to-add-activities-to-the-toolbox-legacy.md) Zeigt, wie Aktivitäten zur Toolbox hinzugefügt werden.

 Vorgehens [Weise: Erstellen einer deklarativen Regel Bedingung (Legacy)](../workflow-designer/how-to-create-a-declarative-rule-condition-legacy.md) Zeigt die Schritte zum Erstellen einer deklarativen Regel Bedingung an.

 Vorgehens [Weise: Erstellen eines PolicyActivity-Regelsatzes (Legacy)](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md) Zeigt die Schritte zum Erstellen eines PolicyActivity-Regelsatzes an.

 Vorgehens [Weise: Implementieren eines WCF-Vertrags Vorgangs (Legacy)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) Zeigt die Schritte zum Implementieren eines [!INCLUDE[indigo2](../includes/indigo2-md.md)] Vertrags Vorgangs an.

 Vorgehens [Weise: Aufrufen eines WCF-Vertrags Vorgangs (Legacy)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md) Zeigt die Schritte zum Aufrufen eines [!INCLUDE[indigo2](../includes/indigo2-md.md)] Vertrags Vorgangs an.

## <a name="see-also"></a>Siehe auch
 [Windows Workflow Foundation Aktivitäten](http://go.microsoft.com/fwlink?LinkID=65005) [entwickeln von Workflows](http://go.microsoft.com/fwlink?LinkID=65010) entwickeln von [Workflow Aktivitäten](http://go.microsoft.com/fwlink?LinkID=65023)