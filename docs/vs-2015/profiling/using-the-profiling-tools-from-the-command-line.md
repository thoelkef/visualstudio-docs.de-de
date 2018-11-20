---
title: Verwenden der Profilerstellungstools über die Befehlszeile | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- command line, performance tools
- command-line tools, performance tools
- profiling tools,command line
- tools, command-line
- command line, tools
ms.assetid: 6593fa82-181e-4009-a0ed-02aa24c2c063
caps.latest.revision: 40
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9cb3fafa78d49904c346212e8fd4062c966a63f5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51775146"
---
# <a name="using-the-profiling-tools-from-the-command-line"></a>Verwenden der Profilerstellungstools über die Befehlszeile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mithilfe der Befehlszeilentools der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Profilerstellungstools können Sie über die Eingabeaufforderung für Anwendungen Profile erstellen und die Profilerstellung mithilfe von Batchdateien und Skripts automatisieren. Darüber hinaus können Sie über eine Eingabeaufforderung auch Berichtsdateien erstellen. Sie können Daten auf Computern, auf denen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nicht installiert ist, mithilfe des einfachen eigenständigen Profilers sammeln.  
  
> [!NOTE]
>  Verbesserte Sicherheitsfunktionen in Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung des Visual Studio-Profilers auf diesen Plattformen. Außerdem benötigen Windows Store-Apps neue Erfassungsmethoden. Informationen hierzu finden Sie unter [Performance Tools on Windows 8 and Windows Server 2012 applications (Profilerstellung für Windows 8- und Windows Server 2012-Anwendungen)](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="common-tasks"></a>Allgemeine Aufgaben  
  
|Aufgabe|Verwandter Inhalt|  
|----------|---------------------|  
|**Festlegen des Speicherorts von Symbolen:** Damit die Namen von Funktionen und Parametern angezeigt werden, muss der Profiler Zugriff auf die Symboldateien (.pdb) der Binärdateien haben, für die eine Profilerstellung durchgeführt wurde. Diese Dateien müssen die Symboldateien für das Microsoft-Betriebssystem und Microsoft-Anwendungen umfassen, die Sie in der Analyse anzeigen möchten. Sie können mithilfe des öffentlichen Microsoft-Symbolservers sicherstellen, dass Sie über die richtigen PDB-Dateien für die Microsoft-Binärdateien verfügen.|-   [How to: Specify Symbol File Locations from the Command Line (Vorgehensweise: Angeben von Symboldateispeicherorten über die Befehlszeile)](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md)|  
|**Profilerstellung für die Anwendung:** Welche Befehlszeilentools und -optionen Sie für die Profilerstellung einer Zielanwendung verwenden, hängt vom Typ der Anwendung, der Profilerstellungsmethode und davon ab, ob das Ziel eine verwaltete oder eine native Anwendung ist.|-   [Verwenden von Profilerstellungsmethoden über die Befehlszeile](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md)<br />-   [Profiling Stand-Alone Applications (Profilerstellung für eigenständige Anwendungen)](../profiling/command-line-profiling-of-stand-alone-applications.md)<br />-   [Profiling ASP.NET Web Applications (Profilerstellung für ASP.NET-Webanwendungen)](../profiling/command-line-profiling-of-aspnet-web-applications.md)<br />-   [Profiling Services (Profilerstellung für Dienste)](../profiling/command-line-profiling-of-services.md)|  
|**Erstellen von XML- und CSV-Berichten:** Durch die Profilerstellung über die Eingabeaufforderung werden Datendateien erstellt, die auf der Benutzeroberfläche von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] angezeigt werden können. Mit dem Befehlszeilentool VSPerfReport können auch XML-Dateien oder CSV-Dateien (Comma-Separated Value) der Daten generiert werden.|-   [Creating Profiler Reports from the Command Line (Erstellen von Profiler-Berichten über die Befehlszeile)](../profiling/creating-profiler-reports-from-the-command-line.md)<br />-   [VSPerfReport](../profiling/vsperfreport.md)|  
|**Profilerstellung von Code auf Computern ohne Visual Studio:** Sie können den eigenständigen Profiler der Profilerstellungstools verwenden, um Daten für Anwendungen auf Computern zu sammeln, auf denen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nicht installiert ist.|-   [How to: Install the Stand-Alone Profiler (Vorgehensweise: Installieren des eigenständigen Profilers)](../profiling/how-to-install-the-stand-alone-profiler.md)|  
  
## <a name="reference"></a>Referenz  
 [Command-Line Profiling Tools Reference (Referenz zu Profilerstellungstools für die Befehlszeile)](../profiling/command-line-profiling-tools-reference.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Performance Explorer (Leistungs-Explorer)](../profiling/performance-explorer.md)



