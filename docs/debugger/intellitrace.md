---
title: "Verwenden von IntelliTrace | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.historicaldebug.overview"
helpviewer_keywords: 
  - "debugger, (Siehe auch IntelliTrace [Visual Studio ALM])"
  - "Debugger, Verlauf der Ausführungsaufzeichnung"
  - "Debuggen, (Siehe auch IntelliTrace [Visual Studio ALM])"
  - "Debuggen, Verlauf der Ausführungsaufzeichnung"
  - "IntelliTrace"
  - "IntelliTrace [Visual Studio ALM]"
  - "IntelliTrace, Sammeln von Daten aus Test Manager"
  - "IntelliTrace, Debuggen nach einem Absturz"
  - "IntelliTrace, Debuggen von Anwendungen"
  - "Test-Manager, Debuggen mit IntelliTrace"
ms.assetid: 486bfec2-39bd-4d78-892a-42352128ee52
caps.latest.revision: 135
caps.handback.revision: 133
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Verwenden von IntelliTrace
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Durch die Verwendung von IntelliTrace zum Erfassen und Nachverfolgen Ihres Codeausführungsverlaufs können Sie beim Debuggen Ihrer Anwendung Zeit sparen.  Sie können leicht Fehler finden, da mit IntelliTrace Folgendes möglich ist:  
  
-   Aufzeichnen bestimmter Ereignisse  
  
     Sie können ähnlichen Code sowie im Fenster **Lokal** während der Debugger\-Ereignisse angezeigte Daten, und Funktionsaufrufinformationen überprüfen.  
  
-   Schwer nachstellbare oder während der Bereitstellung auftretende Fehler beim Debuggen  
  
 Sie können IntelliTrace in der Visual Studio Enterprise Edition verwenden\(jedoch nicht in der Professional oder Community Edition\).  
  
## Wie möchten Sie vorgehen?  
  
