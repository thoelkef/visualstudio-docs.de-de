---
title: 'Funktionsansicht: .NET-Speichersamplingdaten | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Functions view
ms.assetid: 5d9c6302-2ffd-430e-9535-13ce795f9f7c
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bfdfbab17538648b816c094409f9396cc5f638b8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51788315"
---
# <a name="functions-view---net-memory-sampling-data"></a>Funktionsansicht: .NET-Speichersamplingdaten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In der Funktionsansicht der Profilerstellungsdaten für die .NET-Speicherbelegung, die mithilfe der Samplingmethode erfasst wurden, werden sowohl die Funktionen angezeigt, die während der Profilerstellungsausführung Arbeitsspeicher belegt haben, als auch die Größe und die Anzahl der Speicherbelegungen.  
  
|Spalte|Beschreibung|  
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



