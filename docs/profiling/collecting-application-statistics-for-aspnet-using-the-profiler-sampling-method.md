---
title: Erfassen von Statistiken für ASP.NET-Web-Apps | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, sampling method
- sampling profling method
ms.assetid: f8383ab1-eb49-4d3f-8608-d8b4d51a81be
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 9be304398fcefaf6a38ca7e1d557f2c9146b4872
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/11/2018
---
# <a name="collect-statistics-for-aspnet-web-apps"></a>Erfassen von Statistiken für ASP.NET-Web-Apps

In diesem Abschnitt werden die Prozeduren und Optionen zum Sammeln von Leistungsstatistiken für eine ASP.NET-Webanwendung mithilfe der Befehlszeilentools **VSPerfASPNETCmd** und **VSPerfCmd** sowie mithilfe der Samplingmethode zur Profilerstellung beschrieben.  
  
> [!NOTE]
>  Verbesserte Sicherheitsfunktionen in Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung des Visual Studio-Profilers auf diesen Plattformen. Außerdem benötigen UWP-Apps neue Erfassungsmethoden. Siehe [Profilerstellungstools für Windows 8- und Windows Server 2012-Anwendungen](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
> [!NOTE]
>  Mit dem Tool **VSPerfCmd** stehen Ihnen zwar sämtliche Funktionen der Profilerstellungstools zur Verfügung (beispielsweise Anhalten und Fortsetzen der Profilerstellung oder Sammeln zusätzlicher Daten aus Prozessor- und Windows-Leistungsindikatoren), es wird jedoch empfohlen, das Befehlszeilentool **VSPerfASPNETCmd** zu verwenden, wenn Sie diese Funktionen nicht benötigen. Das Befehlszeilentool **VSPerfASPNETCmd** ist die bevorzugte Methode für die Profilerstellung für ASP.NET-Websites mithilfe des eigenständigen Profilers. Anders als beim Befehlszeilentool [VSPerfCmd](../profiling/vsperfcmd.md) müssen keine Umgebungsvariablen festgelegt werden, und der Computer muss nicht neu gestartet werden. Weitere Informationen finden Sie unter [Schnelle Website-Profilerstellung mit VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).  
  
## <a name="common-tasks"></a>Allgemeine Aufgaben  
  
|Aufgabe|Verwandter Inhalt|  
|----------|---------------------|  
|**Anfügen des Profilers an eine ASP.NET-Anwendung**|-   [Vorgehensweise: Anfügen des Profilers an eine ASP.NET-Webanwendung zum Sammeln von Anwendungsstatistiken über die Befehlszeile](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line.md)|  
  
## <a name="related-tasks"></a>Verwandte Aufgaben  
  
### <a name="profiling-aspnet-web-applications"></a>Profilerstellung für ASP.NET-Webanwendungen  
  
|Aufgabe|Verwandter Inhalt|  
|----------|---------------------|  
|**Profilerstellung mit der Instrumentationsmethode**|-   [Sammeln ausführlicher Zeitsteuerungsdaten für eine ASP.NET-Webanwendung über die Befehlszeile mit der Profiler-Instrumentationsmethode](../profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method.md)|  
|**Profilerstellung der Speicherbelegung und Garbage Collection**|-   [Sammeln von Speicherdaten aus einer ASP.NET-Webanwendung über die Profiler-Befehlszeile](../profiling/collecting-memory-data-from-an-aspnet-web-application.md)|  
|**Profilerstellung für Ressourcenkonflikte und Threadaktivität**|-   [Sammeln von Parallelitätsdaten für einen Dienst über die Profiler-Befehlszeile](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|  
  
### <a name="sampling-method"></a>Samplingmethode  
  
|Aufgabe|Verwandter Inhalt|  
|----------|---------------------|  
|**Profilerstellung für eigenständige (Client-)Anwendungen**|-   [Sammeln von Anwendungsstatistiken für eigenständige Anwendungen über die Profiler-Befehlszeile](../profiling/collecting-application-statistics-for-stand-alone-applications.md)|  
|-   **Profilerstellung für Dienste**|-   [Sammeln von Anwendungsstatistiken für Dienste mithilfe der Profiler-Samplingmethode](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|  
  
### <a name="analyzing-sampling-data-views-and-reports"></a>Analysieren von Ansichten und Berichten für Samplingdaten  
 [Datenansichten der Profiler-Samplingmethode](../profiling/profiler-sampling-method-data-views.md)