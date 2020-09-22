---
title: Sammeln von Speicherdaten aus einer ASP.NET-Webanwendung über die Profiler-Befehlszeile | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- .NET memory profiling method
- profiling tools,.NET memory method
ms.assetid: 57acf2b0-327a-4c0e-8078-ac2f6d99457d
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0f7c759d4c2c4760be6782a518f4cdf209e828d4
ms.sourcegitcommit: fb8babf5cd72f1fc2f97ffe4ad7b62d91f325f61
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/07/2020
ms.locfileid: "90842318"
---
# <a name="collecting-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line"></a>Sammeln von Speicherdaten aus einer ASP.NET-Webanwendung über die Profiler-Befehlszeile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Abschnitt werden die Prozeduren und Optionen für das Sammeln von Speicherbelegungs- und Objektlebensdauerdaten für eine ASP.NET-Webanwendung mithilfe des Befehls **VSPerfCmd** in der Befehlszeile beschrieben.  
  
> [!NOTE]
> Mit dem Tool **VSPerfCmd** stehen Ihnen sämtliche Funktionen der Profilerstellungstools zur Verfügung, beispielsweise Anhalten und Fortsetzen der Profilerstellung oder Sammeln zusätzlicher Daten aus Prozessor- und Windows-Leistungsindikatoren. Sie können auch das Befehlszeilentool **VSPerfASPNETCmd** verwenden, wenn Sie diese Funktionen nicht benötigen. Anders als beim Befehlszeilentool [VSPerfCmd](../profiling/vsperfcmd.md) müssen keine Umgebungsvariablen festgelegt werden, und der Computer muss nicht neu gestartet werden. Weitere Informationen finden Sie unter [schnelle Website-Profilerstellung mit vsperfaspnetcmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).  
  
## <a name="common-tasks"></a>Allgemeine Aufgaben  
  
|Aufgabe|Verwandter Inhalt|  
|----------|---------------------|  
|**Anfügen des Profilers an eine aktive ASP.NET-Anwendung**|-   [Vorgehensweise: Anfügen des Profilers an eine ASP.NET-Webanwendung zum Sammeln von Arbeitsspeicherdaten](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)|  
|**Instrumentieren statisch kompilierter Binärdateien**|-   [Gewusst wie: Instrumentieren einer statisch kompilierten ASP.NET-Anwendung und Sammeln von Speicherdaten](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)|  
|**Instrumentieren dynamisch kompilierter Binärdateien**|-   [Gewusst wie: Instrumentieren einer dynamisch kompilierten ASP.NET-Anwendung und Sammeln von Speicherdaten](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)|  
  
## <a name="related-tasks"></a>Related Tasks  
  
### <a name="profiling-aspnet-web-applications"></a>Profilerstellung für ASP.NET-Webanwendungen  
  
|Aufgabe|Verwandter Inhalt|  
|----------|---------------------|  
|**Profilerstellung mit der Samplingmethode**|-   [Sammeln von Anwendungs Statistiken mithilfe von Sampling](../profiling/collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line.md)|  
|**Profilerstellung mit der Instrumentationsmethode**|-   [Sammeln ausführlicher Zeit Steuerungsdaten mithilfe der Instrumentierung](/visualstudio/profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method?view=vs-2015)|  
|**Profilerstellung für Ressourcenkonflikte und Threadaktivität**|-   [Sammeln von Parallelitätsdaten](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
  
### <a name="profiling-net-framework-memory-data"></a>Profilerstellung für .NET Framework-Arbeitsspeicherdaten  
  
|Aufgabe|Verwandter Inhalt|  
|----------|---------------------|  
|**Profilerstellung für eigenständige (Client-)Anwendungen**|-   [Sammeln von .NET Framework-Speicherdaten für eigenständige Anwendungen über die Profiler-Befehlszeile](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Profilerstellung für Dienste**|-   [Sammeln von .NET-Arbeitsspeicherdaten](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|  
  
### <a name="analyzing-net-memory-data-views-and-reports"></a>Analysieren von Ansichten und Berichten für .NET-Arbeitsspeicherdaten  
 [.NET-Arbeitsspeicher Datenansichten](../profiling/dotnet-memory-data-views.md)  
  
## <a name="reference"></a>Verweis  
 [Befehlszeilen Profilerstellungstools Referenz](../profiling/command-line-profiling-tools-reference.md)
