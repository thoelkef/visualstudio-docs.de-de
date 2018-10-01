---
title: Core-Schnittstellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], core interfaces
ms.assetid: 666b9116-8550-4bdd-bc15-55fc57de87df
caps.latest.revision: 25
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2223059344c8f3d15eb94edc0dc2d2d1dc6fa336
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47516227"
---
# <a name="core-interfaces"></a>Wichtige Schnittstellen
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Kernschnittstellen](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/core-interfaces).  
  
Die folgenden Schnittstellen sind die Core-Schnittstellen für die Erweiterung des Debuggers mit den [!INCLUDE[vsipsdk](../../../includes/vsipsdk-md.md)].  
  
## <a name="discussion"></a>Diskussion  
 Diese Schnittstellen werden in erster Linie verwendet, um die Debug-Engine (DE) zu erstellen. Sie sind hier nach Kategorien organisiert:  
  
-   [Breakpoints](#Breakpoints)  
  
-   [Kontext](#Contexts)  
  
-   [Core-Server](#CoreServer)  
  
-   [Debug-Engines](#DebugEngines)  
  
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
  
 Die Entitäten, die die Schnittstellen implementieren können, sind:  
  
-   Debug-Engine (DE)  
  
-   Anschlusslieferant (PS)  
  
-   Ausdrucksauswertung (EE)  
  
-   Visual Studio (VS)  
  
##  <a name="Breakpoints"></a> Haltepunkte  
 Diese Schnittstellen beziehen sich auf die Implementierung und die nachverfolgung von Haltepunkten.  
  
|Interface|Implementiert von|Beschreibung|  
|---------------|--------------------|-----------------|  
|[IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)|DE|Stellt einen Haltepunkt an einer Speicheradresse gebunden.|  
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|Von der DE gesendet, wenn Sie ein Haltepunkt an einer Speicheradresse gebunden ist.|  
|[IDebugBreakpointChecksumRequest2](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2.md)|VS|Stellt eine Dokument-Prüfsumme für eine Haltepunkt-Anforderung dar.|  
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|Von die DE gesendet, wenn Sie ein Haltepunkt an einem Speicherort gebunden werden kann.|  
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|Von der DE gesendet, wenn ein Haltepunkt erreicht wird.|  
|[IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)|VS|Stellt eine Anforderung für einen Haltepunkt dar. Beim Erstellen eines ausstehenden Haltepunkts verwendet.|  
|[IDebugBreakpointRequest3](../../../extensibility/debugger/reference/idebugbreakpointrequest3.md)|VS|Stellt eine Anforderung für einen Haltepunkt dar. Beim Erstellen eines ausstehenden Haltepunkts verwendet.|  
|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|DE|Stellt die Informationen verwendet, um einen Haltepunkt zu binden.|  
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|Von der DE gesendet, wenn Sie ein Haltepunkt aus einer Speicheradresse aufgehoben wird.|  
|[IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)|DE|Stellt einen ungültigen Breakpoint (zurückgegeben von `IDebugBreakpointErrorEvent2`).|  
|[IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)|DE|Stellt die Auflösung von Informationen über einen ungültigen Breakpoint.|  
|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|DE|Stellt eine Position in einer Funktion, in denen ein Haltepunkt gesetzt ist.|  
|[IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)|DE|Stellt einen Haltepunkt an, der gebunden werden soll; Erstellen einen gebundenen Haltepunkt verwendet.|  
|[IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)|DE|Stellt eine Enumeration dar, über einen Satz von gebundener Haltepunkte.|  
|[IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)|DE|Stellt eine Enumeration dar, über einen Satz von Breakpoints, die auf einen Speicherbereich konnte nicht gebunden werden.|  
  
##  <a name="Contexts"></a> Kontexte  
 Diese Schnittstellen stellen verschiedene Arten von Kontexten, in das derzeit debuggte Programm dar.  
  
|Interface|Implementiert von|Beschreibung|  
|---------------|--------------------|-----------------|  
|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|DE|Die Anfangsposition einer Code-Anweisung darstellt.|  
|[IDebugCodeContext3](../../../extensibility/debugger/reference/idebugcodecontext3.md)|DE|Erweitert die [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) Schnittstelle für den Abruf von Modul und die Prozess-Schnittstellen zu aktivieren.|  
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VISUAL STUDIO, DE|Stellt eine Position in einem Dokument dar.|  
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|Stellt den Kontext in der zum Auswerten eines Ausdrucks dar.|  
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|Stellt die Anfangsposition im Arbeitsspeicher, der eine Sammlung von Bytes an.|  
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|Stellt einen Stack-Frame-Kontext an einem Haltepunkt oder die Ausnahme dar.|  
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|Stellt einen Stack-Frame-Kontext an einem Haltepunkt oder die Ausnahme dar.|  
|[IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)|DE|Stellt eine Enumeration über einen Satz von Codekontexte dar.|  
  
##  <a name="CoreServer"></a> Core-Server  
 Diese Schnittstellen stellen dar, den Computer, auf dem ein Programm im Debugmodus befindet. Diese implementiert werden, indem [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] jedoch von Debug-Engines in aufgerufen werden kann.  
  
|Interface|Implementiert von|Beschreibung|  
|---------------|--------------------|-----------------|  
|[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)|VS|Bietet Zugriff auf die Ports und Portanbieter sowie Informationen über den Computer.|  
|[IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)|VS|Stellt eine [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) , unterstützt das Remotedebuggen.|  
  
##  <a name="DebugEngines"></a> Debug-Engines  
 Diese Schnittstellen stellen die Debug-Engines und deren zugeordneten Ereignissen dar.  
  
|Interface|Implementiert von|Beschreibung|  
|---------------|--------------------|-----------------|  
|[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)|DE|Stellt eine benutzerdefinierten Debug-Engine dar.|  
|[IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)|DE|Stellt eine benutzerdefinierten Debug-Engine, die Laden von Symbolen, JustMyCode und Ausnahmen unterstützt.|  
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|Durch jede neue Instanz des DE gesendet, um anzugeben, dass sie Debugaufgaben behandelt werden kann.|  
|[IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)|DE|Stellt eine benutzerdefinierten Debug-Engine, die beim Starten Programme unterstützt.|  
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE, PS|Stellt einen Programm-Knoten, der mehrere Debug-Engines behandelt.|  
|[IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)|DE|Bietet eine Möglichkeit, das SDM beim Abrufen einer Schnittstelle für die Debug-Engine von einem Thread, Programme oder Stapelrahmen entspricht.|  
  
##  <a name="Documents"></a> Dokumente  
 Diese Schnittstellen stellen Dokumente (Quelldateien) und den zugeordneten Elementen dar.  
  
|Interface|Implementiert von|Beschreibung|  
|---------------|--------------------|-----------------|  
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|Gesendet durch die DE um fordern ein Dokument geöffnet werden.|  
|[IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)|DE|Stellt einen Stream von disassemblierten Anweisungen aus einem Dokument dar.|  
|[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)|VISUAL STUDIO, DE|Stellt ein Dokument vom DE, einen Namen und eine Klasse-ID (CLSID) angeben.|  
|[IDebugDocumentChecksum2](../../../extensibility/debugger/reference/idebugdocumentchecksum2.md)|DE, EE|Stellt eine Prüfsumme für eine Debug-Dokument und ermöglicht die Prüfsumme zwischen Komponenten übergeben.|  
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VISUAL STUDIO, DE|Stellt einen Dokumentkontext, eine Position in einem Dokument, einem bestimmten Kontext der Anweisung und der Code entspricht.|  
|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|VISUAL STUDIO, DE|Stellt eine allgemeine Position in einem Dokument dar.|  
|[IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)|VS|Stellt eine Position in einer Quelldatei als ein Zeichenoffset dar.|  
|[IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)|VISUAL STUDIO, DE|Stellt ein Textdokument, die von der DE bereitgestellt (abgeleitet [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)), den tatsächlichen Text bereitstellt.|  
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|Durch die DE gesendet, Änderungen an einer Quelldatei an, die im Arbeitsspeicher befindet.|  
  
##  <a name="Events"></a> Ereignisse  
 Diese Schnittstellen darstellen, alle Ereignisse, die zwischen dem DE und sitzungsbasierter Debug-Manager (SDM) gesendet werden.  
  
|Interface|Implementiert von|Beschreibung|  
|---------------|--------------------|-----------------|  
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|Gesendet durch die DE um fordern ein Dokument geöffnet werden.|  
|[IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md)|DE|Die Debug-Engine (DE) sendet diese Schnittstelle für die Sitzung Debug-Manager (SDM), um den Status festzulegen Leiste Nachricht während des Symbols lädt.|  
|[IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)|DE|Von der DE gesendet, wenn eine Unterbrechung in der Anwendung abgeschlossen wurde.|  
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|Von der DE gesendet, wenn ein Haltepunkt gebunden ist.|  
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|Von der DE gesendet, wenn ein Haltepunkt nicht gebunden werden.|  
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|Von der DE gesendet, wenn ein Haltepunkt erreicht wird.|  
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|Von der DE gesendet, wenn ein Haltepunkt aufgehoben wird.|  
|[IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)|DE|Durch die DE gesendet, um festzustellen, ob er an einem bestimmten Standort beendet werden sollte.|  
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|Durch die DE gesendet, Änderungen an einer Quelldatei an, die im Arbeitsspeicher befindet.|  
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|Durch jede neue Instanz des DE gesendet, um anzugeben, dass sie Debugaufgaben behandelt werden kann.|  
|[IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)|DE|Durch die DE gesendet, um anzugeben, dass die zu debuggende Programm wird die erste Anweisung ausgeführt wird.|  
|[IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)|DE|Eine Schnittstelle, die durch andere Ereignisschnittstellen, die einen Fehler zurückgeben können, verwendet wird, um lesbare Fehlermeldungen bereitzustellen.|  
|[IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)|DE, PS|Die Basisschnittstelle, von der alle anderen Ereignis Schnittstellen abgeleitet werden.|  
|[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)|VS|Stellt eine Schnittstelle implementiert, die durch die SDM an die Ereignisse, die (in Form von Objekten, die eine bestimmtes Ereignis-Schnittstelle implementiert) gesendet werden.|  
|[IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)|DE|Von der DE gesendet, wenn in der zu debuggende Programm wird eine Ausnahme aufgetreten ist.|  
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|Von der DE gesendet, wenn eine asynchrone ausdrucksauswertung abgeschlossen ist.|  
|IDebugFindSymbolEvent2||VERALTET. VERWENDEN SIE NICHT.|  
|[IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|DE|Von der DE gesendet, wenn es sich bei der Verarbeitung für eine abgefangene Ausnahme abgeschlossen wurde.|  
|[IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|DE|Von der DE gesendet, wenn ein Programm Ladevorgang abgeschlossen wurde.|  
|[IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)|DE|Durch die DE, damit die IDE-Anzeige eine informative Meldung an den Benutzer gesendet.|  
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|Von der DE gesendet, wenn ein Modul geladen oder entladen wird.|  
|[IDebugNoSymbolsEvent2](../../../extensibility/debugger/reference/idebugnosymbolsevent2.md)|DE|Signalisiert dem [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] debugger-Benutzeroberfläche auf den Benutzer zu warnen, dass die Symbole für die gestartete ausführbare Datei nicht gefunden.|  
|[IDebugOutputStringEvent2](../../../extensibility/debugger/reference/idebugoutputstringevent2.md)|DE|Von der DE, damit die IDE-Anzeige eine beliebige Zeichenfolge gesendet.|  
|[IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)|VISUAL STUDIO, DE|Gesendet von einem Port portereignisse an alle Listener zu kommunizieren.|  
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|DE, PS|Vom DE oder Port gesendet, wenn ein Prozess erstellt wurde.|  
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|DE, PS|Vom DE oder Port gesendet, wenn ein Prozess zerstört wurde.|  
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|DE, PS|Vom DE oder Port gesendet, wenn ein Programm erstellt wurde.|  
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|DE, PS|Vom DE oder Port gesendet, wenn ein Programm zerstört wurde.|  
|[IDebugProgramDestroyEventFlags2](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2.md)|DE|Ermöglicht es eine Debug-Engine, um das Standardverhalten überschreiben die [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Benutzeroberfläche, wenn Sie eine Debugsitzung zu beenden.|  
|[IDebugProgramNameChangedEvent2](../../../extensibility/debugger/reference/idebugprogramnamechangedevent2.md)|DE|Gesendet von der Debug-Engine (DE) für die Sitzung Debug-Manager (SDM), wenn der Name eines Programms ändert.|  
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|Durch die DE, wenn eine neue Eigenschaft gesendet (dargestellt durch die `IDebugProperty2` Schnittstelle) erstellt wurde.|  
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|Von der DE gesendet, wenn eine Eigenschaft zerstört wurde.|  
|[IDebugReturnValueEvent2](../../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|DE|Von der DE gesendet, wenn es sich bei schrittweise aus oder über eine Funktion, sodass der Rückgabewert ordnungsgemäß angezeigt werden kann.|  
|[IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)|VS|Ermöglicht das debug-Engines zum Lesen von metrikeinstellungen Remote.|  
|[IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|DE|Von der DE gesendet, wenn ein Schritt in, überspringen oder aus einer Anweisung abgeschlossen wurde.|  
|[IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|DE|Durch die DE gesendet, um den Erfolg oder Fehler beim Laden von Symbolen für ein Modul anzugeben.|  
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|Von der DE gesendet, wenn ein Thread erstellt wurde.|  
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|Von der DE gesendet, wenn ein Thread zerstört wurde.|  
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|Von der DE gesendet, wenn ein Thread seinen Namen geändert wurde.|  
  
##  <a name="Expressions"></a> Ausdrücke  
 Diese Schnittstellen stellen dar, die Ausdrücke in einem bestimmten Kontext ausgewertet werden soll.  
  
|Interface|Implementiert von|Beschreibung|  
|---------------|--------------------|-----------------|  
|[IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)|DE|Stellt einen Ausdruck ausgewertet werden soll. Abgerufen aus der [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) Schnittstelle.|  
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|Stellt einen Kontext, in dem ein Ausdruck ausgewertet wird. Abgerufen aus der [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) Schnittstelle.|  
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|Von der DE gesendet, wenn eine asynchrone ausdrucksauswertung abgeschlossen ist.|  
  
##  <a name="Memory"></a> Arbeitsspeicher  
 Diese Schnittstellen stellen Sequenzen von Bytes im Arbeitsspeicher dar.  
  
|Interface|Implementiert von|Beschreibung|  
|---------------|--------------------|-----------------|  
|[IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)|DE|Stellt eine Sequenz von Bytes im Arbeitsspeicher, die aus gelesen oder geschrieben werden können.|  
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|Stellt einen Speicherort im Arbeitsspeicher einer Sequenz von Bytes an.|  
  
##  <a name="Modules"></a> Module  
 Diese Schnittstellen stellen dar, ein Modul, das in eine ausführbare Datei entspricht oder. DLL-Datei.  
  
|Interface|Implementiert von|Beschreibung|  
|---------------|--------------------|-----------------|  
|[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)|DE|Stellt eine einzelne ausführbare Datei oder DLL an.|  
|[IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)|DE|Stellt eine [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) , Symbole unterstützt.|  
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|Von der DE gesendet, wenn ein Modul geladen oder entladen wird.|  
|[IDebugSourceServerModule](../../../extensibility/debugger/reference/idebugsourceservermodule.md)|DE|Stellt die Source Server-Informationen, die in einer PDB-Datei enthalten ist.|  
|[IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)|DE|Stellt eine Enumeration dar, über einen Satz von Modulen, die bekannt sind ein [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md).|  
  
##  <a name="Ports"></a> Ports  
 Diese Schnittstellen werden die Ports und Portanbieter darstellen.  
  
|Interface|Implementiert von|Beschreibung|  
|---------------|--------------------|-----------------|  
|[IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)|VISUAL STUDIO, PS|Stellt den Standardport auf dem lokalen Computer.|  
|[IDebugFirewallConfigurationCallback2](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2.md)|VS|Ermöglicht es eine Debug-Engine, die DCOM verwendet wird, stellen die [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Benutzeroberfläche, um sicherzustellen, dass die Firewall das Remotedebugging nicht blockiert wird.|  
|[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)|VISUAL STUDIO, PS|Stellt einen Port an.|  
|[IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)|PS|Gesendet von einem Port portereignisse an alle Listener zu kommunizieren.|  
|[IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)|PS|Stellt einen Port, der starten und Beenden von Prozessen.|  
|[IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)|PS|Verwendet, um die an- und Abmelden von Programmen mit einem Port. können den Port zum Nachverfolgen der aktuell gedebuggten Programme ab.|  
|[IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)|PS|Stellt eine benutzerdefinierte Benutzeroberfläche für die Auswahl des Ports dar.|  
|[IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)|VS|Stellt eine Anforderung für einen Port aus dem ein neuer Port erstellt oder gespeichert werden.|  
|[IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)|PS|Stellt eine Anbieter von Ports dar.|  
|[IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)|PS|Stellt eine Anbieter von Ports, die beibehalten werden kann (auf Datenträger speichern) Informationen zu den Ports er erstellt.|  
|[IDebugPortSupplierDescription2](../../../extensibility/debugger/reference/idebugportsupplierdescription2.md)|PS|Ermöglicht die [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Benutzeroberfläche zum Anzeigen von Text in die **Transportinformationen** Teil der **an den Prozess anhängen** Dialogfeld.|  
|[IDebugWindowsComputerPort2](../../../extensibility/debugger/reference/idebugwindowscomputerport2.md)|VS|Ermöglicht das Abfragen von Informationen über den Zielcomputer.|  
|[IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)|VISUAL STUDIO, PS|Stellt eine Enumeration dar, über einen Satz von Ports.|  
|[IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)|VS|Stellt eine Enumeration über einen Satz von Portanbieter dar.|  
  
##  <a name="Processes"></a> Prozesse  
 Diese Schnittstellen darstellen, Prozesse, die eine einzelne ausführbare Datei, die ein oder mehrere Programme enthält.  
  
|Interface|Implementiert von|Beschreibung|  
|---------------|--------------------|-----------------|  
|[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)|PS, DE|Stellt einen Prozess, der auf einem Computer ausgeführt wird.|  
|[IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)|PS, DE|Stellt einen Prozess, der unterstützt Aktiv Debuggen (verwendet, um Schritt zu ersetzen, fortsetzen und Methoden für die [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) Schnittstelle).|  
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|DE, PS|Vom DE oder Port gesendet, wenn ein Prozess erstellt wurde.|  
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|DE, PS|Vom DE oder Port gesendet, wenn ein Prozess zerstört wurde.|  
|[IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)|PS|Stellt einen Prozess, der nachverfolgt werden muss, welche Sitzung verbunden ist.|  
|[IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)|PS|Stellt eine Enumeration von einer Reihe von Prozessen auf einem Port dar.|  
  
##  <a name="Programs"></a> Programme  
 Diese Schnittstellen darstellen, Programme, die logischen Einheiten der Ausführung, die nicht unbedingt eine physische ausführbare Datei oder dieses Moduls entsprechen.  
  
|Interface|Implementiert von|Beschreibung|  
|---------------|--------------------|-----------------|  
|[IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)|DE|Stellt eine [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , die zusammen mit anderen Programmen, die zur gleichen Zeit im Debugmodus befindlichen arbeiten muss.|  
|[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)|DE, PS|Stellt eine logische Einheit der Ausführung dar.|  
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|DE, PS|Vom DE oder Port gesendet, wenn ein Programm erstellt wurde.|  
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|DE, PS|Vom DE oder Port gesendet, wenn ein Programm zerstört wurde.|  
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE, PS|Stellt eine [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) , die verarbeitet werden können, indem mehrere Debug-Engines.|  
|[IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)|PS|Stellt eine [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , der Lage sein, nachzuverfolgen, welche Sitzung angefügt ist.|  
|[IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)|DE, PS|Stellt eine [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , die Informationen über den Prozess, in dem er ausgeführt wird, zurückgeben können.|  
|[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)|DE, PS|Stellt ein Programm, das debuggt werden kann.|  
|[IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)|DE, PS|Ermöglicht es einen Knoten Programm beim Anfügen an das zugeordnete Programm benachrichtigt werden sollen.|  
|[IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)|DE|Bietet eine Möglichkeit, das SDM zum Abfragen einer bereitgestellten Kompatibilitätsrichtlinie zu den Programmen, die von diesem DE gesteuert.|  
|[IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)|VS|Wird von DEs zum Registrieren von Programmen mit dem SDM angezeigt, dass sie gedebuggt werden.|  
|[IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)|DE, PS|Stellt eine [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) kann, die Schnittstellen Prozess oder Thread hinweg gemarshallt.|  
|[IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)|DE, PS|Stellt eine Enumeration, der ein Satz von Programmen an.|  
  
##  <a name="Properties"></a> Eigenschaften  
 Diese Schnittstellen stellen Eigenschaften ein Wert in einem bestimmten Kontext, in der Regel das Ergebnis der Auswertung eines Ausdrucks dar.  
  
|Interface|Implementiert von|Beschreibung|  
|---------------|--------------------|-----------------|  
|[IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)|EE|Stellt eine [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) seinen Wert auf benutzerdefinierte Weise anzeigen kann.|  
|[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)|DE|Stellt einen Wert, der einen Stapelrahmen, Dokument oder das Ergebnis der Auswertung eines Ausdrucks.|  
|[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)|DE|Stellt eine [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) , beliebig lange Zeichenfolgen unterstützt.|  
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|Durch die DE, wenn eine neue Eigenschaft gesendet (dargestellt durch die [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) Schnittstelle) erstellt wurde.|  
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|Von der DE gesendet, wenn eine Eigenschaft zerstört wurde.|  
|[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)|DE|Stellt einen Verweis auf eine Eigenschaft, die außerhalb der bestimmten Stapelrahmen vorhanden sein kann.|  
|[IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)|DE|Stellt eine Enumeration dar, über einen Satz von [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) Strukturen die Variablen, Register, Parameter und Ausdrücke zu beschreiben.|  
|[IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)|DE|Stellt eine Enumeration dar, über einen Satz von [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) Strukturen.|  
  
##  <a name="StackFrames"></a> Stapelrahmen  
 Diese Schnittstellen stellen einen Stapelrahmen, einen Kontext dar. in der ein Haltepunkt oder eine Ausnahme aufgetreten ist.  
  
|Interface|Implementiert von|Beschreibung|  
|---------------|--------------------|-----------------|  
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|Stellt einen Kontext dar, in denen ein Haltepunkt oder eine Ausnahme aufgetreten ist.|  
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|Stellt eine [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) die verarbeiten kann Ausnahmen abgefangen.|  
|[IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)|DE|Stellt eine Enumeration dar, über der Menge der [CODE_PATH](../../../extensibility/debugger/reference/code-path.md) Strukturen geben an, die Funktion Aufrufsequenz, die zum Erreichen eines bestimmten Stapelrahmens.|  
|[IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)|DE|Stellt eine Enumeration dar, über einen Satz von [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) -Strukturen, die Stapelrahmen zu beschreiben.|  
  
##  <a name="Threads"></a> Threads  
 Diese Schnittstellen darstellen, Threads und deren zugeordneten Ereignissen.  
  
|Interface|Implementiert von|Beschreibung|  
|---------------|--------------------|-----------------|  
|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|DE|Stellt einen Ausführungsthread dar.|  
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|Von der DE gesendet, wenn ein Thread erstellt wurde.|  
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|Von der DE gesendet, wenn ein Thread zerstört wurde.|  
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|Von der DE gesendet, wenn ein Thread seinen Namen geändert wurde.|  
|[IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)|DE|Stellt eine Enumeration über eine Reihe von Threads dar.|  
  
##  <a name="TypeVisualizers"></a> Typ-Schnellansichten  
 Diese Schnittstellen bieten Unterstützung für Typ-Schnellansichten. Diese Schnittstellen werden in der Regel von einer ausdrucksauswertung implementiert.  
  
|Interface|Implementiert von|Beschreibung|  
|---------------|--------------------|-----------------|  
|[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)|EE|Stellt ein Array von Bytes in eine visualisierungslösung Typ dargestellt werden.|  
|[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)|EE|Stellt Methoden für den Zugriff auf Daten in eine visualisierungslösung Typ übergeben werden.|  
|[IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)|EE|Stellt eine Eigenschaft für den Zugriff auf [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) Implementierungen.|  
  
## <a name="see-also"></a>Siehe auch  
 [API-Referenz](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)   
 [Erstellen einer benutzerdefinierten Debug-Engine](../../../extensibility/debugger/creating-a-custom-debug-engine.md)

