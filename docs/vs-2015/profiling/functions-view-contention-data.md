---
title: Funktionsansicht – Konfliktdaten | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Functions view
ms.assetid: 208773b0-1a54-4b7a-ad37-2b6fd4f731d4
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1aaab824f40c0cd6ba0a240a6f3035d7ebcccd00
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68141893"
---
# <a name="functions-view---contention-data"></a>Funktionsansicht – Konfliktdaten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Funktionsberichtansicht der Konfliktdatenlisten der Funktionen in der Profilerstellungsausführung, deren Ausführung während der Profilerstellung blockiert wurde.  
  
 In der folgenden Tabelle werden die Werte erklärt, die in der Funktionsansicht einer Profilerstellungsdatendatei angezeigt werden, die anhand der Parallelitätsmethode erstellt wurde.  
  
|Spalte|Beschreibung|  
|------------|-----------------|  
|**Exklusive blockierte Zeit %**|Der Zeitraum, in dem diese Funktion keinen Code im Text der Funktion ausführen konnte. Diese umfasst nicht den Zeitaufwand für Funktionen, die von dieser Funktion aufgerufen wurden.|  
|**Exklusive blockierte Zeit %**|Der Prozentsatz der gesamten blockierten Zeit in der Profilerstellung, für die nur diese Funktion blockiert wurde.|  
|**Exklusive Konflikte**|Wie oft die Funktion vom Ausführen von Code im Text der Funktion abgehalten wurde. Konflikte in Funktionen, die von dieser Funktion aufgerufen wurden, werden nicht einbezogen.|  
|**Exklusive Konflikte %**|Der Prozentsatz aller Konflikte in der Profilerstellung, die allein in dieser Funktion aufgetreten sind.|  
|**Funktionsadresse**|Die Adresse der Funktion.|  
|**Funktionsname**|Der vollqualifizierte Name der Funktion.|  
|**Inklusive blockierte Zeit**|Die Zeit, die diese Funktion oder eine Funktion, die von dieser Funktion aufgerufen wurde, nicht ausgeführt werden konnte.|  
|**Inklusive blockierte Zeit %**|Der Prozentsatz der gesamten blockierten Zeit während der Profilerstellung, die für diese Funktion oder Methode blockiert wurde.|  
|**Inklusive Konflikte %**|Wie oft diese Funktion oder eine Funktion, die von dieser Funktion aufgerufen wurde, nicht ausgeführt werden konnte.|  
|**Inklusive Konflikte %**|Der Prozentsatz aller Konflikte während der Profilerstellung, die allein in dieser Funktion oder Methode aufgetreten sind.|  
|**Funktionszeilennummer**|Die Zeilennummer des Anfangs dieser Funktion in der Quelldatei.|  
|**Modulname**|Der Name des Moduls, das die Funktion enthält.|  
|**Modulpfad**|Der Pfad des Moduls, das die Funktion enthält.|  
|**Prozess-ID**|Der Prozess-ID (PID) des Prozesses, in dem die Funktion ausgeführt wurde.|  
|**Prozessname**|Der Prozessname.|  
|**Quelldatei**|Die Quelldatei, die die Definition der Funktion enthält.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Vorgehensweise: Anpassen von Spalten in der Berichtsansicht](../profiling/how-to-customize-report-view-columns.md)   
 [Funktions Ansicht](../profiling/functions-view.md)   
 [Funktions Ansicht-Instrumentation](../profiling/functions-view-dotnet-memory-instrumentation-data.md)   
 [Funktions Ansicht-Sampling](../profiling/functions-view-dotnet-memory-sampling-data.md)   
 [Funktions Ansicht](../profiling/functions-view-instrumentation-data.md)   
 [Funktionsansicht](../profiling/functions-view-sampling-data.md)
