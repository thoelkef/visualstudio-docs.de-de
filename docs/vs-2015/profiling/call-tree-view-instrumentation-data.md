---
title: Aufrufstrukturansicht – Instrumentationsdaten | Microsoft-Dokumentation
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
- Call Tree view
ms.assetid: 306bd176-0ce9-4a10-89ca-20b043d37d4e
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 630f75468adf5995eb887ac5f73d82462bfe32a4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51786242"
---
# <a name="call-tree-view---instrumentation-data"></a>Aufrufstrukturansicht – Instrumentationsdaten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Werte einer Funktion in der Aufrufstruktur geben die Zeit für die Funktionsinstanzen an, die von der übergeordneten Funktion in der Aufrufliste aufgerufen wurden. Prozentwerte werden berechnet, indem der Wert der Funktionsinstanzen mit der gesamten verstrichenen inklusiven Zeit aller Funktionen in der Profilerstellung verglichen wird.  
  
## <a name="general"></a>Allgemein  
 Die allgemeinen Spalten bezeichnen die Funktion in einer Ansichtszeile.  
  
|Spalte|Beschreibung|  
|------------|-----------------|  
|**Funktionsname**|Der Name der Funktion.|  
|**Funktionsadresse**|Die Adresse der Funktion.|  
|**Funktionszeilennummer**|Die Zeilennummer des Anfangs dieser Funktion in der Quelldatei.|  
|**Anzahl der Aufrufe**|Die Gesamtzahl der Aufrufe der Funktion.|  
|**Quelldatei**|Die Quelldatei, die die Definition der Funktion enthält.|  
|**Modulname**|Der Name des Moduls, das die Funktion enthält.|  
|**Modulpfad**|Der Pfad des Moduls, das die Funktion enthält.|  
|**Prozess-ID**|Die Prozess-ID (PID) der Profilerstellung.|  
|**Prozessname**|Der Name, der dem Prozess zugewiesen ist.|  
|**Exklusive Zeit der Restkapazität für Überprüfungen**|Der von der Instrumentation verursachte zusätzliche Zeitaufwand für diese Funktion. Der zusätzliche Testaufwand wurde von allen exklusiven Zeiten subtrahiert.|  
|**Inklusive Zeit der Restkapazität für Überprüfungen**|Der von der Instrumentation verursachte zusätzliche Zeitaufwand für diese Funktion und ihre untergeordneten Funktionen. Der zusätzliche Testaufwand wurde von allen inklusiven Zeiten subtrahiert.|  
|**Ebene**|Die Tiefe der Funktion in der Aufrufstruktur. Nur in [VSPerfReport](../profiling/vsperfreport.md)-Befehlszeilenberichten.|  
  
## <a name="elapsed-inclusive-values"></a>Verstrichene inklusive Zeit  
 Die Werte für die verstrichene inklusive Zeit geben die Zeit an, die sich Funktionsinstanzen, die von der übergeordneten Funktion in der Aufrufliste aufgerufen wurden, in der Aufrufliste befanden. Die Zeit umfasst die Zeit in untergeordneten Funktionen, die von der Funktion aufgerufen wurden, und die Zeit für Aufrufe des Betriebssystems, z.B. Kontextwechsel und Eingabe-/Ausgabeoperationen.  
  
|Spalte|Beschreibung|  
|------------|-----------------|  
|**verstrichene inklusive Zeit**|Die gesamte verstrichene inklusive Zeit aller Aufrufe dieser Funktion in diesem Kontext.|  
|**verstrichene inklusive Zeit %**|Der Prozentsatz der gesamten verstrichenen inklusiven Zeit, die innerhalb der gesamten verstrichenen inklusiven Zeit dieser Funktion in diesem Kontext auf die Profilerstellung entfällt.|  
|**Durchschnittliche verstrichene inklusive Zeit**|Die durchschnittliche verstrichene inklusive Zeit eines Aufrufs dieser Funktion in diesem Kontext.|  
|**Maximal verstrichene inklusive Zeit**|Die maximale verstrichene inklusive Zeit eines Aufrufs dieser Funktion in diesem Kontext.|  
|**Mindestens verstrichene inklusive Zeit**|Die mindestens verstrichene inklusive Zeit eines Aufrufs dieser Funktion in diesem Kontext.|  
  
## <a name="elapsed-exclusive-values"></a>Verstrichene exklusive Zeit  
 Die Werte für die verstrichene exklusive Zeit geben die Zeit an, die Funktionsinstanzen, die von der übergeordneten Funktion in der Aufrufstruktur aufgerufen wurden, Code im Funktionsrumpf ausgeführt haben, d.h., als sich die Funktion an erster Stelle der Aufrufliste befunden hat. Die Zeit beinhaltet die Zeit für Aufrufe des Betriebssystems, z.B. Kontextwechsel und Eingabe-/Ausgabeoperationen. Die Zeit, die in von der Funktion aufgerufenen untergeordneten Funktionen aufgewendet wurde, wird jedoch nicht berücksichtigt.  
  
