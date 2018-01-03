---
title: "Ausführen von Profilerstellungstools mit oder ohne den Debugger | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3fcdccad-c1bd-4c67-bcec-bf33a8fb5d63
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 2507ec49129692914ba6d11e4f651d5895b49c8b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="running-profiling-tools-with-or-without-the-debugger"></a>Ausführen von Profilerstellungstools mit oder ohne den Debugger
Visual Studio bietet Ihnen nun eine Auswahl von Leistungstools, von denen einige (z.B. **CPU-Auslastung** und **Speicherauslastung**) mit oder ohne den Debugger ausgeführt werden können. Leistungstools ohne Debugger sind für Releasekonfigurationen gedacht, während die Tools mit integriertem Debugger zur Ausführung auf Debugkonfigurationen vorgesehen sind.  
  
## <a name="should-i-run-the-tool-with-or-without-the-debugger"></a>Sollte ich das Tool mit oder ohne Debugger ausführen?  
 Mit Leistungstools mit integriertem Debugger können Sie viele Aufgaben ausführen, die mit Leistungstools ohne Debugger nicht möglich sind, z. B. Haltepunkte festlegen und Variablenwerte überprüfen. Tools ohne Debugger bieten Ihnen eine Erfahrung, die mehr dem ähnelt, was Benutzer der veröffentlichten Anwendung sehen.  
  
 Hier sind einige Fragen, anhand der Sie entscheiden können, welche Art von Tool für Ihre Zwecke geeignet ist:  
  
1.  Wurde das Problem gefunden, während die Anwendung entwickelt wurde, oder wurde es in einer veröffentlichten Version gefunden?  
  
     Wenn das Problem während der Entwicklung gefunden wurde, müssen Sie die Leistungstools wahrscheinlich nicht in einem Releasebuild ausführen. Wenn das Problem in einer Releaseversion gefunden wurde, sollten Sie das Problem mit einer Releasekonfiguration reproduzieren und dann entscheiden, ob der Debugger bei der weiteren Untersuchung hilfreich sein würde.  
  
2.  Wird das Problem durch eine CPU-intensive Verarbeitung verursacht?  
  
     Viele Probleme sind auf externe Leistungsprobleme zurückzuführen, z.B. Datei-E/A oder Netzwerkreaktionsfähigkeit. Es sollte daher keinen großen Unterschied machen, ob Sie die Leistungstools mit oder ohne den Debugger ausführen. Wenn Ihr Problem auf CPU-intensive Aufrufe zurückzuführen ist, kann der Unterschied zwischen Release- und Debugkonfigurationen beträchtlich sein, daher sollten Sie überprüfen, ob das Problem im Releasebuild besteht, bevor Sie die Tools mit integriertem Debugger verwenden.  
  
3.  Müssen Sie die Leistung genau messen oder ist eine ungefähre Angabe akzeptabel?  
  
     In Debugbuilds sind bestimmte Optimierungen nicht vorhanden, die Releasebuilds bereitstellen, z.B. Inlinefunktionsaufrufe und Konstanten, das Löschen nicht verwendeter Codepfade und das Speichern von Variablen auf eine Art und Weise, dass diese vom Debugger nicht verwendet werden können. Der Debugger selbst ändert seine Leistung, da er bestimmte Vorgänge ausführt, die zum Debuggen erforderlich sind (z. B. das Abfangen von Ausnahmen und Ladeereignisse für Module). Leistungsangaben in den im Debugger integrierten Tools sind weniger genau, da sie keine Debuggeroptimierungen berücksichtigen. Im Vergleich mit anderen relativen Messwerten, die beim Debuggen erfasst werden, können sie jedoch nützlich sein. Leistungsangaben für Releasekonfigurationen mit den Tools ohne Debugger sind viel präziser.
  
