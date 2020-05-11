---
title: Profilerstellung für Dienste über die Befehlszeile | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling toos,services
- profiling services
ms.assetid: f0d62318-b0e8-49c6-9a30-9f7a6adef2f6
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b20835eaf8b81bd64bd90aa75d2efb32975a7c53
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "74772830"
---
# <a name="command-line-profiling-of-services"></a>Profilerstellung für Dienste über die Befehlszeile
In diesem Abschnitt werden die Prozeduren und Optionen zum Sammeln von Leistungsdaten für Windows-Dienste mithilfe der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Profilerstellungstools über die Befehlszeile beschrieben.

> [!NOTE]
> Verbesserte Sicherheitsfeatures in Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung des Visual Studio-Profilers auf diesen Plattformen. Außerdem benötigen UWP-Apps neue Erfassungsmethoden. Weitere Informationen finden Sie unter [Profilerstellung für Windows 8- und Windows Server 2012-Anwendungen](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Allgemeine Aufgaben

| Aufgabe | Verwandte Inhalte |
| - | - |
| **Sammeln von Anwendungsstatistikdaten:** Sammeln Sie Leistungsstatistikdaten mit der Samplingmethode. Datensampling ist beim Analysieren von CPU-Auslastungsproblemen und zum Verständnis der allgemeinen Leistungsmerkmale einer Anwendung hilfreich. | -   [Sammeln von Anwendungsstatistiken durch Sampling](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md) |
| **Sammeln ausführlicher Zeitsteuerungsdaten:** Sammeln Sie ausführliche Zeitsteuerungsinformationen mit der Instrumentationsmethode. Instrumentationsdaten sind beim Analysieren von EA-Problemen und für die detaillierte Analyse von Anwendungsszenarios hilfreich. | -   [Sammeln ausführlicher Zeitsteuerungsdaten mithilfe der Instrumentierung](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md) |
| **Sammeln von .NET-Arbeitsspeicherdaten:** Sammeln Sie mit Sampling oder Instrumentation Daten zur .NET-Speicherbelegung, die Auskunft über die Größe und Anzahl zugeordneter Objekte geben. Sie können auch Objektlebensdauerdaten sammeln, die die Größe und Anzahl von Objekten angeben, die in jeder Garbage Collection-Generation freigegeben werden. | -   [Sammeln von .NET-Arbeitsspeicherdaten](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md) |
| **Sammeln von Parallelitätsdaten:** Sammeln Sie mit der Parallelitätsmethode Ressourcenkonfliktdaten und Threadaktivitätsdaten, die Auskunft über CPU-Auslastung, Threadkonflikte, Threadmigration, Synchronisierungsverzögerungen, überlappende EA-Bereiche und andere Systemereignisse geben. | -   [Sammeln von Parallelitätsdaten](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md) |
| **Hinzufügen von Ebeneninteraktionsdaten:** Sie können Leistungsdaten zu synchronen ADO.NET-Aufrufen des Diensts hinzufügen, die an eine Microsoft [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)]-Datenbank erfolgt sind. | -   [Erfassen von Ebeneninteraktionsdaten](../profiling/adding-tier-interaction-data-from-the-command-line.md) |

## <a name="related-tasks"></a>Verwandte Aufgaben

|Aufgabe|Verwandte Inhalte|
|----------|---------------------|
|**Profilerstellung für eigenständige (Client-)Anwendungen**|-   [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)|
|**Profilerstellung für ASP.NET-Anwendungen**|-   [Profilerstellung für ASP.NET-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)|
