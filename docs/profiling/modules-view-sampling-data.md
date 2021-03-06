---
title: Modulansicht – Profiler-Samplingdaten | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Modules view
- sampling profiling method,Modules view
ms.assetid: 816f5633-65d7-41e5-aee1-033628d4e2df
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 7ead219ddf482af5917842118d386c6fefe67973
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "74772713"
---
# <a name="modules-view---sampling-data"></a>Modulansicht: Samplingdaten
In der Modulansicht der Samplingdaten werden die Leistungsdaten, für die in den Profilerstellungsdaten ein Sampling ausgeführt wurde, nach Modulen gruppiert angezeigt. Jedes Modul ist der Stamm einer hierarchischen Struktur. Die Funktionen des Moduls, für die ein Sampling ausgeführt wurde, werden unter dem Modulknoten aufgeführt.

> [!NOTE]
> Verbesserte Sicherheitsfeatures in Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung des Visual Studio-Profilers auf diesen Plattformen. Außerdem benötigen UWP-Apps neue Erfassungsmethoden. Informationen hierzu finden Sie unter [Performance Tools on Windows 8 and Windows Server 2012 applications (Profilerstellung für Windows 8- und Windows Server 2012-Anwendungen)](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

 Wenn die Funktion ausgeführt wurde, als Samplings gesammelt wurden, die Funktion sich also ganz oben in der Aufrufliste befunden hat, werden die zum jeweiligen Zeitpunkt ausgeführten Quellzeilen und Anweisungsadressen unter dem Funktionsknoten aufgeführt. Da die Daten für eine Quellzeile oder einen Anweisungszeiger erfasst werden, wenn die Zeile oder die Anweisung ausgeführt wird, sind die inklusiven und exklusiven Werte der Zeilen- und der Anweisungsdaten immer gleich.

|Spalte|Beschreibung|
|------------|-----------------|
|**Name**|Der Name des Moduls, der Funktion, der Zeilennummer oder der Adresse des Anweisungszeigers.|
|**Prozess-ID**|Die Prozess-ID (PID) der Profilerstellung.|
|**Prozessname**|Der Name des Prozesses.|
|**Modulname**|Der Name des Moduls mit der Funktion, der Zeile oder dem Anweisungszeiger.|
|**Modulpfad**|Der Pfad des Moduls mit dem Modul, der Funktion, der Zeile oder dem Anweisungszeiger.|
|**Quelldatei**|Die Quelldatei, die die Definition der Funktion enthält.|
|**Funktionszeilennummer**|Die Zeilennummer des Anfangs dieser Funktion in der Quelldatei.|
|**Inklusive Samplings**|- Bei einer Funktion die Anzahl der Samplings, in der diese Funktion oder eine von dieser Funktion aufgerufene Funktion ausgeführt wurde (d.h. die Anzahl von Samplings in der Aufrufliste, in denen diese Funktion enthalten war).<br />- Bei einem Modul die Anzahl der Samplings, bei denen mindestens eine Funktion dieses Moduls ausgeführt wurde.<br />- Bei einer Zeile oder einer Anweisung die Anzahl der Samplings, in denen diese Zeile oder Anweisung ausgeführt wurde.|
|**Inklusive Samplings in %**|- Bei einer Funktion oder einem Modul der Anteil aller Samplings, die während der Profilerstellung inklusiven Samplings dieser Funktion oder dieses Moduls entsprechen.<br />- Bei einer Zeile oder einer Anweisung der Anteil der Samplings, in denen während der Profilerstellung diese Zeile oder Anweisung ausgeführt wurde.|
|**Exklusive Samplings**|- Bei einer Funktion die Anzahl der Samplings in der Aufrufliste, in denen diese Funktion direkt ausgeführt wurde (d.h. in denen sich die Funktion an erster Stelle in der Aufrufliste befand).<br />- Bei einem Modul die Summe der exklusiven Samplings der Funktionen im Modul.<br />- Bei einer Zeile oder einer Anweisung die Anzahl der Samplings, in denen diese Zeile oder Anweisung ausgeführt wurde.|
|**Exklusive Samplings %**|- Bei einer Funktion oder einem Modul der Anteil aller Samplings, die während der Profilerstellung exklusiven Samplings dieser Funktion oder dieses Moduls entsprechen.<br />- Bei einer Zeile oder einer Anweisung der Anteil der Samplings, in denen während der Profilerstellung diese Zeile oder Anweisung ausgeführt wurde.|

## <a name="see-also"></a>Weitere Informationen
- [Modulansicht: Sampling](../profiling/modules-view-dotnet-memory-sampling-data.md)
- [Modulansicht: .NET-Speicherinstrumentierungsdaten](../profiling/modules-view-dotnet-memory-instrumentation-data.md)
- [Modulansicht](../profiling/modules-view-instrumentation-data.md)
