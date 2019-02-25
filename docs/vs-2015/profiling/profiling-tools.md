---
title: Profilerstellungstools | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.diagnosticshub.overview
ms.assetid: 0fb6cd5d-e16a-4526-84a5-19e63c625bc5
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 93ef837da86056acc720abff9ad33cbf457a108f
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2019
ms.locfileid: "54780843"
---
# <a name="profiling-tools"></a>Profilerstellungstools
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Profilerstellungs- und Diagnosetools helfen bei der Diagnose von Speicher- und CPU-Auslastung und anderen Problemen auf Anwendungsebene. Mit diesen Tools können Sie Daten (z.B. Variablenwerte, Funktionsaufrufe und Ereignisse) über einen Zeitraum sammeln, in dem Sie Ihre Anwendung im Debugger ausführen. Sie können den Status Ihrer Anwendung an verschiedenen Punkten der Codeausführung anzeigen.  
  
 Lesen Sie die nachfolgende Zusammenfassung, um zu sehen, welche Tools für Ihren Projekttyp (z.B. Desktop, UWP, ASP.NET) verfügbar sind.  
  
 Sie können auf die Profilerstellungstools mithilfe der Tools **Debuggen &gt; Fenster &gt; Diagnosetools anzeigen** zugreifen, um die Tools während der Debugsitzung verwenden zu können oder mithilfe von **Debuggen &gt; Leistungsanalyse** zum Ausführen einer fokussierten Leistungsanalyse.  Weitere Informationen zu den verschiedenen Herangehensweisen finden Sie unter [Running Profiling Tools With or Without the Debugger](../profiling/running-profiling-tools-with-or-without-the-debugger.md) .  
  
 ![DebugDiagnosticsToolsMenu](../profiling/media/debugdiagnosticstoolsmenu.png "DebugDiagnosticsToolsMenu")  
  
 Unter [What's New in Profiling Tools in Visual Studio 2017](../profiling/what-s-new-in-profiling-tools.md) (Neuigkeiten in Profilerstellungstools in Visual Studio 2017) lernen Sie neue Features dieser Version kennen.  
  
 In den folgenden Abschnitte, werden die verschiedenen Leistungstools erklärt, die in Visual Studio verfügbar sind.  
  
## <a name="memory-usage"></a>Speicherauslastung  
 ![DiagMemorySmall](../profiling/media/diagmemorysmall.png "DiagMemorySmall")  
  
 Suchen Sie Speicherverluste und ineffiziente Arbeitsspeichernutzung während des Debuggens mit dem **Speicherauslastungstool** . Mit dem Tool können Sie Momentaufnahmen des verwalteten und nativen Speicherheaps machen. Sie können dieses Tool mit Desktop-Apps, universellen Windows-Apps und ASP.NET-Apps verwenden. Das Tool **Speicherauslastung** kann entweder während des Debuggens über das Fenster **Diagnosetools** ausgeführt werden (**Debuggen &gt; Fenster &gt; Diagnosetools anzeigen**) oder außerhalb des Debuggers über (**Debuggen &gt; Leistungsanalyse...**). Unter [Analyze Memory Usage](../profiling/memory-usage.md) (Analysieren der Speicherauslastung) und [Memory Usage without the Debugger](http://msdn.microsoft.com/library/8883bc5f-df86-4f84-aa2b-a21150f499b0) (Speicherauslastung ohne Debugger) finden Sie weitere Informationen.  
  
## <a name="cpu-usage"></a>CPU-Auslastung  
 ![DiagCPUSmall](../profiling/media/diagcpusmall.png "DiagCPUSmall")  
  
 Das Tool **CPU-Auslastung** Tool zeigt Ihnen, wo die CPU Zeit für die Ausführung von C++-, C#-/VB- und JavaScript-Code verbringt.  Sie können dieses Tool sowohl mit Desktop- als auch universellen Windows-Apps ausführen sowie mit Azure App Service-Apps. Das Tool **CPU-Auslastung** kann entweder während des Debuggens über das Fenster **Diagnosetools** ausgeführt werden (**Debuggen &gt; Fenster &gt; Diagnosetools anzeigen**) oder außerhalb des Debuggers (**Debuggen &gt; Leistungsanalyse...**). Weitere Informationen zu den verschiedenen Herangehensweisen finden Sie unter [CPU-Auslastung](../profiling/cpu-usage.md) .  
  
## <a name="performance-explorer"></a>Leistungs-Explorer  
 ![PerfTools](../profiling/media/perftools.png "PerfTools")  
  
 Mit dem **Leistungs-Explorer** (**Debuggen &gt; Profiler &gt; Leistungs-Explorer**) können Sie viele unterschiedliche Tools verwenden, einschließlich **CPU-Sampling**,  **Instrumentierung**, **.NET-Speicherbelegung**und **Ressourcenkonflikt**. Sie können Leistungs-Explorer-Tools mit Desktop-Apps und ASP.NET-Apps verwenden, jedoch nicht mit universellen Windows-Apps. Weitere Informationen finden Sie unter [Leistungs-Explorer](../profiling/performance-explorer.md).  
  
## <a name="gpu-usage"></a>GPU-Nutzung  
 ![DiagGPUUsage](../profiling/media/diaggpuusage.png "DiagGPUUsage")  
  
 Verwenden Sie das Tool [GPU-Nutzung](../debugger/gpu-usage.md), um die Nutzung übergeordneter Hardware Ihrer Direct3D-App besser zu verstehen. Sie können dieses Tool jeweils mit Desktop- und universellen Windows-Apps verwenden, jedoch nicht mit ASP.NET-Apps. Das Tool **GPU-Nutzung** kann entweder während des Debuggens über das Fenster **Diagnosetools** ausgeführt werden (**Debuggen &gt; Diagnosetools anzeigen**) oder außerhalb des Debuggers (**Debuggen &gt; Leistungsanalyse...**).  
  
## <a name="application-timeline"></a>Anwendungszeitachse  
 ![DiagAppTimeline](../profiling/media/diagapptimeline.png "DiagAppTimeline")  
  
 Das [Application Timeline](../profiling/application-timeline.md)-Tool hilft Ihnen dabei, die Leistung von XAML-Anwendungen zu verbessern, indem es eine detaillierte Ansicht des Ressourcenverbrauchs der Anwendung bereitstellt. Sie können die **Anwendungszeitachse** mit Desktop- und universellen Windows-Apps verwenden, jedoch nicht mit ASP.NET-Apps. Das Tool **Anwendungszeitachse** kann im Fenster **Diagnosetools** (**Debuggen &gt; Leistungsanalyse...**) ausgeführt werden.  
  
## <a name="perftips"></a>PerfTips  
 ![DiagPerfTips](../profiling/media/diagperftips.png "DiagPerfTips")  
  
 Wenn der Debugger die Ausführung an einem Haltepunkt oder während einer schrittweisen Ausführung stoppt, wird die verstrichene Zeit zwischen der Pause und dem vorherigen Haltepunkt als QuickInfo im Editor-Fenster angezeigt. Mit diesen [PerfTips](../profiling/perftips.md) können Sie die Leistung Ihrer App während des Debuggens überwachen und analysieren. Sie können **PerfTips** in Desktop-Apps, universellen Windows-Apps und ASP.NET-Apps anzeigen.  
  
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
 Im Produktivbetrieb empfiehlt es sich, die Profilerstellung mithilfe von [vsperf.exe über die Befehlszeile](../profiling/using-the-profiling-tools-from-the-command-line.md) durchzuführen, um ein CPU-Profil zu erhalten. Azure App Service bietet Ihnen über [Server Explorer oder das Kudu-Portal](https://azure.microsoft.com/blog/remote-profiling-support-in-azure-app-service/)die Möglichkeit, von einem entfernten Standort aus ein Profil zu erstellen.  
  
## <a name="which-tool-should-i-use"></a>Welches Tool soll ich verwenden?  
 Hier sehen Sie eine Tabelle, in der die verschiedenen Tools aufgelistet sind, die Visual Studio anbietet sowie die verschiedenen Projekttypen, die Sie mit diesen verwenden können:  
  
|Leistungstool|Windows-Desktop|Windows Universell/Store|ASP.NET|  
|----------------------|---------------------|------------------------------|-------------|  
|[Speicherauslastung](../profiling/memory-usage.md)|ja|ja|Nein|  
|[CPU-Auslastung](../profiling/cpu-usage.md)|ja|ja|nur Azure App Service|  
|[GPU-Nutzung](../debugger/gpu-usage.md)|ja|ja|Nein|  
|[Anwendungszeitachse](../profiling/application-timeline.md)|ja|ja|Nein|  
|[PerfTips](../profiling/perftips.md)|ja|ja für XAML, nicht für HTML|Nein|  
|[Leistungs-Explorer](../profiling/performance-explorer.md)|ja|Nein|ja|  
|[IntelliTrace](../debugger/intellitrace.md)|nur .NET Enterprise|nur .NET Enterprise|nur .NET Enterprise|  
|[HTML UI responsiveness](../profiling/html-ui-responsiveness.md)|Nein|ja für HTML, nicht für XAML|Nein|  
|[JavaScript-Speicher](../profiling/javascript-memory.md)|Nein|ja für HTML, nicht für XAML|Nein|  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio-IDE](../ide/visual-studio-ide.md)
