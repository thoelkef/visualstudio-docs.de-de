---
title: Prozessansicht - Konfliktdaten | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Process view
ms.assetid: 8821d98c-0771-43b2-a38b-e9039a3abd75
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 30c938088538bcecc71e3a7e37d5ae403dd476e1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778400"
---
# <a name="process-view---contention-data"></a>Prozessansicht: Konfliktdaten
Die Prozessansicht zeigt Konfliktdaten für die Prozesse und Threads, die während der Profilerstellung ausgeführt wurden.

 Wenn Symbole verfügbar sind, werden Prozesse nach Namen aufgelistet. Wenn keine Symbole verfügbar sind, werden Prozesse nach zugewiesener Speicheradresse im Hexadezimalformat aufgelistet. Threads werden als untergeordnete Elemente des Prozesses aufgeführt, in dem sie erstellt wurden.

 In der nachstehenden Tabelle werden die Werte der Spalten in der Prozessansicht erklärt.

|Spalte|Beschreibung|
|------------|-----------------|
|**Anfangszeit**|Die Anzahl von Millisekunden oder Prozessorzyklen vom Anfang der Profilerstellung zum Anfang des Prozesses oder Threads.|
|**Blockierte Zeit**|Die Gesamtzeit, für die die Ausführung von Funktionen des Prozesses oder Threads blockiert wurden.|
|**Blockierte Zeit in %**|Der Prozentsatz der Lebensdauer des Prozesses oder Threads, in dem die Ausführung von Funktionen für den Prozess oder Thread blockiert wurden.|
|**Konflikte**|Die Anzahl der Versuche, die Ausführung der Funktionen für den Prozess oder Thread zu blockieren.|
|**Konflikte %**|Der Prozentsatz aller Konflikte in der Profilerstellungsausführung, die Konflikte des Prozesses oder Threads waren.|
|**Endzeit**|Die Anzahl von Millisekunden oder Prozessorzyklen vom Anfang der Profilerstellung bis zum Anfang des Prozesses oder Threads.|
|**ID**|Der vom System generierter Bezeichner für den Prozess oder Thread.|
|**Lebensdauer**|Die Anzahl von Millisekunden oder Prozessorzyklen vom Anfang des Prozesses oder Threads bis ans Endes des Prozesses oder Threads oder dem Ende der Profilerstellung.|
|**Type**|Typ der Zeile, entweder vom Prozess oder Thread.<br /><br /> Nur in **VSReport**-Befehlszeilenberichten. Weitere Informationen finden Sie unter [VSPerfReport](../profiling/vsperfreport.md).|
|**Name**|Der Name des Prozesses oder Threads.|
|**Eindeutige ID**|Ein durch die Profilerstellung generierter Bezeichner, der für den Prozess oder Thread eindeutig ist.|

## <a name="see-also"></a>Siehe auch
- [How to: Anpassen von Spalten in Berichtsansichten](../profiling/how-to-customize-report-view-columns.md)
- [Prozessansicht](../profiling/process-view.md)
