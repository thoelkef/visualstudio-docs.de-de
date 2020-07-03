---
title: Übersicht über das Debuggen mit Active Script | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Active Script Debugging overview
ms.assetid: ce4ec768-d017-4dfa-a7e3-cced3a29e679
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0181ee305c99a1d0af1d3e1e965c6ac8fe16f375
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835666"
---
# <a name="active-script-debugging-overview"></a>Debuggen mit Active Script - Übersicht
Die Schnittstellen zum Debuggen mit Active Script ermöglichen ein sprachneutrales, hostneutrales Debuggen und unterstützen eine Vielzahl von Entwicklungsumgebungen.  
  
 ![Script Host-Prozess](../winscript/media/scp56activdbgarchgif.gif "Scp56ActivDbgArchgif")  
Abbildung 1  
  
 Eine sprachneutrale Debugumgebung kann alle Programmiersprachen oder eine Kombination aus Programmiersprachen unterstützen, ohne dass bestimmte Kenntnisse einer dieser Sprachen erforderlich sind. Zudem unterstützt die Debugumgebung sprachübergreifendes Stepping sowie sprachübergreifende Haltepunkte. (Hauptschwerpunkt dieser Übersicht ist die Unterstützung von Skriptsprachen, wie z.B. VBScript und [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].)  
  
 Ein hostneutraler Debugger kann automatisch mit einem beliebigen Active Scripting-Host verwendet werden, z.B. Internet Explorer oder einem benutzerdefinierten Host. Der Host steuert, was dem Benutzer vom Debugger angezeigt wird: angefangen bei der Struktur des Dokuments bis hin zu den Inhalten und Syntaxfarben der Debugdokumente. Dadurch kann der debuggte Quellcode im Kontext des Hostdokuments angezeigt werden. Internet Explorer kann beispielsweise ein Skript auf einer HTML-Seite anzeigen.  
  
 In den folgenden Unterabschnitten werden die einzelnen Schlüsselkomponenten in Active Debugging und die zugehörigen Schnittstellen erläutert. Bevor Sie fortfahren, müssen jedoch einige Active Debugging-Schlüsselkonzepte definiert werden:  
  
 **Hostanwendung**  
 Die Anwendung, die die Skript-Engines hostet und eine skriptfähige Reihe von Objekten (oder „Objektmodellen“) bereitstellt.  
  
 **Sprach-Engine**  
 Eine Komponente, die Analyse-, Ausführungs- und Debugabstraktionen für eine bestimmte Sprache bereitstellt.  
  
 **Debugger-IDE**  
 Die Anwendung, die die Debugging-Benutzeroberfläche durch die Kommunikation mit der Hostanwendung und Sprach-Engines bereitstellt.  
  
 **Computerbasierter Debug-Manager** Eine Komponente, die eine Registrierung von debugfähigen Anwendungsprozessen verwaltet.  
  
 **Process Debug Manager**  
 Eine Komponente, die die Struktur von debugfähigen Dokumenten für eine bestimmte Anwendung verwaltet, die ausgeführten Threads nachverfolgt usw.  
  
 **Dokument Kontext**  
 Ein Dokumentenkontext ist eine Abstraktion, die einen bestimmten Bereich im Quellcode eines Hostdokuments darstellt.  
  
 **Code Kontext**  
 Ein Codekontext stellt eine bestimmte Position im ausgeführten Code einer Sprach-Engine dar (einen „virtuellen Anweisungszeiger“) dar.  
  
 **Ausdruckskontext**  
 Ein bestimmter Kontext (z.B. ein Stapelrahmen), in dem Ausdrücke von einer Sprach-Engine ausgewertet werden können.  
  
 **Objektkatalog**  
 Eine strukturierte, sprachunabhängige Darstellung von Name, Typ, Wert und Unterobjekten eines Objekts, die für die Implementierung einer „Überwachungsfenster“-Benutzeroberfläche geeignet ist.  
  
 Es folgt eine Übersicht über alle Active Debugging-Schlüsselkomponenten und entsprechenden, zugeordneten Schnittstellen, gefolgt von den Details zu diesen Schnittstellen.  
  
