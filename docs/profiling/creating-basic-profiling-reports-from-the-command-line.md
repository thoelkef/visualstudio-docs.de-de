---
title: Erstellen einfacher Profilerstellungsberichte über die Befehlszeile | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 6d73e21e-c04e-48ea-91cc-e517a5f2cd3f
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: cd9748d88a9398792274c386a42bdaa3ce48ba70
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777789"
---
# <a name="create-basic-profiling-reports-from-the-command-line"></a>Erstellen einfacher Profilerstellungsberichte über die Befehlszeile
In diesem Artikel werden die grundlegenden VSPerfReport-Befehle beschrieben, über die durch Trennzeichen getrennte Berichtdateien (*CSV*) aus einer *VSP*- oder *VSPS*-Profilerstellungs-Datendatei erstellt werden. Eine Beschreibung aller Berichtsoptionen finden Sie unter [VSPerfReport](../profiling/vsperfreport.md).

## <a name="report-commands"></a>Berichtsbefehle
 Verwenden Sie einen der folgenden Befehle, um für eine angegebene Profilerstellungs-Datendatei einen Bericht zu erstellen.

 **VSPerfReport** `VSPFile` **/Summary:All** generiert alle für die *VSP*- oder *VSPS*-Datei verfügbaren Berichte.

 **VSPerfReport** `VSPFile` **/Summary:** `ReportType`[,`ReportType`...] generiert die angegebenen Berichtstypen.

 **VSPerfReport** `VSPFile` **/CallTrace** generiert einen Bericht, der alle Datensammlungsereignisse auflistet. Nur bei der Instrumentation.

## <a name="summary-report-type-parameters"></a>Zusammenfassungsbericht für Typparameter
 In der folgenden Tabelle werden die Berichte beschrieben, die von der angegebenen Berichtstypoption generiert werden. Die Spalten eines Berichts sind von der Profilerstellungsmethode abhängig, die zur Datensammlung verwendet wurde.

|Zusammenfassungsparameter|Berichtsbeschreibung|Berichtsverweis|
|-----------------------|------------------------|----------------------|
|**CallerCallee**|Stellt über- und untergeordnete Beziehungen zwischen Funktionen dar.|-   [Samplingdaten](../profiling/caller-callee-view-sampling-data.md)<br />-   [Instrumentierungsdaten](../profiling/caller-callee-view-instrumentation-data.md)<br />-   [.NET-Speichersamplingdaten](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)<br />-   [.NET-Speicherinstrumentierungsdaten](../profiling/caller-callee-view-net-memory-instrumentation-data.md)<br />-   [Konfliktdaten](../profiling/caller-callee-view-contention-data.md)|
|**Function**|Führt Profilerstellungsdaten nach Funktion auf.|-   [Samplingdaten](../profiling/functions-view-sampling-data.md)<br />-   [Instrumentierungsdaten](../profiling/functions-view-instrumentation-data.md)<br />-   [.NET-Speichersamplingdaten](../profiling/functions-view-dotnet-memory-sampling-data.md)<br />-   [.NET-Speicherinstrumentierungsdaten](../profiling/functions-view-dotnet-memory-instrumentation-data.md)<br />-   [Konfliktdaten](../profiling/functions-view-contention-data.md)|
|**CallTree**|Stellt die Ausführungspfade und die Profilerstellungsdaten von Funktionen in der Profilerstellungsausführung dar.|-   [Instrumentierungsdaten](../profiling/call-tree-view-instrumentation-data.md)<br />-   [Samplingdaten](../profiling/call-tree-view-sampling-data.md)<br />-   [.NET-Speichersamplingdaten](../profiling/call-tree-view-dotnet-memory-sampling-data.md)<br />-   [.NET-Speicherinstrumentierungsdaten](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)<br />-   [Konfliktdaten](../profiling/call-tree-view-contention-data.md)|
|**Zähler**|Führt Profilerstellungsmarkierungen und Windows-Leistungsindikatorwerte auf, die während der Profilerstellungsausführung gesammelt wurden.|-   [Markierungsansicht](../profiling/marks-view.md)|
|**Ip**|Führt Profilerstellungsdaten nach Anweisung auf.|-   [Samplingdaten](../profiling/instruction-pointers-ips-view-sampling-data.md)<br />-   [.NET-Speichersamplingdaten](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)<br />-   [Konfliktdaten](../profiling/instruction-pointers-ips-view-contention-data.md)|
|**Life**|Führt die Lebensdauer von zugeordneten Objekten auf.|-   [Objektlebensdaueransicht](../profiling/object-lifetime-view.md)|
|**Line**|Führt Profilerstellungsdaten nach Quellcodezeile auf.|-   [Samplingdaten](../profiling/lines-view-sampling-data.md)<br />-   [.NET-Speichersamplingdaten](../profiling/lines-view-dotnet-memory-sampling-data.md)<br />-   [Konfliktdaten](../profiling/lines-view-contention-data.md)|
|**Header**|Headerinformationen der Profilerstellungs-Datendatei.|Dateispezifisch.|
|**Markieren**|Profilerstellungsmarkierungen, die während der Profilerstellungsausführung gesammelt wurden.|-   [Markierungsansicht](../profiling/marks-view.md)|
|**Modul**|Führt Profilerstellungsdaten für Module auf.|-   [Samplingdaten](../profiling/modules-view-sampling-data.md)<br />-   [Instrumentierungsdaten](../profiling/modules-view-instrumentation-data.md)<br />-   [.NET-Speichersamplingdaten](../profiling/modules-view-dotnet-memory-sampling-data.md)<br />-   [.NET-Speicherinstrumentierungsdaten](../profiling/modules-view-dotnet-memory-instrumentation-data.md)<br />-   [Konfliktdaten](../profiling/modules-view-contention-data.md)|
|**Process**|Führt Profilerstellungsdaten für Prozesse auf.|-   [Prozessansicht](../profiling/process-view.md)<br />-   [Konfliktdaten](../profiling/process-view-contention-data.md)|
|**Thread**|Führt Profilerstellungsdaten für Threads auf.|-   [Prozessansicht](../profiling/process-view.md)|
|**Type**|Führt Zuordnungsprofilerstellungsdaten nach Typ auf.|-   [Zuordnungsansicht](../profiling/dotnet-memory-allocations-view.md)|
|**Konflikt**|Ressourcenkonflikte.|-   [Ressourcenkonflikte](../profiling/resource-contentions-view-contention-data.md)|
|**RuleWarnings**|Führt Leistungsregelprobleme auf.|– Führt die CheckId, die Beschreibung und den Quellcodespeicherort des Regelproblems auf.|
|**ETW**|Führt alle während der Profilerstellungsausführung erfassten Ereignisse der Ereignisablaufverfolgung für Windows (ETW) auf.|-   [ETW-Bericht](../profiling/event-tracing-for-windows-etw-report.md)|
