---
title: Aufrufer-/Aufgerufener-Ansicht | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.callercallee
helpviewer_keywords:
- profiling tools, reports, Caller/Callee view
- profiling tools, Caller/Callee view
- performance reports, Caller/Callee view
- Caller/Callee view
ms.assetid: d3511bcf-cce0-4cbe-aecb-b94c7c80ad1b
caps.latest.revision: 37
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 58aca542571066ecfa9328c9600972665e757150
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54788943"
---
# <a name="callercallee-view"></a>Aufrufer-/Aufgerufener-Ansicht
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In der Aufrufer-/Aufgerufener-Ansicht werden Profilerstellungsinformationen für eine ausgewählte Funktion und ihre übergeordneten und untergeordneten Funktionen angezeigt. Die Aufrufer-/Aufgerufener-Ansicht enthält drei Raster:  
  
 **Aktuelle Funktion** wird im mittleren Raster angezeigt und zeigt Profilerstellungsinformationen für die ausgewählte Funktion an. Die Werte beinhalten alle Aufrufe der Funktion, die während der Profilerstellungsausführung gesammelt wurden.  
  
 **Funktionen, die die aktuelle Funktion aufgerufen haben** wird im obersten Raster angezeigt und gibt die Anzahl der Werte der ausgewählten (aktuellen) Funktion an, die durch Aufrufe der (übergeordneten) Aufruferfunktion generiert wurden.  
  
 **Funktionen, die von der aktuellen Funktion aufgerufen wurden** wird im untersten Raster angezeigt und gibt Profilerstellungsinformationen für die aufgerufenen (untergeordneten) Funktionen der ausgewählten Funktion an, wenn die untergeordnete Funktion von der aktuellen Funktion aufgerufen wurde.  
  
 Welche Spalten in der Aufrufer-/Aufgerufener-Ansicht verfügbar sind, ist abhängig von der Profilerstellungsmethode (Sampling oder Instrumentation), die zum Sammeln der Daten verwendet wurde, und davon, ob in der Profilerstellungsausführung .NET-Arbeitsspeicherdaten gesammelt wurden.  
  
 Für den mittleren Bereich der Berichtsansicht können Sie eine andere Funktion als aktuelle Funktion auswählen, indem Sie in einem der anderen beiden Bereiche der Ansicht auf die gewünschte Funktion doppelklicken. Die Berichtsansicht wird automatisch aktualisiert, um die Änderungen widerzuspiegeln.  
  
 Sie können die Daten durch Klicken auf die Spaltennamen sortieren. Der Aufrufer-/Aufgerufener-Ansicht können zusätzliche Spalten hinzugefügt werden. Weitere Informationen finden Sie unter [Vorgehensweise: Anpassen von Spalten in der Berichtsansicht der Profilerstellungstools](../profiling/how-to-customize-report-view-columns.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Aufrufer-/Aufgerufener-Ansicht – Profiler-Samplingdaten](../profiling/caller-callee-view-sampling-data.md)   
 [Aufrufer-/Aufgerufener-Ansicht – Profiler-Instrumentationsdaten](../profiling/caller-callee-view-instrumentation-data.md)   
 [Aufrufer-/Aufgerufener-Ansicht – .NET-Speicherinstrumentationsdaten im Profiler](../profiling/caller-callee-view-net-memory-instrumentation-data.md)   
 [Aufrufer-/Aufgerufener-Ansicht – .NET-Speichersamplingdaten im Profiler](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Aufrufer-/Aufgerufener-Ansicht – Profiler-Konfliktdaten](../profiling/caller-callee-view-contention-data.md)