## <a name="language-engine"></a>Sprach-Engine  
 Die Sprach-Engine bietet:  
  
- Sprachanalyse und -ausführung.  
  
- Debugunterstützung (Haltepunkte usw.).  
  
- Ausdrucksauswertung.  
  
- Syntaxfarben.  
  
- Objektkatalog.  
  
- Stapelenumeration und -analyse.  
  
  Im Folgenden werden die Schnittstellen aufgeführt, die eine Skript-Engine für die Bereitstellung von Debuggen, Ausdrucksauswertung und Objektkatalog benötigt. Die Hostanwendung verwendet diese Schnittstellen für die Zuordnung zwischen dem zugehörigen Dokumentkontext und den Codekontexten der Engine. Die Debugger-Benutzeroberfläche verwendet sie für die Ausdrucksauswertung, die Stapelenumeration und den Objektkatalog.  
  
  [IActiveScriptDebug-Schnittstelle](../winscript/reference/iactivescriptdebug-interface.md)  
  Stellt Syntaxfarben und Codekontextenumeration bereit.  
  
  [IActiveScriptErrorDebug-Schnittstelle](../winscript/reference/iactivescripterrordebug-interface.md)  
  Gibt Dokumentkontexte und Stapelrahmen für Fehler zurück.  
  
  [IActiveScriptSiteDebug-Schnittstelle](../winscript/reference/iactivescriptsitedebug-interface.md)  
  Vom Host über die Skript-Engine für den Debugger bereitgestellter Link.  
  
  [IDebugCodeContext-Schnittstelle](../winscript/reference/idebugcodecontext-interface.md)  
  Stellt in einem Thread einen virtuellen „Anweisungszeiger“ bereit.  
  
  [IEnumDebugCodeContexts-Schnittstelle](../winscript/reference/ienumdebugcodecontexts-interface.md)  
  Führt die Codekontexte auf, die einem Dokumentenkontext entsprechen.  
  
  [IDebugStackFrame-Schnittstelle](../winscript/reference/idebugstackframe-interface.md)  
  Stellt einen logischen Stapelrahmen im Threadstapel dar.  
  
  [IDebugExpressionContext-Schnittstelle](../winscript/reference/idebugexpressioncontext-interface.md)  
  Stellt Kontext bereit, in dem Ausdrücke ausgewertet werden können.  
  
  [IDebugStackFrameSniffer-Schnittstelle](../winscript/reference/idebugstackframesniffer-interface.md)  
  Bietet eine Möglichkeit zum Aufführen logischer Stapelrahmen.  
  
  [IDebugExpression-Schnittstelle](../winscript/reference/idebugexpression-interface.md)  
  Stellt einen asynchron ausgewerteten Ausdruck dar.  
  
  [IDebugSyncOperation-Schnittstelle](../winscript/reference/idebugsyncoperation-interface.md)  
  Ermöglicht einer Skript-Engine die Abstraktion eines Vorgangs, der ausgeführt werden muss, während er in einen bestimmten blockierten Thread eingebettet ist.  
  
  [IDebugAsyncOperation-Schnittstelle](../winscript/reference/idebugasyncoperation-interface.md)  
  Bietet asynchronen Zugriff auf einen synchronen Debugvorgang.  
  
  [IDebugAsyncOperationCallBack-Schnittstelle](../winscript/reference/idebugasyncoperationcallback-interface.md)  
  Stellt Statusereignisse im Zusammenhang mit der Bearbeitung einer `IDebugAsyncOperation`-Schnittstellenauswertung bereit.  
  
  [IEnumDebugExpressionContexts-Schnittstelle](../winscript/reference/ienumdebugexpressioncontexts-interface.md)  
  Zählt eine Sammlung von `IDebugExpressionContexts`-Objekten auf.  
  
  [IProvideExpressionContexts-Schnittstelle](../winscript/reference/iprovideexpressioncontexts-interface.md)  
  Bietet eine Möglichkeit zum Aufzählen von Ausdruckskontexten, die von einer bestimmten Komponente bekannt sind.  
  
  [IDebugFormatter-Schnittstelle](../winscript/reference/idebugformatter-interface.md)  
  Ermöglicht, dass eine Sprache oder IDE den Wechsel zwischen VARIANT-Werten oder VARTYPE-Typen und -Zeichenfolgen anpasst.  
  
  [IDebugStackFrameSnifferEx-Schnittstelle](../winscript/reference/idebugstackframesnifferex-interface.md)  
  Zählt die logischen Stapelrahmen für das PDM auf.  
  
