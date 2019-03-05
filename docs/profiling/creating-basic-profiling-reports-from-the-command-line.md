---
title: Erstellen einfacher Profilerstellungsberichte über die Befehlszeile | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 6d73e21e-c04e-48ea-91cc-e517a5f2cd3f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6ac35f506aadfcceebcbcf0dd4f6ec5b6dc33107
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56616923"
---
# <a name="create-basic-profiling-reports-from-the-command-line"></a>Erstellen einfacher Profilerstellungsberichte über die Befehlszeile
In diesem Artikel werden die grundlegenden VSPerfReport-Befehle beschrieben, über die durch Trennzeichen getrennte Berichtdateien (*CSV*) aus einer *VSP*- oder *VSPS*-Profilerstellungs-Datendatei erstellt werden. Eine Beschreibung aller Berichtsoptionen finden Sie unter [VSPerfReport](../profiling/vsperfreport.md).

## <a name="report-commands"></a>Berichtsbefehle
 Verwenden Sie einen der folgenden Befehle, um für eine angegebene Profilerstellungs-Datendatei einen Bericht zu erstellen.

 Mit **VSPerfReport** `VSPFile` **/Summary:All** werden alle für die *VSP*- oder *VSPS*-Datei verfügbaren Berichte generiert.

 Mit **VSPerfReport** `VSPFile` **/Summary:**`ReportType`[,`ReportType`...] werden die angegebenen Berichtstypen generiert.

 Mit **VSPerfReport** `VSPFile` **/CallTrace** wird ein Bericht generiert, der alle Datensammlungsereignisse aufführt. Nur bei der Instrumentation.

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