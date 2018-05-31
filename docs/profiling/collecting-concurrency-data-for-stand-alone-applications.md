---
title: Sammeln von Parallelitätsdaten für eigenständige Anwendungen über die Profiler-Befehlszeile | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- concurrency profiling method
- profiling tools,concurrency method
ms.assetid: 0a2c6d8a-50b3-48aa-b617-9137b049d21e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 20ae775a6dc49dd2a6dd3cb391eeaf69ff7fa32c
ms.sourcegitcommit: 37144589d9f850ff81ec7bfb884429989925a43d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2018
ms.locfileid: "34335943"
---
# <a name="collect-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line"></a>Sammeln von Parallelitätsdaten für eigenständige Anwendungen über die Profiler-Befehlszeile
Mit der Parallelitätsmethode der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Profilerstellungstools können Sie Ressourcenkonfliktdaten und Threadaktivitätsdaten sammeln, die Auskunft über CPU-Auslastung, Threadkonflikte, Threadmigration, Synchronisierungsverzögerungen, überlappende E/A-Bereiche und andere Systemereignisse geben.  
  

## <a name="common-tasks"></a>Allgemeine Aufgaben  
  
|Aufgabe|Verwandter Inhalt|  
|----------|---------------------|  
|**Starten einer .NET Framework-Anwendung und Profilerstellung von Parallelitätsdaten**|-   [Vorgehensweise: Starten einer eigenständigen .NET Framework-Anwendung mit dem Profiler zum Sammeln von Parallelitätsdaten über die Befehlszeile](../profiling/how-to-launch-a-stand-alone-dotnet-framework-app-to-collect-concurrency-data.md)|  
|**Starten einer C/C++-Anwendung und Profilerstellung von Parallelitätsdaten**|-   [Vorgehensweise: Starten einer nativen, eigenständigen Anwendung mit dem Profiler zum Sammeln von Parallelitätsdaten über die Befehlszeile](../profiling/how-to-launch-a-stand-alone-native-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**Anfügen des Profilers an eine aktive .NET Framework-Anwendung**|-   [Vorgehensweise: Anfügen des Profilers an eine eigenständige .NET Framework-Anwendung zum Sammeln von Parallelitätsdaten über die Befehlszeile](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-concurrency-data.md)|  
|**Anfügen des Profilers an eine aktive C/C++-Anwendung**|-   [Vorgehensweise: Anfügen des Profilers an eine native, eigenständige Anwendung und Sammeln von Parallelitätsdaten über die Befehlszeile](../profiling/how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-concurrency-data-by-using-the-command-line.md)|  
  
## <a name="related-tasks"></a>Verwandte Aufgaben
  
### <a name="profile-stand-alone-applications"></a>Profilerstellung für eigenständige Anwendungen  
  
|Aufgabe|Verwandter Inhalt|  
|----------|---------------------|  
|**Profilerstellung mit der Samplingmethode**|-   [Sammeln von Anwendungsstatistiken durch Sampling](../profiling/collecting-application-statistics-for-stand-alone-applications.md)|  
|**Profilerstellung mit der Instrumentationsmethode**|-   [Sammeln ausführlicher Zeitsteuerungsdaten mithilfe der Instrumentierung](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md)|  
|**Profilerstellung der .NET-Speicherbelegung und Garbage Collection**|-   [Sammeln von .NET Framework-Arbeitsspeicherdaten](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md)|  
|**Hinzufügen von Ebeneninteraktionsdaten**|-   [Erfassen von Ebeneninteraktionsdaten](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
  
### <a name="profile-concurrency-issues"></a>Parallelitätsprobleme bei der Profilerstellung  
  
|Aufgabe|Verwandter Inhalt|  
|----------|---------------------|  
|**Profilerstellung für ASP.NET-Anwendungen**|-   [Sammeln von Parallelitätsdaten](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|  
|**Profilerstellung für Dienste**|-   [Sammeln von Parallelitätsdaten](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|  
  
### <a name="analyze-concurrency-data-views-and-reports"></a>Analysieren von Ansichten und Berichten zu Parallelitätsdaten  
 [Ansichten für Ressourcenkonfliktdaten](../profiling/resource-contention-data-views.md)  
  
 [Nebenläufigkeitsschnellansicht](../profiling/concurrency-visualizer.md)  
  
## <a name="reference"></a>Referenz  
 [Referenz zu Profilerstellungstools für die Befehlszeile](../profiling/command-line-profiling-tools-reference.md)