##  <a name="BKMK_Quick_start__Collect_diagnostic_data"></a> Sammeln von Profilerstellungsdaten während des Debuggens  
 Der folgende Abschnitt beschreibt das lokale Debuggen. Informationen zum Debuggen auf einem Gerät oder zum Remotedebuggen erhalten Sie in späteren Abschnitten.  
  
1.  Öffnen Sie das Projekt, das Sie debuggen möchten, und klicken Sie anschließend auf **Debuggen / Debugging starten** (oder klicken Sie auf der Symbolleiste auf **Starten** , oder drücken Sie **F5**).  
  
2.  Das Fenster **Diagnosetools** wird automatisch angezeigt, es sei denn, Sie haben es deaktiviert. Klicken Sie auf **Debuggen / Windows / Diagnosetools anzeigen**, um das Fenster erneut aufzurufen.  
  
3.  Führen Sie die Szenarien aus, für die Sie Daten erfassen möchten.  
  
     Während der Debuggingsitzung können Sie Informationen zu Ereignissen, Prozessarbeitsspeicher und CPU-Auslastung anzeigen.  
  
     Folgende Abbildung zeigt das Fenster **Diagnosetools** in Visual Studio 2015 Update 1:  
  
     ![DiagnosticTools&#45;Update1](../profiling/media/diagnostictools-update1.png "DiagnosticTools-Update1")  
  
4.  Mithilfe der Einstellung **Tools auswählen** auf der Symbolleiste können Sie auswählen, ob Sie die **Speicherauslastung** oder die **CPU-Auslastung** (oder beides) anzeigen möchten. Wenn Sie Visual Studio Enterprise ausführen, können Sie IntelliTrace unter **Tools / Optionen / IntelliTrace** aktivieren oder deaktivieren.  
  
5.  Die Diagnosesitzung endet, wenn Sie das Debugging beenden.  
  
 In Visual Studio 2015 Update 1 können Sie sich im Fenster **Diagnosetools** einfach auf die Ereignisse konzentrieren, die für Sie von Interesse sind.   Die Ereignisnamen werden nun mit den Kategoriepräfixen (**Bewegung**, **Programmausgabe**, **Haltepunkt**, **Datei** usw.) angezeigt, damit Sie die Liste schnell nach einer bestimmten Kategorie durchsuchen oder die Kategorien überspringen können, die Sie nicht interessieren.  
  
 Das Fenster hat jetzt ein Suchfeld, damit Sie nach einer bestimmten Zeichenfolge in der Ereignisliste suchen können. Folgende Abbildung zeigt beispielsweise die Ergebnisse der Suche nach der Zeichenfolge "install", der vier Ereignisse entsprechen:  
  
 ![DiagnosticsEventSearch](../profiling/media/diagnosticseventsearch.png "DiagnosticsEventSearch")  
  
 Sie können in dem Fenster Ereignisse auch in die Ansicht hineinfiltern bzw. aus dieser herausfiltern. In der Dropdownliste **Filtern** können Sie bestimmte Kategorien von Ereignissen aktivieren bzw. deaktivieren: Die Kategorienamen entsprechen den Präfixnamen.  
  
 ![DiagnosticEventFilter](../profiling/media/diagnosticeventfilter.png "DiagnosticEventFilter")  
  
 Weitere Informationen finden Sie unter [Suchen und Filtern auf der Registerkarte "Ereignisse" im Fenster "Diagnosetools"](http://blogs.msdn.com/b/visualstudioalm/archive/2015/11/12/searching-and-filtering-the-events-tab-of-the-diagnostic-tools-window.aspx).  
  
## <a name="collect-profiling-data-without-debugging"></a>Sammeln von Profilerstellungsdaten ohne das Debuggen  
 Für die Ausführung einiger Profilerstellungstools sind Administratorrechte erforderlich. Führen Sie daher entweder Visual Studio als Administrator aus, oder führen Sie die Tools als Administrator aus, wenn Sie die Diagnosesitzung starten.  
  
1.  Öffnen Sie das Projekt in Visual Studio.  
  
2.  Klicken Sie im Menü **Debuggen** auf **Leistungsprofiler…**. (Tastenkombination: Alt + F2).  
  
3.  Wählen Sie auf der Diagnosestartseite ein oder mehrere Tools aus, die in der Sitzung ausgeführt werden sollen. Es werden nur die Tools angezeigt, die für den Projekttyp, das Betriebssystem und die Programmiersprache infrage kommen. Wenn Sie ein Diagnosetool auswählen, werden die Optionen für Tools deaktiviert, die nicht in derselben Diagnosesitzung ausgeführt werden können. Hier ist eine mögliche Auswahl für eine Windows Universal-App in C#:  
  
     ![Diagnosetools auswählen](../profiling/media/diag_selecttool.png "DIAG_SelectTool")  
  
4.  Klicken Sie zum Starten der Diagnosesitzung auf **Start**.  
  
5.  Führen Sie die Szenarien aus, für die Sie Daten auflisten möchten.  
  
     Während Sie die Sitzung ausführen, zeigen einige Tools Grafiken der Echtzeitdaten auf der Startseite der Diagnosetools an.  
  
     ![Daten auf der Seite „Leistung und Diagnose“ erfassen](../profiling/media/pdhub_collectdata.png "PDHUB_CollectData")  
  
6.  Klicken Sie zum Beenden der Diagnosesitzung auf **Auflistung anhalten**.  
  
 Nachdem Sie das Sammeln von Daten in einer Diagnosesitzung beendet haben, werden die Daten analysiert, und der Bericht wird auf der Seite "Diagnose" angezeigt.  
  
 Sie können auch gespeicherte DIAGNOSTIC-Sitzungsdateien über die Liste der zuvor geöffneten Elemente auf der Startseite für die Diagnosetools öffnen.  
  
 ![Öffnen einer gespeicherten Diagnosesitzungsdatei](../profiling/media/pdhub_openexistingdiagsession.png "PDHUB_OpenExistingDiagSession")  
  
## <a name="the-profiling-report"></a>Der Profilerstellungsbericht  
 ![Diagnosetools-Bericht](../profiling/media/diag_report.png "DIAG_Report")  
  
|||  
|-|-|  
|![Schritt 1](../profiling/media/procguid_1.png "ProcGuid_1")|Die Zeitachse zeigt die Länge der Profilerstellungssitzung, der App-Lebenszyklusaktivierungsereignisse und der Benutzermarkierungen an.|  
|![Schritt 2](../profiling/media/procguid_2.png "ProcGuid_2")|Sie können den Bericht auf einen Teil der Zeitachse einschränken, indem Sie die blauen Striche ziehen, um einen Bereich der Zeitachse auszuwählen.|  
|![Schritt 3](../profiling/media/procguid_3.png "ProcGuid_3")|Ein Tool zeigt mindestens ein Hauptdiagramm an. Wenn Ihre Diagnosesitzung mit mehreren Tools erstellt wird, werden alle Hauptdiagramme angezeigt.|  
|![Schritt 4](../profiling/media/procguid_4.png "ProcGuid_4")|Sie können die einzelnen Diagramme reduzieren und erweitern.|  
|![Schritt 5](../profiling/media/procguid_6.png "ProcGuid_6")|Wenn Ihre Daten Informationen mehrerer Tools enthalten, werden die Details für das Tool unter Registerkarten aufgelistet.|  
|![Schritt 6](../profiling/media/procguid_6a.png "ProcGuid_6a")|Ein Tool kann eine oder mehrere Detailansichten haben. Die Ansicht wird durch den ausgewählten Bereich der Zeitachse gefiltert.|  
  
## <a name="setting-the-analysis-target-to-another-device"></a>Festlegen des Analyseziels auf ein anderes Gerät  
 Sie können nicht nur Ihre App im Visual Studio-Projekt starten, sondern auch Diagnosesitzungen auf alternativen Zielen ausführen. Beispielsweise empfiehlt es sich, die Diagnose von Leistungsproblemen mit einer Version Ihrer App auszuführen, die aus dem Windows App Store installiert wurde.  
  
 ![Analyseziel für Diagnosetools auswählen](../profiling/media/pdhub_chooseanalysistarget.png "PDHUB_ChooseAnalysisTarget")  
  
 Sie können Apps starten, die bereits auf einem Gerät installiert sind, oder Sie können die Diagnosetools an Apps anfügen, die bereits ausgeführt werden. Bei der Auswahl von **Ausgeführte App** oder **Installierte App** wählen Sie die App in einer Liste aus, die die Apps auf dem angegebenen Bereitstellungsziel erkennt.  
  
 ![Auswählen einer ausgeführten oder installierten App für die Diagnose](../profiling/media/pdhub_selectrunningapp.png "PDHUB_SelectRunningApp")  
  
 Wenn Sie **Internet Explorer** auswählen, geben Sie die URL an, und Sie können das Windows Phone-Bereitstellungsziel ändern.  
  
 ![URL angeben, die in Internet Explorer angezeigt wird](../profiling/media/pdhub_choosephoneanalysistarget.png "PDHUB_ChoosePhoneAnalysisTarget")  
  
## <a name="remote-debugging"></a>Remote Debugging  
 Für das Ausführen einer Diagnosesitzung auf einem Remote-PC oder -Tablet müssen die Visual Studio-Remotetools installiert sein und auf dem Remotezielgerät ausgeführt werden. Informationen zu Desktop-Apps finden Sie unter [Remotedebugging](../debugger/remote-debugging.md).  Informationen zu universellen Windows-Apps finden Sie unter [Run UWP apps on a remote machine (Ausführen von UWP-Apps auf einem Remotecomputer)](../debugger/run-windows-store-apps-on-a-remote-machine.md).  
  
## <a name="blog-posts-and-msdn-articles-from-the-diagnostics-development-team"></a>Blogbeiträge und MSDN-Artikel vom Diagnoseentwicklungsteam  
 MSD[MSDN Magazine: Analysieren der Leistung beim Debuggen in Visual Studio 2015](https://msdn.microsoft.com/en-us/magazine/dn973013.aspx)  
  
 [MSDN Magazine: Schnellere Problemdiagnose mit IntelliTrace](https://msdn.microsoft.com/en-us/magazine/dn973014.aspx)  
  
 [Blogbeitrag: Diagnostizieren von Ereignishandlerverlusten mit dem Speicherauslastungstool in Visual Studio 2015](http://blogs.msdn.com/b/visualstudioalm/archive/2015/04/29/diagnosing-event-handler-leaks-with-the-memory-usage-tool-in-visual-studio-2015.aspx)  
  
 [Video: Verlaufsbezogenes Debuggen mit IntelliTrace in Microsoft Visual Studio Ultimate 2015](https://channel9.msdn.com/Events/Ignite/2015/BRK3716)  
  
 [Video: Debuggen von Leistungsproblemen mit Visual Studio 2015](https://channel9.msdn.com/Events/Build/2015/3-731)  
  
 [PerfTips: Informationen zur Leistung auf einen Blick beim Debuggen mit Visual Studio](http://blogs.msdn.com/b/visualstudioalm/archive/2014/08/18/perftips-performance-information-at-a-glance-while-debugging-with-visual-studio.aspx)  
  
 [Diagnostic Tools debugger window in Visual Studio 2015 (Fenster des Diagnosetoolsdebugger in Visual Studio 2015)](http://blogs.msdn.com/b/visualstudioalm/archive/2015/01/16/diagnostic-tools-debugger-window-in-visual-studio-2015.aspx)  
  
 [IntelliTrace in Visual Studio Enterprise 2015](http://blogs.msdn.com/b/visualstudioalm/archive/2015/01/16/intellitrace-in-visual-studio-ultimate-2015.aspx)
