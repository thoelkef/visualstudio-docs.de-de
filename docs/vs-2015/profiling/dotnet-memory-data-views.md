---
title: .NET-Arbeitsspeicherdatenansichten | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- .NET memory profiling method views
- profiling tools,.NET memory profiling views
ms.assetid: 79184d8e-769b-4ace-be2b-521147772081
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7d31213dc970fa7cb28c4d4620c6731692db83d2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68185239"
---
# <a name="net-memory-data-views"></a>.NET-Arbeitsspeicherdatenansichten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dieser Abschnitt enthält Referenzinformationen für die Ansichten und die Berichte von Profiler-Datendateien, die Profilerstellungsdaten für den .NET-Arbeitsspeicher enthalten.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Summary View (Zusammenfassungsansicht)](../profiling/summary-view-dotnet-memory-data.md)  
 Führt die Funktionen und Typen auf, die den meisten Speicher belegen.  
  
 [Allocations View (Zuordnungsansicht)](../profiling/dotnet-memory-allocations-view.md)  
 Führt die während der Profilerstellung zugeordneten Typen sowie die Aufrufstrukturen (Ausführungspfade) auf, die zu der Zuordnung des Typs führten.  
  
 [Object Lifetime View (Objektlebensdaueransicht)](../profiling/object-lifetime-view.md)  
 Führt die während der Profilerstellung zugeordneten Typen sowie die Anzahl der Instanzen, die Größe in Bytes und die Garbage Collection-Generierung des Typs auf.  
  
 [Call Tree View – Sampling (Aufrufstrukturansicht – Sampling)](../profiling/call-tree-view-dotnet-memory-sampling-data.md)  
 Zeigt eine hierarchische Struktur an, die die Ausführungspfade und Speicherbelegung von Funktionen während der Profilerstellung darstellt.  
  
 [Modules View – Sampling (Modulansicht – Sampling)](../profiling/modules-view-dotnet-memory-sampling-data.md)  
 Organisiert die .NET-Arbeitsspeicherbelegungsdaten nach Modul und führt die Funktionen, Quellcodezeilen und Anweisungen auf, die ausgeführt wurden, als Speicher belegt wurde.  
  
 [Caller/Callee View – .NET Memory Sampling Data (Ansicht „Aufrufer/Aufgerufener“ – .NET-Speichersamplingdaten)](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)  
 Führt Speicherbelegungsdaten für eine ausgewählte Funktion, für die Funktionen, die die ausgewählte Funktion aufgerufen haben, sowie für die Funktionen auf, die von der ausgewählten Funktion aufgerufen wurden.  
  
 [Functions View – Sampling (Funktionsansicht – Sampling)](../profiling/functions-view-dotnet-memory-sampling-data.md)  
 Führt Speicherbelegungsdaten für die Funktionen in der Profilerstellung auf.  
  
 [Lines View – Sampling (Zeilenansicht – Sampling)](../profiling/lines-view-dotnet-memory-sampling-data.md)  
 Führt Speicherbelegungsdaten für die Quellcodezeilen von Funktionen in der Profilerstellung auf.  
  
 [Instruction Pointers (IPs) View – Sampling (Anweisungszeigeransicht – Sampling)](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)  
 Führt Speicherbelegungsdaten für die Anweisungen in der Profilerstellung auf.  
  
 [Call Tree View – Instrumentation (Aufrufstrukturansicht – Instrumentierung)](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)  
 Zeigt eine hierarchische Struktur an, die die Ausführungspfade, die Speicherbelegungsdaten und ausführliche Zeitsteuerungsdaten für instrumentierte Funktionen in der Profilerstellung darstellt.  
  
 [Modules View – Instrumentation (Modulansicht – Instrumentierung)](../profiling/modules-view-dotnet-memory-instrumentation-data.md)  
 Organisiert Profilerstellungsdaten nach Modul und führt die Funktionen, Speicherbelegungsdaten und ausführliche Zeitsteuerungsdaten für das Modul auf.  
  
 [Caller/Callee View – NET Memory Instrumentation Data (Ansicht „Aufrufer/Aufgerufener“ – .NET-Speicherinstrumentierungsdaten)](../profiling/caller-callee-view-net-memory-instrumentation-data.md)  
 Führt Speicherbelegungsdaten und ausführliche Zeitsteuerungsinformationen für eine ausgewählte instrumentierte Funktion, für die Funktionen, die die ausgewählte Funktion aufgerufen haben, und die Funktionen auf, die von der ausgewählten Funktion aufgerufen wurden.  
  
 [Functions View – Instrumentation (Funktionsansicht – Instrumentierung)](../profiling/functions-view-dotnet-memory-instrumentation-data.md)  
 Führt Speicherbelegungsdaten für die instrumentierten Funktionen in der Profilerstellung auf.  
  
## <a name="reference"></a>Referenz  
 [Funktionsdetailansicht](../profiling/function-details-view.md)  
 Zeigt ein grafisches Diagramm der Beziehung zwischen einer ausgewählten Funktion und den Funktionen an, die die ausgewählte Funktion aufgerufen haben und von dieser aufgerufen wurden.  
  
 [Process View (Prozessansicht)](../profiling/process-view.md)  
 Führt Start- und Endzeiten von Prozessen und Threads auf.  
  
 [Marks View (Markierungsansicht)](../profiling/marks-view.md)  
 Führt in eine Profilerstellungs-Datendatei eingefügte ETW- und Samplingereignisse auf.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Datenansichten der Profiler-Samplingmethode](../profiling/profiler-sampling-method-data-views.md)  
 Referenzinformationen zu den Ansichten und Berichten für Profiler-Datendateien, die mit der Samplingmethode generiert wurden.  
  
 [Instrumentation Method Data Views (Datenansichten der Instrumentationsmethode)](../profiling/instrumentation-method-data-views.md)  
 Referenzinformationen zu den Ansichten und Berichten für Profiler-Datendateien, die mit der Instrumentierungsmethode generiert werden.
