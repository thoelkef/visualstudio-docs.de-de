---
title: "Sammeln von Parallelit&#228;tsdaten f&#252;r einen Dienst &#252;ber die Profiler-Befehlszeile | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 275aacba-b2af-4d34-8931-ee30d777a256
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Sammeln von Parallelit&#228;tsdaten f&#252;r einen Dienst &#252;ber die Profiler-Befehlszeile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Mit der Parallelitätsmethode der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Profilerstellungstools können Sie Ressourcenkonfliktdaten und Threadaktivitätsdaten sammeln, die Aufschluss über CPU\-Auslastung, Threadkonflikte, Threadmigration, Synchronisierungsverzögerungen, überlappende EA\-Bereiche und andere Systemereignisse geben.  
  
> [!NOTE]
>  Verbesserte Sicherheitsfeatures in Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung des Visual Studio\-Profilers auf diesen Plattformen.  Außerdem benötigen Windows Store\-Apps neue Erfassungsmethoden.  Siehe [Profilerstellung für Windows 8\- und Windows Server 2012\-Anwendungen](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## Allgemeine Aufgaben  
  
|Aufgabe|Verwandter Inhalt|  
|-------------|-----------------------|  
|**Anfügen an einen aktiven .NET\-Dienst**|-   [Gewusst wie: Anfügen des Profilers an einen .NET\-Dienst zum Sammeln von Parallelitätsdaten](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**Hinzufügen von Ebeneninteraktionsdaten**|-   [Erfassen von Ebeneninteraktionsdaten](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
|**Anfügen an einen aktiven C\/C\+\+\-Dienst**|-   [Gewusst wie: Anfügen des Profilers an einen systemeigenen Dienst zum Sammeln paralleler Daten](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|  
  
## Verwandte Aufgaben  
  
### Profilerstellung für Windows\-Dienste  
  
|Aufgabe|Verwandter Inhalt|  
|-------------|-----------------------|  
|**Profilerstellung mit der Samplingmethode**|-   [Sammeln von Anwendungsstatistiken durch Sampling](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|  
|**Profilerstellung mit der Instrumentationsmethode**|-   [Sammeln ausführlicher Zeitsteuerungsdaten mithilfe der Instrumentation](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method-from-the-profiler-command-line.md)|  
|**Profilerstellung für .NET\-Speicherbelegung und Garbage Collection**|-   [Sammeln von .NET\-Arbeitsspeicherdaten](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|  
  
### Parallelitätsdaten für die Profilerstellung  
  
|Aufgabe|Verwandter Inhalt|  
|-------------|-----------------------|  
|**Profilerstellung für eigenständige Anwendungen**|-   [Sammeln von Parallelitätsdaten](../profiling/collecting-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Profilerstellung für ASP.NET\-Webanwendungen**|-   [Sammeln von Parallelitätsdaten](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
  
### Analysieren von Ansichten und Berichten für Parallelitätsdaten  
 [Ansichten für Ressourcenkonfliktdaten](../profiling/resource-contention-data-views.md)  
  
 [Parallelitätsschnellansicht](../profiling/concurrency-visualizer.md)  
  
## Verweis  
 [Referenz zu Profilerstellungstools für die Befehlszeile](../profiling/command-line-profiling-tools-reference.md)