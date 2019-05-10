---
title: 'Modulansicht: Konfliktdaten | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Modules view
ms.assetid: 1a9aa122-2d8f-4a09-b503-92975aa6b648
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9a2553396614cacbc22925f8f7f3a61d56c50541
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2019
ms.locfileid: "54771035"
---
# <a name="modules-view---contention-data"></a>Modulansicht: Konfliktdaten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Modulansicht der Konfliktdaten zeigt von den Modulen gruppierte Parallelitätsdaten an, die in den Profilerstellungsdaten abgefragt wurden. Jedes Modul ist der Stamm einer hierarchischen Struktur. Die Funktionen der Module, in denen Konfliktereignisse aufgetreten sind, werden unter dem Modulknoten aufgeführt.  
  
 Wenn die Funktion ihren eigenen Code ausgeführt hat, während ein Konfliktereignis aufgetreten ist, die Funktion sich also ganz oben in der Aufrufliste befunden hat, werden die ausgeführten Quellzeilen und Anweisungsadressen unter dem Funktionsknoten aufgeführt. Da die Daten für eine Quellzeile oder einen Anweisungszeiger erfasst werden, wenn die Zeile oder die Anweisung ausgeführt wird, sind die inklusiven und exklusiven Werte der Zeilen- und der Anweisungsdaten immer gleich.  
  
 Die folgende Tabelle beschreibt die Werte der Spalten in der Modulansicht der Konfliktdaten.  
  
|Spalte|Beschreibung|  
|------------|-----------------|  
|**Exklusive blockierte Zeit %**|– Bei einer Funktion die Zeit, für die die Funktion keinen Code im Text der Funktion ausführen konnte. Diese umfasst nicht den Zeitaufwand für Funktionen, die von dieser Funktion aufgerufen wurden.<br />– Bei einem Modul die Summe der exklusiv blockierten Zeit der Funktionen im Modul.<br />– Bei einer Zeile oder einer Anweisung die Zeit, für die diese Zeile oder Anweisung nicht ausgeführt werden konnte.|  
|**Exklusive blockierte Zeit %**|– Bei einer Funktion oder einem Modul der Anteil der gesamten blockierten Zeit während der Profilerstellung, die der exklusiven blockierten Zeit dieser Funktion oder dieses Moduls entspricht.<br />– Bei einer Zeile oder einer Anweisung der Anteil der blockierten Zeit während der Profilerstellung, für die diese Zeile oder Anweisung nicht ausgeführt werden konnte.|  
|**Exklusive Konflikte**|– Bei einer Funktion, wie oft diese vom Ausführen von Code im Text der Funktion abgehalten wurde. Konflikte in Funktionen, die von dieser Funktion aufgerufen wurden, werden nicht einbezogen.<br />– Bei einem Modul die Summe der exklusiven Konflikte der Funktionen im Modul.<br />– Bei einer Zeile oder einer Anweisung, wie oft diese Zeile oder Anweisung nicht ausgeführt werden konnte.|  
|**Exklusive Konflikte %**|– Bei einer Funktion oder einem Modul der Anteil aller Konflikte während der Profilerstellung, bei denen es sich um exklusive Konflikte dieser Funktion oder dieses Moduls handelt.<br />– Bei einer Zeile oder Anweisung der Anteil aller Konflikte während der Profilerstellung, bei denen es sich um Konflikte handelt, die diese Zeile oder Anweisung von der Ausführung abgehalten haben.|  
|**Inklusive blockierte Zeit**|– Bei einer Funktion die Zeit, für die diese Funktion oder eine Funktion, die von dieser Funktion aufgerufen wurde, nicht ausgeführt werden konnte.<br />– Bei einem Modul die Summe der blockierten Zeit, für die sich mindestens eine Funktion dieses Moduls im Stapel befunden hat.<br />– Bei einer Zeile oder einer Anweisung die Zeit, für die diese Zeile oder Anweisung nicht ausgeführt werden konnte.|  
|**Inklusive blockierte Zeit %**|– Bei einer Funktion oder einem Modul der Anteil der gesamten blockierten Zeit Ausführung der Profilerstellung, die der inklusiven blockierten Zeit dieser Funktion oder dieses Moduls entspricht.<br />– Bei einer Zeile oder einer Anweisung der Anteil der blockierten Zeit während der Profilerstellung, für die diese Zeile oder Anweisung ausgeführt wurde.|  
|**Inklusive Konflikte %**|– Bei einer Funktion, wie oft diese oder eine Funktion, die von dieser Funktion aufgerufen wurde, nicht ausgeführt werden konnte.<br />– Bei einem Modul die Anzahl von Konflikten, bei denen sich mindestens eine Funktion dieses Moduls im Stapel befunden hat.<br />– Bei einer Zeile oder einer Anweisung, wie oft diese Zeile oder Anweisung nicht ausgeführt werden konnte.|  
|**Inklusive Konflikte %**|– Bei einer Funktion oder einem Modul der Anteil aller Konflikte während der Profilerstellung, bei denen es sich um inklusive Konflikte dieser Funktion oder dieses Moduls handelt.<br />– Bei einer Zeile oder einer Anweisung der Anteil der blockierten Zeit während der Profilerstellung, für die diese Zeile oder Anweisung ausgeführt wurde.|  
|**Funktionszeilennummer**|Die Zeilennummer des Anfangs dieser Funktion in der Quelldatei.|  
|**Modulname**|Der Name des Moduls mit der Funktion, der Zeile oder dem Anweisungszeiger.|  
|**Modulpfad**|Der Pfad des Moduls mit dem Modul, der Funktion, der Zeile oder dem Anweisungszeiger.|  
|**Name**|Der Name des Moduls oder der Funktion.|  
|**Prozess-ID**|Die Prozess-ID (PID) der Profilerstellung.|  
|**Prozessname**|Der Prozessname.|  
|**Quelldatei**|Die Quelldatei, die die Definition der Funktion enthält.|  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Anpassen von Spalten in Berichtsansichten](../profiling/how-to-customize-report-view-columns.md)   
 [Modulansicht](../profiling/modules-view.md)   
 [Modulansicht – Instrumentation](../profiling/modules-view-dotnet-memory-instrumentation-data.md)   
 [Modulansicht – Sampling](../profiling/modules-view-dotnet-memory-sampling-data.md)   
 [Modulansicht](../profiling/modules-view-instrumentation-data.md)   
 [Modulansicht](../profiling/modules-view-sampling-data.md)
