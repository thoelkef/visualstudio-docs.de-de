---
title: "Sammeln von Anwendungsstatistiken f&#252;r eine ASP.NET-Webanwendungen &#252;ber die Befehlszeile mit der Profiler-Samplingmethode | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Profilerstellungstools, Samplingmethode"
  - "Sampling-Profilerstellungsmethode"
ms.assetid: f8383ab1-eb49-4d3f-8608-d8b4d51a81be
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Sammeln von Anwendungsstatistiken f&#252;r eine ASP.NET-Webanwendungen &#252;ber die Befehlszeile mit der Profiler-Samplingmethode
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In diesem Abschnitt werden die Prozeduren und Optionen zum Sammeln von Leistungsstatistiken für eine ASP.NET\-Webanwendung mithilfe der Befehlszeilentools **VSPerfASPNETCmd** und **VSPerfCmd** sowie mithilfe der Samplingmethode zur Profilerstellung beschrieben.  
  
> [!NOTE]
>  Verbesserte Sicherheitsfeatures in Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung des Visual Studio\-Profilers auf diesen Plattformen.  Außerdem benötigen Windows Store\-Apps neue Erfassungsmethoden.  Siehe [Profilerstellung für Windows 8\- und Windows Server 2012\-Anwendungen](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
> [!NOTE]
>  Mit dem Tool **VSPerfCmd** stehen Ihnen zwar sämtliche Funktionen der Profilerstellungstools zur Verfügung \(beispielsweise Anhalten und Fortsetzen der Profilerstellung oder Sammeln zusätzlicher Daten aus Prozessor\- und Windows\-Leistungsindikatoren\), es wird jedoch empfohlen, den Befehl **VSPerfASPNETCmd** zu verwenden, wenn Sie diese Funktionen nicht benötigen.  Das Befehlszeilentool **VSPerfASPNETCmd** ist die bevorzugte Methode für die Profilerstellung für ASP.NET\-Websites mithilfe des eigenständigen Profilers.  Verglichen mit dem Befehlszeilentool [VSPerfCmd](../profiling/vsperfcmd.md) müssen keine Umgebungsvariablen festgelegt werden, und der Computer muss nicht neu gestartet werden.  Weitere Informationen finden Sie unter [Schnelle Website\-Profilerstellung mit VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).  
  
## Allgemeine Aufgaben  
  
|Aufgabe|Verwandter Inhalt|  
|-------------|-----------------------|  
|**Anfügen des Profilers an eine ASP.NET\-Anwendung**|-   [Gewusst wie: Anfügen des Profilers an eine ASP.NET\-Webanwendung zum Sammeln von Anwendungsstatistiken](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line.md)|  
  
## Verwandte Aufgaben  
  
### Profilerstellung für ASP.NET\-Webanwendungen  
  
|Aufgabe|Verwandter Inhalt|  
|-------------|-----------------------|  
|**Profilerstellung mit der Instrumentationsmethode**|-   [Sammeln ausführlicher Zeitsteuerungsdaten mithilfe der Instrumentation](../profiling/collecting-detailed-timing-data-for-an-aspnet-web-application-using-the-profiler-instrumentation-method-from-the-command-line.md)|  
|**Profilerstellung für Speicherbelegung und Garbage Collection**|-   [Sammeln von Arbeitsspeicherdaten](../profiling/collecting-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line.md)|  
|**Profilerstellung für Ressourcenkonflikte und Threadaktivität**|-   [Sammeln von Parallelitätsdaten](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
  
### Samplingmethode  
  
|Aufgabe|Verwandter Inhalt|  
|-------------|-----------------------|  
|**Profilerstellung für eigenständige \(Client\-\)Anwendungen**|-   [Sammeln von Anwendungsstatistiken durch Sampling](../profiling/collecting-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|-   **Profilerstellung für Dienste**|-   [Sammeln von Anwendungsstatistiken durch Sampling](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|  
  
### Analysieren von Ansichten und Berichten für Samplingdaten  
 [Datenansichten der Samplingmethode](../profiling/profiler-sampling-method-data-views.md)