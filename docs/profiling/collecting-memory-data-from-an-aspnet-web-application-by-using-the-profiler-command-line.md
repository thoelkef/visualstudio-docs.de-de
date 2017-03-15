---
title: "Sammeln von Speicherdaten aus einer ASP.NET-Webanwendung &#252;ber die Profiler-Befehlszeile | Microsoft Docs"
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
  - ".NET-Arbeitsspeicher-Profilerstellungsmethode"
  - "Profilerstellungstools, .NET-Arbeitsspeichermethode"
ms.assetid: 57acf2b0-327a-4c0e-8078-ac2f6d99457d
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Sammeln von Speicherdaten aus einer ASP.NET-Webanwendung &#252;ber die Profiler-Befehlszeile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In diesem Abschnitt werden die Prozeduren und die Optionen zum Sammeln von Daten zur Speicherbelegung und zur Objektlebensdauer für eine ASP.NET\-Webanwendung mithilfe des Befehlszeilentools **VSPerfCmd** beschrieben.  
  
> [!NOTE]
>  Mit dem Tool **VSPerfCmd** erhalten Sie Vollzugriff auf die Funktionen der Profilerstellungstools – einschließlich Anhalten und Fortsetzen der Profilerstellung sowie Sammeln zusätzlicher Daten aus Prozessor\- und Windows\-Leistungsindikatoren.  Wenn Sie diese Funktionen nicht benötigen, können Sie auch das Befehlszeilentool **VSPerfASPNETCmd** verwenden.  Verglichen mit dem Befehlszeilentool [VSPerfCmd](../profiling/vsperfcmd.md) müssen keine Umgebungsvariablen festgelegt werden, und der Computer muss nicht neu gestartet werden.  Weitere Informationen finden Sie unter [Schnelle Website\-Profilerstellung mit VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).  
  
## Allgemeine Aufgaben  
  
|Aufgabe|Verwandter Inhalt|  
|-------------|-----------------------|  
|**Anfügen des Profilers an eine ausgeführte ASP.NET\-Anwendung**|-   [Gewusst wie: Anfügen des Profilers an eine ASP.NET\-Webanwendung zum Sammeln von Arbeitsspeicherdaten](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)|  
|**Instrumentieren statisch kompilierter Binärdateien**|-   [Gewusst wie: Instrumentieren einer statisch kompilierten ASP.NET\-Anwendung und Sammeln von Speicherdaten](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)|  
|**Instrumentieren dynamisch kompilierter Binärdateien**|-   [Gewusst wie: Instrumentieren einer dynamisch kompilierten ASP.NET\-Anwendung und Sammeln von Speicherdaten](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)|  
  
## Verwandte Aufgaben  
  
### Profilerstellung für ASP.NET\-Webanwendungen  
  
|Aufgabe|Verwandter Inhalt|  
|-------------|-----------------------|  
|**Profilerstellung mit der Samplingmethode**|-   [Sammeln von Anwendungsstatistiken durch Sampling](../profiling/collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line.md)|  
|**Profilerstellung mit der Instrumentationsmethode**|-   [Sammeln ausführlicher Zeitsteuerungsdaten mithilfe der Instrumentation](../profiling/collecting-detailed-timing-data-for-an-aspnet-web-application-using-the-profiler-instrumentation-method-from-the-command-line.md)|  
|**Profilerstellung für Ressourcenkonflikte und Threadaktivität**|-   [Sammeln von Parallelitätsdaten](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
  
### Profilerstellung für .NET Framework\-Arbeitsspeicherdaten  
  
|Aufgabe|Verwandter Inhalt|  
|-------------|-----------------------|  
|**Profilerstellung für eigenständige \(Client\-\)Anwendungen**|-   [Sammeln von .NET Framework\-Arbeitsspeicherdaten](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Profilerstellung für Dienste**|-   [Sammeln von .NET\-Arbeitsspeicherdaten](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|  
  
### Analysieren von Ansichten und Berichten für .NET\-Arbeitsspeicherdaten  
 [.NET\-Arbeitsspeicherdatenansichten](../profiling/dotnet-memory-data-views.md)  
  
## Verweis  
 [Referenz zu Profilerstellungstools für die Befehlszeile](../profiling/command-line-profiling-tools-reference.md)