---
title: Sammeln von Anwendungsstatistiken für Dienste mithilfe der Profiler-Samplingmethode | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 07840ab2-3a92-4744-ac87-48b19e0ceecd
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f3f556a039ab131a563a90010112009b39f4c981
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840909"
---
# <a name="collecting-application-statistics-for-services-by-using-the-profiler-sampling-method"></a>Sammeln von Anwendungsstatistiken für Dienste mithilfe der Profiler-Samplingmethode
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Abschnitt werden die Prozeduren und Optionen zum Sammeln von Leistungsstatistiken für Windows-Dienste mithilfe der Samplingmethode über die Befehlszeile beschrieben.  
  
> [!NOTE]
> Verbesserte Sicherheitsfeatures in Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung des Visual Studio-Profilers auf diesen Plattformen. Außerdem benötigen Windows Store-Apps neue Erfassungsmethoden. Informationen hierzu finden Sie unter [Performance Tools on Windows 8 and Windows Server 2012 applications (Profilerstellung für Windows 8- und Windows Server 2012-Anwendungen)](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="common-tasks"></a>Allgemeine Aufgaben  
  
|Aufgabe|Verwandte Inhalte|  
|----------|---------------------|  
|**Anfügen des Profilers an einen .NET-Dienst**|-   [Vorgehensweise: Anfügen des Profilers an einen .NET-Dienst zum Sammeln von Anwendungsstatistiken über die Befehlszeile](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-application-statistics-by-using-the-command-line.md)|  
|**Hinzufügen von Ebeneninteraktionsdaten**|-   [Hinzufügen von Ebeneninteraktionsdaten über die Befehlszeile](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
|**Anfügen des Profilers an einen C/C++-Dienst**|-   [Vorgehensweise: Anfügen des Profilers an einen nativen Dienst zum Sammeln von Anwendungsstatistiken über die Befehlszeile](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line.md)|  
  
## <a name="related-tasks"></a>Related Tasks  
  
### <a name="profiling-windows-services"></a>Profilerstellung für Windows-Dienste  
  
|Aufgabe|Verwandte Inhalte|  
|----------|---------------------|  
|**Profilerstellung mit der Instrumentationsmethode**|-   [Sammeln ausführlicher Zeit Steuerungsdaten mithilfe der Instrumentierung](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method-from-the-profiler-command-line.md)|  
|**Profilerstellung der .NET-Speicherbelegung und Garbage Collection**|-   [Sammeln von .NET-Arbeitsspeicherdaten](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|  
|**Profilerstellung für Ressourcenkonflikte und Threadaktivität**|-   [Sammeln von Parallelitätsdaten](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|  
  
### <a name="profiling-by-using-the-sampling-method"></a>Profilerstellung mithilfe der Samplingmethode  
  
|Aufgabe|Verwandte Inhalte|  
|----------|---------------------|  
|**Profilerstellung für eigenständige (Client-)Anwendungen**|-   [Sammeln von Anwendungs Statistiken mithilfe von Sampling](../profiling/collecting-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Profilerstellung für ASP.NET-Webanwendungen**|-   [Sammeln von Anwendungs Statistiken mithilfe von Sampling](/visualstudio/profiling/collecting-concurrency-data-for-an-aspnet-web-application?view=vs-2015)|  
  
### <a name="analyzing-sampling-data-views-and-reports"></a>Analysieren von Ansichten und Berichten für Samplingdaten  
 [Datenansichten der Samplingmethode](../profiling/profiler-sampling-method-data-views.md)
