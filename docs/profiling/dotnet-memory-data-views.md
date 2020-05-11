---
title: .NET-Arbeitsspeicherdatenansichten | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .NET memory profiling method views
- profiling tools,.NET memory profiling views
ms.assetid: 79184d8e-769b-4ace-be2b-521147772081
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 7e74027512eba0d64593133a3bbe758570cbf567
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779271"
---
# <a name="net-memory-data-views"></a>.NET-Arbeitsspeicherdatenansichten
Dieser Abschnitt enthält Referenzinformationen für die Ansichten und die Berichte von Profiler-Datendateien, die Profilerstellungsdaten für den .NET-Arbeitsspeicher enthalten.

## <a name="in-this-section"></a>In diesem Abschnitt
- [Summary View (Zusammenfassungsansicht)](../profiling/summary-view-dotnet-memory-data.md)

 Führt die Funktionen und Typen auf, die den meisten Speicher belegen.

- [Allocations View (Zuordnungsansicht)](../profiling/dotnet-memory-allocations-view.md)

 Führt die während der Profilerstellung zugeordneten Typen sowie die Aufrufstrukturen (Ausführungspfade) auf, die zu der Zuordnung des Typs führten.

- [Object Lifetime View (Objektlebensdaueransicht)](../profiling/object-lifetime-view.md)

 Führt die während der Profilerstellung zugeordneten Typen sowie die Anzahl der Instanzen, die Größe in Bytes und die Garbage Collection-Generierung des Typs auf.

- [Call Tree View – Sampling (Aufrufstrukturansicht – Sampling)](../profiling/call-tree-view-dotnet-memory-sampling-data.md)

 Zeigt eine hierarchische Struktur an, die die Ausführungspfade und Speicherbelegung von Funktionen während der Profilerstellung darstellt.

- [Modulansicht - Sampling](../profiling/modules-view-dotnet-memory-sampling-data.md)

 Organisiert die .NET-Arbeitsspeicherbelegungsdaten nach Modul und führt die Funktionen, Quellcodezeilen und Anweisungen auf, die ausgeführt wurden, als Speicher belegt wurde.

- [Caller/Callee View – .NET Memory Sampling Data (Ansicht „Aufrufer/Aufgerufener“ – .NET-Speichersamplingdaten)](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)

 Führt Speicherbelegungsdaten für eine ausgewählte Funktion, für die Funktionen, die die ausgewählte Funktion aufgerufen haben, sowie für die Funktionen auf, die von der ausgewählten Funktion aufgerufen wurden.

- [Functions View – Sampling (Funktionsansicht – Sampling)](../profiling/functions-view-dotnet-memory-sampling-data.md)

 Führt Speicherbelegungsdaten für die Funktionen in der Profilerstellung auf.

- [Zeilenansicht - Sampling](../profiling/lines-view-dotnet-memory-sampling-data.md)

 Führt Speicherbelegungsdaten für die Quellcodezeilen von Funktionen in der Profilerstellung auf.

- [Instruction Pointers (IPs) View – Sampling (Anweisungszeigeransicht – Sampling)](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)

 Führt Speicherbelegungsdaten für die Anweisungen in der Profilerstellung auf.

- [Call Tree View – Instrumentation (Aufrufstrukturansicht – Instrumentierung)](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)

 Zeigt eine hierarchische Struktur an, die die Ausführungspfade, die Speicherbelegungsdaten und ausführliche Zeitsteuerungsdaten für instrumentierte Funktionen in der Profilerstellung darstellt.

- [Modules View – Instrumentation (Modulansicht – Instrumentierung)](../profiling/modules-view-dotnet-memory-instrumentation-data.md)

 Organisiert Profilerstellungsdaten nach Modul und führt die Funktionen, Speicherbelegungsdaten und ausführliche Zeitsteuerungsdaten für das Modul auf.

- [Aufrufer-/Aufgerufener-Ansicht – .NET-Speicherinstrumentierungsdaten im Profiler](../profiling/caller-callee-view-net-memory-instrumentation-data.md)

 Führt Speicherbelegungsdaten und ausführliche Zeitsteuerungsinformationen für eine ausgewählte instrumentierte Funktion, für die Funktionen, die die ausgewählte Funktion aufgerufen haben, und die Funktionen auf, die von der ausgewählten Funktion aufgerufen wurden.

- [Functions View – Instrumentation (Funktionsansicht – Instrumentierung)](../profiling/functions-view-dotnet-memory-instrumentation-data.md)

 Führt Speicherbelegungsdaten für die instrumentierten Funktionen in der Profilerstellung auf.

## <a name="reference"></a>Verweis
- [Funktionsdetailansicht](../profiling/function-details-view.md)

 Zeigt ein grafisches Diagramm der Beziehung zwischen einer ausgewählten Funktion und den Funktionen an, die die ausgewählte Funktion aufgerufen haben und von dieser aufgerufen wurden.

- [Prozessansicht](../profiling/process-view.md)

 Führt Start- und Endzeiten von Prozessen und Threads auf.

- [Marks View (Markierungsansicht)](../profiling/marks-view.md)

 Führt in eine Profilerstellungs-Datendatei eingefügte ETW- und Samplingereignisse auf.

## <a name="related-sections"></a>Verwandte Abschnitte
- [Datenansichten der Profiler-Samplingmethode](../profiling/profiler-sampling-method-data-views.md)

 Referenzinformationen zu den Ansichten und Berichten für Profiler-Datendateien, die mit der Samplingmethode generiert wurden.

- [Instrumentierungsmethoden-Datenansichten](../profiling/instrumentation-method-data-views.md)

 Referenzinformationen zu den Ansichten und Berichten für Profiler-Datendateien, die mit der Instrumentierungsmethode generiert werden.
