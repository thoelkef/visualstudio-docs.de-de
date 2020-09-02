---
title: Funktionsansicht – .NET-Speicherinstrumentierungsdaten | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Functions view
ms.assetid: cd45b379-394b-4b71-828c-92cd89e46ae0
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 340a12bfb8dc9a26c4200682851bb0acc684dddf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62419909"
---
# <a name="functions-view---net-memory-instrumentation-data"></a>Funktionsansicht – .NET-Speicherinstrumentierungsdaten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In der Funktionsansicht der Profilerstellungsdaten für die .NET-Speicherbelegung, die mithilfe der Instrumentierungsmethode erfasst wurden, werden die Funktionen angezeigt, die während der Profilerstellungsausführung Arbeitsspeicher belegt haben. In der Funktionszeile werden die Größe und die Anzahl der Speicherbelegungen sowie die Zeiterfassungsdaten für die Funktion angezeigt.  
  
## <a name="general"></a>Allgemein  
  
|Spalte|Beschreibung|  
|------------|-----------------|  
|**Funktionsname**|Der Name der Funktion.|  
|**Funktionsadresse**|Die Adresse der Funktion.|  
|**Funktionszeilennummer**|Die Zeilennummer des Anfangs dieser Funktion in der Quelldatei.|  
|**Anzahl der Aufrufe**|Die Gesamtzahl der Aufrufe der Funktion.|  
|**Quelldatei**|Die Quelldatei mit der Definition dieser Funktion.|  
|**Modulname**|Der Name des Moduls, das die Funktion enthält.|  
|**Modulpfad**|Der Pfad des Moduls, das die Funktion enthält.|  
|**Prozess-ID**|Die Prozess-ID (PID) der Profilerstellung.|  
|**Prozessname**|Der Prozessname.|  
|**Exklusive Zeit der Restkapazität für Überprüfungen**|Der von der Instrumentation verursachte zusätzliche Zeitaufwand für diese Funktion. Der zusätzliche Testaufwand wurde von allen exklusiven Zeiten subtrahiert.|  
|**Inklusive Zeit der Restkapazität für Überprüfungen**|Der von der Instrumentation verursachte zusätzliche Zeitaufwand für diese Funktion und ihre untergeordneten Funktionen. Der zusätzliche Testaufwand wurde von allen inklusiven Zeiten subtrahiert.|  
  
## <a name="net-memory-values"></a>.NET-Arbeitsspeicherwerte  
 Die inklusiven .NET-Arbeitsspeicherwerte einer Funktion geben die Anzahl (Zuordnungen) und die Größe (Bytes) der Objekte an, die von der Funktion und ihren untergeordneten Funktionen erstellt wurden.  
  
 Die exklusiven Arbeitsspeicherwerte geben die Anzahl und die Größe der Objekte an, die von der Funktion, nicht jedoch von den zugehörigen untergeordneten Funktionen erstellt wurden.  
  
|Spalte|Beschreibung|  
|------------|-----------------|  
|**Inklusive Speicherbelegungen**|Die Gesamtanzahl der Objekte, die in dieser Funktion und in von dieser Funktion aufgerufenen Funktionen erstellt wurden.|  
|**Inklusive Speicherbelegungen in %**|Der Prozentsatz aller Objekte, die während der Profilerstellung Speicher belegt haben und inklusive Belegungen dieser Funktion waren.|  
|**Exklusive Speicherbelegungen**|Die Gesamtanzahl der Objekte, die während der Ausführung des Codes im Funktionsrumpf erstellt wurden. Diese Zahl schließt keine Objekte ein, die in den von dieser Funktion aufgerufenen Funktionen erstellt wurden.|  
|**Exklusive Zuordnungen %**|Der Prozentsatz aller Objekte, die während der Profilerstellung erstellt wurden und exklusive Belegungen dieser Funktion waren.|  
|**Inklusive Bytes in %**|Die Anzahl der Bytes im Arbeitsspeicher, die in dieser Funktion und in von dieser Funktion aufgerufenen Funktionen belegt wurden.|  
|**Inklusive Bytes in %**|Der Prozentsatz aller Bytes im Arbeitsspeicher, die während der Profilerstellung belegt wurden und inklusive Bytes dieser Funktion waren.|  
|**Exklusive Bytes**|Die Anzahl der Bytes im Arbeitsspeicher, die von dieser Funktion, nicht jedoch von von dieser Funktion aufgerufenen Funktionen belegt wurden.|  
|**Exklusive Bytes %**|Der Prozentsatz aller Bytes im Arbeitsspeicher, die während der Profilerstellung belegt wurden und exklusive Belegungen dieser Funktion waren.|  
  
## <a name="elapsed-inclusive-values"></a>Werte für verstrichene inklusive Zeit  
 Werte für die verstrichene inklusive Zeit geben an, wie lange sich eine Funktion in der Aufrufliste befunden hat. Die Zeit umfasst den zeitlichen Aufwand für untergeordnete Funktionen und Aufrufe des Betriebssystems (z.B. Kontextwechsel und Eingabe-/Ausgabeoperationen).  
  
