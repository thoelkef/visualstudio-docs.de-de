---
title: Steuern der Datensammlung | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- advanced tasks for profiling tools
- profiling tools, advanced tasks
ms.assetid: e713ad63-b948-46f3-8db9-59b30922ebe5
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e34c4db965cacefabe752774e393a4339042040e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68182707"
---
# <a name="controlling-data-collection"></a>Steuern der Datenauflistung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mit den [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Profilerstellungstools können Sie steuern, wann Profilerstellungsdaten während einer Leistungssitzung gesammelt werden, und die Funktionen angeben, für die ein Profil erstellt wird. Dieser Abschnitt beschreibt, wie Sie über das Fenster des **Leistungs- Explorers** und der **Steuerung der Datensammlung** das Sammeln von Daten starten und beenden und wie Sie die Anzahl der Objekte beschränken, für die Profilerstellungsdaten gesammelt werden sollen.  
  
## <a name="common-tasks"></a>Allgemeine Aufgaben  
  
|Aufgabe|Verwandter Inhalt|  
|----------|---------------------|  
|**Starten und Beenden der Profilerstellung:** Sie können für eine Anwendung ein Profil erstellen, sobald diese Anwendung gestartet wird. Außerdem lässt sich ein Profiler an einen Prozess anfügen, der bereits ausgeführt wird. Wenn die Zielanwendung ausgeführt wird, können Sie die Datensammlung anhalten und fortsetzen. Sie beenden eine Profilerstellungssitzung, indem Sie die Zielanwendung schließen oder den Profiler von einem laufenden Prozess trennen.|-   [How to: Start and End Performance Data Collection (Vorgehensweise: Starten und Beenden der Sammlung von Leistungsdaten)](../profiling/how-to-start-and-end-performance-data-collection.md)<br />-   [How to: Attach and Detach Performance Tools to Running Processes (Vorgehensweise: Anfügen eines Profilers an einen laufenden Prozess und Trennen eines Profilers von einem laufenden Prozess)](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md)<br />-   [How to: Pause and Resume Performance Data Collection (Vorgehensweise: Anhalten und Fortsetzen der Sammlung von Leistungsdaten)](../profiling/how-to-pause-and-resume-performance-data-collection.md)|  
|**Konfigurieren der instrumentierten Profilerstellung, um die gesammelten Daten einzuschränken:** Mit Leistungssitzungskonfigurationseigenschaften können Sie das Sammeln von Daten in Profilerstellungsausführungen einschränken, in denen die Instrumentationsmethode verwendet wird. Sie können bestimmte DLL-Dateien, Namespaces, Klassen und Funktionen einschließen oder ausschließen. Außerdem können Sie Funktionen ausschließen, die einem von Ihnen angegebenen Größenschwellenwert nicht entsprechen.|-   [How to: Limit Instrumentation to Specific DLLs (Vorgehensweise: Beschränken der Instrumentierung auf bestimmte DLLs)](../profiling/how-to-limit-instrumentation-to-specific-dlls.md)<br />-   [How to: Limit Instrumentation to Specific Functions (Vorgehensweise: Beschränken der Instrumentierung auf bestimmte Funktionen)](../profiling/how-to-limit-instrumentation-to-specific-functions.md)<br />-   [How to: Exclude or Include Short Functions from Instrumentation (Vorgehensweise: Ausschließen oder Einschließen kurzer Funktionen in die Instrumentierung)](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)|  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Konfigurieren von Leistungssitzungen](../profiling/configuring-performance-sessions.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Performance Explorer (Leistungs-Explorer)](../profiling/performance-explorer.md)
