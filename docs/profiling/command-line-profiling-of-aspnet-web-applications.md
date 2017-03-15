---
title: "Profilerstellung f&#252;r ASP.NET-Webanwendungen &#252;ber die Befehlszeile | Microsoft Docs"
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
  - "Profilerstellung für ASP.NET-Anwendungen"
  - "Profilerstellungstools, ASP.NET-Anwendungen"
ms.assetid: 897c00d5-5767-433b-a960-4a29c6023ede
caps.latest.revision: 21
caps.handback.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Profilerstellung f&#252;r ASP.NET-Webanwendungen &#252;ber die Befehlszeile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In diesem Abschnitt werden die Vorgehensweisen und Optionen zum Erfassen von Leistungsdaten für [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Webanwendungen mit den [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Profilerstellungstools über die Befehlszeile beschrieben.  
  
> [!NOTE]
>  Verbesserte Sicherheitsfeatures in Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung des Visual Studio\-Profilers auf diesen Plattformen.  Außerdem benötigen Windows Store\-Apps neue Erfassungsmethoden.  Siehe [Profilerstellung für Windows 8\- und Windows Server 2012\-Anwendungen](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## Allgemeine Aufgaben  
  
|Aufgabe|Verwandter Inhalt|  
|-------------|-----------------------|  
|**Einfaches Erfassen grundlegender ASP.NET\-Profilerstellungsdaten:** Verwenden Sie das Tool **VSPerfASPNETCmd**, um Sampling\-, Instrumentations\-, .NET\-Arbeitsspeicher\-, Konflikt\- oder Ebeneninteraktionsdaten ohne die Konfigurationsanforderungen und die Neustarts von Internetinformationsdienste \(IIS\) zu sammeln, die bei **VSPerfCmd** erforderlich sind.  Mit **VSPerfASPNETCmd** können keine zusätzlichen Daten erfasst werden, und auch die Datensammlung lässt sich nicht beeinflussen. **Note:**  **VSPerfASPNETCmd** ist das bevorzugte Tool, wenn mit dem eigenständigen Profiler ein Profil für ASP.NET\-Websites erstellt wird.|-   [Schnelle Website\-Profilerstellung mit VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)|  
|**Sammeln von Anwendungsstatistikdaten:** Sammeln Sie Leistungsstatistikdaten mit der Samplingmethode.  Samplingdaten sind beim Analysieren von CPU\-Auslastungsproblemen sowie zum Verständnis der allgemeinen Leistungsmerkmale einer Anwendung hilfreich.|-   [Sammeln von Anwendungsstatistiken durch Sampling](../profiling/collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line.md)|  
|**Sammeln ausführlicher Zeitsteuerungsdaten:** Sammeln Sie ausführliche Zeitsteuerungsinformationen mit der Instrumentationsmethode.  Instrumentationsdaten sind beim Analysieren von EA\-Problemen und für die detaillierte Analyse von Anwendungsszenarios hilfreich.|-   [Sammeln ausführlicher Zeitsteuerungsdaten mithilfe der Instrumentation](../profiling/collecting-detailed-timing-data-for-an-aspnet-web-application-using-the-profiler-instrumentation-method-from-the-command-line.md)|  
|**Sammeln von .NET\-Arbeitsspeicherdaten:** Sammeln Sie mit Sampling oder Instrumentation Daten zur .NET\-Speicherbelegung, die Auskunft über die Größe und Anzahl zugeordneter Objekte geben.  Sie können auch Objektlebensdauerdaten sammeln, die die Größe und Anzahl von Objekten angeben, die in jeder Garbage Collection\-Generation freigegeben werden.|-   [Sammeln von Arbeitsspeicherdaten](../profiling/collecting-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line.md)|  
|**Sammeln von Parallelitätsdaten:** Verwenden Sie die Parallelitätsmethode, um Daten zu Ressourcenkonflikten zu sammeln. **Note:**  Das Sammeln von Threadaktivitäts\- und Visualisierungsdaten wird für Webanwendungen nicht unterstützt.|-   [Sammeln von Parallelitätsdaten](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
|**Hinzufügen von Ebeneninteraktionsdaten:** Sie können Leistungsdaten zu synchronen [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)]\-Aufrufen der [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Webanwendung an eine Microsoft [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)]\-Datenbank hinzufügen.|-   [Erfassen von Ebeneninteraktionsdaten](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
  
## Verwandte Aufgaben  
  
|Aufgabe|Verwandter Inhalt|  
|-------------|-----------------------|  
|**Profilerstellung für eigenständige \(Client\-\)Anwendungen**|-   [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)|  
|**Profilerstellung für Dienste**|-   [Profilerstellungsdienste](../profiling/command-line-profiling-of-services.md)|