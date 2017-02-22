---
title: "Verwenden der Profilerstellungstools &#252;ber die Befehlszeile | Microsoft Docs"
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
  - "Befehlszeile, Leistungstools"
  - "Befehlszeilentools, Leistungstools"
  - "Profilerstellungstools, Befehlszeile"
  - "Tools, Befehlszeile"
  - "Befehlszeile, Tools"
ms.assetid: 6593fa82-181e-4009-a0ed-02aa24c2c063
caps.latest.revision: 35
caps.handback.revision: 35
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Verwenden der Profilerstellungstools &#252;ber die Befehlszeile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können die Befehlszeilentools der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Profilerstellungstools für die Profilerstellung von Anwendungen an der Eingabeaufforderung und für die Automatisierung der Profilerstellung mithilfe von Batchdateien und Skripts verwenden.  Sie können auch Berichtsdateien an einer Eingabeaufforderung generieren.  Sie können Daten auf Computern, auf denen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nicht installiert ist, mithilfe des einfachen eigenständigen Profilers sammeln.  
  
> [!NOTE]
>  Verbesserte Sicherheitsfeatures in Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung des Visual Studio\-Profilers auf diesen Plattformen.  Außerdem benötigen Windows Store\-Apps neue Erfassungsmethoden.  Siehe [Profilerstellung für Windows 8\- und Windows Server 2012\-Anwendungen](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## Allgemeine Aufgaben  
  
|Aufgabe|Verwandter Inhalt|  
|-------------|-----------------------|  
|**Festlegen des Speicherorts von Symbolen**: Um die Namen von Funktionen und Parametern anzuzeigen, muss der Profiler Zugriff auf die Symboldateien \(.pdb\) der Binärdateien haben, für die eine Profilerstellung durchgeführt wurde.  Diese Dateien müssen die Symboldateien für das Microsoft\-Betriebssystem und Microsoft\-Anwendungen umfassen, die Sie in der Analyse anzeigen möchten.  Sie können mithilfe des öffentlichen Microsoft\-Symbolservers sicherstellen, dass Sie über die richtigen PDB\-Dateien für die Microsoft\-Binärdateien verfügen.|-   [Gewusst wie: Angeben von Symboldateispeicherorten über die Befehlszeile](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md)|  
|**Profilerstellung für die Anwendung**: Die Befehlszeilentools und \-optionen, die Sie für die Profilerstellung einer Zielanwendung verwenden, hängen vom Typ der Anwendung, der Profilerstellungsmethode und davon ab, ob das Ziel eine verwaltete oder eine systemeigene Anwendung ist.|-   [Verwenden von Profilerstellungsmethoden über die Befehlszeile](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md)<br />-   [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)<br />-   [Profilerstellung für ASP.NET\-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)<br />-   [Profilerstellungsdienste](../profiling/command-line-profiling-of-services.md)|  
|**Erstellen von XML\- und CSV\-Berichten**: Durch die Profilerstellung an der Eingabeaufforderung werden Datendateien erstellt, die auf der Benutzeroberfläche von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] angezeigt werden können.  Sie können auch mit dem Befehlszeilentool VSPerfReport XML\-Dateien oder CSV \(Comma\-Separated Value\)\-Dateien der Daten generieren.|-   [Erstellen von Profiler\-Berichten über die Befehlszeile](../profiling/creating-profiler-reports-from-the-command-line.md)<br />-   [VSPerfReport](../profiling/vsperfreport.md)|  
|**Profilerstellung von Code auf Computern ohne Visual Studio**: Sie können den eigenständigen Profiler der Profilerstellungstools verwenden, um Daten für Anwendungen auf Computern zu sammeln, auf denen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nicht installiert ist.|-   [Gewusst wie: Installieren des eigenständigen Profilers](../profiling/how-to-install-the-stand-alone-profiler.md)|  
  
## Verweis  
 [Referenz zu Profilerstellungstools für die Befehlszeile](../profiling/command-line-profiling-tools-reference.md)  
  
## Siehe auch  
 [Verwenden von Profilerstellungstools](../profiling/performance-explorer.md)