|Spalte|Beschreibung|  
|------------|-----------------|  
|**Verstrichene inklusive Zeit**|Die insgesamt verstrichene inklusive Zeit aller Aufrufe dieser Funktion.|  
|**Verstrichene inklusive Zeit %**|Der Prozentsatz der gesamten verstrichenen inklusiven Zeit, die innerhalb der verstrichenen inklusiven Zeit dieser Funktion auf die Profilerstellung entfällt.|  
|**Durchschnittlich verstrichene inklusive Zeit**|Die durchschnittlich verstrichene inklusive Zeit für einen Aufruf dieser Funktion.|  
|**Maximal verstrichene inklusive Zeit**|Die maximal verstrichene inklusive Zeit für einen Aufruf dieser Funktion.|  
|**Mindestens verstrichene inklusive Zeit**|Die mindestens verstrichene inklusive Zeit für einen Aufruf dieser Funktion.|  
  
## <a name="elapsed-exclusive-values"></a>Verstrichene exklusive Zeit  
 Werte für verstrichene exklusive Zeit geben die Zeit an, die eine Funktion direkt an erster Stelle der Aufrufliste ausgeführt wurde. Sie umfasst nur den zeitlichen Aufwand für Aufrufe des Betriebssystems (z.B. Kontextwechsel oder Eingabe-/Ausgabeoperationen), aber nicht die Zeit, die für untergeordnete Funktionen aufgewendet wurde.  
  
|Spalte|Beschreibung|  
|------------|-----------------|  
|**Verstrichene exklusive Zeit**|Die insgesamt verstrichene exklusive Zeit aller Aufrufe dieser Funktion.|  
|**Verstrichene exklusive Zeit %**|Der Prozentsatz der während der Profilerstellung insgesamt verstrichenen exklusiven Zeit, die sich auf die insgesamt verstrichene exklusive Zeit dieser Funktion bezieht.|  
|**Durchschnittlich verstrichene exklusive Zeit**|Die maximal verstrichene inklusive Zeit für einen Aufruf dieser Funktion.|  
|**Maximal verstrichene exklusive Zeit**|Die maximal verstrichene exklusive Zeit für einen Aufruf dieser Funktion.|  
|**Mindestens verstrichene exklusive Zeit**|Die verstrichene exklusive Mindestzeit für einen Aufruf dieser Funktion.|  
  
## <a name="application-inclusive-values"></a>Werte für inklusive Anwendungszeit  
 Werte für die inklusive Anwendungszeit geben die Zeit an, die sich eine Funktion in der Aufrufliste befunden hat. Die Zeit umfasst die Zeit in untergeordneten Funktionen, jedoch nicht die Zeit für Aufrufe des Betriebssystems, z.B. Kontextwechsel und Eingabe-/Ausgabeoperationen.  
  
|Spalte|Beschreibung|  
|------------|-----------------|  
|**Inklusive Anwendungszeit**|Die insgesamt verstrichene inklusive Zeit aller Aufrufe dieser Funktion.|  
|**Inklusive Anwendungszeit %**|Der Prozentsatz der insgesamt verstrichenen inklusiven Zeit, die innerhalb der gesamten inklusiven Anwendungszeit dieser Funktion auf die Profilerstellung entfällt.|  
|**Durchschnittliche inklusive Anwendungszeit**|Die im Durchschnitt für einen Aufruf dieser Funktion aufgewendete inklusive Anwendungszeit.|  
|**Maximale inklusive Anwendungszeit**|Die maximal verstrichene inklusive Zeit für einen Aufruf dieser Funktion.|  
|**Minimale inklusive Anwendungszeit**|Die mindestens verstrichene inklusive Zeit für einen Aufruf dieser Funktion.|  
  
## <a name="application-exclusive-values"></a>Werte für exklusive Anwendungszeit  
 Werte für exklusive Anwendungszeit geben die Zeit an, die eine Funktion direkt an erster Stelle der Aufrufliste ausgeführt wurde. Diese Zeit umfasst weder die Zeit in Aufrufen an das Betriebssystem (z.B. Kontextwechsel und Eingabe-/Ausgabevorgänge) noch die Zeit in untergeordneten Funktionen.  
  
|Spalte|Beschreibung|  
|------------|-----------------|  
|**Exklusive Anwendungszeit**|Die gesamte exklusive Anwendungszeit aller Aufrufe dieser Funktion.|  
|**Exklusive Anwendungszeit %**|Der Prozentsatz der gesamten verstrichenen exklusiven Zeit, die innerhalb der exklusiven Gesamtanwendungszeit dieser Funktion auf die Profilerstellung entfällt.|  
|**Durchschnittliche exklusive Anwendungszeit**|Die im Durchschnitt für einen Aufruf dieser Funktion aufgewendete exklusive Anwendungszeit.|  
|**Maximale exklusive Anwendungszeit**|Die maximale exklusive Anwendungszeit für einen Aufruf dieser Funktion.|  
|**Minimale exklusive Anwendungszeit**|Die exklusive Mindestanwendungszeit für einen Aufruf dieser Funktion.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Vorgehensweise: Anpassen von Spalten in der Berichtsansicht](../profiling/how-to-customize-report-view-columns.md)   
 [Funktions Ansicht-Sampling](../profiling/functions-view-dotnet-memory-sampling-data.md)   
 [Funktions Ansicht](../profiling/functions-view-instrumentation-data.md)   
 [Funktionsansicht](../profiling/functions-view-sampling-data.md)
