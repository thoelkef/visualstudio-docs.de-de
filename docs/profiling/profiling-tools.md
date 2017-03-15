---
title: Profilerstellungstools | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.diagnosticshub.overview
ms.assetid: 0fb6cd5d-e16a-4526-84a5-19e63c625bc5
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 5ec205ee98f61b400112a39197e1f2aa9dddbd7d
ms.openlocfilehash: 2d6ec94f7e68a84a4bb4a606882997fadec49e01
ms.lasthandoff: 02/22/2017

---
# <a name="profiling-tools"></a>Profilerstellungstools
Profilerstellungs- und Diagnosetools helfen bei der Diagnose von Speicher- und CPU-Auslastung und anderen Problemen auf Anwendungsebene. Mit diesen Tools können Sie Daten (z.B. Variablenwerte, Funktionsaufrufe und Ereignisse) über einen Zeitraum sammeln, in dem Sie Ihre Anwendung im Debugger ausführen. Sie können den Status Ihrer Anwendung an verschiedenen Punkten der Codeausführung anzeigen.  
  
 Lesen Sie die nachfolgende Zusammenfassung, um zu sehen, welche Tools für Ihren Projekttyp (z.B. Desktop, UWP, ASP.NET) verfügbar sind.  
  
 Sie können auf die Profilerstellungstools mithilfe der Tools **Debuggen / Fenster / Diagnosetools anzeigen** zugreifen, um die Tools während der Debugsitzung zu verwenden, oder Sie können mit anderen Ansätzen eine Postmortem-Analyse durchführen.  Weitere Informationen zu den verschiedenen Ansätzen finden Sie unter [Running Profiling Tools With or Without the Debugger](../profiling/running-profiling-tools-with-or-without-the-debugger.md) (Ausführen von Profilerstellungstools mit oder ohne Debugger).
  
 ![DebugDiagnosticsToolsMenu](../profiling/media/debugdiagnosticstoolsmenu.png "DebugDiagnosticsToolsMenu")
  
 Unter [What's New in Profiling Tools in Visual Studio&2017;](../profiling/what-s-new-in-profiling-tools.md) (Neuigkeiten in Profilerstellungstools in Visual Studio&2017;) lernen Sie neue Features dieser Version kennen.
  
 In den folgenden Abschnitte, werden die verschiedenen Leistungstools erklärt, die in Visual Studio verfügbar sind.
  
## <a name="memory-usage"></a>Speicherauslastung  
 ![DiagMemorySmall](../profiling/media/diagmemorysmall.png "DiagMemorySmall")  
  
 Suchen Sie Speicherverluste und ineffiziente Arbeitsspeichernutzung während des Debuggens mit dem **Speicherauslastungstool** . Mit dem Tool können Sie Momentaufnahmen des verwalteten und nativen Speicherheaps machen. Sie können dieses Tool mit Desktop-Apps, universellen Windows-Apps und ASP.NET-Apps verwenden. Das Tool **Speicherauslastung** kann entweder während des Debuggens über das Fenster **Diagnosetools** ausgeführt werden (**Debuggen &gt; Fenster &gt; Diagnosetools anzeigen**) oder außerhalb des Debuggers über (**Debuggen &gt; Leistungsanalyse...**). Unter [Analyze Memory Usage](../profiling/memory-usage.md) (Analysieren der Speicherauslastung) und [Memory Usage without the Debugger](../profiling/Memory-Usage-without-Debugging2.md) (Speicherauslastung ohne Debugger) finden Sie weitere Informationen.  
  
## <a name="cpu-usage"></a>CPU-Auslastung  
 ![DiagCPUSmall](../profiling/media/diagcpusmall.png "DiagCPUSmall")  
  
 Das Tool **CPU-Auslastung** Tool zeigt Ihnen, wo die CPU Zeit für die Ausführung von C++-, C#-/VB- und JavaScript-Code verbringt.  Sie können dieses Tool sowohl mit Desktop- als auch universellen Windows-Apps sowie mit ASP.NET und Azure App Service-Apps ausführen. Das Tool **CPU-Auslastung** kann entweder während des Debuggens über das Fenster **Diagnosetools** ausgeführt werden (**Debuggen &gt; Fenster &gt; Diagnosetools anzeigen**) oder außerhalb des Debuggers (**Debuggen &gt; Leistungsanalyse...**). Weitere Informationen finden Sie unter [Beginners Guide to Performance Profiling](../profiling/beginners-guide-to-performance-profiling.md) (Einführung in die Leistungsprofilerstellung) und [Analyze CPU Usage](../profiling/cpu-usage.md) (Analysieren der CPU-Auslastung).
  
## <a name="gpu-usage"></a>GPU-Nutzung  
 ![DiagGPUUsage](../profiling/media/diaggpuusage.png "DiagGPUUsage")  
  
 Verwenden Sie das Tool [GPU-Nutzung](../debugger/gpu-usage.md), um die Nutzung übergeordneter Hardware Ihrer Direct3D-App besser zu verstehen. Sie können dieses Tool jeweils mit Desktop- und universellen Windows-Apps verwenden, jedoch nicht mit ASP.NET-Apps. Das Tool **GPU-Nutzung** kann entweder während des Debuggens über das Fenster **Diagnosetools** ausgeführt werden (**Debuggen &gt; Diagnosetools anzeigen**) oder außerhalb des Debuggers (**Debuggen &gt; Leistungsanalyse...**).  
  
## <a name="application-timeline"></a>Anwendungszeitachse  
 ![DiagAppTimeline](../profiling/media/diagapptimeline.png "DiagAppTimeline")  
  
 Das [Application Timeline](../profiling/application-timeline.md)-Tool hilft Ihnen dabei, die Leistung von XAML-Anwendungen zu verbessern, indem es eine detaillierte Ansicht des Ressourcenverbrauchs der Anwendung bereitstellt. Sie können die **Anwendungszeitachse** mit Desktop- und universellen Windows-Apps verwenden, jedoch nicht mit ASP.NET-Apps. Das Tool **Anwendungszeitachse** kann im Fenster **Diagnosetools** (**Debuggen &gt; Leistungsanalyse...**) ausgeführt werden.
  
## <a name="perftips"></a>PerfTips  
 ![DiagPerfTips](../profiling/media/diagperftips.png "DiagPerfTips")  
  
 Wenn der Debugger die Ausführung an einem Haltepunkt oder während einer schrittweisen Ausführung stoppt, wird die verstrichene Zeit zwischen der Pause und dem vorherigen Haltepunkt als QuickInfo im Editor-Fenster angezeigt. Mit diesen [PerfTips](../profiling/perftips.md) können Sie die Leistung Ihrer App während des Debuggens überwachen und analysieren. Sie können **PerfTips** in Desktop-Apps, universellen Windows-Apps und ASP.NET-Apps anzeigen.

## <a name="performance-explorer"></a>Leistungs-Explorer  
 ![PerfTools](../profiling/media/perftools.png "PerfTools")  
  
 Mit dem **Leistungs-Explorer** (**Debuggen &gt; Profiler &gt; Leistungs-Explorer**) können Sie viele unterschiedliche Tools verwenden, einschließlich **CPU-Sampling**,  **Instrumentierung**, **.NET-Speicherbelegung**und **Ressourcenkonflikt**. Sie können Leistungs-Explorer-Tools mit Desktop-Apps und ASP.NET-Apps verwenden, jedoch nicht mit universellen Windows-Apps. Weitere Informationen finden Sie unter [Leistungs-Explorer](../profiling/performance-explorer.md).

 > [!NOTE]
 > Wenn Sie keine spezielle Aufgabe wie die Instrumentierung durchführen möchten, verwenden Sie Diagnosetools wie „Speicherauslastung“ und „CPU-Auslastung“ statt des Leistungs-Explorers (der nun ein Legacytool ist).
  
## <a name="javascript-memory"></a>JavaScript-Memory  
 ![DiagJSMemory](../profiling/media/diagjsmemory.png "DiagJSMemory")  
  
 Mit den [JavaScript Memory](../profiling/javascript-memory.md)-Tools können Sie leistungsbezogene Codeprobleme messen, auswerten und beheben, indem Sie Zeitsteuerungsinformationen bei jedem Aufrufen und Beenden jeder Funktion in Ihrer App sammeln. Sie können dieses Toll mit universellen Windows-HTML-Apps verwenden. Das Tool **JavaScript-Funktionstiming** kann im Fenster **Diagnosetools** (**Debuggen &gt; Leistungsanalyse...**) ausgeführt werden.  
  
## <a name="html-ui-responsiveness"></a>HTML-UI-Reaktionsfähigkeit  
 ![DiagHTMLResp](../profiling/media/diaghtmlresp.png "DiagHTMLResp")  
  
 Mit dem [HTML-UI-Reaktionsfähigkeit](../profiling/html-ui-responsiveness.md)-Tool können Sie Leistungsprobleme in Ihren Apps isolieren, einschließlich fehlende Reaktionsfähigkeit, langsame Ladezeit und visuelle Updates, die weniger häufig als erwartet auftreten. Sie können dieses Toll mit universellen Windows-HTML-Apps verwenden. Das Tool **HTML-UI-Reaktionsfähigkeit** kann im Fenster **Diagnosetools** (**Debuggen &gt; Leistungsanalyse...**) ausgeführt werden.  
  
## <a name="intellitrace"></a>IntelliTrace  
 ![DiagIntelliTrace](../profiling/media/diagintellitrace.png "DiagIntelliTrace")  
  
 Mit[IntelliTrace](../debugger/intellitrace.md) können Sie bestimmte Ereignisse aufzeichnen, Daten im Fenster **Lokal** während Debuggerereignissen und Funktionsaufrufen untersuchen sowie Fehler debuggen, die schwer zu reproduzieren sind.  IntelliTrace ist in erster Linie ein Tool zum Debuggen, aber es enthält auch Informationen, die für Leistungsuntersuchungen verwendet werden kann. Sie können dieses Tool nur in Visual Studio Enterprise mit Desktop-Apps, universellen Windows-Apps und ASP.NET C#-Apps verwenden. Sie finden IntelliTrace im Fenster **Diagnosetools** während des Debuggens (**Debuggen &gt; Fenster &gt; Diagnosetools anzeigen**).  
  
## <a name="profiling-in-production"></a>Profilerstellung im Produktivbetrieb  
 Im Produktivbetrieb empfiehlt es sich, die Profilerstellung mithilfe von [vsperf.exe über die Befehlszeile](../profiling/using-the-profiling-tools-from-the-command-line.md) durchzuführen, um ein CPU-Profil zu erhalten. Azure App Service bietet Ihnen über [Server Explorer oder das Kudu-Portal](https://azure.microsoft.com/en-us/blog/remote-profiling-support-in-azure-app-service/)die Möglichkeit, von einem entfernten Standort aus ein Profil zu erstellen.  
  
## <a name="which-tool-should-i-use"></a>Welches Tool soll ich verwenden?  
 Hier sehen Sie eine Tabelle, in der die verschiedenen Tools aufgelistet sind, die Visual Studio anbietet sowie die verschiedenen Projekttypen, die Sie mit diesen verwenden können:  
  
|Leistungstool|Windows-Desktop|Windows Universell/Store|ASP.NET|  
|----------------------|---------------------|------------------------------|-------------|  
|[Speicherauslastung](../profiling/memory-usage.md)|ja|ja|ja|  
|[CPU-Auslastung](../profiling/cpu-usage.md)|ja|ja|ja|  
|[GPU-Nutzung](../debugger/gpu-usage.md)|ja|ja|nein|  
|[Anwendungszeitachse](../profiling/application-timeline.md)|ja|ja|nein|  
|[PerfTips](../profiling/perftips.md)|ja|ja für XAML, nicht für HTML|nein|  
|[Leistungs-Explorer](../profiling/performance-explorer.md)|ja|nein|ja|  
|[IntelliTrace](../debugger/intellitrace.md)|nur .NET Enterprise|nur .NET Enterprise|nur .NET Enterprise|  
|[HTML-UI-Reaktionsfähigkeit](../profiling/html-ui-responsiveness.md)|nein|ja für HTML, nicht für XAML|nein|  
|[JavaScript-Speicher](../profiling/javascript-memory.md)|nein|ja für HTML, nicht für XAML|nein|  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio-IDE](../ide/visual-studio-ide.md)
