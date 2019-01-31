---
title: Sammeln von Anwendungsstatistiken für eigenständige Anwendungen über die Profiler-Befehlszeile | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method
- profilng tools,sampling method
ms.assetid: be2dbdd0-fc88-45f9-a1d5-bcb4f64e17ad
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 181b57b2f625dbdf60f00fa85761912d5c935635
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54780707"
---
# <a name="collecting-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line"></a>Sammeln von Anwendungsstatistiken für eigenständige Anwendungen über die Profiler-Befehlszeile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Abschnitt werden die Prozeduren und Optionen zum Sammeln von Leistungsstatistiken für eine Clientanwendung (eigenständig) mit der Samplingmethode über die Befehlszeile beschrieben.  
  
> [!NOTE]
>  Verbesserte Sicherheitsfunktionen in Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung des Visual Studio-Profilers auf diesen Plattformen. Außerdem benötigen Windows Store-Apps neue Erfassungsmethoden. Informationen hierzu finden Sie unter [Performance Tools on Windows 8 and Windows Server 2012 applications (Profilerstellung für Windows 8- und Windows Server 2012-Anwendungen)](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="common-tasks"></a>Allgemeine Aufgaben  
  
|Aufgabe|Verwandter Inhalt|  
|----------|---------------------|  
|**Starten einer Anwendung mit der Profilerstellung**|-   [Vorgehensweise: Starten einer eigenständigen Anwendung und Sammeln von Anwendungsstatistiken](../profiling/how-to-launch-a-stand-alone-application-with-the-profiler-and-collect-application-statistics-by-using-the-command-line.md)|  
|**Anfügen des Profilers an eine aktive .NET Framework-Anwendung**|-   [Vorgehensweise: Anfügen des Profilers an eine .NET Framework-Anwendung und Sammeln von Anwendungsstatistiken](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-and-collect-application-statistics-by-using-the-command-line.md)|  
|**Anfügen des Profilers an eine aktive C/C++-Anwendung**|-   [Vorgehensweise: Anfügen des Profilers an eine native Anwendung und Sammeln von Anwendungsstatistiken](../profiling/how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-application-statistics-by-using-the-command-line.md)|  
|**Hinzufügen von Ebeneninteraktionsdaten**|-   [Hinzufügen von Ebeneninteraktionsdaten über die Befehlszeile](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
  
## <a name="related-tasks"></a>Verwandte Aufgaben  
  
### <a name="profiling-stand-alone-applications"></a>Profilerstellung für eigenständige Anwendungen  
  
|Aufgabe|Verwandter Inhalt|  
|----------|---------------------|  
|**Instrumentieren einer Anwendung**|-   [Sammeln ausführlicher Zeitsteuerungsdaten für eine eigenständige Anwendung über die Profiler-Befehlszeile](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application-by-using-the-profiler-command-line.md)|  
|**Sammeln von .NET-Speicherbelegungs- und Garbage Collection-Daten**|-   [Sammeln von .NET Framework-Speicherdaten für eigenständige Anwendungen über die Profiler-Befehlszeile](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Erfassen von Ressourcenkonflikt- und Threadausführungsdaten**|-   [Sammeln von Parallelitätsdaten](../profiling/collecting-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
  
### <a name="profiling-by-using-the-sampling-method"></a>Profilerstellung mithilfe der Samplingmethode  
  
|Aufgabe|Verwandter Inhalt|  
|----------|---------------------|  
|**Profilerstellung für ASP.NET-Webanwendungen**|-   [Sammeln von Anwendungsstatistiken für ASP.NET-Webanwendungen über die Befehlszeile mit der Profiler-Samplingmethode](/visualstudio/profiling/collecting-concurrency-data-for-an-aspnet-web-application?view=vs-2015)|  
|**Profilerstellung für Dienste**|-   [Sammeln von Anwendungsstatistiken für Dienste mithilfe der Profiler-Samplingmethode](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md) Beschreibt das Sammeln von Leistungsstatistiken mit der Samplingmethode von Windows-Diensten.|  
  
### <a name="analyzing-sampling-data-views-and-reports"></a>Analysieren von Ansichten und Berichten für Samplingdaten  
 [Datenansichten der Profiler-Samplingmethode](../profiling/profiler-sampling-method-data-views.md)
