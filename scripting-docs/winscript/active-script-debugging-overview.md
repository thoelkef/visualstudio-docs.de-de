---
title: "Debuggen mit Active Script - &#220;bersicht | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Debuggen mit Active Script - Übersicht"
ms.assetid: ce4ec768-d017-4dfa-a7e3-cced3a29e679
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Debuggen mit Active Script - &#220;bersicht
Die Active Script\-Debugschnittstellen ermöglichen sprachunabhängiges, hostneutrales Debuggen und unterstützen eine Vielzahl der Entwicklungsumgebung.  
  
 ![Script Host&#45;Prozess](../winscript/media/scp56activdbgarchgif.png "Scp56ActivDbgArchgif")  
Abbildung 1  
  
 Eine sprachneutrale Debugumgebung kann jede Programmiersprache oder Mischung von Programmiersprachen, ohne bestimmtes Kenntnisse der keiner dieser Sprachen verfügen unterstützen.  Die Debugumgebung unterstützt auch das sprachübergreifende schrittweise Ausführung und die Haltepunkte.  \(Diese Übersicht konzentriert sich hauptsächlich auf Stützskriptsprachen, wie VBScript und [!INCLUDE[javascript](../includes/javascript-md.md)].\)  
  
 Ein hostneutraler Debugger kann mit jedem Active Scripting\-Host, wie Internet Explorer oder einem benutzerdefinierten Host automatisch verwendet werden.  Die Hoststeuerelemente, was der Debugger dem Benutzer, der Struktur der Dokumentstruktur dem Inhalt und der Syntaxfarbe der Debug\- Dokumente darstellt.  Dies ermöglicht dem debuggten im Kontext des Dokuments angezeigt werden, Quellcode.  Beispielsweise kann ein Skript in Internet Explorer einer HTML\-Seite anzeigen.  
  
 In den folgenden Unterabschnitten werden, jede Schlüsselkomponente im aktiven Debuggen und die zugeordneten Schnittstellen erläutert.  jedoch bevor sie weiter fortfahren, verschlüsseln mehrere aktive Debuggingskonzepte muss definiert werden:  
  
 Hostanwendung  
 Die Anwendung, die die Skriptmodule hostet und einen Satz von \- Objekten skriptfähigen bereitstellt \(oder "Objektmodell"\).  
  
 Sprachmodul  
 Eine Komponente, die Analyse, Ausführung und Debuggingsabstraktionen für eine bestimmte Sprache bereitstellt.  
  
 Debugger IDE  
 Die Anwendung, die das Debuggen von Benutzeroberfläche vom Kommunizieren mit der Hostanwendung und den Sprachmodulen bereitstellt.  
  
 Debuggen Manager des Computers  
 Eine Komponente, die eine Registrierung von debugfähigen Anwendungsprozessen beibehält.  
  
 Debuggen Manager des Prozesses  
 Eine Komponente, die die Struktur von debugfähigen Dokumenten für eine bestimmte Anwendung verwaltete, erfasst die aktiven Threads, u. a.  
  
 Dokumentenkontext  
 Ein Dokumentenkontext ist eine Abstraktion, die einen bestimmten Bereich im Quellcode des Dokuments darstellt.  
  
 Codekontext  
 Ein Codekontext stellt einen bestimmten Speicherort im ausgeführten Code eines Sprachmoduls dar \("virtueller Anweisungszeiger".\)  
  
 Ausdruckskontext  
 Ein bestimmter Kontext \(beispielsweise ein Stapelrahmen\), in dem Ausdrücke möglicherweise durch ein Sprachmodul ausgewertet werden.  
  
 Objektdurchsuchen  
 Eine strukturierte, sprach\- Darstellung eines Namens des Objekts, ein Typ, ein Wert und Unterobjekte, geeignet für das Implementieren eines "Überwachungsfensters" Benutzeroberfläche.  
  
 Im Folgenden finden Sie eine Übersicht der einzelnen aktiven Debuggingsschlüsselkomponenten und \-c$entsprechens, die zugeordneten Schnittstellen, gefolgt von den Details dieser Schnittstellen.  
  
## Sprachmodul  
 Das Sprachmodul stellt die bereit:  
  
-   Sprachenanalyse und \-ausführung.  
  
-   Debugunterstützung \(Haltepunkte usw.\).  
  
-   Ausdrucksauswertung.  
  
-   Syntaxfarbe.  
  
-   Objektdurchsuchen.  
  
-   Stapelenumeration und \-Analyse.  
  
 Im Folgenden sind die Schnittstellen, die ein Skriptmodul unterstützen muss, um das Debuggen, Ausdrucksauswertung und das Objektdurchsuchen bereitzustellen.  Diese Schnittstellen werden von der Hostanwendung, zwischen dem Dokumentenkontext und den Codekontexten des Moduls, und durch den Debugger Benutzeroberfläche zuzuordnen Ausdrucksauswertung, Stapelenumeration und das Objektdurchsuchen auch Zweck verwendet.  
  
 [IActiveScriptDebug\-Schnittstelle](../winscript/reference/iactivescriptdebug-interface.md)  
 Stellt Syntaxfarben\- und Codekontextenumeration bereit.  
  
 [IActiveScriptErrorDebug\-Schnittstelle](../winscript/reference/iactivescripterrordebug-interface.md)  
 EINGABETASTEdokumentenkontexte und \-Stapelrahmen für Fehler.  
  
 [IActiveScriptSiteDebug\-Schnittstelle](../winscript/reference/iactivescriptsitedebug-interface.md)  
 Host zur Verfügung gestellter Link von Skriptmodul zu Debugger.  
  
 [IDebugCodeContext\-Schnittstelle](../winscript/reference/idebugcodecontext-interface.md)  
 Stellt einen virtuellen "Anweisungszeiger" in einem Thread bereit.  
  
 [IEnumDebugCodeContexts\-Schnittstelle](../winscript/reference/ienumdebugcodecontexts-interface.md)  
 Listet die Codekontexte auf, die einem Dokumentenkontext entsprechen.  
  
 [IDebugStackFrame\-Schnittstelle](../winscript/reference/idebugstackframe-interface.md)  
 Stellt einen logischen Stapelrahmen im Threadstapel dar.  
  
 [IDebugExpressionContext\-Schnittstelle](../winscript/reference/idebugexpressioncontext-interface.md)  
 Stellt Kontext bereit, in dem Ausdrücke ausgewertet werden können.  
  
 [IDebugStackFrameSniffer\-Schnittstelle](../winscript/reference/idebugstackframesniffer-interface.md)  
 Bietet eine Möglichkeit, logische Stapelrahmen aufzulisten.  
  
 [IDebugExpression\-Schnittstelle](../winscript/reference/idebugexpression-interface.md)  
 Stellt einen asynchron ausgewerteten Ausdruck dar.  
  
 [IDebugSyncOperation\-Schnittstelle](../winscript/reference/idebugsyncoperation-interface.md)  
 Ermöglicht einem Skriptmodul, eine Operation zu extrahieren, der ausgeführt werden muss, während er in einer bestimmten geschachtelt ist, blockierte Thread.  
  
 [IDebugAsyncOperation\-Schnittstelle](../winscript/reference/idebugasyncoperation-interface.md)  
 Bietet asynchronen Zugriff auf einen synchronen Debugvorgang.  
  
 [IDebugAsyncOperationCallBack\-Schnittstelle](../winscript/reference/idebugasyncoperationcallback-interface.md)  
 Stellt die Statusereignisse bereit, die den Status einer `IDebugAsyncOperation`\-Schnittstellenauswertung verknüpft sind.  
  
 [IEnumDebugExpressionContexts\-Schnittstelle](../winscript/reference/ienumdebugexpressioncontexts-interface.md)  
 Listet eine Auflistung `IDebugExpressionContexts`\-Objekte auf.  
  
 [IProvideExpressionContexts\-Schnittstelle](../winscript/reference/iprovideexpressioncontexts-interface.md)  
 Stellt eine Methode bereit, die Ausdruckskontexte aufzulisten, die von einer bestimmten Komponente bezeichnet werden.  
  
 [IDebugFormatter\-Schnittstelle](../winscript/reference/idebugformatter-interface.md)  
 Ermöglicht einer Sprache oder ein IDE, um die Konvertierung zwischen VARIANTEN Werten oder VARTYPE\-Typen und Zeichenfolgen anzupassen.  
  
 [IDebugStackFrameSnifferEx\-Schnittstelle](../winscript/reference/idebugstackframesnifferex-interface.md)  
 Listet die logischen Stapelrahmen für das PDM auf.  
  
## Host  
 Der Host:  
  
-   Hostet die Sprachmodule.  
  
-   Stellt ein Objektmodell bereit \(Satz von Objekten, die erstellt werden können\).  
  
-   Definiert eine Struktur von Dokumenten, die gedebuggt werden können und deren Inhalt.  
  
-   Organisiert Skripts in virtuelle Anwendungen.  
  
 Es gibt zwei Arten von Hosts:  
  
-   Ein stummer Host unterstützt nur die grundlegenden Active Scripting\-Schnittstellen.  Sie verfügt über kein Steuerelement über Elementstruktur oder Organisationen; Dies wird vollständig durch die Skripts bestimmt, die den \- Sprachmodulen bereitgestellt werden.  
  
-   Ein Smarthost unterstützt einen umfangreicheren Satz von Schnittstellen, der zulässig, um die Dokumentstruktur, den Dokumentinhalt beziehen und die Syntaxfarbe zu definieren.  Es gibt eine Reihe von Hilfeschnittstellen beschrieben, im folgenden Unterabschnitt, die es Ihnen erleichtern, damit ein Host ein Smarthost ist.  
  
### Smarthost\-Hilfe\-Schnittstellen  
 Die `IDebugDocumentHelper`\-Methoden stellen einen groß vereinfachten Satz von Schnittstellen, die ein Host verwenden kann, um die Vorteile des SmartHostings zu erhalten, ohne die volle Komplexität \(und Leistungsfähigkeit\) der vollständigen Hostschnittstellen zu behandeln.  
  
 Ein Host ist nicht erforderlich, diese Schnittstellen zu verwenden, benötigen.  Unter Verwendung dieser Schnittstellen kann mehrere, schwierigere Schnittstellen zu implementieren oder zu verwenden.  
  
 [IDebugDocumentHelper\-Schnittstelle](../winscript/reference/idebugdocumenthelper-interface.md)  
 Wird von PDM und stellt die Implementierungen für viele Schnittstellen bereit, die für intelligente Hosting erforderlich sind.  
  
 [IDebugDocumentHost\-Schnittstelle](../winscript/reference/idebugdocumenthost-interface.md)  
 Implementiert \(optional\) durch den Host, um hostspezifische Funktionen, wie Syntaxfarbe, dem Debugger verfügbar zu machen.  
  
 Weitere Informationen finden Sie unter [Implementieren von Smart Host\-Hilfsprogrammschnittstellen](../winscript/implementing-smart-host-helper-interfaces.md).  
  
### Vollständige Smarthost\-Schnittstellen  
 Es folgt der gesamte Satz von Schnittstellen, die ein Smarthost implementieren oder verwenden muss, wenn er nicht die Hilfeschnittstellen verwendet.  
  
 Schnittstellen implementiert vom Host:  
  
 [IDebugDocumentInfo\-Schnittstelle](../winscript/reference/idebugdocumentinfo-interface.md)  
 Enthält Informationen zu einem Dokument bereit, das möglicherweise instanziiert wird.  
  
 [IDebugDocumentProvider\-Schnittstelle](../winscript/reference/idebugdocumentprovider-interface.md)  
 Stellt eine Möglichkeit für ein Dokument bei Bedarf instanziieren bereit.  
  
 [IDebugDocument\-Schnittstelle](../winscript/reference/idebugdocument-interface.md)  
 Alle Basisschnittstelle für Dokumente debuggen.  
  
 [IDebugDocumentText\-Schnittstelle](../winscript/reference/idebugdocumenttext-interface.md)  
 Bietet Zugriff auf einer nur für Text Debug\- Version des Dokuments.  
  
 [IDebugDocumentTextAuthor\-Schnittstelle](../winscript/reference/idebugdocumenttextauthor-interface.md)  
 Ermöglicht das Bearbeiten der nur für Text Debug\- Version des Dokuments.  
  
 [IDebugDocumentContext\-Schnittstelle](../winscript/reference/idebugdocumentcontext-interface.md)  
 Stellt eine abstrakte Darstellung eines Teils des Dokuments bereit, das gedebuggt wird.  
  
 Schnittstellen implementiert wird PDM im Namen des Hosts:  
  
 [IDebugApplicationNode\-Schnittstelle](../winscript/reference/idebugapplicationnode-interface.md)  
 Erweitert die Funktionen der `IDebugDocumentProvider`\-Schnittstelle durch Bereitstellen eines Kontexts innerhalb einer Projektstruktur.  
  
## Debugger IDE  
 Die IDE ist ein sprachneutrales debuggendes Benutzeroberfläche.  Es stellt die bereit:  
  
-   Dokumentanzeigen\/Editoren.  
  
-   Haltepunktverwaltung.  
  
-   Ausdrucksauswertung und Überwachungsfenster.  
  
-   Stapelrahmendurchsuchen.  
  
-   \-\/Klassendurchsuchen.  
  
-   Durchsuchen der virtuellen Anwendungsstruktur.  
  
 Schnittstellen implementiert vom Debugger:  
  
 [IApplicationDebugger\-Schnittstelle](../winscript/reference/iapplicationdebugger-interface.md)  
 Die primäre Schnittstelle verfügbar gemacht aus einer Sitzung des Debuggers IDE.  
  
 [IApplicationDebuggerUI\-Schnittstelle](../winscript/reference/iapplicationdebuggerui-interface.md)  
 Gibt eine externe Komponente mehr Kontrolle über die Benutzeroberfläche des Debuggers.  
  
 [IDebugExpressionCallBack\-Schnittstelle](../winscript/reference/idebugexpressioncallback-interface.md)  
 Stellt Statusereignisse für `IDebugExpression` Auswertungsstatus bereit.  
  
 [IDebugDocumentTextEvents\-Schnittstelle](../winscript/reference/idebugdocumenttextevents-interface.md)  
 Stellt die Ereignisse bereit, die Änderungen am zugeordneten Textdokument angeben.  
  
 [IDebugApplicationNodeEvents\-Schnittstelle](../winscript/reference/idebugapplicationnodeevents-interface.md)  
 Stellt die Ereignisschnittstelle für die `IDebugApplicationNode`\-Schnittstelle bereit.  
  
### Machine Manager Debug  
 Der Computername Debug\- Manager stellt den Anschlusspunkt zwischen virtuellen Anwendungen und Debuggern vom Führen und vom Auflisten einer Liste der aktiven virtuellen Anwendungen bereit.  
  
 [IDebugSessionProvider\-Schnittstelle](../winscript/reference/idebugsessionprovider-interface.md)  
 Richtet eine Debugsitzung für eine laufende Anwendung ein.  
  
 [IMachineDebugManager\-Schnittstelle](../winscript/reference/imachinedebugmanager-interface.md)  
 Die primäre Schnittstelle zum Computer Debug\- Manager.  
  
 [IMachineDebugManagerCookie\-Schnittstelle](../winscript/reference/imachinedebugmanagercookie-interface.md)  
 Wie die `IMachineDebugManager`\-Schnittstelle, jedoch auf diese Schnittstelle unterstützt Debug\- Cookies.  
  
 [IMachineDebugManagerEvents\-Schnittstelle](../winscript/reference/imachinedebugmanagerevents-interface.md)  
 Signaländerungen in der Liste der laufenden Anwendung, die von ausgeführt wird, bearbeiten Debug\- Manager Computer.  
  
 [IEnumRemoteDebugApplications\-Schnittstelle](../winscript/reference/ienumremotedebugapplications-interface.md)  
 Listet die ausgeführten Anwendungen auf einem Computer auf.  
  
### Prozessdebug\-Manager  
 Das PDM bewirkt Folgendes:  
  
-   Synchronisiert das Debuggen mehrerer Sprachmodulen.  
  
-   Verwendet eine Struktur von debugfähigen Dokumenten bei.  
  
-   Führt Stapelrahmen zusammen.  
  
-   Koordinatenhaltepunkte und Springen über Sprachmodule.  
  
-   Titelthreads.  
  
-   Verwendet einen Debuggerthread für asynchrone Verarbeitung bei.  
  
-   Verständigt sich mit dem Computer Debug\- Manager und dem Debugger IDE.  
  
 Im Folgenden werden die Schnittstellen, die von bereitgestellt werden, verarbeiten Debug\- Manager.  
  
 [IProcessDebugManager\-Schnittstelle](../winscript/reference/iprocessdebugmanager-interface.md)  
 Primäre Schnittstelle Debug ProzessManager.  Diese Schnittstelle kann eine virtuelle Anwendung von einem Prozess erstellen, hinzufügen oder entfernen.  
  
 [IRemoteDebugApplication\-Schnittstelle](../winscript/reference/iremotedebugapplication-interface.md)  
 Stellt eine laufende Anwendung dar.  
  
 [IDebugApplication\-Schnittstelle](../winscript/reference/idebugapplication-interface.md)  
 Macht nicht remotefähig Debugmethoden für Sprachmodule und Hosts verfügbar.  
  
 [IRemoteDebugApplicationThread\-Schnittstelle](../winscript/reference/iremotedebugapplicationthread-interface.md)  
 Stellt einen Ausführungsthread innerhalb einer bestimmten Anwendung dar.  
  
 [IDebugApplicationThread\-Schnittstelle](../winscript/reference/idebugapplicationthread-interface.md)  
 Ermöglicht Sprachmodule und Hosts, die Threadsynchronisierung bereitzustellen und Threadbesonderen, DEBUGZustandsinformationen beizubehalten.  
  
 [IEnumRemoteDebugApplicationThreads\-Schnittstelle](../winscript/reference/ienumremotedebugapplicationthreads-interface.md)  
 Listet die aktiven Threads in einer Anwendung.  
  
 [IDebugThreadCall\-Schnittstelle](../winscript/reference/idebugthreadcall-interface.md)  
 Dispatches gemarshallte Aufrufe.  
  
 [IDebugApplicationNode\-Schnittstelle](../winscript/reference/idebugapplicationnode-interface.md)  
 Verwendet eine Position für ein Dokument in der Hierarchie beibehalten.  
  
 [IEnumDebugApplicationNodes\-Schnittstelle](../winscript/reference/ienumdebugapplicationnodes-interface.md)  
 Listet untergeordnete Knoten eines Knotens auf, der mit einer Anwendung zugeordnet ist.  
  
 [IEnumDebugStackFrames\-Schnittstelle](../winscript/reference/ienumdebugstackframes-interface.md)  
 Listet die Stapelrahmen entsprechend einem Thread auf, zusammengeführt von Modulen.  
  
 [IDebugCookie\-Schnittstelle](../winscript/reference/idebugcookie-interface.md)  
 Ermöglicht das Debuggen in den Skriptdebuggern festgelegt werden Cookie.  
  
 [IDebugHelper\-Schnittstelle](../winscript/reference/idebughelper-interface.md)  
 Dient als Factory für Objektkataloge und einfache Verbindungspunkte für Skriptmodule.  
  
 [ISimpleConnectionPoint\-Schnittstelle](../winscript/reference/isimpleconnectionpoint-interface.md)  
 Stellt eine einfache Möglichkeit zum Beschreiben und Auflisten der Ereignisse bereit, die auf einem bestimmten Verbindungspunkt, für Skriptmodule ausgelöst werden.  
  
## Siehe auch  
 [Active Script\-Debuggerschnittstellen](../winscript/reference/active-script-debugger-interfaces.md)