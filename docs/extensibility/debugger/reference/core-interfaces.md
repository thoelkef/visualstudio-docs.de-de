---
title: Kernschnittstellen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], core interfaces
ms.assetid: 666b9116-8550-4bdd-bc15-55fc57de87df
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8bf01ffceb122ad99d5ecca8fabfaa102a8fc505
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737582"
---
# <a name="core-interfaces"></a>Wichtige Schnittstellen
Die folgenden Schnittstellen sind die Kernschnittstellen zum Erweitern [!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)]des Debuggers mithilfe der .

## <a name="discussion"></a>Diskussion
 Diese Schnittstellen werden in erster Linie zum Erstellen des Debugmoduls (DE) verwendet. Sie sind hier nach Kategorien geordnet:

- [Haltepunkte](#Breakpoints)

- [Kontexte](#Contexts)

- [Core Server](#CoreServer)

- [Debug-Engines](#DebugEngines)

- [Dokumente](#Documents)

- [Ereignisse](#Events)

- [Ausdrücke](#Expressions)

- [Memory](#Memory)

- [Module](#Modules)

- [Ports](#Ports)

- [Prozesse](#Processes)

- [Programs](#Programs)

- [Eigenschaften](#Properties)

- [Stapelrahmen](#StackFrames)

- [Threads](#Threads)

- [Typ Visualizer](#TypeVisualizers)

  Die Entitäten, die die Schnittstellen implementieren können, sind:

- Debug-Engine (DE)

- Hafenlieferant (PS)

- Ausdrucksauswertung (EE)

- Visual Studio (VS)

## <a name="breakpoints"></a><a name="Breakpoints"></a>Haltepunkte
 Diese Schnittstellen beziehen sich auf die Implementierung und Nachverfolgung von Haltepunkten.

|Schnittstelle|Implementiert von|BESCHREIBUNG|
|---------------|--------------------|-----------------|
|[IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)|DE|Stellt einen Haltepunkt dar, der an einen Speicherspeicherort gebunden ist.|
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|Wird von der DE gesendet, wenn ein Haltepunkt an einen Speicherspeicherort gebunden ist.|
|[IDebugBreakpointChecksumRequest2](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2.md)|VS|Stellt eine Dokumentprüfsumme für eine Haltepunktanforderung dar.|
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|Wird von der DE gesendet, wenn ein Haltepunkt nicht an einen Speicherspeicherort gebunden werden kann.|
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|Gesendet von der DE, wenn ein Haltepunkt erreicht ist.|
|[IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)|VS|Stellt eine Anforderung für einen Haltepunkt dar. beim Erstellen eines ausstehenden Haltepunkts verwendet werden.|
|[IDebugBreakpointRequest3](../../../extensibility/debugger/reference/idebugbreakpointrequest3.md)|VS|Stellt eine Anforderung für einen Haltepunkt dar. beim Erstellen eines ausstehenden Haltepunkts verwendet werden.|
|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|DE|Stellt die Informationen dar, die zum Binden eines Haltepunkts verwendet werden.|
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|Wird von der DE gesendet, wenn ein Haltepunkt von einem Speicherspeicherort ungebunden ist.|
|[IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)|DE|Stellt einen ungültigen Haltepunkt `IDebugBreakpointErrorEvent2`dar (zurückgegeben von ).|
|[IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)|DE|Stellt die Auflösungsinformationen zu einem ungültigen Haltepunkt dar.|
|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|DE|Stellt eine Position in einer Funktion dar, in der ein Haltepunkt festgelegt ist.|
|[IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)|DE|Stellt einen Haltepunkt dar, der gebunden werden soll; beim Erstellen eines gebundenen Haltepunkts verwendet werden.|
|[IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)|DE|Stellt eine Enumeration über einen Satz gebundener Haltepunkte dar.|
|[IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)|DE|Stellt eine Enumeration über eine Reihe von Haltepunkten dar, die nicht an einen Speicherspeicherort gebunden werden konnten.|

## <a name="contexts"></a><a name="Contexts"></a>Kontexten
 Diese Schnittstellen stellen verschiedene Arten von Kontexten innerhalb des zu debuggenden Programms dar.

|Schnittstelle|Implementiert von|BESCHREIBUNG|
|---------------|--------------------|-----------------|
|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|DE|Stellt die Startposition einer Codeanweisung dar.|
|[IDebugCodeContext3](../../../extensibility/debugger/reference/idebugcodecontext3.md)|DE|Erweitert die [IDebugCodeContext2-Schnittstelle,](../../../extensibility/debugger/reference/idebugcodecontext2.md) um das Abrufen von Modul- und Prozessschnittstellen zu ermöglichen.|
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS, DE|Stellt eine Position in einem Dokument dar.|
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|Stellt den Kontext dar, in dem ein Ausdruck ausgewertet werden soll.|
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|Stellt den Startspeicherort im Speicher einer Auflistung von Bytes dar.|
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|Stellt einen Stapelrahmenkontextkontext an einem Haltepunkt oder einer Ausnahme dar.|
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|Stellt einen Stapelrahmenkontextkontext an einem Haltepunkt oder einer Ausnahme dar.|
|[IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)|DE|Stellt eine Enumeration über eine Gruppe von Codekontexten dar.|

## <a name="core-server"></a><a name="CoreServer"></a>Core Server
 Diese Schnittstellen stellen den Computer dar, auf dem ein Programm gedebuggég wird. Diese werden [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] von implementiert, können aber von Debug-Engines aufgerufen werden.

|Schnittstelle|Implementiert von|BESCHREIBUNG|
|---------------|--------------------|-----------------|
|[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)|VS|Bietet Zugriff auf Ports und Portlieferanten sowie Informationen über den Computer.|
|[IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)|VS|Stellt einen [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) dar, der Remote-Debugging unterstützt.|

## <a name="debug-engines"></a><a name="DebugEngines"></a>Debug-Engines
 Diese Schnittstellen stellen Debugmodule und die zugehörigen Ereignisse dar.

|Schnittstelle|Implementiert von|BESCHREIBUNG|
|---------------|--------------------|-----------------|
|[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)|DE|Stellt ein benutzerdefiniertes Debugmodul dar.|
|[IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)|DE|Stellt ein benutzerdefiniertes Debugmodul dar, das das Laden von Symbolen, JustMyCode und Ausnahmen unterstützt.|
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|Wird von jeder neuen Instanz der DE gesendet, um anzugeben, dass sie bereit ist, Debugaufgaben zu verarbeiten.|
|[IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)|DE|Stellt ein benutzerdefiniertes Debugmodul dar, das das Starten von Programmen unterstützt.|
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE, PS|Stellt einen Programmknoten dar, der mehrere Debugmodule verarbeitet.|
|[IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)|DE|Bietet eine Möglichkeit für das SDM, eine Schnittstelle zum Debugmodul von einem Thread- oder Programm- oder Stapelrahmen zu erhalten.|

## <a name="documents"></a><a name="Documents"></a>Dokumente
 Diese Schnittstellen stellen Dokumente (Quelldateien) und die zugehörigen Elemente dar.

|Schnittstelle|Implementiert von|BESCHREIBUNG|
|---------------|--------------------|-----------------|
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|Wird von der DE gesendet, um ein zu öffnendes Dokument anzufordern.|
|[IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)|DE|Stellt einen Strom von zerlegten Anweisungen aus einem Dokument dar.|
|[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)|VS, DE|Stellt ein dokument dar, das von der DE bereitgestellt wird und einen Namen und eine Klassen-ID (CLSID) angibt.|
|[IDebugDocumentChecksum2](../../../extensibility/debugger/reference/idebugdocumentchecksum2.md)|DE, EE|Stellt eine Prüfsumme für ein Debugdokument dar und ermöglicht das Übergeben der Prüfsumme zwischen Komponenten.|
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS, DE|Stellt einen Dokumentkontext dar, eine Position innerhalb eines Dokuments, die einer bestimmten Anweisung und einem bestimmten Codekontext entspricht.|
|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|VS, DE|Stellt eine allgemeine Position innerhalb eines Dokuments dar.|
|[IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)|VS|Stellt eine Position in einer Quelldatei als Zeichenoffset dar.|
|[IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)|VS, DE|Stellt ein Textdokument dar, das von der DE (abgeleitet von [IDebugDocument2 )](../../../extensibility/debugger/reference/idebugdocument2.md)bereitgestellt wird und den tatsächlichen Text liefert.|
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|Wird von der DE gesendet, um Änderungen an einer Quelldatei anzugeben, die sich im Arbeitsspeicher befindet.|

## <a name="events"></a><a name="Events"></a>Ereignisse
 Diese Schnittstellen stellen alle Ereignisse dar, die zwischen der DE und dem Sitzungsdebug-Manager (SDM) gesendet werden.

| Schnittstelle | Implementiert von | BESCHREIBUNG |
| - |----------------| - |
| [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md) | DE | Wird von der DE gesendet, um ein zu öffnendes Dokument anzufordern. |
| [IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md) | DE | Das Debugmodul (DE) sendet diese Schnittstelle an den Sitzungsdebug-Manager (SDM), um die Statusleistenmeldung während des Symbolladens festzulegen. |
| [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) | DE | Wird von der DE gesendet, wenn eine Unterbrechung des Programms abgeschlossen wurde. |
| [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) | DE | Wird von der DE gesendet, wenn ein Haltepunkt gebunden ist. |
| [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) | DE | Wird von der DE gesendet, wenn ein Haltepunkt nicht gebunden werden kann. |
| [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) | DE | Gesendet von der DE, wenn ein Haltepunkt erreicht ist. |
| [IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md) | DE | Wird von der DE gesendet, wenn ein Haltepunkt ungebunden ist. |
| [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md) | DE | Gesendet von der DE, um zu bestimmen, ob es an einem bestimmten Ort anhalten soll. |
| [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md) | DE | Wird von der DE gesendet, um Änderungen an einer Quelldatei anzugeben, die sich im Arbeitsspeicher befindet. |
| [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) | DE | Wird von jeder neuen Instanz der DE gesendet, um anzugeben, dass sie bereit ist, Debugaufgaben zu verarbeiten. |
| [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) | DE | Wird von der DE gesendet, um anzugeben, dass das zu debuggende Programm bereit ist, die erste Anweisung auszuführen. |
| [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) | DE | Eine Schnittstelle, die von anderen Ereignisschnittstellen verwendet wird, die möglicherweise einen Fehler zurückgeben, um lesbare Fehlermeldungen bereitzustellen. |
| [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) | DE, PS | Basisschnittstelle, von der alle anderen Ereignisschnittstellen abgeleitet werden. |
| [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) | VS | Stellt eine vom SDM implementierte Schnittstelle dar, an die Ereignisse (ausgedrückt als Objekte, die eine bestimmte Ereignisschnittstelle implementieren) gesendet werden. |
| [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) | DE | Wird von der DE gesendet, wenn in dem zu debuggenden Programm eine Ausnahme aufgetreten ist. |
| [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) | DE | Wird von der DE gesendet, wenn eine asynchrone Ausdrucksauswertung abgeschlossen ist. |
| IDebugFindSymbolEvent2 | | VERALTET. NICHT VERWENDEN. |
| [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) | DE | Wird von der DE gesendet, wenn die Verarbeitung für eine abgefangene Ausnahme abgeschlossen wurde. |
| [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) | DE | Wird von der DE gesendet, wenn das Laden eines Programms abgeschlossen wurde. |
| [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md) | DE | Wird von der DE gesendet, damit die IDE dem Benutzer eine Informationsmeldung anzeigt. |
| [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md) | DE | Wird von der DE gesendet, wenn ein Modul geladen oder entladen wird. |
| [IDebugNoSymbolsEvent2](../../../extensibility/debugger/reference/idebugnosymbolsevent2.md) | DE | Signalisiert [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] die Debugger-Benutzeroberfläche, um den Benutzer zu warnen, dass Symbole für die gestartete ausführbare Datei nicht gefunden werden konnten. |
| [IDebugOutputStringEvent2](../../../extensibility/debugger/reference/idebugoutputstringevent2.md) | DE | Wird von der DE gesendet, damit die IDE eine beliebige Zeichenfolge anzeigt. |
| [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) | VS, DE | Wird von einem Port gesendet, um Portereignisse an jeden Listener zu kommunizieren. |
| [IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md) | DE, PS | Wird von der DE oder dem Port gesendet, wenn ein Prozess erstellt wurde. |
| [IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) | DE, PS | Wird von der DE oder dem Port gesendet, wenn ein Prozess zerstört wurde. |
| [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) | DE, PS | Wird von der DE oder dem Port gesendet, wenn ein Programm erstellt wurde. |
| [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) | DE, PS | Wird von der DE oder dem Port gesendet, wenn ein Programm zerstört wurde. |
| [IDebugProgramDestroyEventFlags2](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2.md) | DE | Ermöglicht einem Debugmodul, das Standardverhalten [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] der Benutzeroberfläche zu überschreiben, wenn Sie eine Debugsitzung beenden. |
| [IDebugProgramNameChangedEvent2](../../../extensibility/debugger/reference/idebugprogramnamechangedevent2.md) | DE | Wird vom Debugmodul (DE) an den Sitzungsdebug-Manager (SDM) gesendet, wenn sich der Name eines Programms ändert. |
| [IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md) | DE | Wird von der DE gesendet, wenn `IDebugProperty2` eine neue Eigenschaft (dargestellt durch die Schnittstelle) erstellt wurde. |
| [IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md) | DE | Gesendet von der DE, wenn eine Eigenschaft zerstört wurde. |
| [IDebugReturnValueEvent2](../../../extensibility/debugger/reference/idebugreturnvalueevent2.md) | DE | Wird vom DE gesendet, wenn man aus oder über eine Funktion tritt, damit der Rückgabewert korrekt angezeigt werden kann. |
| [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md) | VS | Ermöglicht Debug-Modulen das Remotelesen von Metrikeinstellungen. |
| [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md) | DE | Gesendet von der DE, wenn ein Schritt in, über oder aus einer Anweisung abgeschlossen wurde. |
| [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) | DE | Wird von der DE gesendet, um den Erfolg oder Misserfolg von Ladesymbolen für ein Modul anzuzeigen. |
| [IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md) | DE | Wird von der DE gesendet, wenn ein Thread erstellt wurde. |
| [IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) | DE | Wird von der DE gesendet, wenn ein Thread zerstört wurde. |
| [IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md) | DE | Wird von der DE gesendet, wenn ein Thread seinen Namen geändert hat. |

## <a name="expressions"></a><a name="Expressions"></a>-Ausdrücke
 Diese Schnittstellen stellen Ausdrücke dar, die in einem bestimmten Kontext ausgewertet werden sollen.

|Schnittstelle|Implementiert von|BESCHREIBUNG|
|---------------|--------------------|-----------------|
|[IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)|DE|Stellt einen zu bewertenden Ausdruck dar. Von der [IDebugExpressionContext2-Schnittstelle](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) abgerufen.|
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|Stellt einen Kontext dar, in dem ein Ausdruck ausgewertet wird. Von der [IDebugStackFrame2-Schnittstelle](../../../extensibility/debugger/reference/idebugstackframe2.md) abgerufen.|
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|Wird von der DE gesendet, wenn eine asynchrone Ausdrucksauswertung abgeschlossen ist.|

## <a name="memory"></a><a name="Memory"></a>Speicher
 Diese Schnittstellen stellen Sequenzen von Bytes im Arbeitsspeicher dar.

|Schnittstelle|Implementiert von|BESCHREIBUNG|
|---------------|--------------------|-----------------|
|[IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)|DE|Stellt eine Sequenz von Bytes im Arbeitsspeicher dar, aus der gelesen oder geschrieben werden kann.|
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|Stellt eine Position im Speicher einer Folge von Bytes dar.|

## <a name="modules"></a><a name="Modules"></a>Module
 Diese Schnittstellen stellen ein Modul dar, das einer ausführbaren Datei oder entspricht. DLL-Datei.

|Schnittstelle|Implementiert von|BESCHREIBUNG|
|---------------|--------------------|-----------------|
|[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)|DE|Stellt eine einzelne ausführbare Datei oder DLL dar.|
|[IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)|DE|Stellt ein [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) dar, das Symbole unterstützt.|
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|Wird von der DE gesendet, wenn ein Modul geladen oder entladen wird.|
|[IDebugSourceServerModule](../../../extensibility/debugger/reference/idebugsourceservermodule.md)|DE|Stellt die Quellserverinformationen dar, die in einer PDB-Datei enthalten sind.|
|[IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)|DE|Stellt eine Enumeration über eine Gruppe von Modulen dar, die von einem [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)bekannt sind.|

## <a name="ports"></a><a name="Ports"></a>Ports
 Diese Schnittstellen stellen Ports und Hafenlieferanten dar.

| Schnittstelle | Implementiert von | BESCHREIBUNG |
| - |----------------| - |
| [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md) | VS, PS | Stellt den Standardport auf dem lokalen Computer dar. |
| [IDebugFirewallConfigurationCallback2](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2.md) | VS | Aktiviert ein Debugmodul, das DCOM verwendet, um die [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Benutzeroberfläche zu fragen, um sicherzustellen, dass die Firewall das Remote-Debuggen nicht blockiert. |
| [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) | VS, PS | Stellt einen Port dar. |
| [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) | PS | Wird von einem Port gesendet, um Portereignisse an jeden Listener zu kommunizieren. |
| [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md) | PS | Stellt einen Port dar, der Prozesse starten und beenden kann. |
| [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) | PS | Wird verwendet, um Programme mit einem Port zu registrieren und zu entmelden; ermöglicht es dem Port, Programme zu verfolgen, die derzeit gedebuggt werden. |
| [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md) | PS | Stellt eine benutzerdefinierte Benutzeroberfläche zum Auswählen des Ports dar. |
| [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) | VS | Stellt eine Anforderung für einen Port dar, von dem aus ein neuer Port erstellt oder lokalisiert wird. |
| [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) | PS | Stellt einen Anbieter von Ports dar. |
| [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md) | PS | Stellt einen Lieferanten von Ports dar, die Informationen über die von ihm erstellten Ports beibehalten (auf Dem Datenträger speichern) können. |
| [IDebugPortSupplierDescription2](../../../extensibility/debugger/reference/idebugportsupplierdescription2.md) | PS | Ermöglicht [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] der Benutzeroberfläche die Anzeige von Text im Abschnitt **Transportinformationen** im Dialogfeld An fügen an **den Prozess** an. |
| [IDebugWindowsComputerPort2](../../../extensibility/debugger/reference/idebugwindowscomputerport2.md) | VS | Ermöglicht abfragen nach Informationen über den Zielcomputer. |
| [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md) | VS, PS | Stellt eine Enumeration über eine Reihe von Ports dar. |
| [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) | VS | Stellt eine Enumeration über eine Gruppe von Portlieferanten dar. |

## <a name="processes"></a><a name="Processes"></a>Prozesse
 Diese Schnittstellen stellen Prozesse dar, eine einzelne ausführbare Datei, die ein oder mehrere Programme enthält.

|Schnittstelle|Implementiert von|BESCHREIBUNG|
|---------------|--------------------|-----------------|
|[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)|PS, DE|Stellt einen Prozess dar, der auf einem Computer ausgeführt wird.|
|[IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)|PS, DE|Stellt einen Prozess dar, der das Debuggen aktiv unterstützt (wird verwendet, um Step-, Continue- und Execute-Methoden auf der [IDebugProgram2-Schnittstelle](../../../extensibility/debugger/reference/idebugprogram2.md) zu ersetzen).|
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|DE, PS|Wird von der DE oder dem Port gesendet, wenn ein Prozess erstellt wurde.|
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|DE, PS|Wird von der DE oder dem Port gesendet, wenn ein Prozess zerstört wurde.|
|[IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)|PS|Stellt einen Prozess dar, der nachverfolgen muss, welche Sitzung mit ihm verbunden ist.|
|[IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)|PS|Stellt eine Aufzählung einer Gruppe von Prozessen auf einem Port dar.|

## <a name="programs"></a><a name="Programs"></a>Programme
 Diese Schnittstellen stellen Programme dar, logische Ausführungseinheiten, die nicht unbedingt einer physischen ausführbaren Datei oder einem Modul entsprechen.

|Schnittstelle|Implementiert von|BESCHREIBUNG|
|---------------|--------------------|-----------------|
|[IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)|DE|Stellt ein [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) dar, das mit anderen Programmen, die gleichzeitig gedebuggen werden, zusammenarbeiten muss.|
|[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)|DE, PS|Stellt eine logische Ausführungseinheit dar.|
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|DE, PS|Wird von der DE oder dem Port gesendet, wenn ein Programm erstellt wurde.|
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|DE, PS|Wird von der DE oder dem Port gesendet, wenn ein Programm zerstört wurde.|
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE, PS|Stellt einen [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) dar, der von mehreren Debugmodulen verarbeitet werden kann.|
|[IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)|PS|Stellt ein [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) dar, das in der Lage sein muss, nachzuverfolgen, welche Sitzung an sie angefügt ist.|
|[IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)|DE, PS|Stellt ein [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) dar, das Informationen über den Prozess zurückgeben kann, in dem es ausgeführt wird.|
|[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)|DE, PS|Stellt ein Programm dar, das gedebuggégiert werden kann.|
|[IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)|DE, PS|Ermöglicht die Benachrichtigung eines Programmknotens über den Versuch, eine Verbindung an das zugeordnete Programm anzufügen.|
|[IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)|DE|Bietet dem SDM die Möglichkeit, eine DE zu den von dieser DE gesteuerten Programmen abzufragen.|
|[IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)|VS|Wird von DEs verwendet, um Programme beim SDM zu registrieren, um anzuzeigen, dass sie gedebuggiert werden.|
|[IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)|DE, PS|Stellt einen [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) dar, der Schnittstellen über Thread- oder Prozessgrenzen hinweg marshallen kann.|
|[IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)|DE, PS|Stellt eine Aufzählung einer Reihe von Programmen dar.|

## <a name="properties"></a>Eigenschaften von <a name="Properties"></a>
 Diese Schnittstellen stellen Eigenschaften dar, einen Wert, der einem bestimmten Kontext zugeordnet ist, in der Regel das Ergebnis einer Ausdrucksauswertung.

|Schnittstelle|Implementiert von|BESCHREIBUNG|
|---------------|--------------------|-----------------|
|[IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)|EE|Stellt eine [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) dar, die ihren Wert auf benutzerdefinierte Weise anzeigen kann.|
|[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)|DE|Stellt einen Wert eines Stapelrahmens, Dokuments oder des Ergebnisses einer Ausdrucksauswertung dar.|
|[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)|DE|Stellt eine [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) dar, die beliebig lange Zeichenfolgen unterstützt.|
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|Wird von der DE gesendet, wenn eine neue Eigenschaft (dargestellt durch die [IDebugProperty2-Schnittstelle)](../../../extensibility/debugger/reference/idebugproperty2.md) erstellt wurde.|
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|Gesendet von der DE, wenn eine Eigenschaft zerstört wurde.|
|[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)|DE|Stellt einen Verweis auf eine Eigenschaft dar, die außerhalb eines bestimmten Stapelrahmens vorhanden sein kann.|
|[IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)|DE|Stellt eine Enumeration über eine Reihe von [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) Strukturen dar, die Variablen, Register, Parameter und Ausdrücke beschreiben.|
|[IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)|DE|Stellt eine Enumeration über eine Reihe von [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) Strukturen dar.|

## <a name="stack-frames"></a><a name="StackFrames"></a>Stack-Frames
 Diese Schnittstellen stellen einen Stapelrahmen dar, einen Kontext, in dem ein Haltepunkt oder eine Ausnahme aufgetreten ist.

|Schnittstelle|Implementiert von|BESCHREIBUNG|
|---------------|--------------------|-----------------|
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|Stellt einen Kontext dar, in dem ein Haltepunkt oder eine Ausnahme aufgetreten ist.|
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|Stellt einen [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) dar, der abgefangene Ausnahmen verarbeiten kann.|
|[IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)|DE|Stellt eine Enumeration über den Satz von [CODE_PATH](../../../extensibility/debugger/reference/code-path.md) Strukturen dar, die die Funktionsaufrufsequenz angeben, die verwendet wird, um zu einem bestimmten Stapelrahmen zu gelangen.|
|[IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)|DE|Stellt eine Enumeration über einen Satz von [FRAMEINFO-Strukturen](../../../extensibility/debugger/reference/frameinfo.md) dar, die Stapelrahmen beschreiben.|

## <a name="threads"></a><a name="Threads"></a>Threads
 Diese Schnittstellen stellen Threads und die zugehörigen Ereignisse dar.

|Schnittstelle|Implementiert von|BESCHREIBUNG|
|---------------|--------------------|-----------------|
|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|DE|Stellt einen Ausführungsthread dar.|
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|Wird von der DE gesendet, wenn ein Thread erstellt wurde.|
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|Wird von der DE gesendet, wenn ein Thread zerstört wurde.|
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|Wird von der DE gesendet, wenn ein Thread seinen Namen geändert hat.|
|[IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)|DE|Stellt eine Enumeration über eine Gruppe von Threads dar.|

## <a name="type-visualizers"></a><a name="TypeVisualizers"></a>Typ Visualizer
 Diese Schnittstellen bieten Unterstützung für Typvisualisierer. Diese Schnittstellen werden in der Regel von einem Ausdrucksevaluator implementiert.

|Schnittstelle|Implementiert von|BESCHREIBUNG|
|---------------|--------------------|-----------------|
|[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)|EE|Stellt ein Array von Bytes dar, das einer Typvisualisierung angezeigt werden soll.|
|[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)|EE|Stellt Methoden zum Abrufen des Zugriffs auf Daten bereit, die an eine Typvisualisierung übergeben werden sollen.|
|[IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)|EE|Stellt eine Eigenschaft dar, die Zugriff auf [IPropertyProxyEESide-Implementierungen](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) bietet.|

## <a name="see-also"></a>Weitere Informationen
- [API-Referenz](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
- [Erstellen einer benutzerdefinierten Debug-Engine](../../../extensibility/debugger/creating-a-custom-debug-engine.md)
