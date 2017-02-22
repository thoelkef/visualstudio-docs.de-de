---
title: "Erstellen einfacher Profilerstellungsberichte &#252;ber die Befehlszeile | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6d73e21e-c04e-48ea-91cc-e517a5f2cd3f
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Erstellen einfacher Profilerstellungsberichte &#252;ber die Befehlszeile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In diesem Thema werden die grundlegenden VSPerfReport\-Befehle beschrieben, über die durch Trennzeichen getrennte Berichtdateien \(CSV\) aus einer VSP\- oder VSPS\-Profilerstellungs\-Datendatei erstellt werden.  Eine Beschreibung aller Berichtsoptionen finden Sie unter [VSPerfReport](../profiling/vsperfreport.md).  
  
## Berichtsbefehle  
 Verwenden Sie einen der folgenden Befehle, um für eine angegebene Profilerstellungs\-Datendatei einen Bericht zu erstellen.  
  
 **VSPerfReport** `VSPFile` **\/Summary:All**  
 Generiert alle für die VSP\- oder VSPS\-Datei verfügbaren Berichte.  
  
 **VSPerfReport** `VSPFile` **\/Summary:**`ReportType`\[,`ReportType`...\]  
 Generiert die angegebenen Berichtstypen.  
  
 **VSPerfReport** `VSPFile` **\/CallTrace**  
 Generiert einen Bericht, in dem jedes Datensammlungsereignis aufgeführt ist.  Nur bei der Instrumentation.  
  
## Zusammenfassungsbericht für Typparameter  
 In der folgenden Tabelle werden die Berichte beschrieben, die von der angegebenen Berichtstypoption generiert werden.  Die Spalten eines Berichts sind von der Profilerstellungsmethode abhängig, die zur Datensammlung verwendet wurde.  
  
|Zusammenfassungsparameter|Berichtsbeschreibung|Berichtsverweis|  
|-------------------------------|--------------------------|---------------------|  
|**CallerCallee**|Stellt über\- und untergeordnete Beziehungen zwischen Funktionen dar.|-   [Samplingdaten](../profiling/caller-callee-view-sampling-data.md)<br />-   [Instrumentationsdaten](../profiling/caller-callee-view-instrumentation-data.md)<br />-   [.NET\-Speichersamplingdaten](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)<br />-   [.NET\-Speicherinstrumentationsdaten](../profiling/caller-callee-view-net-memory-instrumentation-data.md)<br />-   [Konfliktdaten](../profiling/caller-callee-view-contention-data.md)|  
|**Function**|Führt Profilerstellungsdaten nach Funktion auf.|-   [Samplingdaten](../profiling/functions-view-sampling-data.md)<br />-   [Instrumentationsdaten](../profiling/functions-view-instrumentation-data.md)<br />-   [.NET\-Speichersamplingdaten](../profiling/functions-view-dotnet-memory-sampling-data.md)<br />-   [.NET\-Speicherinstrumentationsdaten](../profiling/functions-view-dotnet-memory-instrumentation-data.md)<br />-   [Konfliktdaten](../profiling/functions-view-contention-data.md)|  
|**CallTree**|Stellt die Ausführungspfade und die Profilerstellungsdaten von Funktionen in der Profilerstellungsausführung dar.|-   [Instrumentationsdaten](../profiling/call-tree-view-instrumentation-data.md)<br />-   [Samplingdaten](../profiling/call-tree-view-sampling-data.md)<br />-   [.NET\-Speichersamplingdaten](../profiling/call-tree-view-dotnet-memory-sampling-data.md)<br />-   [.NET\-Speicherinstrumentationsdaten](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)<br />-   [Konfliktdaten](../profiling/call-tree-view-contention-data.md)|  
|**Counter**|Führt Profilerstellungsmarkierungen und Windows\-Leistungsindikatorwerte auf, die während der Profilerstellungsausführung gesammelt wurden.|-   [Markierungsansicht](../profiling/marks-view.md)|  
|**Ip**|Führt Profilerstellungsdaten nach Anweisung auf.|-   [Samplingdaten](../profiling/instruction-pointers-ips-view-sampling-data.md)<br />-   [.NET\-Speichersamplingdaten](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)<br />-   [Konfliktdaten](../profiling/instruction-pointers-ips-view-contention-data.md)|  
|**Life**|Führt die Lebensdauer von zugeordneten Objekten auf.|-   [Objektlebensdaueransicht](../profiling/object-lifetime-view.md)|  
|**Line**|Führt Profilerstellungsdaten nach Quellcodezeile auf.|-   [Samplingdaten](../profiling/lines-view-sampling-data.md)<br />-   [.NET\-Speichersamplingdaten](../profiling/lines-view-dotnet-memory-sampling-data.md)<br />-   [Konfliktdaten](../profiling/lines-view-contention-data.md)|  
|**Header**|Headerinformationen der Profilerstellungs\-Datendatei.|Dateispezifisch.|  
|**Mark**|Profilerstellungsmarkierungen, die während der Profilerstellungsausführung gesammelt wurden.|-   [Markierungsansicht](../profiling/marks-view.md)|  
|**Module**|Führt Profilerstellungsdaten für Module auf.|-   [Samplingdaten](../profiling/modules-view-sampling-data.md)<br />-   [Instrumentationsdaten](../profiling/modules-view-instrumentation-data.md)<br />-   [.NET\-Speichersamplingdaten](../profiling/modules-view-dotnet-memory-sampling-data.md)<br />-   [.NET\-Speicherinstrumentationsdaten](../profiling/modules-view-dotnet-memory-instrumentation-data.md)<br />-   [Konfliktdaten](../profiling/modules-view-contention-data.md)|  
|**Process**|Führt Profilerstellungsdaten für Prozesse auf.|-   [Prozessansicht](../profiling/process-view.md)<br />-   [Konfliktdaten](../profiling/process-view-contention-data.md)|  
|**Thread**|Führt Profilerstellungsdaten für Threads auf.|-   [Prozessansicht](../profiling/process-view.md)|  
|**Type**|Führt Zuordnungsprofilerstellungsdaten nach Typ auf.|-   [Zuordnungsansicht](../profiling/dotnet-memory-allocations-view.md)|  
|**Contention**|Ressourcenkonflikte.|-   [Ressourcenkonflikte](../profiling/resource-contentions-view-contention-data.md)|  
|**RuleWarnings**|Führt Leistungsregelprobleme auf.|-   Führt die CheckId, die Beschreibung und  den Quellcodespeicherort des Regelproblems auf.|  
|**ETW**|Führt alle während der Profilerstellungsausführung erfassten Ereignisse der Ereignisablaufverfolgung für Windows \(ETW\) auf.|-   [ETW\-Bericht](../profiling/event-tracing-for-windows-etw-report.md)|