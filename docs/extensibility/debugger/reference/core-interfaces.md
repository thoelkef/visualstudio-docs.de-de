---
title: "Core-Schnittstellen | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Debuggen [Debugging-SDK] Core-Schnittstellen"
ms.assetid: 666b9116-8550-4bdd-bc15-55fc57de87df
caps.latest.revision: 24
caps.handback.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
---
# Core-Schnittstellen
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Die folgenden Schnittstellen sind die wichtigsten Schnittstellen zum Erweitern des Debuggers, indem sie [!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)]verwenden.  
  
## Erörterung  
 Diese Schnittstellen werden hauptsächlich verwendet, um das Debugmodul \(DE\) zu erstellen.  Sie werden hier nach Kategorien organisiert:  
  
-   [Haltepunkte](#Breakpoints)  
  
-   [Kontexte](#Contexts)  
  
-   [Kern\-Server](#CoreServer)  
  
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
  
-   [Typ\-Schnellansichten](#TypeVisualizers)  
  
 Die Entitäten, die die Schnittstellen implementiert werden können, sind:  
  
-   Modul \(Debug\) DE  
  
-   Anschluss\-Lieferant \(PS\)  
  
-   Ausdrucksauswertung \(EE\)  
  
-   GEGEN \(Visual Studio\)  
  
##  <a name="Breakpoints"></a> Haltepunkte  
 Diese Schnittstellen werden zur Implementierung und zur Nachverfolgung von Haltepunkten verknüpft.  
  
|Schnittstelle|Vorbei implementiert|Beschreibung|  
|-------------------|--------------------------|------------------|  
|[IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)|DE|Stellt einen Haltepunkt dar, der an einer bestimmten Speicheradresse gebunden ist.|  
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|Gesendet von DE, wenn ein Haltepunkt an einer bestimmten Speicheradresse gebunden ist.|  
|[IDebugBreakpointChecksumRequest2](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2.md)|GEGEN|Stellt eine Anforderung Haltepunkt für eine prüfsumme Dokumente dar.|  
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|Gesendet von DE, wenn ein Haltepunkt an einer bestimmten Speicheradresse nicht gebunden werden kann.|  
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|Gesendet von DE, wenn ein Haltepunkt erreicht wird.|  
|[IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)|GEGEN|Stellt eine Anforderung für einen Haltepunkt dar. verwendet, wenn ein anstehender Haltepunkt erstellt wird.|  
|[IDebugBreakpointRequest3](../../../extensibility/debugger/reference/idebugbreakpointrequest3.md)|GEGEN|Stellt eine Anforderung für einen Haltepunkt dar. verwendet, wenn ein anstehender Haltepunkt erstellt wird.|  
|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|DE|Stellt die Informationen dar, die verwendet werden, um einen Haltepunkt zu binden.|  
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|Gesendet von DE, wenn ein Haltepunkt an einer bestimmten Speicheradresse ungebunden ist.|  
|[IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)|DE|Stellt einen ungültigen Haltepunkt dar \(zurückgegeben von `IDebugBreakpointErrorEvent2`\).|  
|[IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)|DE|Stellt die Auflösungs zu einem ungültigen Haltepunkt dar.|  
|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|DE|Stellt eine Position in einer Funktion dar, bei der ein Haltepunkt festgelegt wird.|  
|[IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)|DE|Stellt einen Haltepunkt dar, der gebunden werden soll. verwendet, wenn ein gebundener Haltepunkt erstellt wird.|  
|[IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)|DE|Stellt eine Enumeration über einen Satz von gebundenen Haltepunkte dar.|  
|[IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)|DE|Stellt eine Enumeration über einen Satz von Haltepunkten dar, die nicht an einer bestimmten Speicheradresse gebunden werden können.|  
  
##  <a name="Contexts"></a> Kontexte  
 Diese Schnittstellen stellen verschiedene Arten von Kontexten innerhalb des Programms, das gedebuggt wird.  
  
|Schnittstelle|Vorbei implementiert|Beschreibung|  
|-------------------|--------------------------|------------------|  
|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|DE|Stellt die Startposition einer Code Anweisung dar.|  
|[IDebugCodeContext3](../../../extensibility/debugger/reference/idebugcodecontext3.md)|DE|Erweitert die [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)\-Schnittstelle, um den Abruf des Moduls und der Prozess Schnittstellen zu aktivieren.|  
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|GEGEN, DE|Stellt eine Position in einem Dokument dar.|  
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|Stellt den Kontext dar, in dem ein Ausdruck ausgewertet werden.|  
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|Stellt die Anfangsposition auf den Gedenken an eine Auflistung von Bytes dar.|  
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|Stellt einen Stapelrahmen Elementkontext an einem Haltepunkt oder einer Ausnahme dar.|  
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|Stellt einen Stapelrahmen Elementkontext an einem Haltepunkt oder einer Ausnahme dar.|  
|[IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)|DE|Stellt eine Enumeration über einen Satz von Code kontexten dar.|  
  
##  <a name="CoreServer"></a> Kern\-Server  
 Diese Schnittstellen stellen den Computer an, auf dem ein Programm gedebuggt wird.  Diese werden implementiert, über [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] kann jedoch in Modulen Debuggen von aufgerufen werden.  
  
|Schnittstelle|Vorbei implementiert|Beschreibung|  
|-------------------|--------------------------|------------------|  
|[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)|GEGEN|Stellt Zugriff auf die Ports und Anschlusslieferanten sowie Informationen über den Computer bereit.|  
|[IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)|GEGEN|Stellt [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) dar, das Remotedebuggen unterstützt.|  
  
##  <a name="DebugEngines"></a> Debuggen von Modulen  
 Diese Schnittstellen stellen die Module und ihre zugeordneten Ereignisse dar.  
  
|Schnittstelle|Vorbei implementiert|Beschreibung|  
|-------------------|--------------------------|------------------|  
|[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)|DE|Stellt ein benutzerdefiniertes Debuggen Modul dar.|  
|[IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)|DE|Stellt ein benutzerdefiniertes Debuggen Modul dar, das Laden von Symbolen, JustMyCode und Ausnahmen unterstützt.|  
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|Gesendet durch jede neue Instanz DEs, um es ist angegeben, werden von Debuggen zu behandeln.|  
|[IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)|DE|Stellt ein benutzerdefiniertes Modul dar, das Debuggen starten programme unterstützt.|  
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|PS, DE|Stellt einen Knoten dar, der Programmierung von Modulen, die mehrere behandelt.|  
|[IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)|DE|Stellt eine Methode bereit, mit denen das SDM eine Schnittstelle zum Debuggen von Modul aus einem Thread, einem Programm oder einem Stapelrahmen abgerufen wird.|  
  
##  <a name="Documents"></a> Dokumente  
 Diese Schnittstellen stellen Dokumente \(Quelldateien\) und die zugehörigen Elemente dar.  
  
|Schnittstelle|Vorbei implementiert|Beschreibung|  
|-------------------|--------------------------|------------------|  
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|Gesendet von DE, um ein Dokument geöffnet werden soll.|  
|[IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)|DE|Stellt einen Stream von disassemblierten Anweisungen aus einem Dokument dar.|  
|[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)|GEGEN, DE|Stellt ein Dokument dar, das von DE angegeben wird, und gibt den Namen und die Klassen\-ID \(CLSID\).|  
|[IDebugDocumentChecksum2](../../../extensibility/debugger/reference/idebugdocumentchecksum2.md)|EE, DE|Stellt eine Prüfsumme für eine Debug\- Dokument dar und ermöglicht die Übergabe der Prüfsumme zwischen Komponenten.|  
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|GEGEN, DE|Stellt einen Dokumentenkontext, eine Position in einem Dokument entsprechend einem bestimmten Anweisungen und Code Elementkontext dar.|  
|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|GEGEN, DE|Stellt eine allgemeine Position in einem Dokument dar.|  
|[IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)|GEGEN|Stellt eine Position in einer Quelldatei als Zeichenoffset dar.|  
|[IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)|GEGEN, DE|Stellt ein Textdokument dar, das von DE angegeben ist \(abgeleitet von [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)\) und gibt den tatsächlichen Text an.|  
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|Gesendet von DE, um Änderungen in einer Quelldatei anzugeben, die im Arbeitsspeicher ist.|  
  
##  <a name="Events"></a> Ereignisse  
 Diese Schnittstellen stellen alle Ereignisse dar, die zwischen Debug\- und dem DE Manager der Sitzung \(SDM\) gesendet werden.  
  
|Schnittstelle|Vorbei implementiert|Beschreibung|  
|-------------------|--------------------------|------------------|  
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|Gesendet von DE, um ein Dokument geöffnet werden soll.|  
|[IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md)|DE|Das Debugmodul \(DE\) sendet diese Schnittstelle zum Debuggen von Manager der Sitzung \(SDM\), um die Auslastung Symbol während der für eine Statusleiste festzulegen.|  
|[IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)|DE|Gesendet von DE, wenn eine Unterbrechung im Programm abgeschlossen wurde.|  
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|Gesendet von DE, wenn ein Haltepunkt gebunden ist.|  
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|Gesendet von DE, wenn ein Haltepunkt gebunden werden kann.|  
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|Gesendet von DE, wenn ein Haltepunkt erreicht wird.|  
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|Gesendet von DE, wenn ein Haltepunkt ungebunden ist.|  
|[IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)|DE|Gesendet von DE, um zu bestimmen, ob es an einer bestimmten Stelle aufhören soll.|  
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|Gesendet von DE, um Änderungen in einer Quelldatei anzugeben, die im Arbeitsspeicher ist.|  
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|Gesendet durch jede neue Instanz DEs, um es ist angegeben, werden von Debuggen zu behandeln.|  
|[IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)|DE|Gesendet von DE anzugeben ist, um das Programm, das gedebuggt wird, die erste Anweisung auszuführen.|  
|[IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)|DE|Eine Schnittstelle, die von anderen Ereignisschnittstellen zurückgäben verwendet wird, die möglicherweise einen Fehler, eine lesbare Fehlermeldungen bereitstellen.|  
|[IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)|PS, DE|Basisschnittstelle, von der alle anderen Ereignisschnittstellen abgeleitet sind.|  
|[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)|GEGEN|Stellt eine Schnittstelle dar, die vom SDM implementiert wird, auf dem die Ereignisse \(ausgedrückt als Objekte, die eine bestimmte Ereignisschnittstelle implementiert\) gesendet werden.|  
|[IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)|DE|Gesendet von DE, wenn eine Ausnahme aufgetreten ist im Programm, das gedebuggt wird.|  
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|Gesendet von DE, wenn eine asynchrone Ausdrucksauswertung abgeschlossen ist.|  
|IDebugFindSymbolEvent2||VERALTET.  NOT TUN USE.|  
|[IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|DE|Gesendet von DE, wenn die Verarbeitung für eine abgefangene Ausnahme abgeschlossen wurde.|  
|[IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|DE|Gesendet von DE, wenn ein Programm Ladevorgang abgeschlossen hat.|  
|[IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)|DE|Gesendet von DE, um die IDE\-Anzeige eine Informationsmeldung an den Benutzer haben.|  
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|Gesendet von DE, wenn ein Modul geladen oder entladen wird.|  
|[IDebugNoSymbolsEvent2](../../../extensibility/debugger/reference/idebugnosymbolsevent2.md)|DE|Signalisiert den [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Debugger Benutzeroberfläche, um den Benutzer zu warnen, dass keine Symbole für die gestartete ausführbare Datei befinden können.|  
|[IDebugOutputStringEvent2](../../../extensibility/debugger/reference/idebugoutputstringevent2.md)|DE|Gesendet von DE, um die IDE\-Anzeige eine beliebige Zeichenfolge sein.|  
|[IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)|GEGEN, DE|Gesendet von Ereignissen Port, um einen Port zu einem Listener zu übermitteln.|  
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|PS, DE|Gesendet von DE oder den Port, wenn ein Prozess erstellt wurde.|  
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|PS, DE|Gesendet von DE oder den Port, wenn ein Vorgang zerstört wurde.|  
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|PS, DE|Gesendet von DE oder den Port, wenn ein Programm erstellt wurde.|  
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|PS, DE|Gesendet von DE oder den Port, wenn ein Programm zerstört wurde.|  
|[IDebugProgramDestroyEventFlags2](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2.md)|DE|Aktiviert eine Debug\- Modul, das Standardverhalten des [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Benutzeroberfläche zu überschreiben, wenn Sie eine Debugsitzung beenden.|  
|[IDebugProgramNameChangedEvent2](../../../extensibility/debugger/reference/idebugprogramnamechangedevent2.md)|DE|Gesendet vom Modul \(Debuggen\) für die DE Debuggen Manager der Sitzung \(SDM\), wenn der Name eines Programms geändert wird.|  
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|Gesendet von DE, wenn eine neue Eigenschaft \(dargestellt durch die `IDebugProperty2`\-Schnittstelle\) erstellt wurde.|  
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|Gesendet von DE, wenn eine Eigenschaft zerstört wurde.|  
|[IDebugReturnValueEvent2](../../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|DE|Gesendet von DE, wenn die schrittweise Ausführung oder über den Rückgabewert einer Funktion heraus deshalb richtig angezeigt werden kann.|  
|[IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)|GEGEN|Aktiviert Debuggen von Modulen, um metrische Einstellungen remote zu lesen.|  
|[IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|DE|Gesendet von DE, wenn ein Schritt, über eine Anweisung oder ein Paket abgeschlossen wurde.|  
|[IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|DE|Gesendet von DE, um den Erfolg oder Fehler der Symbole für ein Modul geladen wird.|  
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|Gesendet von DE, wenn ein Thread erstellt wurde.|  
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|Gesendet von DE, wenn ein Thread zerstört wurde.|  
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|Gesendet von DE, wenn ein Thread seinen Namen geändert hat.|  
  
##  <a name="Expressions"></a> Ausdrücke  
 Diese Schnittstellen stellen die in einem bestimmten Kontext dar, der Ausdrücke ausgewertet werden soll.  
  
|Schnittstelle|Vorbei implementiert|Beschreibung|  
|-------------------|--------------------------|------------------|  
|[IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)|DE|Stellt einen Ausdruck dar, der ausgewertet werden soll.  Abrufen von der [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)\-Schnittstelle.|  
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|Stellt einen Kontext dar, in dem ein Ausdruck ausgewertet wird.  Abrufen von der [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)\-Schnittstelle.|  
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|Gesendet von DE, wenn eine asynchrone Ausdrucksauswertung abgeschlossen ist.|  
  
##  <a name="Memory"></a> Arbeitsspeicher  
 Diese Schnittstellen stellen Bytefolgen im Arbeitsspeicher dar.  
  
|Schnittstelle|Vorbei implementiert|Beschreibung|  
|-------------------|--------------------------|------------------|  
|[IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)|DE|Stellt eine Folge von Bytes im Speicher dar, aus dem gelesen bzw. geschrieben werden kann.|  
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|Stellt einen Speicherort für das Gedenken an eine Bytefolge dar.|  
  
##  <a name="Modules"></a> Module  
 Diese Schnittstellen stellen ein Modul dar, das in eine ausführbare Datei oder DLL entspricht.  
  
|Schnittstelle|Vorbei implementiert|Beschreibung|  
|-------------------|--------------------------|------------------|  
|[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)|DE|Stellt eine einzelne ausführbare Datei oder DLL dar.|  
|[IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)|DE|Stellt [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) dar, die Symbole unterstützt.|  
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|Gesendet von DE, wenn ein Modul geladen oder entladen wird.|  
|[IDebugSourceServerModule](../../../extensibility/debugger/reference/idebugsourceservermodule.md)|DE|Der Quellserver Stellt die Informationen dar, die in einer PDB\-Datei enthalten ist.|  
|[IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)|DE|Stellt eine Enumeration über einen Satz von Modulen dar, die von [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)bekannt ist.|  
  
##  <a name="Ports"></a> Ports  
 Diese Schnittstellen stellen Ports und Anschlusslieferanten dar.  
  
|Schnittstelle|Vorbei implementiert|Beschreibung|  
|-------------------|--------------------------|------------------|  
|[IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)|PS, GEGEN|Stellt den standardmäßigen Anschluss auf dem lokalen Computer dar.|  
|[IDebugFirewallConfigurationCallback2](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2.md)|GEGEN|Aktiviert eine Debug\- Modul DCOM verwendet wird, um das [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Benutzeroberfläche zu bitten, um sicherzustellen, dass die Firewall das Remotedebuggen nicht blockiert.|  
|[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)|PS, GEGEN|Stellt einen Anschluss dar.|  
|[IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)|PS|Gesendet von Ereignissen Port, um einen Port zu einem Listener zu übermitteln.|  
|[IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)|PS|Stellt einen Anschluss dar, der gestartet und Prozesse beenden kann.|  
|[IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)|PS|Wird verwendet, um Programme mit einem Anschluss registrieren bzw. deren Registrierung aufheben kann. erlaubt den Port an den Titel programmen, die momentan gedebuggt werden.|  
|[IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)|PS|Stellt eine benutzerdefinierte Benutzeroberfläche zum Auswählen des Ports dar.|  
|[IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)|GEGEN|Stellt eine Anforderung dar, die einen Port, aus dem ein neuer Port erstellt und gespeichert wird.|  
|[IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)|PS|Stellt einen Lieferanten von Ports dar.|  
|[IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)|PS|Stellt einen Lieferanten von Ports dar, die auf dem Datenträger speichern \(\) Informationen über die Ports beibehalten können, die sie erstellt hat.|  
|[IDebugPortSupplierDescription2](../../../extensibility/debugger/reference/idebugportsupplierdescription2.md)|PS|Aktiviert das [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Benutzeroberfläche, um Text innerhalb des **ÜbertragungsinformationenAn den Prozess anhängen**\-Abschnitt des Dialogfelds angezeigt.|  
|[IDebugWindowsComputerPort2](../../../extensibility/debugger/reference/idebugwindowscomputerport2.md)|GEGEN|Behält die Abfragen Informationen über den Zielcomputer.|  
|[IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)|PS, GEGEN|Stellt eine Enumeration über einen Satz von Ports dar.|  
|[IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)|GEGEN|Stellt eine Enumeration zu einem Satz Anschlusslieferanten dar.|  
  
##  <a name="Processes"></a> Prozesse  
 Diese Schnittstellen stellen Prozesse, eine einzelne ausführbare Datei dar, die eine oder mehrere Programme enthält.  
  
|Schnittstelle|Vorbei implementiert|Beschreibung|  
|-------------------|--------------------------|------------------|  
|[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)|PS, DE|Stellt einen Prozess dar, der auf einem Computer ausgeführt wird.|  
|[IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)|PS, DE|Stellt einen Prozess dar, der aktiv das Debuggen unterstützt \(verwendet, um Schritt zu ersetzen, Methoden der Schnittstelle [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) fortzusetzen und auszuführen\).|  
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|PS, DE|Gesendet von DE oder den Port, wenn ein Prozess erstellt wurde.|  
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|PS, DE|Gesendet von DE oder den Port, wenn ein Vorgang zerstört wurde.|  
|[IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)|PS|Stellt einen Prozess dar, der nachverfolgt werden muss, welche Sitzung an das Objekt angefügt ist.|  
|[IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)|PS|Stellt eine Enumeration eines Satzes von Prozessen auf einen Anschluss dar.|  
  
##  <a name="Programs"></a> Programme  
 Diese Schnittstellen stellen Programme, logische Gruppierungen der Ausführung dar, die nicht unbedingt zu einer physischen ausführbaren Datei oder ein Modul entsprechen.  
  
|Schnittstelle|Vorbei implementiert|Beschreibung|  
|-------------------|--------------------------|------------------|  
|[IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)|DE|Stellt [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) dar, das in Übereinstimmung mit anderen Programmen bearbeitet werden muss, die gleichzeitig gedebuggt werden.|  
|[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)|PS, DE|Stellt eine logische Gruppierung der Ausführung dar.|  
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|PS, DE|Gesendet von DE oder den Port, wenn ein Programm erstellt wurde.|  
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|PS, DE|Gesendet von DE oder den Port, wenn ein Programm zerstört wurde.|  
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|PS, DE|Stellt [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) dar, das von Debugsymbolinformationen für mehrere Module behandelt werden kann.|  
|[IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)|PS|Stellt [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) dar, das erforderlich ist, um nachzuverfolgen, welche Sitzung an das Objekt angefügt ist.|  
|[IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)|PS, DE|Stellt [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) dar, das Informationen über den Vorgang kann, in dem es ausgeführt wird.|  
|[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)|PS, DE|Stellt ein Programm, das gedebuggt werden kann.|  
|[IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)|PS, DE|Ermöglicht es einem von einem Versuch Knoten Programm benachrichtigt zu werden, wenn der zugeordneten Programm anzufügen.|  
|[IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)|DE|Stellt eine Methode bereit, um das Programm zu DE SDM abfragt, die von diesem DE gesteuert werden.|  
|[IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)|GEGEN|Wird von DES, um Programme mit dem SDM zu registrieren, um werden sie anzuzeigen.|  
|[IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)|PS, DE|Stellt [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) dar, das Schnittstellen über Thread marshallen kann oder Grenzen verarbeitet.|  
|[IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)|PS, DE|Stellt eine Enumeration eines Satzes von Programmen dar.|  
  
##  <a name="Properties"></a> Eigenschaften  
 Diese Schnittstellen stellen Eigenschaften, einen Wert dar, der einem bestimmten Kontext, in der Regel das Ergebnis von einer Ausdrucksauswertung zugeordnet ist.  
  
|Schnittstelle|Vorbei implementiert|Beschreibung|  
|-------------------|--------------------------|------------------|  
|[IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)|EE|Stellt [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) dar, das seinen Wert auf eine benutzerdefinierte Weise anzeigen kann.|  
|[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)|DE|Erstellt einen Wert eines Stapelrahmens, eines Dokuments oder des Ergebnisses einer Ausdrucksauswertung dar.|  
|[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)|DE|Stellt [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) dar, das willkürlich langer Zeichenfolgen unterstützt.|  
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|Gesendet von DE, wenn eine neue Eigenschaft \(dargestellt durch die [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)\-Schnittstelle\) erstellt wurde.|  
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|Gesendet von DE, wenn eine Eigenschaft zerstört wurde.|  
|[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)|DE|Stellt einen Verweis auf eine Eigenschaft dar, die außerhalb eines bestimmten Stapelrahmens vorhanden sein kann.|  
|[IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)|DE|Stellt eine Enumeration zu einem Satz [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) Strukturen dar, die Variablen, Register, Parameter und Ausdrücke beschrieben werden.|  
|[IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)|DE|Stellt eine Enumeration zu einem Satz [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) Strukturen dar.|  
  
##  <a name="StackFrames"></a> Stapelrahmen  
 Diese Schnittstellen stellen einen Stapelrahmen, einen Kontext dar, in dem ein Haltepunkt oder eine Ausnahme aufgetreten ist.  
  
|Schnittstelle|Vorbei implementiert|Beschreibung|  
|-------------------|--------------------------|------------------|  
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|Stellt einen Kontext dar, in dem ein Haltepunkt oder eine Ausnahme aufgetreten ist.|  
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|Stellt [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) dar, die abgefangene Ausnahmen behandeln kann.|  
|[IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)|DE|Stellt eine Enumeration zu dem Satz von [CODE\_PATH](../../../extensibility/debugger/reference/code-path.md) Strukturen Funktionsaufruf dar, die die Zeichenfolge angeben, die verwendet wird, um zu einem bestimmten Stapelrahmen abzurufen.|  
|[IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)|DE|Stellt eine Enumeration zu einem Satz [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) Strukturen dar, die Stapelrahmen beschreiben.|  
  
##  <a name="Threads"></a> Threads  
 Diese Schnittstellen stellen Threads und die zugehörigen Ereignisse dar.  
  
|Schnittstelle|Vorbei implementiert|Beschreibung|  
|-------------------|--------------------------|------------------|  
|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|DE|Stellt einen Ausführungsthread dar.|  
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|Gesendet von DE, wenn ein Thread erstellt wurde.|  
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|Gesendet von DE, wenn ein Thread zerstört wurde.|  
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|Gesendet von DE, wenn ein Thread seinen Namen geändert hat.|  
|[IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)|DE|Stellt eine Enumeration über einen Satz von Threads dar.|  
  
##  <a name="TypeVisualizers"></a> Typ\-Schnellansichten  
 Diese Schnittstellen bieten Unterstützung für den Typ schnellansichten.  Diese Schnittstellen werden in der Regel von einer Ausdrucksauswertung implementiert.  
  
|Schnittstelle|Vorbei implementiert|Beschreibung|  
|-------------------|--------------------------|------------------|  
|[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)|EE|Stellt ein dar schnellansicht Typ einer Bytearray dargestellt werden soll.|  
|[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)|EE|Stellt Methoden zum Abrufen des Zugriffs auf die zu einer Typ schnellansicht Daten übergeben werden sollen.|  
|[IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)|EE|Stellt eine Eigenschaft dar, die Zugriff auf [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) Implementierungen bietet.|  
  
## Siehe auch  
 [API\-Referenz](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)   
 [Erstellen einer benutzerdefinierten Debugmodul](../../../extensibility/debugger/creating-a-custom-debug-engine.md)