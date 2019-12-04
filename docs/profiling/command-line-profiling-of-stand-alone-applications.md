---
title: Profilerstellung für eigenständige Anwendungen über die Befehlszeile | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profillng tools,stand-alone applications
- profling stand-alone applications
ms.assetid: a47f2bf2-186d-4120-bb79-34e2f3a1ee42
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: c5fd11f12f368c266dd19577925db7cec1867e39
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779557"
---
# <a name="command-line-profiling-of-stand-alone-applications"></a>Profilerstellung für eigenständige Anwendungen über die Befehlszeile
In diesem Abschnitt werden die Prozeduren und die Optionen zum Erfassen von Leistungsdaten für eigenständige (Client-)Anwendungen unter Verwendung der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Profilerstellungstools über die Befehlszeile beschrieben.

## <a name="common-tasks"></a>Allgemeine Aufgaben

| Aufgabe | Verwandter Inhalt |
| - | - |
| **Sammeln von Anwendungsstatistiken:** Verwenden Sie die Samplingmethode, um Leistungsstatistiken zu sammeln. Datensampling ist beim Analysieren von CPU-Auslastungsproblemen und zum Verständnis der allgemeinen Leistungsmerkmale einer Anwendung hilfreich. | -   [Sammeln von Anwendungsstatistiken durch Sampling](../profiling/collecting-application-statistics-for-stand-alone-applications.md) |
| **Sammeln von detaillierten Zeiterfassungsdaten:** Sammeln Sie ausführlichen Zeiterfassungsdaten mit der Instrumentierungsmethode. Instrumentationsdaten sind beim Analysieren von E/A-Problemen und für die detaillierte Analyse von Anwendungsszenarios hilfreich. | -   [Sammeln ausführlicher Zeitsteuerungsdaten mithilfe der Instrumentierung](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md) |
| **Sammeln von .NET-Arbeitsspeicherdaten:** Sammeln Sie mit der Sampling- oder Instrumentierungsmethode .NET-Speicherbelegungsdaten, die Auskunft über die Größe und Anzahl zugeordneter Objekte geben. Sie können auch Objektlebensdauerdaten sammeln, die die Größe und Anzahl von Objekten angeben, die in jeder Garbage Collection-Generation freigegeben werden. | -   [Sammeln von .NET Framework-Arbeitsspeicherdaten](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md) |
| **Sammeln von Parallelitätsdaten:** Sammeln Sie mit der Parallelitätsmethode Ressourcenkonfliktdaten und Threadaktivitätsdaten, die Auskunft über CPU-Auslastung, Threadkonflikte, Threadmigration, Synchronisierungsverzögerungen, überlappende E/A-Bereiche und andere Systemereignisse geben. | -   [Sammeln von Parallelitätsdaten](../profiling/collecting-concurrency-data-for-stand-alone-applications.md) |
| **Hinzufügen von Ebeneninteraktionsdaten:** Sie können Leistungsdaten zu synchronen ADO.NET-Aufrufen der Anwendung hinzufügen, die an eine Microsoft [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)]-Datenbank erfolgt sind. Das Hinzufügen von Ebeneninteraktionsdaten zu einer Profilerstellung erfordert bestimmte Verfahren der Befehlszeilenprofilerstellungstools. | -   [Erfassen von Ebeneninteraktionsdaten](../profiling/adding-tier-interaction-data-from-the-command-line.md) |
| **Probieren Sie es aus:** Verwenden Sie schrittweise Prozeduren bei der Profilerstellung für eine Beispielclientanwendung durch die Verwendung der Sampling- oder Instrumentierungsmethode. | -   [Exemplarische Vorgehensweise: Profilerstellung über die Befehlszeile mit Sampling](../profiling/walkthrough-command-line-profiling-using-sampling.md)<br />-   [Exemplarische Vorgehensweise: Profilerstellung über die Befehlszeile mit Instrumentierung](command-line-profiling-of-stand-alone-applications.md) |

## <a name="related-tasks"></a>Verwandte Aufgaben

|Aufgabe|Verwandter Inhalt|
|----------|---------------------|
|**Profilerstellung für ASP.NET-Anwendungen**|-   [Profilerstellung für ASP.NET-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)|
|**Profilerstellung für Dienste**|-   [Profilerstellung für Dienste](../profiling/command-line-profiling-of-services.md)|
