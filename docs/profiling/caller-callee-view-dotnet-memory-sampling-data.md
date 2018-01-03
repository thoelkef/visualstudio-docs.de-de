---
title: "Aufrufer-/Aufgerufener-Ansicht – .NET-Speichersamplingdaten | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Caller/Callee view
ms.assetid: 36f5b4de-5686-4f40-9e72-f4aee27d833c
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 275ec14b1b6a0d43d2c8fdb88bbf1056db86d097
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="callercallee-view---net-memory-sampling-data"></a>Aufrufer-/Aufgerufener-Ansicht – .NET-Speichersamplingdaten
In der Aufrufer-/Aufgerufener-Ansicht werden .NET-Speicherdaten einer Profilerstellung für eine ausgewählte Funktion und ihre übergeordneten und untergeordneten Funktionen angezeigt. Die Aufrufer-/Aufgerufener-Ansicht enthält drei Raster.  
  
 **Aktuelle Funktion** wird im mittleren Raster angezeigt und gibt Speicherinformationen zur Profilerstellung für die ausgewählte Funktion an. Die Werte umfassen alle Samplingaufrufe der Funktion.  
  
 **Funktionen, die die aktuelle Funktion aufgerufen haben** wird im obersten Raster angezeigt und gibt den Wert der ausgewählten (aktuellen) Funktion an, die durch Aufrufe der (übergeordneten) Aufruferfunktion generiert wurde.  
  
 **Funktionen, die von der aktuellen Funktion aufgerufen wurden** wird im untersten Raster angezeigt und gibt Speicherdaten zur Profilerstellung für die aufgerufenen (untergeordneten) Funktionen der ausgewählten Funktion an, wenn die untergeordnete Funktion von der aktuellen Funktion aufgerufen wurde.  
  
 Doppelklicken Sie auf eine Zeile einer Aufrufer- oder Aufgerufener-Funktion, um diese Zeile zur aktuellen Funktion zu machen.  
  
