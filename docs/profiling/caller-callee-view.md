---
title: Aufrufer-/Aufgerufener-Ansicht | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 973c65927e3732cff44ab8eecb684f3c75af8614
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34264293"
---
# <a name="callercallee-view"></a>Aufrufer-/Aufgerufener-Ansicht
In der Aufrufer-/Aufgerufener-Ansicht werden Profilerstellungsinformationen für eine ausgewählte Funktion und ihre übergeordneten und untergeordneten Funktionen angezeigt. Die Aufrufer-/Aufgerufener-Ansicht enthält drei Raster:  
  
 **Aktuelle Funktion** wird im mittleren Raster angezeigt und zeigt Profilerstellungsinformationen für die ausgewählte Funktion an. Die Werte beinhalten alle Aufrufe der Funktion, die während der Profilerstellungsausführung gesammelt wurden.  
  
 **Funktionen, die die aktuelle Funktion aufgerufen haben** wird im obersten Raster angezeigt und gibt die Anzahl der Werte der ausgewählten (aktuellen) Funktion an, die durch Aufrufe der (übergeordneten) Aufruferfunktion generiert wurden.  
  
 **Funktionen, die von der aktuellen Funktion aufgerufen wurden** wird im untersten Raster angezeigt und gibt Profilerstellungsinformationen für die aufgerufenen (untergeordneten) Funktionen der ausgewählten Funktion an, wenn die untergeordnete Funktion von der aktuellen Funktion aufgerufen wurde.  
  
 Welche Spalten in der Aufrufer-/Aufgerufener-Ansicht verfügbar sind, ist abhängig von der Profilerstellungsmethode (Sampling oder Instrumentation), die zum Sammeln der Daten verwendet wurde, und davon, ob in der Profilerstellungsausführung .NET-Arbeitsspeicherdaten gesammelt wurden.  
  
 Für den mittleren Bereich der Berichtsansicht können Sie eine andere Funktion als aktuelle Funktion auswählen, indem Sie in einem der anderen beiden Bereiche der Ansicht auf die gewünschte Funktion doppelklicken. Die Berichtsansicht wird automatisch aktualisiert, um die Änderungen widerzuspiegeln.  
  
 Sie können die Daten durch Klicken auf die Spaltennamen sortieren. Der Aufrufer-/Aufgerufener-Ansicht können zusätzliche Spalten hinzugefügt werden. Weitere Informationen finden Sie unter [Vorgehensweise: Anpassen von Spalten in der Berichtsansicht der Profilerstellungstools](../profiling/how-to-customize-report-view-columns.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Caller/Callee view – sampling data (Aufrufer-/Aufgerufener-Ansicht – Samplingdaten)](../profiling/caller-callee-view-sampling-data.md)   
 [Caller/Callee view – instrumentation data (Aufrufer-/Aufgerufener-Ansicht – Instrumentierungsdaten)](../profiling/caller-callee-view-instrumentation-data.md)   
 [Caller/Callee view – .NET memory instrumentation data (Aufrufer-/Aufgerufener-Ansicht – Instrumentierungsdaten des .NET-Arbeitsspeichers)](../profiling/caller-callee-view-net-memory-instrumentation-data.md)   
 [Caller/Callee view – .NET memory sampling data (Aufrufer-/Aufgerufener-Ansicht – Samplingdaten des .NET-Arbeitsspeichers)](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Caller/Callee view –  contention data (Ansicht der Aufrufer/Aufgerufenen – Konfliktdaten)](../profiling/caller-callee-view-contention-data.md)