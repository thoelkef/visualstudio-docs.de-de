---
title: Modulansicht – .NET-Speichersamplingdaten im Profiler | Microsoft-Dokumentation
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
- Modules view
ms.assetid: 9c05b51a-8382-44cf-a8f7-3fabdd2e8f1b
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3334edce4d29792e44f4cab0840a9f46763d74aa
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49185385"
---
# <a name="modules-view---net-memory-sampling-data"></a>Modulansicht – .NET-Speichersamplingdaten im Profiler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In der Modulansicht der .NET-Speicherbelegungsdaten, die mithilfe der Instrumentationsmethode erfasst wurden, werden die Arbeitsspeicher- und Zeitsteuerungsdaten nach den Modulen gruppiert, die während der Profilerstellung ausgeführt wurden. Jedes Modul ist der Stamm einer hierarchischen Struktur. Die Funktionen des Moduls werden unter dem Modulknoten aufgeführt.  
  
 Die Quelldatei-Zeilennummern von Anweisungen, die Speicher belegen, sind unter dem Funktionsknoten aufgeführt. Die Adressen der Anweisungen, die die Zuordnung vornehmen, sind unter dem Zeilenknoten aufgeführt. Die inklusiven und exklusiven Werte für Zeilen- und Anweisungsdaten sind immer identisch.  
  
|Spalte|Beschreibung|  
|------------|-----------------|  
|**Name**|Der Name des Moduls, der Funktion, der Zeilennummer oder der Anweisungsadresse.|  
|**Prozess-ID**|Die Prozess-ID (PID) der Profilerstellung.|  
|**Prozessname**|Der Prozessname.|  
|**Modulname**|Der Name des Moduls, das die Funktion enthält.|  
|**Modulpfad**|Der Pfad des Moduls.|  
|**Quelldatei**|Die Quelldatei, die die Definition der Funktion enthält.|  
|**Funktionszeilennummer**|Die Zeilennummer des Anfangs dieser Funktion in der Quelldatei.|  
|**Inklusive Speicherbelegungen**|- Bei einer Funktion die Gesamtzahl von Objekten, die von der Funktion erstellt wurden. Die Zahl umfasst auch Objekte, die von den von der Funktion aufgerufenen Funktionen erstellt wurden.<br />- Bei einem Modul die Anzahl von Objekten, die während einer Profilerstellung zugeordnet wurden, als mindestens eine Funktion des Moduls ausgeführt wurde. Diese Zahl umfasst auch Objekte, die in von den Modulfunktionen aufgerufenen Funktionen erstellt wurden.<br />- Bei einer Zeile oder Anweisung die Gesamtzahl der Objekte, die von der Zeile oder der Anweisung zugeordnet wurden.|  
|**Inklusive Speicherbelegungen in %**|Der Prozentsatz aller Objekte, die während der Profilerstellung als inklusive Zuordnungen dieses Moduls, dieser Funktion, dieser Zeile oder dieser Anweisung zugeordnet wurden.|  
|**Exklusive Zuordnungen**|- Bei der aktuellen Funktion die Anzahl von Objekten, die während der Ausführung von Code im Funktionstext (d.h. während sich die Funktion auf der obersten Ebene der Aufrufliste befand) erstellt wurden. Diese Zahl umfasst keine Objekte, die in den von dieser Funktion aufgerufenen Funktionen erstellt wurden.<br />- Bei einem Modul die Summe der exklusiven Zuordnungen der Funktionen im Modul.<br />- Bei einer Zeile oder Anweisung die Gesamtzahl von Objekten, die von dieser Zeile oder Anweisung zugeordnet wurden.|  
|**Exklusive Zuordnungen in %**|Der Prozentsatz aller Objekte, die während der Profilerstellung als exklusive Zuordnungen dieses Moduls, dieser Funktion, dieser Zeile oder dieser Anweisung zugeordnet wurden.|  
|**Inklusive Bytes in %**|- Bei einer Funktion die Gesamtzahl von Bytes, die von der Funktion zugeordnet wurden. Diese Zahl umfasst auch Bytes, die in von der Funktion aufgerufenen Funktionen zugeordnet wurden.<br />- Bei einem Modul die Anzahl von bei einer Profilerstellung zugeordneten Bytes, die während der Ausführung von mindestens einer Funktion des Moduls zugeordnet wurden. Diese Zahl umfasst auch Objekte, die in allen von den Modulfunktionen aufgerufenen Funktionen erstellt wurden.<br />- Bei einer Zeile oder Anweisung die Gesamtzahl von Objekten, die von dieser Zeile oder Anweisung zugeordnet wurden.|  
|**Inklusive Bytes in %**|Der Prozentsatz aller während der Profilerstellung zugeordneten Bytes, die inklusive Bytes des Moduls, der Funktion, der Zeile oder der Anweisung waren.|  
|**Exklusive Bytes**|- Bei einer Funktion die Gesamtzahl von Bytes, die von der Funktion zugeordnet wurden. Diese Zahl umfasst nicht die Bytes, die in den von der Funktion aufgerufenen Funktionen zugeordnet wurden.<br />- Bei einem Modul die Summe der exklusiven Bytes, die von den Funktionen im Modul zugeordnet wurden.<br />- Bei einer Zeile oder Anweisung die Gesamtzahl von Objekten, die von der Zeile oder der Anweisung zugeordnet wurden.|  
|**Exklusive Bytes in %**|Der Prozentsatz aller während der Profilerstellung zugeordneten Bytes, die exklusive Bytes des Moduls, der Funktion, der Zeile oder der Anweisung waren.|  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Anpassen von Spalten in Berichtsansichten](../profiling/how-to-customize-report-view-columns.md)   
 [Modulansicht – Instrumentation](../profiling/modules-view-dotnet-memory-instrumentation-data.md)   
 [Modulansicht](../profiling/modules-view-sampling-data.md)   
 [Modulansicht](../profiling/modules-view-instrumentation-data.md)



