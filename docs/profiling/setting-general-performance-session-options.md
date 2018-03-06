---
title: "Festlegen allgemeiner Leistungsoptionen für Sitzungen | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.property.general
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 36e27189102fbab8e698320c49bd008adf1eda50
ms.sourcegitcommit: 36ab8429333b31f03992a9fe8fc669db8e09c968
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2018
---
# <a name="setting-general-performance-session-options"></a>Festlegen allgemeiner Leistungsoptionen für Sitzungen

Sie können die Auflistungsmethode und Benennungskonventionen für Profilerstellungsdaten für eine Leistungssitzung der Visual Studio-Profilerstellungstools auf der Seite **Allgemein** des Dialogfelds „Eigenschaften“ für die Leistungssitzung festlegen. Zum Öffnen dieses Dialogfelds klicken Sie im **Leistungs-Explorer** mit der rechten Maustaste auf die Leistungssitzung, und klicken Sie dann auf **Eigenschaften**.

## <a name="choosing-data-collection-methods"></a>Auswählen von Datensammlungsmethoden

Die Basisauflistungsmethode kann durch Auswählen einer der Optionen unter **Profilauflistung** festgelegt werden. Die Optionen sind in der folgenden Tabelle beschrieben:

|||
|-|-|
|**Sampling**. Die Samplingmethode sammelt in regelmäßigen Abständen Profilerstellungsinformationen. Diese Methode ist nützlich für das Auffinden von Prozessornutzungsproblemen und ist die vorgeschlagene Methode zum Starten der meisten Leistungsuntersuchungen.|- [Collecting Performance Statistics by Using Sampling (Sammeln von Leistungsstatistiken durch Sampling)](../profiling/collecting-performance-statistics-by-using-sampling.md)|
|**Instrumentierung**. Die Instrumentierungsmethode springt in eine Kopie eines Modulprofilerstellungscodes, durch den jeder Eintritt, jeder Austritt und jeder Funktionsaufruf der Funktionen in dem Modul während der Profilerstellungsausführung aufgezeichnet wird. Mithilfe dieser Methode können ausführliche Zeitsteuerungsdaten zu einem Abschnitt des Codes erfasst werden. Zudem werden mit dieser Methode die Auswirkungen von Eingabe- und Ausgabeoperationen auf die Leistung der Anwendung besser verständlich.|- [Collecting Detailed Timing Data by Using Instrumentation (Sammeln ausführlicher Zeitsteuerungsdaten mithilfe der Instrumentierung) ](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)|
|**Parallelität**. Die Parallelitätsmethode erfasst Daten für jedes Ereignis, das die Ausführung des Codes blockiert, z. B., wenn ein Thread darauf wartet, dass der gesperrte Zugriff auf eine Anwendungsressource freigegeben wird. Diese Methode ist hilfreich für das Analysieren von Multithreadanwendungen.|- [Collecting Thread and Process Concurrency Data (Sammeln von Nebenläufigkeitsdaten zu Threads und Prozessen) ](../profiling/collecting-thread-and-process-concurrency-data.md)|

 .NET-Arbeitsspeicherdaten können mit der Sampling- oder Instrumentierungsmethode erfasst werden. Sie wählen den Typ der Daten unter **Profilerstellung für .NET-Arbeitsspeicher** aus.

|||
|-|-|
|**.NET-Objektzuordnungsinformationen auflisten**. Standardmäßig enthalten Daten die Anzahl und die Größe von zugeordneten Objekten. Aktivieren oder deaktivieren Sie dieses Kontrollkästchen, um die .NET-Arbeitsspeicherdatensammlung zu aktivieren oder zu deaktivieren.<br /><br /> **Lebensdauerinformationen für .NET-Objekt auflisten**. Aktivieren Sie dieses Kontrollkästchen, um Daten zu den Garbage Collection-Generierungen einzuschließen, die verwendet wurden, um die Speicherobjekte freizugeben.|- [Sammeln von Daten zur .NET-Speicherbelegung und Lebensdauer](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)|

 Eine Profilerstellungs-Sitzungsseite wird angezeigt, wenn Sie beginnen, ein Profil für eine Anwendung zu erstellen, bei dem Sie die Profilerstellung anhalten, fortsetzen und beenden können.

 ![Profilerstellungs-Sitzungsseite](../profiling/media/prof_profilingsessionpage.png "PROF_ProfilingSessionPage")

## <a name="setting-profiling-data-file-options"></a>Festlegen von Optionen für die Profilerstellungs-Datendatei

|||
|-|-|
|**Bericht**. Standardmäßig erhält die Profilerstellungs-Datendatei (.vsp) den Namen der profilierten Anwendung, und sie befindet sich im Projektmappen- oder Projektordner. Es wird auch eine Datumszeichenfolge an den Namen angefügt, und Datendateien, die andernfalls doppelte Namen hätten, wird eine inkrementierte Zahl hinzugefügt. Sie können diese Optionen ändern.|- [How to: Set Performance Data File Name Option (Vorgehensweise: Festlegen von Dateinamenoptionen für Profilerstellungsdaten)](../profiling/how-to-set-performance-data-file-name-options.md)|