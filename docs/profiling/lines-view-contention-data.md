---
title: Zeilenansicht - Konfliktdaten | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Lines view
ms.assetid: 859b02d2-eddf-4ad3-95de-0df67ee2ab03
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 572400794af73ed70503ce39327d678c5ffa195a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63000616"
---
# <a name="lines-view---contention-data"></a>Zeilenansicht: Konfliktdaten
In der Zeilenansicht der Konfliktdaten werden die Leistungsdaten für die Anweisungen aufgeführt, die ausgeführt wurden, als die Samplings bei der Profilerstellung erfasst wurden. In einer Quelldatei kann eine Anweisung mehrere Zeilen umfassen, und eine einzelne Zeile kann mehr als eine Anweisung enthalten.

 Eine Anweisung wird mit den folgenden Daten identifiziert:

- Die Quelldatei, die die Funktionsanweisung enthält.

- Die Funktion, die die Anweisung enthält.

- Die Quellzeile, an der die Anweisung beginnt.

- Das Zeichen in der Quellzeile, an dem die Anweisung beginnt.

- Die Quellzeile, an der die Anweisung endet.

- Das Zeichen in der Quellzeile, an dem die Anweisung endet.

  Die Zeilennamensspalte, die eine sortierbare Verkettung der Bezeichnerdaten bereitstellt.

  In der folgenden Tabelle werden die Spalten des Zeilenansichtsberichts beschrieben.

|Spalte|Beschreibung|
|------------|-----------------|
|**Exklusive blockierte Zeit**|Die Zeitspanne, während der diese Anweisung bei der Ausführung eines Codes in der Anweisung aufgrund eines Konfliktereignisses blockiert wurde. Blockierte Zeit in Funktionen, die von der Anweisung aufgerufen wurden, ist nicht enthalten.|
|**Exklusive blockierte Zeit %**|Der Prozentsatz der gesamten blockierten Zeit im Prozess, die exklusive blockierte Zeit der Anweisung war.|
|**Exklusive Konflikte**|Die Anzahl des Vorkommens, während der diese Anweisung bei der Ausführung eines Codes in der Anweisung aufgrund eines Konfliktereignisses blockiert wurde. Konfliktereignisse in Funktionen, die von der Anweisung aufgerufen wurden, sind nicht enthalten.|
|**Exklusive Konflikte %**|Der Prozentsatz aller Konfliktereignisse im Prozess, die exklusive Konflikte dieser Anweisung waren.|
|**Funktionsadresse**|Die Adresse der Funktion, die diese Anweisung enthält.|
|**Funktionsname**|Der vollqualifizierte Name der Funktion, die diese Anweisung enthält.|
|**Inklusive blockierte Zeit**|Die blockierte Zeit in dieser Anweisung und Funktionen, die in der Anweisung aufgerufen wurden.|
|**Inklusive blockierte Zeit %**|Der Prozentsatz der gesamten blockierten Zeit im Prozess, die inklusive blockierte Zeit der Anweisung war.|
|**Inklusive Konflikte**|Die Anzahl des Vorkommens, dass diese Anweisung und Funktionen, die in der Anweisung aufgerufen wurden, bei der Ausführung blockiert wurden.|
|**Inklusive Konflikte %**|Der Prozentsatz aller Konfliktereignisse im Prozess, die inklusive Konflikte dieser Anweisung waren.|
|**Zeilenname**|Ein vom Profiler generierter Bezeichner der Zeile. Der Bezeichner verwendet folgende Syntax:`SourceFile`**;[**`LineNumberStart`**,**`CharacterStart`**]->;[**`LineNumberEnd`**,**`CharacterEnd`**]**|
|**Funktionszeilennummer**|Die Zeilennummer des Anfangs dieser Funktion in der Quelldatei.|
|**Modulname**|Der Name des Moduls, das die Anweisung enthält.|
|**Modulpfad**|Der Pfad des Moduls, das die Anweisung enthält.|
|**Prozess-ID**|Die Prozess-ID (PID) des Profilerstellungsprozesses.|
|**Prozessname**|Der Prozessname.|
|**Quellanfangszeichen**|Der Offset des Startzeichens in der Quelldateizeile, an dem diese Anweisung beginnt.|
|**Quellendzeichen**|Der Offset des Startzeichens in der Quelldateizeile, an dem diese Anweisung endet.|
|**Quelldatei**|Der Name der Quelldatei, die die Funktionsanweisung enthält.|
|**Quellanfangszeile**|Die Zeilennummer in der Quelldatei, bei der die Anweisung beginnt.|
|**Quellendzeile**|Die Zeilennummer in der Quelldatei, bei der die Anweisung endet.|

## <a name="see-also"></a>Siehe auch
- [Vorgehensweise: Anpassen von Spalten in Berichtsansichten](../profiling/how-to-customize-report-view-columns.md)
- [Zeilenansicht](../profiling/lines-view.md)
- [Zeilenansicht: Sampling](../profiling/lines-view-dotnet-memory-sampling-data.md)
- [Zeilenansicht](../profiling/lines-view-sampling-data.md)