---
title: Festlegen allgemeiner Leistungsoptionen für Sitzungen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.general
ms.assetid: 6b60bd1b-2198-4261-b84e-9b2d8494a992
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6e135b92cad94f2154341ca79c785d9e40ccb000
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60064751"
---
# <a name="setting-general-performance-session-options"></a>Festlegen allgemeiner Leistungsoptionen für Sitzungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können die Auflistungsmethode und Benennungskonventionen für Profilerstellungsdaten für eine Leistungssitzung der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Profilerstellungstools auf der Seite **Allgemein** des Dialogfelds „Eigenschaften“ für die Leistungssitzung festlegen. Zum Öffnen dieses Dialogfelds klicken Sie im **Leistungs-Explorer** mit der rechten Maustaste auf die Leistungssitzung, und klicken Sie dann auf **Eigenschaften**.  
  
 **Anforderungen**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
## <a name="choosing-data-collection-methods"></a>Auswählen von Datensammlungsmethoden  
 Die Basisauflistungsmethode kann durch Auswählen einer der Optionen unter **Profilauflistung** festgelegt werden. Die Optionen sind in der folgenden Tabelle beschrieben:  
  
|||  
|-|-|  
|**Sampling**. Die Samplingmethode sammelt in regelmäßigen Abständen Profilerstellungsinformationen. Diese Methode ist nützlich für das Auffinden von Prozessornutzungsproblemen und ist die vorgeschlagene Methode zum Starten der meisten Leistungsuntersuchungen.|-   [Collecting Performance Statistics by Using Sampling (Sammeln von Leistungsstatistiken durch Sampling)](../profiling/collecting-performance-statistics-by-using-sampling.md)|  
|**Instrumentierung**. Die Instrumentationsmethode springt in eine Kopie eines Modulprofilerstellungscodes, durch den jeder Eintritt, jeder Austritt und jeder Funktionsaufruf der Funktionen in dem Modul während der Profilerstellungsausführung aufgezeichnet wird. Diese Methode eignet sich, um detaillierte Zeitdaten zu einem Abschnitt des Codes zu erfassen und um die Auswirkungen von Eingabe- und Ausgabevorgängen auf die Anwendungsleistung zu verstehen.|-   [Collecting Detailed Timing Data by Using Instrumentation (Sammeln ausführlicher Zeitsteuerungsdaten mithilfe der Instrumentierung) ](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)|  
|**Parallelität**. Die Parallelitätsmethode erfasst Daten für jedes Ereignis, das die Ausführung des Codes blockiert, wie z. B. ein Thread, der darauf wartet, dass der gesperrte Zugriff auf eine Anwendungsressource freigegeben wird. Diese Methode eignet sich für die Analyse von Anwendungen mit mehreren Threads.|-   [Collecting Thread and Process Concurrency Data (Sammeln von Nebenläufigkeitsdaten zu Threads und Prozessen) ](../profiling/collecting-thread-and-process-concurrency-data.md)|  
  
 .NET-Arbeitsspeicherdaten können mit der Sampling- oder Instrumentationsmethode erfasst werden. Sie wählen den Typ der Daten unter **Profilerstellung für .NET-Arbeitsspeicher** aus.  
  
|||  
|-|-|  
|**.NET-Objektzuordnungsinformationen auflisten**. Standardmäßig enthalten Daten die Anzahl und die Größe von zugeordneten Objekten. Aktivieren oder deaktivieren Sie dieses Kontrollkästchen, um die .NET-Arbeitsspeicherdatensammlung zu aktivieren oder zu deaktivieren.<br /><br /> **Lebensdauerinformationen für .NET-Objekt auflisten**. Aktivieren Sie dieses Kontrollkästchen, um Daten zu den Garbage Collection-Generierungen einzuschließen, die verwendet wurden, um die Speicherobjekte freizugeben.|-   [Sammeln von Daten zur .NET-Speicherbelegung und Lebensdauer](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)|  
  
 Eine Profilerstellungs-Sitzungsseite wird angezeigt, wenn Sie beginnen, ein Profil für eine Anwendung zu erstellen, bei dem Sie die Profilerstellung anhalten, fortsetzen und beenden können.  
  
 ![Profilerstellungs-Sitzungsseite](../profiling/media/prof-profilingsessionpage.png "PROF_ProfilingSessionPage")  
  
## <a name="setting-profiling-datra-file-options"></a>Festlegen von Optionen für die Profilerstellungs-Datendatei  
  
|||  
|-|-|  
|**Bericht**. Standardmäßig erhält die Profilerstellungs-Datendatei (.vsp) den Namen der profilierten Anwendung, und sie befindet sich im Projektmappen- oder Projektordner. Es wird auch eine Datumszeichenfolge an den Namen angefügt, und Datendateien, die andernfalls doppelte Namen hätten, wird eine inkrementierte Zahl hinzugefügt. Sie können diese Optionen ändern.|-   [Vorgehensweise: Dateinamensoptionen für Profilerstellungsdaten](../profiling/how-to-set-performance-data-file-name-options.md)|
