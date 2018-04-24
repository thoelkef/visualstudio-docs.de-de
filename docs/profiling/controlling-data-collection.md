---
title: Steuern der Datensammlung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- advanced tasks for profiling tools
- profiling tools, advanced tasks
ms.assetid: e713ad63-b948-46f3-8db9-59b30922ebe5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 824a67ec2ce71a9b7810ace93001a942dc73e60e
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="controlling-data-collection"></a>Steuern der Datenauflistung
Mit den [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Profilerstellungstools können Sie steuern, wann Profilerstellungsdaten während einer Leistungssitzung gesammelt werden, und die Funktionen angeben, für die ein Profil erstellt wird. Dieser Abschnitt beschreibt, wie Sie über das Fenster des **Leistungs- Explorers** und der **Steuerung der Datensammlung** das Sammeln von Daten starten und beenden und wie Sie die Anzahl der Objekte beschränken, für die Profilerstellungsdaten gesammelt werden sollen.  
  
## <a name="common-tasks"></a>Allgemeine Aufgaben  
  
|Aufgabe|Verwandter Inhalt|  
|----------|---------------------|  
|**Starten und Beenden der Profilerstellung:** Sie können für eine Anwendung ein Profil erstellen, sobald diese Anwendung gestartet wird. Außerdem lässt sich ein Profiler an einen Prozess anfügen, der bereits ausgeführt wird. Wenn die Zielanwendung ausgeführt wird, können Sie die Datensammlung anhalten und fortsetzen. Sie beenden eine Profilerstellungssitzung, indem Sie die Zielanwendung schließen oder den Profiler von einem laufenden Prozess trennen.|-   [How to: Start and End Performance Data Collection (Vorgehensweise: Starten und Beenden der Sammlung von Leistungsdaten)](../profiling/how-to-start-and-end-performance-data-collection.md)<br />-   [How to: Attach and Detach Performance Tools to Running Processes (Vorgehensweise: Anfügen eines Profilers an einen laufenden Prozess und Trennen eines Profilers von einem laufenden Prozess)](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md)<br />-   [How to: Pause and Resume Performance Data Collection (Vorgehensweise: Anhalten und Fortsetzen der Sammlung von Leistungsdaten)](../profiling/how-to-pause-and-resume-performance-data-collection.md)|  
|**Konfigurieren der instrumentierten Profilerstellung, um die gesammelten Daten einzuschränken:** Mit Leistungssitzungskonfigurationseigenschaften können Sie das Sammeln von Daten in Profilerstellungsausführungen einschränken, in denen die Instrumentationsmethode verwendet wird. Sie können bestimmte DLL-Dateien, Namespaces, Klassen und Funktionen einschließen oder ausschließen. Außerdem können Sie Funktionen ausschließen, die einem von Ihnen angegebenen Größenschwellenwert nicht entsprechen.|-   [How to: Limit Instrumentation to Specific DLLs (Vorgehensweise: Beschränken der Instrumentierung auf bestimmte DLLs)](../profiling/how-to-limit-instrumentation-to-specific-dlls.md)<br />-   [How to: Limit Instrumentation to Specific Functions (Vorgehensweise: Beschränken der Instrumentierung auf bestimmte Funktionen)](../profiling/how-to-limit-instrumentation-to-specific-functions.md)<br />-   [How to: Exclude or Include Short Functions from Instrumentation (Vorgehensweise: Ausschließen oder Einschließen kurzer Funktionen in die Instrumentierung)](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)|  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Konfigurieren von Leistungssitzungen](../profiling/configuring-performance-sessions.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Performance Explorer (Leistungs-Explorer)](../profiling/performance-explorer.md)