|Spalte|Beschreibung|  
|------------|-----------------|  
|**verstrichene exklusive Zeit**|Die gesamte verstrichene exklusive Zeit aller Aufrufe dieser Funktion in diesem Kontext.|  
|**verstrichene exklusive Zeit %**|Der Prozentsatz der gesamten verstrichenen exklusiven Zeit, die innerhalb der gesamten verstrichenen exklusiven Zeit dieser Funktion in diesem Kontext auf die Profilerstellung entfällt.|  
|**Durchschnittlich verstrichene exklusive Zeit**|Die durchschnittliche verstrichene exklusive Zeit eines Aufrufs dieser Funktion in diesem Kontext.|  
|**Maximal verstrichene exklusive Zeit**|Die maximale verstrichene exklusive Zeit eines Aufrufs dieser Funktion in diesem Kontext.|  
|**Mindestens verstrichene exklusive Zeit**|Die mindestens verstrichene exklusive Zeit eines Aufrufs dieser Funktion in diesem Kontext.|  
  
## <a name="application-inclusive-values"></a>Werte für inklusive Anwendungszeit  
 Die Werte für die inklusive Anwendungszeit geben die Zeit an, die sich Funktionsinstanzen, die von der übergeordneten Funktion in der Aufrufliste aufgerufen wurden, in der Aufrufliste befanden. Die Zeit umfasst nicht die Zeit für Aufrufe des Betriebssystems, z.B. Kontextwechsel und Eingabe-/Ausgabeoperationen. Berücksichtigt wird hingegen die Zeit, die in von der Funktion aufgerufenen untergeordneten Funktionen aufgewendet wurde.  
  
|Spalte|Beschreibung|  
|------------|-----------------|  
|**inklusive Anwendungszeit**|Die gesamte inklusive Anwendungszeit aller Aufrufe dieser Funktion in diesem Kontext.|  
|**inklusive Anwendungszeit %**|Der Prozentsatz der insgesamt verstrichenen inklusiven Zeit, die innerhalb der gesamten inklusiven Anwendungszeit dieser Funktion in diesem Kontext auf die Profilerstellung entfällt.|  
|**Durchschnittliche inklusive Anwendungszeit**|Die durchschnittliche inklusive Anwendungszeit eines Aufrufs dieser Funktion in diesem Kontext.|  
|**Maximale inklusive Anwendungszeit**|Die maximale inklusive Anwendungszeit eines Aufrufs dieser Funktion in diesem Kontext.|  
|**Minimale inklusive Anwendungszeit**|Die minimale inklusive Anwendungszeit eines Aufrufs dieser Funktion in diesem Kontext.|  
  
## <a name="application-exclusive-values"></a>Exklusive Anwendungszeit  
 Die Werte für die exklusive Anwendungszeit geben die Zeit an, die Funktionsinstanzen, die von der übergeordneten Funktion in der Aufrufstruktur aufgerufen wurde, direkt Code im Funktionsrumpf ausgeführt haben, d.h., als sich die Funktion an erster Stelle der Aufrufliste befunden hat. Die Zeit umfasst nicht die Zeit für Aufrufe des Betriebssystems, z.B. Kontextwechsel und Eingabe-/Ausgabeoperationen. Auch die Zeit, die in von der Funktion aufgerufenen untergeordneten Funktionen aufgewendet wurde, wird nicht berücksichtigt.  
  
|Spalte|Beschreibung|  
|------------|-----------------|  
|**exklusive Anwendungszeit**|Die gesamte exklusive Anwendungszeit aller Aufrufe dieser Funktion in diesem Kontext.|  
|**exklusive Anwendungszeit %**|Der Prozentsatz der gesamten verstrichenen exklusiven Zeit, die innerhalb der exklusiven Gesamtanwendungszeit dieser Funktion in diesem Kontext auf die Profilerstellung entfällt.|  
|**Durchschnittliche exklusive Anwendungszeit**|Die durchschnittliche exklusive Anwendungszeit eines Aufrufs dieser Funktion in diesem Kontext.|  
|**Maximale exklusive Anwendungszeit**|Die maximale exklusive Anwendungszeit eines Aufrufs dieser Funktion in diesem Kontext.|  
|**Minimale exklusive Anwendungszeit**|Die minimale exklusive Anwendungszeit eines Aufrufs dieser Funktion in diesem Kontext.|  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Anpassen von Spalten in Berichtsansichten](../profiling/how-to-customize-report-view-columns.md)   
 [Aufrufstrukturansicht](../profiling/call-tree-view-sampling-data.md)   
 [Aufrufstrukturansicht – .NET-Speicherinstrumentationsdaten im Profiler](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)   
 [Aufrufstrukturansicht – Profiler-Samplingdaten](../profiling/call-tree-view-dotnet-memory-sampling-data.md)



