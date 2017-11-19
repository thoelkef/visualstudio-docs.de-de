---
title: Haupt-Schnittstellen | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], core interfaces
ms.assetid: 666b9116-8550-4bdd-bc15-55fc57de87df
caps.latest.revision: "24"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 367917032b836ce6a7d07cf3eba85db14464a957
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="core-interfaces"></a>Core-Schnittstellen
Die folgenden Schnittstellen sind die Core-Schnittstellen für den Debugger zu erweitern, indem Sie mit der [!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)].  
  
## <a name="discussion"></a>Diskussion  
 Diese Schnittstellen werden in erster Linie verwendet, um das Debugging-Modul (DE) zu erstellen. Sie werden hier nach Kategorien unterteilt:  
  
-   [Haltepunkte](#Breakpoints)  
  
-   [Kontext](#Contexts)  
  
-   [Core-Server](#CoreServer)  
  
-   [Debuggen von Modulen](#DebugEngines)  
  
-   [Dokumente](#Documents)  
  
-   [Ereignisse](#Events)  
  
-   [Ausdrücke](#Expressions)  
  
-   [Arbeitsspeicher](#Memory)  
  
-   [Module](#Modules)  
  
-   [Ports](#Ports)  
  
-   [Prozesse](#Processes)  
  
-   [Programme](#Programs)  
  
-   [Eigenschaften](#Properties)  
  
-   [Stapelrahmen](#StackFrames)  
  
-   [Threads](#Threads)  
  
-   [Typ-Schnellansichten](#TypeVisualizers)  
  
 Die Entitäten, die die Schnittstellen implementieren, können sind:  
  
-   Debuggen des Datenbankmoduls (DE)  
  
-   Port Lieferanten (PS)  
  
-   Ausdrucksauswertung (EE)  
  
-   Visual Studio (VS)  
  
##  <a name="Breakpoints"></a>Haltepunkte  
 Diese Schnittstellen beziehen sich auf die Implementierung und die Überwachung von Haltepunkten.  
  
|Schnittstelle|Implementiert durch|Beschreibung|  
|---------------|--------------------|-----------------|  
|[IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)|DE|Steht für einen Haltepunkt an einer Speicheradresse gebunden.|  
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|Durch die DE gesendet, wenn ein Haltepunkt an einer Speicheradresse gebunden ist.|  
|[IDebugBreakpointChecksumRequest2](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2.md)|VS|Stellt eine Dokument-Prüfsumme für eine Anforderung Haltepunkt dar.|  
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|Durch die DE gesendet, fällt ein Haltepunkt an einer Speicheradresse gebunden werden.|  
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|Durch die DE gesendet, wenn ein Haltepunkt erreicht wird.|  
|[IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)|VS|Stellt eine Anforderung für einen Haltepunkt dar; Beim Erstellen eines ausstehenden Haltepunkts verwendet.|  
|[IDebugBreakpointRequest3](../../../extensibility/debugger/reference/idebugbreakpointrequest3.md)|VS|Stellt eine Anforderung für einen Haltepunkt dar; Beim Erstellen eines ausstehenden Haltepunkts verwendet.|  
|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|DE|Stellt die Informationen verwendet, um einen Haltepunkt zu binden.|  
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|Durch die DE gesendet, wenn Sie ein Haltepunkt an einer Speicheradresse aufgehoben wird.|  
|[IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)|DE|Stellt einen ungültigen Breakpoint (zurückgegebenes `IDebugBreakpointErrorEvent2`).|  
|[IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)|DE|Stellt die Auflösung Informationen über einen ungültigen Breakpoint.|  
|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|DE|Stellt eine Position in einer Funktion, in denen ein Haltepunkt festgelegt wurde.|  
|[IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)|DE|Steht für einen Haltepunkt, der gebunden werden soll; Beim Erstellen eines gebundenen Haltepunkts verwendet.|  
|[IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)|DE|Eine Enumeration darstellt für eine Menge von gebundenen Haltepunkten.|  
|[IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)|DE|Eine Enumeration darstellt, über einen Satz von Breakpoints, die nicht auf einen Speicherbereich gebunden werden kann.|  
  
##  <a name="Contexts"></a>Kontexte  
 Diese Schnittstellen darstellen, verschiedene Arten von Kontexten innerhalb des Programms, der debuggt wird.  
  
|Schnittstelle|Implementiert durch|Beschreibung|  
|---------------|--------------------|-----------------|  
|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|DE|Stellt die Anfangsposition des Code-Anweisung dar.|  
|[IDebugCodeContext3](../../../extensibility/debugger/reference/idebugcodecontext3.md)|DE|Erweitert die [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) Schnittstelle, um den Abruf von Modul und die Prozess-Schnittstellen zu aktivieren.|  
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS, DE|Stellt eine Position in einem Dokument dar.|  
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|Stellt den Kontext in der zum Auswerten eines Ausdrucks dar.|  
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|Stellt die Startposition im Arbeitsspeicher, der eine Auflistung von Bytes dar.|  
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|Stellt einen Stack-Frame-Kontext an einem Haltepunkt oder Ausnahme.|  
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|Stellt einen Stack-Frame-Kontext an einem Haltepunkt oder Ausnahme.|  
|[IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)|DE|Eine Enumeration darstellt für eine Menge von Code Kontexten.|  
  
##  <a name="CoreServer"></a>Core-Server  
 Diese Schnittstellen darstellen, den Computer, auf dem eine Anwendung gedebuggt wird. Diese werden durch implementiert [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] jedoch in vom Debugmodule aufgerufen werden kann.  
  
|Schnittstelle|Implementiert durch|Beschreibung|  
|---------------|--------------------|-----------------|  
|[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)|VS|Bietet Zugriff auf die Ports und Port Lieferanten sowie Informationen über den Computer.|  
|[IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)|VS|Stellt eine [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) unterstützt, die das Remotedebuggen.|  
  
##  <a name="DebugEngines"></a>Debuggen von Modulen  
 Diese Schnittstellen darstellen Debugmodule und deren zugeordneten Ereignissen an.  
  
|Schnittstelle|Implementiert durch|Beschreibung|  
|---------------|--------------------|-----------------|  
|[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)|DE|Stellt einen benutzerdefinierten Debugmodul dar.|  
|[IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)|DE|Stellt einen benutzerdefinierten Debugmodul, das Laden von Symbolen, die JustMyCode und Ausnahmen unterstützt.|  
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|Durch jede neue Instanz des DE gesendet, um anzugeben, dass es Debugaufgaben behandeln kann.|  
|[IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)|DE|Stellt einen benutzerdefinierten Debugmodul, das startende von Programmen unterstützt.|  
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DEUTSCHLAND, PS|Stellt einen Programm-Knoten, der mehrere Debugmodule behandelt.|  
|[IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)|DE|Bietet eine Möglichkeit für die SDM eine Schnittstelle für das Debugmodul aus einem Thread, Programm oder Stapelrahmen abzurufen.|  
  
##  <a name="Documents"></a>Dokumente  
 Diese Schnittstellen stellen Dokumente (Quelldateien) und ihre zugehörigen Elemente dar.  
  
|Schnittstelle|Implementiert durch|Beschreibung|  
|---------------|--------------------|-----------------|  
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|Vom DE gesendet und fordern ein Dokument geöffnet werden.|  
|[IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)|DE|Stellt einen Datenstrom von disassemblierten Anweisungen aus einem Dokument dar.|  
|[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)|VS, DE|Stellt ein Dokument vom DE, einen Namen und eine Klasse-ID (CLSID) angeben.|  
|[IDebugDocumentChecksum2](../../../extensibility/debugger/reference/idebugdocumentchecksum2.md)|DEUTSCHLAND, EE|Stellt eine Prüfsumme für eine Debug-Dokument dar und ermöglicht es die Prüfsumme zwischen Komponenten übergeben.|  
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS, DE|Stellt einen Dokumentenkontext, eine Position in einem Dokument, einem bestimmten Kontext der Anweisung und Code entspricht.|  
|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|VS, DE|Stellt eine allgemeine Position in einem Dokument dar.|  
|[IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)|VS|Stellt eine Position in einer Quelldatei als Zeichenoffset dar.|  
|[IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)|VS, DE|Stellt ein Textdokument die DE vom (abgeleitet [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)), den tatsächlichen Text angeben.|  
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|Von DE gesendet, um Änderungen an einer Quelldatei anzugeben, die im Speicher befindet.|  
  
##  <a name="Events"></a> Ereignisse  
 Diese Schnittstellen darstellen, alle Ereignisse, die zwischen dem Code und der Sitzungs-Manager (SDM) gesendet werden.  
  
|Schnittstelle|Implementiert durch|Beschreibung|  
|---------------|--------------------|-----------------|  
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|Vom DE gesendet und fordern ein Dokument geöffnet werden.|  
|[IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md)|DE|Debugging-Modul (DE) sendet diese Schnittstelle zu dem Sitzung Debug-Manager (SDM), legen Sie den Status Strich Nachricht während des Symbol lädt.|  
|[IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)|DE|Von der DE gesendet, wenn eine Unterbrechung in der Anwendung abgeschlossen wurde.|  
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|Durch die DE gesendet, wenn ein Haltepunkt gebunden ist.|  
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|Durch die DE gesendet, wenn ein Breakpoint nicht gebunden werden.|  
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|Durch die DE gesendet, wenn ein Haltepunkt erreicht wird.|  
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|Von der DE gesendet, wenn ein Breakpoint aufgehoben wird.|  
|[IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)|DE|Durch DE gesendet, um zu bestimmen, ob sie an einer bestimmten Stelle beendet werden soll.|  
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|Von DE gesendet, um Änderungen an einer Quelldatei anzugeben, die im Speicher befindet.|  
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|Durch jede neue Instanz des DE gesendet, um anzugeben, dass es Debugaufgaben behandeln kann.|  
|[IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)|DE|Durch die DE gesendet, um anzugeben, dass das derzeit debuggte Programm bereit zum Ausführen der ersten Anweisung ist.|  
|[IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)|DE|Eine Schnittstelle, die von anderen Ereignisschnittstellen, die einen Fehler zurückgeben können, verwendet wird, um lesbare Fehlermeldungen bereitzustellen.|  
|[IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)|DEUTSCHLAND, PS|Die Basisschnittstelle, von der alle anderen Ereignis Schnittstellen abgeleitet sind.|  
|[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)|VS|Stellt eine Schnittstelle implementiert, die durch die SDM an die Ereignisse (ausgedrückt als Objekte, die eine bestimmtes Ereignis-Schnittstelle implementiert) gesendet werden.|  
|[IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)|DE|Von der DE gesendet, wenn eine Ausnahme im zu debuggenden Programms aufgetreten ist.|  
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|Von der DE gesendet, wenn eine asynchroner ausdrucksauswertung abgeschlossen ist.|  
|IDebugFindSymbolEvent2||VERALTET. DARF NICHT VERWENDET WERDEN.|  
|[IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|DE|Durch die DE gesendet, bei der Verarbeitung für eine abgefangene Ausnahme abgeschlossen wurde.|  
|[IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|DE|Durch die DE gesendet, wenn ein Programm Ladevorgang abgeschlossen ist.|  
|[IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)|DE|Durch die DE die IDE-Anzeige haben eine informative Meldung an den Benutzer gesendet.|  
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|Durch die DE gesendet, wenn ein Modul geladen oder entladen wird.|  
|[IDebugNoSymbolsEvent2](../../../extensibility/debugger/reference/idebugnosymbolsevent2.md)|DE|Signalisiert dem [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] debugger-Benutzeroberfläche, die dem Benutzer gewarnt, dass die Symbole nicht gefunden für gestarteten Programmdateien werden konnte.|  
|[IDebugOutputStringEvent2](../../../extensibility/debugger/reference/idebugoutputstringevent2.md)|DE|Die DE die IDE-Anzeige haben eine beliebige Zeichenfolge gesendet.|  
|[IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)|VS, DE|Von einem Port gesendet, portereignisse an alle Listener zu kommunizieren.|  
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|DEUTSCHLAND, PS|Vom DE oder Port gesendet, wenn ein Prozess erstellt wurde.|  
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|DEUTSCHLAND, PS|Vom DE oder Port gesendet, wenn ein Prozess zerstört wurde.|  
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|DEUTSCHLAND, PS|Vom DE oder Port gesendet, wenn ein Programm erstellt wurde.|  
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|DEUTSCHLAND, PS|Vom DE oder Port gesendet, wenn ein Programm zerstört wurde.|  
|[IDebugProgramDestroyEventFlags2](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2.md)|DE|Ermöglicht ein Debugmodul an das Standardverhalten außer Kraft setzen die [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] UI, wenn Sie eine Debugsitzung zu beenden.|  
|[IDebugProgramNameChangedEvent2](../../../extensibility/debugger/reference/idebugprogramnamechangedevent2.md)|DE|An gesendet, aus der Debugging-Modul (DE) der Sitzung Debug-Manager (SDM) Wenn ändert sich der Name eines Programms.|  
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|Durch die DE, wenn eine neue Eigenschaft gesendet (dargestellt durch die `IDebugProperty2` Schnittstelle) erstellt wurde.|  
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|Durch die DE gesendet, wenn eine Eigenschaft zerstört wurde.|  
|[IDebugReturnValueEvent2](../../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|DE|Durch die DE gesendet, Prozedurschritt aus oder über eine Funktion ausgeführt wird, sodass der Rückgabewert ordnungsgemäß angezeigt werden kann.|  
|[IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)|VS|Ermöglicht das Debuggen Module zum Lesen von metrikeinstellungen Remote.|  
|[IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|DE|Von der DE gesendet, wenn es sich bei ein Schritt ausführen, überspringen oder aus einer Anweisung abgeschlossen wurde.|  
|[IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|DE|Durch die DE gesendet, um den Erfolg oder Misserfolg des Laden von Symbolen für ein Modul anzugeben.|  
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|Durch die DE gesendet, wenn ein Thread erstellt wurde.|  
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|Durch die DE gesendet, wenn ein Thread zerstört wurde.|  
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|Durch die DE gesendet, wenn ein Thread seinen Namen geändert wurde.|  
  
##  <a name="Expressions"></a>Ausdrücke  
 Diese Schnittstellen darstellen, Ausdrücke, die in einem bestimmten Kontext ausgewertet werden.  
  
|Schnittstelle|Implementiert durch|Beschreibung|  
|---------------|--------------------|-----------------|  
|[IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)|DE|Stellt einen Ausdruck ausgewertet werden soll. Abgerufenes der [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) Schnittstelle.|  
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|Stellt einen Kontext, in dem ein Ausdruck ausgewertet wird. Abgerufenes der [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) Schnittstelle.|  
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|Von der DE gesendet, wenn eine asynchroner ausdrucksauswertung abgeschlossen ist.|  
  
##  <a name="Memory"></a>Arbeitsspeicher  
 Diese Schnittstellen stellen Sequenzen von Bytes im Speicher dar.  
  
|Schnittstelle|Implementiert durch|Beschreibung|  
|---------------|--------------------|-----------------|  
|[IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)|DE|Stellt eine Folge von Bytes im Arbeitsspeicher, die aus gelesen oder geschrieben werden können.|  
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|Stellt einen Speicherort im Arbeitsspeicher, der eine Folge von Bytes dar.|  
  
##  <a name="Modules"></a> Module  
 Diese Schnittstellen darstellen, ein Modul, das eine ausführbare Datei entspricht oder. DLL-Datei.  
  
|Schnittstelle|Implementiert durch|Beschreibung|  
|---------------|--------------------|-----------------|  
|[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)|DE|Stellt eine einzelne ausführbare Datei oder DLL dar.|  
|[IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)|DE|Stellt eine [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) , die die Symbole unterstützt.|  
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|Durch die DE gesendet, wenn ein Modul geladen oder entladen wird.|  
|[IDebugSourceServerModule](../../../extensibility/debugger/reference/idebugsourceservermodule.md)|DE|Stellt die Quellinformationen für Server, die in einer PDB-Datei enthalten ist.|  
|[IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)|DE|Eine Enumeration darstellt, für eine Menge von Modulen, die bekannt sind ein [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md).|  
  
##  <a name="Ports"></a>Ports  
 Diese Schnittstellen darstellen, Ports und Port Lieferanten.  
  
|Schnittstelle|Implementiert durch|Beschreibung|  
|---------------|--------------------|-----------------|  
|[IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)|VS, PS|Stellt den Standardport auf dem lokalen Computer an.|  
|[IDebugFirewallConfigurationCallback2](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2.md)|VS|Ermöglicht ein Debugmodul DCOM verwendet wird, um Unterstützung bitten, die die [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] UI, um sicherzustellen, dass der Firewall kein Remotedebuggen blockiert wird.|  
|[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)|VS, PS|Stellt einen Port an.|  
|[IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)|PS|Von einem Port gesendet, portereignisse an alle Listener zu kommunizieren.|  
|[IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)|PS|Stellt einen Port, der starten und Prozesse beenden kann.|  
|[IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)|PS|Zum Registrieren und Aufheben der Programme mit einem Port verwendet. können den Port zum Nachverfolgen der gerade gedebuggten Programme.|  
|[IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)|PS|Stellt eine benutzerdefinierte Benutzeroberfläche für den Port auswählen.|  
|[IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)|VS|Stellt eine Anforderung für einen Port aus dem neuer Anschluss erstellt oder gespeichert werden.|  
|[IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)|PS|Stellt ein Hersteller der Ports an.|  
|[IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)|PS|Stellt ein Hersteller der Ports, die beibehalten werden können (auf dem Datenträger speichern) Informationen zu den Ports erstellen.|  
|[IDebugPortSupplierDescription2](../../../extensibility/debugger/reference/idebugportsupplierdescription2.md)|PS|Ermöglicht die [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Benutzeroberfläche zum Anzeigen von Text in der **Transportinformationen** Teil der **an den Prozess anhängen** (Dialogfeld).|  
|[IDebugWindowsComputerPort2](../../../extensibility/debugger/reference/idebugwindowscomputerport2.md)|VS|Ermöglicht das Abfragen von Informationen über den Zielcomputer.|  
|[IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)|VS, PS|Stellt eine Enumeration für eine Menge von Ports dar.|  
|[IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)|VS|Eine Enumeration darstellt, über einen Satz von Port Lieferanten.|  
  
##  <a name="Processes"></a>Prozesse  
 Diese Schnittstellen darstellen, automatisiert, eine einzelne ausführbare Datei, die eine oder mehrere Programme enthält.  
  
|Schnittstelle|Implementiert durch|Beschreibung|  
|---------------|--------------------|-----------------|  
|[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)|PS, DE|Entspricht einem Prozess, der auf einem Computer ausgeführt wird.|  
|[IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)|PS, DE|Entspricht einem Prozess, der aktiv unterstützt debugging (verwendet, um den Schritt zu ersetzen, den Vorgang fortzusetzen, und führen Sie die Methoden für die [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) Schnittstelle).|  
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|DEUTSCHLAND, PS|Vom DE oder Port gesendet, wenn ein Prozess erstellt wurde.|  
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|DEUTSCHLAND, PS|Vom DE oder Port gesendet, wenn ein Prozess zerstört wurde.|  
|[IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)|PS|Entspricht einem Prozess, der zum Nachverfolgen muss, welche Sitzung zugeordnet ist.|  
|[IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)|PS|Stellt eine Enumeration von einer Reihe von Prozessen auf einem Port an.|  
  
##  <a name="Programs"></a>Programme  
 Diese Schnittstellen darstellen, Programme, die logischen Einheiten der Ausführung, die nicht unbedingt um eine physische ausführbare Datei oder ein Modul entsprechen.  
  
|Schnittstelle|Implementiert durch|Beschreibung|  
|---------------|--------------------|-----------------|  
|[IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)|DE|Stellt eine [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , muss in Verbindung mit anderen Programmen, die zur gleichen Zeit gedebuggten arbeitet.|  
|[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)|DEUTSCHLAND, PS|Stellt eine logische Ausführungseinheit dar.|  
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|DEUTSCHLAND, PS|Vom DE oder Port gesendet, wenn ein Programm erstellt wurde.|  
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|DEUTSCHLAND, PS|Vom DE oder Port gesendet, wenn ein Programm zerstört wurde.|  
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DEUTSCHLAND, PS|Stellt eine [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) , die von mehreren Debugmodule verarbeitet werden können.|  
|[IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)|PS|Stellt eine [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) muss, die verfolgen, welche Sitzung zugeordnet ist.|  
|[IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)|DEUTSCHLAND, PS|Stellt eine [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , die Informationen über den Prozess, in dem er ausgeführt wird, zurückgeben können.|  
|[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)|DEUTSCHLAND, PS|Stellt ein Programm, das gedebuggt werden kann.|  
|[IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)|DEUTSCHLAND, PS|Ermöglicht es einem Programm-Knoten, der beim Anfügen an das zugeordnete Programm benachrichtigt werden.|  
|[IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)|DE|Bietet eine Möglichkeit für die SDM zum Abfragen einer bereitgestellten Kompatibilitätsrichtlinie zu den Programmen, die von diesem DE gesteuert.|  
|[IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)|VS|Von DEs verwendet, um Programme zu registrieren, mit dem SDM zeigen die gerade gedebuggt werden.|  
|[IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)|DEUTSCHLAND, PS|Stellt eine [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) kann, die Schnittstellen Prozess oder Thread hinweg gemarshallt.|  
|[IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)|DEUTSCHLAND, PS|Stellt eine Enumeration, der einen Satz von Programmen an.|  
  
##  <a name="Properties"></a> Eigenschaften  
 Diese Schnittstellen stellen Eigenschaften, ein Wert mit einem bestimmten Kontext, in der Regel das Ergebnis der Auswertung von Ausdrücken dar.  
  
|Schnittstelle|Implementiert durch|Beschreibung|  
|---------------|--------------------|-----------------|  
|[IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)|EE|Stellt eine [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) seinen Wert auf benutzerdefinierte Weise anzeigen kann.|  
|[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)|DE|Stellt einen Wert, der einen Stapelrahmen, Dokument oder das Ergebnis der Auswertung von Ausdrücken.|  
|[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)|DE|Stellt eine [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) , beliebig lange Zeichenfolgen unterstützt.|  
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|Durch die DE, wenn eine neue Eigenschaft gesendet (dargestellt durch die [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) Schnittstelle) erstellt wurde.|  
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|Durch die DE gesendet, wenn eine Eigenschaft zerstört wurde.|  
|[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)|DE|Stellt einen Verweis auf eine Eigenschaft, die außerhalb der ein bestimmtes Stapelrahmen vorhanden sein kann.|  
|[IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)|DE|Eine Enumeration darstellt, über einen Satz von [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) Strukturen die Variablen, Register, Parameter und Ausdrücke zu beschreiben.|  
|[IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)|DE|Eine Enumeration darstellt, über einen Satz von [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) Strukturen.|  
  
##  <a name="StackFrames"></a>Stapelrahmen  
 Diese Schnittstellen darstellen, einen Stapelrahmen entspricht, die einen Kontext in der ein Breakpoint oder Ausnahme aufgetreten ist.  
  
|Schnittstelle|Implementiert durch|Beschreibung|  
|---------------|--------------------|-----------------|  
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|Stellt einen Kontext dar, in denen ein Haltepunkt oder eine Ausnahme aufgetreten ist.|  
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|Stellt eine [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) die behandeln können Ausnahmen abgefangen.|  
|[IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)|DE|Eine Enumeration darstellt, über der Menge der [CODE_PATH](../../../extensibility/debugger/reference/code-path.md) Strukturen, die die Funktion angeben Aufrufsequenz verwendet, um einen bestimmten Stapelrahmen entspricht ankommen.|  
|[IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)|DE|Eine Enumeration darstellt, über einen Satz von [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) Strukturen, die Stapelrahmen beschreiben.|  
  
##  <a name="Threads"></a> Threads  
 Diese Schnittstellen darstellen, Threads und deren zugeordneten Ereignissen.  
  
|Schnittstelle|Implementiert durch|Beschreibung|  
|---------------|--------------------|-----------------|  
|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|DE|Stellt einen Ausführungsthread dar.|  
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|Durch die DE gesendet, wenn ein Thread erstellt wurde.|  
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|Durch die DE gesendet, wenn ein Thread zerstört wurde.|  
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|Durch die DE gesendet, wenn ein Thread seinen Namen geändert wurde.|  
|[IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)|DE|Eine Enumeration darstellt für eine Menge von Threads.|  
  
##  <a name="TypeVisualizers"></a>Typ-Schnellansichten  
 Diese Schnittstellen bieten Unterstützung für die Typ-Schnellansichten. Diese Schnittstellen werden in der Regel von der ausdrucksauswertung implementiert.  
  
|Schnittstelle|Implementiert durch|Beschreibung|  
|---------------|--------------------|-----------------|  
|[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)|EE|Stellt ein Array von Bytes für eine Schnellansicht Typ dargestellt wird.|  
|[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)|EE|Stellt Methoden zum Abrufen von Zugriff auf Daten einer Schnellansicht Typ übergeben werden soll.|  
|[IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)|EE|Stellt eine Eigenschaft, die Zugriff auf [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) Implementierungen.|  
  
## <a name="see-also"></a>Siehe auch  
 [API-Referenz](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)   
 [Erstellen eines benutzerdefinierten Debugmoduls](../../../extensibility/debugger/creating-a-custom-debug-engine.md)