## <a name="hosts"></a>Hosts  
 Der Host:  
  
- Hostet die Sprach-Engines.  
  
- Stellt ein Objektmodell (eine Reihe von Objekten, für die Skripts erstellt werden können) bereit.  
  
- Definiert eine debugfähige Dokumentstruktur und die zugehörigen Inhalte.  
  
- Organisiert Skripts in virtuellen Anwendungen.  
  
  Es gibt zwei Hosttypen:  
  
- Ein Dumbhost unterstützt nur die Active Scripting-Hauptschnittstellen. Er hat keine Kontrolle über die Dokumentstruktur oder Organisationen; dies wird komplett von den in den Sprach-Engines bereitgestellten Skripts bestimmt.  
  
- Ein Smarthost unterstützt eine größere Reihe von Schnittstellen. Dies ermöglicht die Definition von Dokumentstruktur, Dokumentinhalten und Syntaxfarben. Es gibt eine Reihe von Hilfsschnittstellen, durch die es für einen Host viel einfacher ist, ein Smarthost zu sein. Auf diese Hilfsschnittstellen wird im nächsten Unterabschnitt eingegangen.  
  
### <a name="smart-host-helper-interfaces"></a>Smarthost-Hilfsschnittstellen  
 Die `IDebugDocumentHelper`-Methoden stellen deutlich vereinfachte Schnittstellen bereit, durch deren Verwendung ein Host die Vorteile von Smarthosting nutzen kann, ohne mit der vollständigen Komplexität (und Stärke) der vollständigen Hostschnittstellen umgehen zu müssen.  
  
 Für die Verwendung dieser Schnittstellen ist selbstverständlich kein Host erforderlich. Durch die Verwendung dieser Schnittstellen kann jedoch vermieden werden, dass eine Reihe von noch komplizierteren Schnittstellen implementiert oder verwendet wird.  
  
 [IDebugDocumentHelper-Schnittstelle](../winscript/reference/idebugdocumenthelper-interface.md)  
 Wird vom PDM implementiert und stellt Implementierungen für viele Schnittstellen bereit, die für das Smarthosting erforderlich sind.  
  
 [IDebugDocumentHost-Schnittstelle](../winscript/reference/idebugdocumenthost-interface.md)  
 Wird (optional) vom Host implementiert, um für den Debugger hostspezifische Funktionen verfügbar zu machen, wie z.B. Syntaxfarben.  
  
 Weitere Informationen finden Sie unter [Implementing Smart Host Helper Interfaces](../winscript/implementing-smart-host-helper-interfaces.md) (Implementieren von Smarthost-Hilfsschnittstellen).  
  
### <a name="full-smart-host-interfaces"></a>Vollständige Smarthost-Schnittstellen  
 Nachfolgend finden Sie alle Schnittstellen, die ein Smarthost implementieren oder verwenden muss, wenn er die Hilfsschnittstellen nicht verwendet.  
  
 Vom Host implementierte Schnittstellen:  
  
 [IDebugDocumentInfo-Schnittstelle](../winscript/reference/idebugdocumentinfo-interface.md)  
 Stellt Informationen zu einem Dokument bereit, das möglicherweise instanziiert wird.  
  
 [IDebugDocumentProvider-Schnittstelle](../winscript/reference/idebugdocumentprovider-interface.md)  
 Bietet die Möglichkeit zum Instanziieren eines Dokuments nach Bedarf.  
  
 [IDebugDocument-Schnittstelle](../winscript/reference/idebugdocument-interface.md)  
 Die Basisschnittstelle für alle Debugdokumente.  
  
 [IDebugDocumentText-Schnittstelle](../winscript/reference/idebugdocumenttext-interface.md)  
 Bietet Zugriff auf eine reine Textversion des Debugdokuments.  
  
 [IDebugDocumentTextAuthor-Schnittstelle](../winscript/reference/idebugdocumenttextauthor-interface.md)  
 Ermöglicht die Bearbeitung der reinen Textversion des Debugdokuments.  
  
 [IDebugDocumentContext-Schnittstelle](../winscript/reference/idebugdocumentcontext-interface.md)  
 Stellt eine abstrakte Darstellung eines Teils des Debugdokuments dar.  
  
 Für den Host vom PDM implementierte Schnittstellen:  
  
 [IDebugApplicationNode-Schnittstelle](../winscript/reference/idebugapplicationnode-interface.md)  
 Erweitert die Funktionalität der `IDebugDocumentProvider`-Schnittstelle durch die Bereitstellung eines Kontexts innerhalb einer Projektstruktur.  
  