|||  
|-|-|  
|**Meine Anwendung mit IntelliTrace debuggen:**<br /><br /> -   Vergangene Ereignisse auflisten.<br />-   Aufrufinformationen mit vergangenen Ereignissen anzeigen.<br />-   Die IntelliTrace\-Sitzung speichern.<br />-   Die Daten steuern, die IntelliTrace erfasst.|-   [Exemplarische Vorgehensweise: Verwenden von IntelliTrace](../debugger/walkthrough-using-intellitrace.md)<br />     [IntelliTrace\-Features](../debugger/intellitrace-features.md)<br />-   [Konfigurieren von IntelliTrace zum Sammeln von Debuginformationen](http://msdn.microsoft.com/de-de/7657ecab-e07e-4b1b-872d-f05d966be37e)<br />-   [Verlaufsbezogenes Debugging](../debugger/historical-debugging.md)|  
|**Sammeln von IntelliTrace\-Daten während einer Testsitzung im Test Manager**|-   [Sammeln weiterer Diagnosedaten in manuellen Tests](/devops-test-docs/test/collect-more-diagnostic-data-in-manual-tests)|  
|**Erfassen IntelliTrace\-Daten aus bereitgestellten Anwendungen**|-   [Verwenden des eigenständigen IntelliTrace\-Collectors](../debugger/using-the-intellitrace-stand-alone-collector.md)|  
|**Starten Sie das Debuggen von einer IntelliTrace\-Protokolldatei \(ITRACE\-Datei\).**|-   [Debuggen einer App mithilfe gespeicherter IntelliTrace\-Daten](../debugger/using-saved-intellitrace-data.md)|  
  
##  <a name="IntelliTraceSupport"></a> Welche Anwendungen kann ich mit IntelliTrace debuggen?  
  
|||  
|-|-|  
|**Unterstützt**|-   Visual Basic\- und Visual C\#\-Anwendungen, die .NET Framework 2.0 oder höher verwenden.<br />     Sie können die meisten Anwendungen debuggen, einschließlich ASP.NET, Microsoft Azure, Windows Forms, WCF, WPF, Windows Workflow, SharePoint 2010, SharePoint 2013 und 64\-Bit\-Anwendungen.<br />     Weitere Informationen zum Debuggen von SharePoint\-Anwendungen mit IntelliTrace finden Sie unter [Exemplarische Vorgehensweise: Debuggen einer SharePoint\-Anwendung mithilfe von IntelliTrace](../Topic/Walkthrough:%20Debugging%20a%20SharePoint%20Application%20by%20Using%20IntelliTrace.md).<br />     Weitere Informationen zum Debuggen von Microsoft Azure\-Apps mit IntelliTrace finden Sie unter [Debuggen eines veröffentlichten Cloud\-Diensts mit IntelliTrace und Visual Studio](http://go.microsoft.com/fwlink/?LinkID=262248).|  
|**Eingeschränkte Unterstützung**|-   F\#\-Apps versuchsweise<br />-   Windows Store\-Apps nur für Ereignisse unterstützt|  
|**Nicht unterstützt**|-   C\+\+, andere Sprachen und Skript<br />-   Windows\-Dienste, Silverlight, Xbox oder [!INCLUDE[winmobile](../debugger/includes/winmobile_md.md)]\-Apps|  
  
> [!NOTE]
>  IntelliTrace kann nicht verwendet werden, um einen Prozess zu debuggen, der bereits ausgeführt wird.  Sie müssen IntelliTrace zu Beginn des Prozesses starten.  
  
##  <a name="IntelliTraceVSTraditional"></a> Warum sollte ich mit IntelliTrace debuggen?  
 Herkömmliche oder *Live*\-Debugvorgänge zeigen nur den aktuellen Status der Anwendung mit eingeschränkten Informationen zu vergangenen Ereignissen.  Sie müssen diese Ereignisse entweder auf Grundlage des aktuellen Anwendungsstatus ableiten, oder Sie müssen diese Ereignisse neu erstellen, indem Sie die Anwendung erneut ausführen.  
  
 IntelliTrace erweitert diese herkömmlichen Debuggenvorgänge, indem bestimmte Ereignisse und Daten an diesen Zeitpunkten erfasst werden.  Somit können Sie auch ohne Neustart der Anwendung die Ereignisse verfolgen und finden auch bereits aufgetretene Fehler.  IntelliTrace ist standardmäßig während des herkömmlichen Debuggen aktiviert, sodass Daten automatisch und unsichtbar erfasst werden.  Sie können also zwischen dem herkömmlichen Debuggen und dem IntelliTrace\-Debuggen problemlos wechseln, um die aufgezeichneten Informationen abzurufen.  Siehe [IntelliTrace\-Features](../debugger/intellitrace-features.md) und [Welche Daten erfasst IntelliTrace?](#WhatData)  
  
 IntelliTrace hilft Ihnen außerdem beim Debuggen von Fehlern, die schwer reproduzierbar sind oder die bei der Bereitstellung auftreten.  Sie können IntelliTrace\-Daten sammeln und in einer IntelliTrace\-Protokolldatei \(ITRACE\-Datei\) speichern.  Eine ITRACE\-Datei enthält Details über Ausnahmen, Leistungsereignisse, Webanforderungen, Testdaten, Threads, Module und andere Systeminformationen.  Sie können diese Datei in Visual Studio Enterprise öffnen, ein Element auswählen und das Debuggen mit IntelliTrace starten.  Sie können also zu jedem beliebigen Ereignis in der Datei gehen und bestimmte Einzelheiten über die Anwendung an diesem Punkt anzeigen lassen.  
  
 IntelliTrace\-Daten können aus den folgenden Quellen gespeichert werden:  
  
-   Eine IntelliTrace\-Sitzung in Visual Studio 2105 Enterprise oder Vorgängerversionen von Visual Studio Ultimate.  
  
-   Eine Testsitzung in Microsoft Test Manager  
  
-   Auf IIS gehostete ASP.NET\-Anwendungen oder SharePoint 2010\- und SharePoint 2013\-Anwendungen, die bei der Bereitstellung ausgeführt werden, wenn Sie Microsoft Monitoring Agent verwenden, entweder allein oder mit System Center 2012.  Siehe [Verwenden des eigenständigen IntelliTrace\-Collectors](../debugger/using-the-intellitrace-stand-alone-collector.md) und [Überwachen mit Microsoft Monitoring Agent](http://technet.microsoft.com/library/dn465153.aspx).  
  
 Im Folgenden werden einige Beispiele aufgeführt, die den Nutzen von IntelliTrace beim Debuggen veranschaulichen:  
  
-   Ihre Anwendung hat eine Datendatei beschädigt, doch Sie wissen nicht, wann das passiert ist.  
  
     Ohne IntelliTrace müssten Sie den Code auf alle möglichen Dateizugriffe durchsuchen, Haltepunkte für diese Zugriffe festlegen und die Anwendung dann erneut ausführen, um die Stelle ausfindig zu machen, an der das Problem aufgetreten ist.  Mit IntelliTrace können Sie alle erfassten Dateizugriffsereignisse und bestimmte Details über die Anwendung finden, wenn Ereignisse auftreten.  
  
-   Eine Ausnahme tritt auf.  
  
     Ohne IntelliTrace erhalten Sie zwar eine Meldung über eine Ausnahme, aber Sie bekommen kaum Informationen über die Ereignisse, die zu der Ausnahme geführt haben.  Sie können in der Aufrufliste die Kette der Aufrufe untersuchen, die zur Ausnahme geführt haben, aber Sie können nicht die Ereignisabfolge während dieser Aufrufe einsehen.  Mit IntelliTrace können Sie die Ereignisse untersuchen, die vor der Ausnahme auftraten.  
  
-   Die Anwendung stürzt auf einem Testcomputer ab, wird jedoch auf einem Entwicklungscomputer erfolgreich ausgeführt.  
  
     Sie können IntelliTrace\-Daten vom Microsoft Test Manager sammeln, die Daten in einer ITRACE\-Datei speichern und diese Datei später einer Team Foundation Server\-Arbeitsaufgabe für die Untersuchung hinzufügen.  Siehe [Sammeln weiterer Diagnosedaten in manuellen Tests](/devops-test-docs/test/collect-more-diagnostic-data-in-manual-tests) und [Debuggen einer App mithilfe gespeicherter IntelliTrace\-Daten](../debugger/using-saved-intellitrace-data.md).  
  
-   Ein Fehler oder ein Absturz geschieht in einer bereitgestellten Anwendung.  
  
     Für Microsoft Azure\-basierte Apps können Sie die IntelliTrace\-Datenerfassung vor der Veröffentlichung Ihrer App konfigurieren.  Während die App ausgeführt wird, werden von IntelliTrace Daten in einer iTrace\-Datei gespeichert.  Weitere Informationen finden Sie unter [Debuggen eines veröffentlichten Cloud\-Diensts mit IntelliTrace und Visual Studio](http://go.microsoft.com/fwlink/?LinkID=262248).  
  
     Für ASP.NET\-Webanwendungen, die auf IIS 7.0, 7,5 und 8,0 gehostet werden, sowie für SharePoint 2010\- oder SharePoint 2013\-Anwendungen verwenden Sie Microsoft Monitoring Agent, entweder alleine oder mit System Center 2012, um IntelliTrace\-Daten in einer ITRACE\-Datei zu speichern.  
  
     Dies ist hilfreich, wenn Sie Probleme mit Apps in der Bereitstellung diagnostizieren möchten.  Siehe [Verwenden des eigenständigen IntelliTrace\-Collectors](../debugger/using-the-intellitrace-stand-alone-collector.md)  
  
##  <a name="WhatData"></a> Welche Daten erfasst IntelliTrace?  
 **Sammeln von Ereignisinformationen**  
  
 Standardmäßig erfasst IntelliTrace nur IntelliTrace\-Ereignisse: Debuggerereignisse, Ausnahmen, .NET Framework\-Ereignisse und andere Systemereignisse, die beim Debuggen hilfreich sein können.  Sie können die IntelliTrace\-Ereignisse auswählen, die Sie sammeln möchten. Debuggerereignisse und \-ausnahmen werden allerdings immer gesammelt.   Siehe [Konfigurieren von IntelliTrace zum Sammeln von Debuginformationen](http://msdn.microsoft.com/de-de/7657ecab-e07e-4b1b-872d-f05d966be37e)  
  
-   **Debuggerereignisse**  
  
     IntelliTrace zeichnet alle Ereignisse auf, die im Visual Studio\-Debugger stattfinden.  Der Anwendungsstart ist beispielsweise ein Debuggerereignis.  Weitere Debuggerereignisse sind Beenden\-Ereignissen, die zur Unterbrechung der Anwendungsausführung führen.  Zum Beispiel wenn das Programm einen Haltepunkt oder einen Ablaufverfolgungspunkt erreicht oder einen **Schritt**befehl ausführt.  
  
     Für optimale Leistung werden nicht alle möglichen Werte für ein Debuggerereignis von IntelliTrace aufgezeichnet.  Stattdessen werden folgende Werte aufgezeichnet:  
  
    -   Werte im **Lokal**fenster.  Lassen Sie das **Lokal**fenster geöffnet, um diese Werte anzuzeigen.  
  
    -   Werte im **Auto**\-Fenster, wenn das **Auto**\-Fenster geöffnet ist  
  
    -   Werte in DataTips, die angezeigt werden, wenn Sie den Mauszeiger über eine Variable im Quellcodefenster bewegen, um den Wert anzuzeigen.  IntelliTrace erfasst keine Werte in angehefteten DataTips.  
  
-   **Ausnahmen**  
  
     IntelliTrace zeichnet den Ausnahmetyp und die Meldung für diese Ausnahmen auf:  
  
    -   Bearbeitete Ausnahmen, in denen die Ausnahme ausgelöst und abgefangen wird  
  
    -   Ausnahmefehler  
  
-   **.NET Framework\-Ereignisse**  
  
     IntelliTrace zeichnet standardmäßig die häufigsten .NET Framework\-Ereignisse auf.  Beispiel:  
  
    -   Für ein Dateizugriffsereignis erfasst IntelliTrace den Dateinamen.  
  
    -   Für ein Checkbox\-Aktivierungsereignis erfasst IntelliTrace den Kontrollkästchenzustand und den Text.  
  
-   **SharePoint 2010\- und SharePoint 2013\-Anwendungsereignisse**  
  
     Sie können Benutzerprofilereignisse und eine Teilmenge von einheitlichen Ereignissen des Protokollierungs\-Systems \(ULS\) für SharePoint 2010\- und 2013\-Anwendungen erfassen, die außerhalb von Visual Studio ausgeführt werden.  Sie können diese Ereignisse in einer ITRACE\-Datei speichern.  Erfordert Visual Studio Enterprise 2015, eine Vorgängerversion von Visual Studio Ultimate oder [Microsoft Monitoring Agent](http://go.microsoft.com/fwlink/?LinkId=320384) musss im **Ablaufverfolgungsmodus** ausgeführt werden.  
  
     Wenn Sie die ITRACE\-Datei öffnen, geben Sie eine SharePoint\-Korrelations\-ID ein, um die entsprechenden Webanforderung zu suchen, die aufgezeichneten Ereignisse anzuzeigen und das Debuggen von einem bestimmten Ereignis aus zu starten.  Wenn die Datei Ausnahmefehler enthält, können Sie eine Korrelations\-ID auswählen, um das Debuggen einer Ausnahme zu starten.  
  
     Thema  
  
    -   [Verwenden des eigenständigen IntelliTrace\-Collectors](../debugger/using-the-intellitrace-stand-alone-collector.md)  
  
    -   [Debuggen einer App mithilfe gespeicherter IntelliTrace\-Daten](../debugger/using-saved-intellitrace-data.md)  
  
    -   [Exemplarische Vorgehensweise: Debuggen einer SharePoint\-Anwendung mithilfe von IntelliTrace](../Topic/Walkthrough:%20Debugging%20a%20SharePoint%20Application%20by%20Using%20IntelliTrace.md)  
  
 **Sammeln von Funktionsaufrufinformationen**  
  
 Sie können IntelliTrace so konfigurieren, dass Aufrufinformationen für Funktionen gesammelt werden.  Anhand dieser Informationen können Sie den Aufruflistenverlauf anzeigen und die Aufrufe im Code vorwärts und rückwärts durchlaufen.  Für jeden Funktionsaufruf werden die folgenden Daten von IntelliTrace aufgezeichnet:  
  
-   Funktionsname  
  
-   Werte primitiver Datentypen, die als Parameter an Funktionseinstiegspunkten übergeben und an Funktionsendpunkten zurückgegeben werden  
  
-   Werte von automatischen Eigenschaften, wenn sie gelesen oder geändert werden  
  
-   Zeiger auf untergeordnete Objekte auf der obersten Ebene ohne Werte \(außer NULL oder keine\)  
  
> [!NOTE]
>  IntelliTrace erfasst nur die ersten 256 Objekte in Arrays und die ersten 256 Zeichen von Zeichenfolgen.  
  
 Siehe [Konfigurieren von IntelliTrace zum Sammeln von Debuginformationen](http://msdn.microsoft.com/de-de/7657ecab-e07e-4b1b-872d-f05d966be37e)  
  
 **Sammeln von Modulinformationen**  
  
 Um zu steuern, wie viel Aufrufsinformationen IntelliTrace erfasst, legen Sie nur die Module fest, die für Sie von Bedeutung sind.  Das kann dabei helfen, die Anwendungsleistung während der Erfassung zu verbessern.   Siehe [Konfigurieren von IntelliTrace zum Sammeln von Debuginformationen](http://msdn.microsoft.com/de-de/7657ecab-e07e-4b1b-872d-f05d966be37e)  
  
##  <a name="AffectPerformance"></a> Verlangsamt IntelliTrace meine Anwendung?  
 Standardmäßig werden von IntelliTrace nur Daten für ausgewählte IntelliTrace\-Ereignisse gesammelt.  Das kann, abhängig von der Struktur und der Organisation Ihres Codes, eventuell die Anwendung verlangsamen.  Wenn IntelliTrace beispielsweise oft ein Ereignis protokolliert, kann dies die Anwendung verlangsamen.  Erwägen Sie, eine Umgestaltung Ihrer Anwendung vorzunehmen.  
  
 Das Sammeln der Aufrufsinformationen verlangsamt die App möglicherweise erheblich.  Außerdem erhöht sich dadurch möglicherweise die Größe aller auf dem Datenträger gespeicherter IntelliTrace\-Protokolldateien \(ITRACE\-Dateien\).  Um diese Auswirkungen zu minimieren, sammeln Sie Aufrufinformationen nur für die Module, die Sie interessieren.  Um die maximale Größe der ITRACE\-Dateien zu ändern, wechseln Sie zu **Tools**, **Optionen**, **IntelliTrace**, **Erweitert**.   Siehe [Konfigurieren von IntelliTrace zum Sammeln von Debuginformationen](http://msdn.microsoft.com/de-de/7657ecab-e07e-4b1b-872d-f05d966be37e)  
  
## In diesem Abschnitt  
 [IntelliTrace\-Features](../debugger/intellitrace-features.md)  
  
 [Konfigurieren von IntelliTrace zum Sammeln von Debuginformationen](http://msdn.microsoft.com/de-de/7657ecab-e07e-4b1b-872d-f05d966be37e)  
  
 [Einbeziehen diagnostischer Ablaufverfolgungsdaten mit Fehlern, die schwer zu reproduzieren sind](/devops-test-docs/test_notintoc/including-diagnostic-trace-data-with-bugs-that-are-difficult-to-reproduce)  
  
 [Diagnostizieren von Problemen nach der Bereitstellung](../debugger/diagnose-problems-after-deployment.md)  
  
 [Debuggen einer App mithilfe gespeicherter IntelliTrace\-Daten](../debugger/using-saved-intellitrace-data.md)  
  
### Blogs  
 [Visual Studio ALM \+ Team Foundation Server](http://go.microsoft.com/fwlink/?LinkId=201340)  
  
### Foren  
 [Visual Studio\-Diagnose](http://go.microsoft.com/fwlink/?LinkId=262263)