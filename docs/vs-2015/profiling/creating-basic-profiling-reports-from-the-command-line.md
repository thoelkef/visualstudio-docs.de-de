---
title: Erstellen einfacher Profilerstellungsberichte über die Befehlszeile | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 6d73e21e-c04e-48ea-91cc-e517a5f2cd3f
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5f13921dea810ab2185e626cc2889f339d9d174f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62537183"
---
# <a name="creating-basic-profiling-reports-from-the-command-line"></a>Erstellen einfacher Profilerstellungsberichte über die Befehlszeile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Thema werden die grundlegenden VSPerfReport-Befehle beschrieben, über die durch Trennzeichen getrennte Berichtdateien (CSV) aus einer VSP- oder VSPS-Profilerstellungs-Datendatei erstellt werden. Eine Beschreibung aller Berichtsoptionen finden Sie unter [VSPerfReport](../profiling/vsperfreport.md).  
  
## <a name="report-commands"></a>Berichtsbefehle  
 Verwenden Sie einen der folgenden Befehle, um für eine angegebene Profilerstellungs-Datendatei einen Bericht zu erstellen.  
  
 **VSPerfReport** `VSPFile` **/Summary:All**  
 Generiert alle für die VSP- oder VSPS-Datei verfügbaren Berichte.  
  
 **VSPerfReport** `VSPFile` **/Summary:** `ReportType` [,`ReportType`...]  
 Generiert die angegebenen Berichtstypen.  
  
 **VSPerfReport** `VSPFile` **/CallTrace**  
 Generiert einen Bericht, in dem jedes Datensammlungsereignis aufgeführt ist. Nur bei der Instrumentation.  
  
## <a name="summary-report-type-parameters"></a>Zusammenfassungsbericht für Typparameter  
 In der folgenden Tabelle werden die Berichte beschrieben, die von der angegebenen Berichtstypoption generiert werden. Die Spalten eines Berichts sind von der Profilerstellungsmethode abhängig, die zur Datensammlung verwendet wurde.  
  
|Zusammenfassungsparameter|Berichtsbeschreibung|Berichtsverweis|  
|-----------------------|------------------------|----------------------|  
|**CallerCallee**|Stellt über- und untergeordnete Beziehungen zwischen Funktionen dar.|-   [Stichprobendaten](../profiling/caller-callee-view-sampling-data.md)<br />-   [Instrumentierungs Daten](../profiling/caller-callee-view-instrumentation-data.md)<br />-   [.NET-Speicher Abtast Daten](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)<br />-   [.NET-Speicher Instrumentations Daten](../profiling/caller-callee-view-net-memory-instrumentation-data.md)<br />-   [Konflikt Daten](../profiling/caller-callee-view-contention-data.md)|  
|**Function**|Führt Profilerstellungsdaten nach Funktion auf.|-   [Stichprobendaten](../profiling/functions-view-sampling-data.md)<br />-   [Instrumentierungs Daten](../profiling/functions-view-instrumentation-data.md)<br />-   [.NET-Speicher Abtast Daten](../profiling/functions-view-dotnet-memory-sampling-data.md)<br />-   [.NET-Speicher Instrumentations Daten](../profiling/functions-view-dotnet-memory-instrumentation-data.md)<br />-   [Konflikt Daten](../profiling/functions-view-contention-data.md)|  
|**CallTree**|Stellt die Ausführungspfade und die Profilerstellungsdaten von Funktionen in der Profilerstellungsausführung dar.|-   [Instrumentierungs Daten](../profiling/call-tree-view-instrumentation-data.md)<br />-   [Stichprobendaten](../profiling/call-tree-view-sampling-data.md)<br />-   [.NET-Speicher Abtast Daten](../profiling/call-tree-view-dotnet-memory-sampling-data.md)<br />-   [.NET-Speicher Instrumentations Daten](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)<br />-   [Konflikt Daten](../profiling/call-tree-view-contention-data.md)|  
|**Leistungsindikator**|Führt Profilerstellungsmarkierungen und Windows-Leistungsindikatorwerte auf, die während der Profilerstellungsausführung gesammelt wurden.|-   [Markierungs Ansicht](../profiling/marks-view.md)|  
|**-**|Führt Profilerstellungsdaten nach Anweisung auf.|-   [Stichprobendaten](../profiling/instruction-pointers-ips-view-sampling-data.md)<br />-   [.NET-Speicher Abtast Daten](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)<br />-   [Konflikt Daten](../profiling/instruction-pointers-ips-view-contention-data.md)|  
|**Life**|Führt die Lebensdauer von zugeordneten Objekten auf.|-   [Objekt Lebensdauer Ansicht](../profiling/object-lifetime-view.md)|  
|**Linie**|Führt Profilerstellungsdaten nach Quellcodezeile auf.|-   [Stichprobendaten](../profiling/lines-view-sampling-data.md)<br />-   [.NET-Speicher Abtast Daten](../profiling/lines-view-dotnet-memory-sampling-data.md)<br />-   [Konflikt Daten](../profiling/lines-view-contention-data.md)|  
|**Kopfzeile**|Headerinformationen der Profilerstellungs-Datendatei.|Dateispezifisch.|  
|**Mark**|Profilerstellungsmarkierungen, die während der Profilerstellungsausführung gesammelt wurden.|-   [Markierungs Ansicht](../profiling/marks-view.md)|  
|**Modul**|Führt Profilerstellungsdaten für Module auf.|-   [Stichprobendaten](../profiling/modules-view-sampling-data.md)<br />-   [Instrumentierungs Daten](../profiling/modules-view-instrumentation-data.md)<br />-   [.NET-Speicher Abtast Daten](../profiling/modules-view-dotnet-memory-sampling-data.md)<br />-   [.NET-Speicher Instrumentations Daten](../profiling/modules-view-dotnet-memory-instrumentation-data.md)<br />-   [Konflikt Daten](../profiling/modules-view-contention-data.md)|  
|**Prozess**|Führt Profilerstellungsdaten für Prozesse auf.|-   [Prozessansicht](../profiling/process-view.md)<br />-   [Konflikt Daten](../profiling/process-view-contention-data.md)|  
|**Thread**|Führt Profilerstellungsdaten für Threads auf.|-   [Prozessansicht](../profiling/process-view.md)|  
|**Type**|Führt Zuordnungsprofilerstellungsdaten nach Typ auf.|-   [Zuordnungs Ansicht](../profiling/dotnet-memory-allocations-view.md)|  
|**Punkte**|Ressourcenkonflikte.|-   [Ressourcenkonflikte](../profiling/resource-contentions-view-contention-data.md)|  
|**RuleWarnings**|Führt Leistungsregelprobleme auf.|– Führt die CheckId, die Beschreibung und den Quellcodespeicherort des Regelproblems auf.|  
|**ETW**|Führt alle während der Profilerstellungsausführung erfassten Ereignisse der Ereignisablaufverfolgung für Windows (ETW) auf.|-   [Etw-Bericht](../profiling/event-tracing-for-windows-etw-report.md)|
