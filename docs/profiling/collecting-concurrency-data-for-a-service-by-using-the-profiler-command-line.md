---
title: Sammeln von Parallelitätsdaten für einen Dienst über die Profiler-Befehlszeile | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 275aacba-b2af-4d34-8931-ee30d777a256
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e3bd10121973c88e7a211aa741664b8ffb9b7bbc
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/11/2018
---
# <a name="collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line"></a>Sammeln von Parallelitätsdaten für einen Dienst über die Profiler-Befehlszeile
Mit der Parallelitätsmethode der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Profilerstellungstools können Sie Ressourcenkonfliktdaten und Threadaktivitätsdaten sammeln, die Auskunft über CPU-Auslastung, Threadkonflikte, Threadmigration, Synchronisierungsverzögerungen, überlappende E/A-Bereiche und andere Systemereignisse geben.  
  
> [!NOTE]
>  Verbesserte Sicherheitsfunktionen in Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung des Visual Studio-Profilers auf diesen Plattformen. Außerdem benötigen UWP-Apps neue Erfassungsmethoden. Siehe [Profilerstellungstools für Windows 8- und Windows Server 2012-Anwendungen](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="common-tasks"></a>Allgemeine Aufgaben  
  
|Aufgabe|Verwandter Inhalt|  
|----------|---------------------|  
|**Anfügen an einen laufenden .NET-Dienst**|-   [Vorgehensweise: Anfügen des Profilers an einen .NET-Dienst zum Sammeln von Parallelitätsdaten über die Befehlszeile](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**Hinzufügen von Ebeneninteraktionsdaten**|-   [Hinzufügen von Ebeneninteraktionsdaten über die Befehlszeile](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
|**Anfügen an einen laufenden C/C++-Dienst**|-   [Vorgehensweise: Anfügen des Profilers an einen eigenständigen Dienst zum Sammeln von Parallelitätsdaten über die Befehlszeile](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|  
  
## <a name="related-tasks"></a>Verwandte Aufgaben  
  
### <a name="profiling-windows-services"></a>Profilerstellung für Windows-Dienste  
  
|Aufgabe|Verwandter Inhalt|  
|----------|---------------------|  
|**Profilerstellung mit der Samplingmethode**|-   [Sammeln von Anwendungsstatistiken durch Sampling](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|  
|**Profilerstellung mit der Instrumentationsmethode**|-   [Sammeln ausführlicher Zeitsteuerungsdaten für eine ASP.NET-Webanwendung über die Befehlszeile mit der Profiler-Instrumentationsmethode](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md)|  
|**Profilerstellung der .NET-Speicherbelegung und Garbage Collection**|-   [Sammeln von Speicherdaten für .NET Framework-Dienste über die Profiler-Befehlszeile](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|  
  
### <a name="profiling-concurrency-data"></a>Profilerstellung für Parallelitätsdaten  
  
|Aufgabe|Verwandter Inhalt|  
|----------|---------------------|  
|**Profilerstellung für eigenständige Anwendungen**|-   [Sammeln paralleler Daten für eigenständige Anwendungen über die Profiler-Befehlszeile](../profiling/collecting-concurrency-data-for-stand-alone-applications.md)|  
|**Profilerstellung für ASP.NET-Webanwendungen**|-   [Sammeln von Parallelitätsdaten für einen Dienst über die Profiler-Befehlszeile](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|  
  
### <a name="analyzing-concurrency-data-views-and-reports"></a>Analysieren von Parallelitätsdatenansichten und -berichten  
 [Ansichten für Ressourcenkonfliktdaten](../profiling/resource-contention-data-views.md)  
  
 [Nebenläufigkeitsschnellansicht](../profiling/concurrency-visualizer.md)  
  
## <a name="reference"></a>Referenz  
 [Command-Line Profiling Tools Reference (Referenz zu Profilerstellungstools für die Befehlszeile)](../profiling/command-line-profiling-tools-reference.md)