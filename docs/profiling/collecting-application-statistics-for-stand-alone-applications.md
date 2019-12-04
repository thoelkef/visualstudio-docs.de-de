---
title: Verwenden der Profiler-Befehlszeile zum Sammeln von Statistiken einer eigenständigen App
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method
- profilng tools,sampling method
ms.assetid: be2dbdd0-fc88-45f9-a1d5-bcb4f64e17ad
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: de399bf493e328e583bdd2765822ca3a66144698
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779635"
---
# <a name="collect-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line"></a>Sammeln von Anwendungsstatistiken für eigenständige Anwendungen über die Profilerbefehlszeile
In diesem Abschnitt werden die Prozeduren und Optionen zum Sammeln von Leistungsstatistiken für eine Clientanwendung (eigenständig) mit der Samplingmethode über die Befehlszeile beschrieben.

> [!NOTE]
> Verbesserte Sicherheitsfunktionen in Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung des Visual Studio-Profilers auf diesen Plattformen. Außerdem benötigen UWP-Apps neue Erfassungsmethoden. Weitere Informationen finden Sie unter [Leistungstools für Windows 8- und Windows Server 2012-Anwendungen](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Allgemeine Aufgaben

|Aufgabe|Verwandter Inhalt|
|----------|---------------------|
|**Starten einer Anwendung mit der Profilerstellung**|-   [Vorgehensweise: Starten einer eigenständigen Anwendung und Sammeln von Anwendungsstatistiken](../profiling/how-to-launch-a-stand-alone-app-and-collect-application-statistics.md)|
|**Anfügen des Profilers an eine aktive .NET Framework-Anwendung**|-   [Vorgehensweise: Anfügen des Profilers an eine .NET Framework-Anwendung und Sammeln von Anwendungsstatistiken](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-application-statistics.md)|
|**Anfügen des Profilers an eine aktive C/C++-Anwendung**|-   [Vorgehensweise: Anfügen des Profilers an eine native Anwendung und Sammeln von Anwendungsstatistiken](../profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-application-statistics.md)|
|**Hinzufügen von Ebeneninteraktionsdaten**|-   [Hinzufügen von Ebeneninteraktionsdaten über die Befehlszeile](../profiling/adding-tier-interaction-data-from-the-command-line.md)|

## <a name="related-tasks"></a>Verwandte Aufgaben

### <a name="profile-stand-alone-applications"></a>Profilerstellung für eigenständige Anwendungen

|Aufgabe|Verwandter Inhalt|
|----------|---------------------|
|**Instrumentieren einer Anwendung**|-   [Sammeln ausführlicher Zeitsteuerungsdaten mithilfe der Instrumentierung](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md)|
|**Sammeln von .NET-Speicherbelegungs- und Garbage Collection-Daten**|-   [Sammeln von .NET Framework-Arbeitsspeicherdaten](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md)|
|**Erfassen von Ressourcenkonflikt- und Threadausführungsdaten**|-   [Sammeln von Parallelitätsdaten](../profiling/collecting-concurrency-data-for-stand-alone-applications.md)|

### <a name="profile-by-using-the-sampling-method"></a>Profilerstellung mit der Samplingmethode

|Aufgabe|Verwandter Inhalt|
|----------|---------------------|
|**Profilerstellung für ASP.NET-Webanwendungen**|-   [Sammeln von Anwendungsstatistiken durch Sampling](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|
|**Profilerstellung für Dienste**|-   [Sammeln von Anwendungsstatistiken durch Sampling](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md) Beschreibt das Sammeln von Leistungsstatistiken mit der Samplingmethode von Windows-Diensten.|

### <a name="analyze-sampling-data-views-and-reports"></a>Analysieren von Ansichten und Berichten für Samplingdaten
- [Datenansichten der Samplingmethode](../profiling/profiler-sampling-method-data-views.md)