|Spalte|description|  
|------------|-----------------|  
|**Prozess-ID**|Die Prozess-ID (PID) der Profilerstellung.|  
|**Prozessname**|Der Prozessname.|  
|**Modulname**|Der Name des Moduls, das die Funktion enthält.|  
|**Modulpfad**|Der Pfad des Moduls, das die Funktion enthält.|  
|**Quelldatei**|Die Quelldatei, die die Definition der Funktion enthält.|  
|**Funktionsname**|Der vollqualifizierte Name der Funktion.|  
|**Funktionszeilennummer**|Die Zeilennummer des Anfangs dieser Funktion in der Quelldatei.|  
|**Funktionsadresse**|Die Adresse der Funktion.|  
|**Type**|Der Kontext der Funktion:<br /><br /> **0** – die aktuelle Funktion<br /><br /> **1** – eine Funktion, die die aktuelle Funktion aufruft<br /><br /> **2** – eine Funktionen, die von der aktuellen Funktion aufgerufen wird<br /><br /> Nur in [VSPerfReport](../profiling/vsperfreport.md)-Befehlszeilenberichten.|  
|**Ebene**|Die Tiefe der Funktion in der Aufrufstruktur. Nur in [VSPerfReport](../profiling/vsperfreport.md)-Befehlszeilenberichten.|  
|**Inklusive Speicherbelegungen**|- Bei der aktuellen Funktion die Anzahl der Objekte, die während der Profilerstellung von der Funktion belegt wurden. Diese Zahl schließt in aufgerufenen Funktionen erstellte Objekte ein.<br />- Bei einer aufrufenden Funktion die Anzahl von inklusiven Zuordnungen der aktuellen Funktion, die von Aufrufen von dieser Funktion generiert wurden.<br />- Bei einer aufgerufenen Funktion die Anzahl von Objekten, die von den Instanzen dieser Funktion zugeordnet wurden, die von der aktuellen Funktion aufgerufen wurden. Die Zahl umfasst Zuordnungen von Funktionen, die von dieser aufgerufenen Funktion aufgerufen wurden.|  
|**Inklusive Speicherbelegungen in %**|Der Prozentsatz aller Objekte, die während der Profilerstellung erstellt wurden und inklusive Belegungen dieser Funktion waren.|  
|**Exklusive Speicherbelegungen**|- Bei der aktuellen Funktion die Anzahl von Objekten, die während der Ausführung von Code im Funktionstext erstellt wurden (d.h., während sich die Funktion an erster Stelle der Aufrufliste befand). Die Zahl umfasst keine Objekte, die in den von der Funktion aufgerufenen Funktionen erstellt wurden.<br />- Bei einer aufrufenden Funktion die Anzahl von exklusiven Zuordnungen der aktuellen Funktion, die von Aufrufen von dieser Funktion generiert wurden.<br />- Bei einer aufgerufenen Funktion die Anzahl von Objekten, die von den Instanzen dieser Funktion erstellt wurden, die von der aktuellen Funktion aufgerufen wurden. Die Zahl umfasst keine Objekte, die von den von der aufgerufenen Funktion aufgerufenen Funktionen erstellt wurden.|  
|**Exklusive Zuordnungen %**|Der Prozentsatz aller Objekte, die während der Profilerstellung erstellt wurden und inklusive Belegungen dieser Funktion waren.|  
|**Inklusive Bytes in %**|- Bei der aktuellen Funktion die Anzahl der Bytes im Arbeitsspeicher, die während der Profilerstellung von der Funktion belegt wurden. Diese Zahl umfasst auch Arbeitsspeicher, der von in dieser Funktion aufgerufenen Funktionen belegt wurde.<br />- Bei einer aufrufenden Funktion die Anzahl von inklusiven Bytes der aktuellen Funktion, die von Aufrufen der aufrufenden Funktion generiert wurden.<br />- Bei einer aufgerufenen Funktion die Anzahl von Bytes, die von den durch Aufrufe aus der aktuellen Funktion generierten Instanzen dieser Funktion belegt wurden. Die Zahl umfasst auch Bytes, die in von dieser aufgerufenen Funktion aufgerufenen Funktionen zugeordnet wurden.|  
|**Inklusive Bytes in %**|Der Prozentsatz aller Bytes des Arbeitsspeichers, die während der Profilerstellung belegt wurden und inklusive Belegungen dieser Funktion waren.|  
|**Exklusive Bytes**|- Bei der aktuellen Funktion die Anzahl der Bytes im Arbeitsspeicher, die während der Profilerstellung von der Funktion belegt wurden. Diese Zahl umfasst nicht den Arbeitsspeicher, der von Funktionen belegt wurde, die von der aktuellen Funktion aufgerufen wurden.<br />- Bei einer aufrufenden Funktion die Anzahl der exklusiven Bytes der aktuellen Funktion, die von Aufrufen von dieser aufrufenden Funktion generiert wurden.<br />- Bei einer aufgerufenen Funktion die Anzahl von Bytes, die von den durch Aufrufe aus der aktuellen Funktion generierten Instanzen dieser Funktion belegt wurden. Diese Zahl umfasst nicht die Bytes, die in den von der Funktion aufgerufenen Funktionen zugeordnet wurden.|  
|**Exklusive Bytes %**|Der Prozentsatz aller Bytes des Arbeitsspeichers, die während der Profilerstellung belegt wurden und exklusive Belegungen dieser Funktion waren.|  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Anpassen von Spalten in Berichtsansichten](../profiling/how-to-customize-report-view-columns.md)   
 [Aufrufer-/Aufgerufener-Ansicht – .NET-Speicherinstrumentationsdaten im Profiler](../profiling/caller-callee-view-net-memory-instrumentation-data.md)   
 [Aufrufer-/Aufgerufener-Ansicht – Profiler-Samplingdaten](../profiling/caller-callee-view-sampling-data.md)   
 [Aufrufer-/Aufgerufener-Ansicht – Profiler-Instrumentationsdaten](../profiling/caller-callee-view-instrumentation-data.md)