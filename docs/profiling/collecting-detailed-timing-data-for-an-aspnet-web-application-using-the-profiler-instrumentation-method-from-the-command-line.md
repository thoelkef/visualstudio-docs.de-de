---
title: "Sammeln ausf&#252;hrlicher Zeitsteuerungsdaten f&#252;r eine ASP.NET-Webanwendung &#252;ber die Befehlszeile mit der Profiler-Instrumentationsmethode | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Instrumentationsprofilerstellungs-Methode"
  - "Profilerstellungstools, Instrumentationsmethode"
ms.assetid: 29f2fc55-aaf7-4e18-a672-8815455fba73
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Sammeln ausf&#252;hrlicher Zeitsteuerungsdaten f&#252;r eine ASP.NET-Webanwendung &#252;ber die Befehlszeile mit der Profiler-Instrumentationsmethode
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In diesem Abschnitt werden die Prozeduren und Optionen zum Erfassen von ausführlichen Leistungsdaten für eine [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Webanwendung mithilfe des **VSPerfCmd**\-Befehlszeilentools und der Instrumentationsmethode beschrieben.  
  
> [!NOTE]
>  Mit dem Tool **VSPerfCmd** erhalten Sie Vollzugriff auf die Funktionen der Profilerstellungstools – einschließlich Anhalten und Fortsetzen der Profilerstellung sowie Sammeln zusätzlicher Daten aus Prozessor\- und Windows\-Leistungsindikatoren.  Wenn Sie diese Funktionen nicht benötigen, können Sie auch das Befehlszeilentool **VSPerfASPNETCmd** verwenden.  Verglichen mit dem Befehlszeilentool [VSPerfCmd](../profiling/vsperfcmd.md) müssen keine Umgebungsvariablen festgelegt werden, und der Computer muss nicht neu gestartet werden.  Weitere Informationen finden Sie unter [Schnelle Website\-Profilerstellung mit VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).  
  
## Allgemeine Aufgaben  
  
|Aufgabe|Verwandter Inhalt|  
|-------------|-----------------------|  
|**Profilerstellung für statisch kompilierte Binärdateien**|-   [Gewusst wie: Instrumentieren einer statisch kompilierten ASP.NET\-Anwendung und Sammeln von ausführlichen Zeitsteuerungsdaten](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line.md)|  
|**Profilerstellung für dynamisch kompilierte Binärdateien**|-   [Gewusst wie: Instrumentieren einer dynamisch kompilierten ASP.NET\-Anwendung und Sammeln von ausführlichen Zeitsteuerungsdaten](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line.md)|  
  
## Verwandte Aufgaben  
  
### Profilerstellung für ASP.NET\-Webanwendungen  
  
|Aufgabe|Verwandter Inhalt|  
|-------------|-----------------------|  
|**Profilerstellung mit der Samplingmethode**|-   [Sammeln von Anwendungsstatistiken durch Sampling](../profiling/collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line.md)|  
|**Profilerstellung für Speicherbelegung und Garbage Collection**|-   [Sammeln von Arbeitsspeicherdaten](../profiling/collecting-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line.md)|  
|**Profilerstellung für Ressourcenkonflikte und Threadaktivität**|-   [Sammeln von Parallelitätsdaten](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
  
### Profilerstellung mithilfe der Instrumentationsmethode  
  
|Aufgabe|Verwandter Inhalt|  
|-------------|-----------------------|  
|**Profilerstellung für eigenständige \(Client\-\)Anwendungen**|-   [Sammeln ausführlicher Zeitsteuerungsdaten mithilfe der Instrumentation](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application-by-using-the-profiler-command-line.md)|  
|**Profilerstellung für Dienste**|-   [Sammeln ausführlicher Zeitsteuerungsdaten mithilfe der Instrumentation](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method-from-the-profiler-command-line.md)|  
  
### Analysieren von Ansichten und Berichten mit Instrumentationsdaten  
 [Instrumentationsmethoden\-Datenansichten](../profiling/instrumentation-method-data-views.md)