## <a name="debugger-ide"></a>Debugger-IDE  
 Die IDE ist eine sprachunabhängige Debugging-Benutzeroberfläche. Die Lösung umfasst Folgendes:  
  
- Dokumentviewer/-editoren.  
  
- Haltepunktverwaltung.  
  
- Fenster für die Ausdrucksauswertung und Überwachungen.  
  
- Stapelrahmen-Browsing.  
  
- Objekt-/Klassenbrowsing.  
  
- Browsing der virtuellen Anwendungsstruktur.  
  
  Alle vom Debugger implementierten Schnittstellen:  
  
  [IApplicationDebugger-Schnittstelle](../winscript/reference/iapplicationdebugger-interface.md)  
  Die primäre Schnittstelle, die von einer Debugger-IDE-Sitzung verfügbar gemacht wird.  
  
  [IApplicationDebuggerUI-Schnittstelle](../winscript/reference/iapplicationdebuggerui-interface.md)  
  Gibt einer externen Komponente mehr Kontrolle über die Benutzeroberfläche des Debuggers.  
  
  [IDebugExpressionCallBack-Schnittstelle](../winscript/reference/idebugexpressioncallback-interface.md)  
  Stellt Statusereignisse für den Auswertungsfortschritt der `IDebugExpression`-Schnittstelle bereit.  
  
  [IDebugDocumentTextEvents-Schnittstelle](../winscript/reference/idebugdocumenttextevents-interface.md)  
  Stellt Ereignisse bereit, die auf Änderungen am zugehörigen Textdokument hinweisen.  
  
  [IDebugApplicationNodeEvents-Schnittstelle](../winscript/reference/idebugapplicationnodeevents-interface.md)  
  Stellt die Ereignisschnittstelle für die `IDebugApplicationNode`-Schnittstelle bereit.  
  
### <a name="machine-debug-manager"></a>Computerbasierter Debug-Manager  
 Der computerbasierte Debug-Manager stellt den Einbindungspunkt zwischen virtuellen Anwendungen und Debuggern bereit, indem eine Liste der aktiven virtuellen Anwendungen verwaltet und aufgezählt wird.  
  
 [IDebugSessionProvider-Schnittstelle](../winscript/reference/idebugsessionprovider-interface.md)  
 Richtet eine Debugsitzung für eine ausgeführte Anwendung ein.  
  
 [IMachineDebugManager-Schnittstelle](../winscript/reference/imachinedebugmanager-interface.md)  
 Die primäre Schnittstelle für den computerbasierten Debug-Manager.  
  
 [IMachineDebugManagerCookie-Schnittstelle](../winscript/reference/imachinedebugmanagercookie-interface.md)  
 Diese Schnittstelle ähnelt der `IMachineDebugManager`-Schnittstelle, unterstützt jedoch Debug-Cookies.  
  
 [IMachineDebugManagerEvents-Schnittstelle](../winscript/reference/imachinedebugmanagerevents-interface.md)  
 Signaländerungen in der ausgeführten Anwendungsliste, die vom computerbasierten Debug-Manager verwaltet werden.  
  
 [IEnumRemoteDebugApplications-Schnittstelle](../winscript/reference/ienumremotedebugapplications-interface.md)  
 Zählt die ausgeführten Anwendungen auf einem Computer auf.  
  
