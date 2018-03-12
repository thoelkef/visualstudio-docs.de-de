---
title: 'Funktionsansicht: .NET-Speichersamplingdaten | Microsoft-Dokumentation'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Functions view
ms.assetid: 5d9c6302-2ffd-430e-9535-13ce795f9f7c
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 92d2df0182f976af36e9182d080ef6b51130c826
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="functions-view---net-memory-sampling-data"></a>Funktionsansicht: .NET-Speichersamplingdaten
In der Funktionsansicht der Profilerstellungsdaten für die .NET-Speicherbelegung, die mithilfe der Samplingmethode erfasst wurden, werden sowohl die Funktionen angezeigt, die während der Profilerstellungsausführung Arbeitsspeicher belegt haben, als auch die Größe und die Anzahl der Speicherbelegungen.  
  
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
|**Inklusive Speicherbelegungen**|Die Gesamtanzahl der Objekte, die in dieser Funktion und ihren untergeordneten Funktionen Speicher belegt haben.|  
|**Inklusive Speicherbelegungen in %**|Der Prozentsatz aller Objekte, die während der Profilerstellung Speicher belegt haben und inklusive Belegungen dieser Funktion waren.|  
|**Exklusive Speicherbelegungen**|Die Anzahl der Objekte, die während der Ausführung der Funktion am Anfang der Aufrufliste erstellt wurden. Diese Zahl schließt nicht die Objekte mit ein, die in untergeordneten Funktionen erstellt wurden.|  
|**Exklusive Zuordnungen %**|Der Prozentsatz aller Objekte, die während der Profilerstellung Speicher belegt haben und exklusive Belegungen dieser Funktion waren.|  
|**Inklusive Bytes in %**|Die Anzahl der Bytes im Arbeitsspeicher, die von dieser Funktion und ihren untergeordneten Funktionen belegt wurden.|  
|**Inklusive Bytes in %**|Der Prozentsatz aller Bytes im Arbeitsspeicher, die während der Profilerstellung belegt wurden und inklusive Bytes dieser Funktion waren.|  
|**Exklusive Bytes**|Die Anzahl der Bytes im Arbeitsspeicher, die von dieser Funktion, nicht jedoch von ihren untergeordneten Funktionen belegt wurden.|  
|**Exklusive Bytes %**|Der Prozentsatz aller Bytes im Arbeitsspeicher, die während der Profilerstellung belegt wurden und exklusive Belegungen dieser Funktion waren.|  
  
## <a name="see-also"></a>Siehe auch  
 [Funktionsansicht - Instrumentierung](../profiling/functions-view-dotnet-memory-instrumentation-data.md)   
 [Funktionsansicht](../profiling/functions-view-sampling-data.md)   
 [Funktionsansicht](../profiling/functions-view-instrumentation-data.md)