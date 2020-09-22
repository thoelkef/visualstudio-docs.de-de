---
title: Profilerstellung für ASP.NET-Webanwendungen über die Befehlszeile | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling ASP.NET applications
- profling tools,ASP.NET applications
ms.assetid: 897c00d5-5767-433b-a960-4a29c6023ede
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c93cb4774953f1425ff0330d7f588cbbf0f0b823
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841252"
---
# <a name="command-line-profiling-of-aspnet-web-applications"></a>Profilerstellung für ASP.NET-Webanwendungen über die Befehlszeile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Abschnitt werden die Vorgehensweisen und Optionen zum Erfassen von Leistungsdaten für [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Webanwendungen mit den [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Profilerstellungstools über die Befehlszeile beschrieben.  
  
> [!NOTE]
> Verbesserte Sicherheitsfunktionen in Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung des Visual Studio-Profilers auf diesen Plattformen. Außerdem benötigen Windows Store-Apps neue Erfassungsmethoden. Siehe [Profilerstellungstools für Windows 8- und Windows Server 2012-Anwendungen](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="common-tasks"></a>Allgemeine Aufgaben  
  
|Aufgabe|Verwandter Inhalt|  
|----------|---------------------|  
|**Einfaches Erfassen grundlegender ASP.NET-Profilerstellungsdaten:** Verwenden Sie das Tool **VSPerfASPNETCmd**, um Sampling-, Instrumentierungs-, .NET-Arbeitsspeicher-, Konflikt- oder Ebeneninteraktionsdaten ohne die Konfigurationsanforderungen und die Neustarts der Internetinformationsdienste (IIS) zu sammeln, die bei **VSPerfCmd** erforderlich sind. Mit **VSPerfASPNETCmd** können keine zusätzlichen Daten erfasst werden, und auch die Datensammlung lässt sich nicht beeinflussen. **Hinweis**:  **VSPerfASPNETCmd** ist das bevorzugte Tool, wenn mit dem eigenständigen Profiler ein Profil für ASP.NET-Websites erstellt wird.|-   [Schnelle Website-Profilerstellung mit vsperfaspnetcmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)|  
|**Sammeln von Anwendungsstatistiken:** Verwenden Sie die Samplingmethode, um Leistungsstatistiken zu sammeln. Samplingdaten sind beim Analysieren von CPU-Auslastungsproblemen sowie zum Verständnis der allgemeinen Leistungsmerkmale einer Anwendung hilfreich.|-   [Sammeln von Anwendungs Statistiken mithilfe von Sampling](../profiling/collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line.md)|  
|**Sammeln von detaillierten Zeiterfassungsdaten:** Sammeln Sie ausführlichen Zeiterfassungsdaten mit der Instrumentierungsmethode. Instrumentationsdaten sind beim Analysieren von EA-Problemen und für die detaillierte Analyse von Anwendungsszenarios hilfreich.|-   [Sammeln ausführlicher Zeit Steuerungsdaten mithilfe der Instrumentierung](/visualstudio/profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method?view=vs-2015)|  
|**Sammeln von .NET-Arbeitsspeicherdaten:** Sammeln Sie mit der Sampling- oder Instrumentierungsmethode .NET-Speicherbelegungsdaten, die Auskunft über die Größe und Anzahl zugeordneter Objekte geben. Sie können auch Objektlebensdauerdaten sammeln, die die Größe und Anzahl von Objekten angeben, die in jeder Garbage Collection-Generation freigegeben werden.|-   [Sammeln von Arbeitsspeicherdaten](../profiling/collecting-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line.md)|  
|**Sammeln von Parallelitätsdaten:** Verwenden Sie die Parallelitätsmethode, um Daten zu Ressourcenkonflikten zu sammeln. **Hinweis**:  Das Sammeln von Threadaktivitäts- und Visualisierungsdaten wird für Webanwendungen nicht unterstützt.|-   [Sammeln von Parallelitätsdaten](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
|**Hinzufügen von Ebeneninteraktionsdaten:** Sie können Leistungsdaten zu synchronen [!INCLUDE[vstecado](../includes/vstecado-md.md)]-Aufrufen der [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Webanwendung an eine Microsoft [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Datenbank hinzufügen.|-   [Hinzufügen von Ebeneninteraktionsdaten über die Befehlszeile](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Aufgabe|Verwandter Inhalt|  
|----------|---------------------|  
|**Profilerstellung für eigenständige (Client-)Anwendungen**|-   [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)|  
|**Profilerstellung für Dienste**|-   [Profilerstellungsdienste](../profiling/command-line-profiling-of-services.md)|