### <a name="process-debug-manager"></a>Prozessbasierter Debug-Manager  
 Der PDM führt folgende Aufgaben durch:  
  
- Er synchronisiert das Debuggen mehrerer Sprach-Engines.  
  
- Er verwaltet eine Struktur mit debugfähigen Dokumenten.  
  
- Er führt Stapelrahmen zusammen.  
  
- Er koordiniert Sprach-Engine-übergreifend Haltepunkte und Stepping.  
  
- Er verfolgt Threads.  
  
- Er verwaltet einen Debugthread für die asynchrone Verarbeitung.  
  
- Er kommuniziert mit dem computerbasierten Debug-Manager und der Debugger-IDE.  
  
  Im Folgenden werden die vom prozessbasierten Debug-Manager bereitgestellten Schnittstellen aufgeführt.  
  
  [IProcessDebugManager-Schnittstelle](../winscript/reference/iprocessdebugmanager-interface.md)  
  Die primäre Schnittstelle für den prozessbasierten Debug-Manager. Diese Schnittstelle kann eine virtuelle Anwendung aus einem Prozess erstellen, hinzufügen oder entfernen.  
  
  [IRemoteDebugApplication-Schnittstelle](../winscript/reference/iremotedebugapplication-interface.md)  
  Stellt eine ausgeführte Anwendung dar.  
  
  [IDebugApplication-Schnittstelle](../winscript/reference/idebugapplication-interface.md)  
  Macht nicht remotefähige Debugmethoden für die Verwendung durch Sprach-Engines und Hosts verfügbar.  
  
  [IRemoteDebugApplicationThread-Schnittstelle](../winscript/reference/iremotedebugapplicationthread-interface.md)  
  Stellt einen Ausführungsthread innerhalb einer bestimmten Anwendung dar.  
  
  [IDebugApplicationThread-Schnittstelle](../winscript/reference/idebugapplicationthread-interface.md)  
  Ermöglicht Sprach-Engines und Hosts, eine Threadsynchronisierung zu bieten und threadspezifische Informationen im Debugstatus zu verwalten.  
  
  [IEnumRemoteDebugApplicationThreads-Schnittstelle](../winscript/reference/ienumremotedebugapplicationthreads-interface.md)  
  Zählt die ausgeführten Threads in einer Anwendung auf.  
  
  [IDebugThreadCall-Schnittstelle](../winscript/reference/idebugthreadcall-interface.md)  
  Sendet gemarshallte Aufrufe.  
  
  [IDebugApplicationNode-Schnittstelle](../winscript/reference/idebugapplicationnode-interface.md)  
  Verwaltet eine Position für ein Dokument in der Hierarchie.  
  
  [IEnumDebugApplicationNodes-Schnittstelle](../winscript/reference/ienumdebugapplicationnodes-interface.md)  
  Zählt die untergeordneten Knoten eines Knotens auf, der einer Anwendung zugeordnet ist.  
  
  [IEnumDebugStackFrames-Schnittstelle](../winscript/reference/ienumdebugstackframes-interface.md)  
  Zählt die einem Thread entsprechenden Stapelrahmen auf, die durch die Engines zusammengeführt wurden.  
  
  [IDebugCookie-Schnittstelle](../winscript/reference/idebugcookie-interface.md)  
  Ermöglicht eine Festlegung des Debug-Cookies in Skriptdebuggern.  
  
  [IDebugHelper-Schnittstelle](../winscript/reference/idebughelper-interface.md)  
  Dient als Factory für Objektkataloge und einfacher Verbindungspunkt für Skript-Engines.  
  
  [ISimpleConnectionPoint-Schnittstelle](../winscript/reference/isimpleconnectionpoint-interface.md)  
  Bietet eine einfache Möglichkeit zum Beschreiben und Aufzählen der Ereignisse, die an einem bestimmten Verbindungspunkt für Skript-Engines ausgelöst werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Active Script-Debuggerschnittstellen](../winscript/reference/active-script-debugger-interfaces.md)
