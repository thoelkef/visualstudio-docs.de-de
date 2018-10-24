---
title: Konfigurieren von Leistungssitzungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- common tasks, performance
- common tasks, profiling tools
- profiling tools, common tasks
- performance, gathering data
ms.assetid: e1c3ba41-ffca-4edf-9a7f-8a5a9244ef9b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1e00c31643a5f894612daa24d4a271856d8e21f1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49853436"
---
# <a name="configure-performance-sessions"></a>Konfigurieren von Leistungssitzungen
Mithilfe von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profilerstellungstools können Sie eine Vielzahl von Leistungsdaten für eine große Anzahl von Anwendungstypen sammeln. In diesem Abschnitt erfahren Sie, wie Sie den Leistungsassistententen und die Eigenschaften der Leistungssitzung sowie der Zielbinärdatei einsetzen, um Profilerstellungstools für das Sammeln von für Sie interessanten Daten zu konfigurieren. Die Konfigurationseigenschaften von Profilerstellungstools lassen sich außerdem dazu verwenden, um zu steuern, wie viele Daten während einer Profilerstellung gesammelt werden. Weitere Informationen finden Sie unter [Control data collection (Steuern der Datensammlung)](../profiling/controlling-data-collection.md).  
  
> [!NOTE]
>  In vielen Fällen können Sie mithilfe der Standardeigenschaften des Leistungsassistenten das Sammeln von Profilerstellungsdaten effizient steuern. Weitere Informationen finden Sie unter [Einführung in die Leistungsprofilerstellung](../profiling/beginners-guide-to-performance-profiling.md) und [Erste Schritte](../profiling/getting-started-with-performance-tools.md).  
  
## <a name="common-tasks"></a>Allgemeine Aufgaben
  
| Aufgabe | Verwandter Inhalt |
| - | - |
| **Festlegen der grundlegenden Profilerstellungsoptionen:** Konfigurieren Sie [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], um den Microsoft-Symbolserver zu verwenden. So stellen Sie sicher, dass Sie für die aktuelle Version von Windows und für andere Microsoft-Anwendungen Zugriff auf Symbole wie Funktions- und Parameternamen haben. Sie können auch andere allgemeinen Optionen angeben, bevor Sie mit einer Profilerstellungssitzung beginnen, wie z.B. Systemberechtigungen für die Profilerstellungstools und die Namen von Profilerstellungs-Datendateien. | -   [Vorgehensweise: Verweisen auf Windows-Symbolinformationen](../profiling/how-to-reference-windows-symbol-information.md)<br />-   [Vorgehensweise: Serialisieren von Symbolinformationen](../profiling/how-to-serialize-symbol-information.md)<br />-   [Vorgehensweise: Festlegen der aktuellen Sitzung](../profiling/how-to-set-the-current-session.md)<br />-   [Vorgehensweise: Festlegen von Berechtigungen](../profiling/how-to-set-permissions.md)<br />-   [Vorgehensweise: Dateinamensoptionen für Profilerstellungsdaten](../profiling/how-to-set-performance-data-file-name-options.md) |
| **Festlegen der zu erfassenden Daten:** Die Prozeduren zur Konfigurierung einer Profilerstellungssitzung sind abhängig vom Typ der Zielanwendung, für die Sie ein Profil erstellen möchten, sowie vom Typ der Leistungsdaten, die Sie sammeln möchten. | -   [Vorgehensweise: Auswählen von Sammlungsmethoden](../profiling/how-to-choose-collection-methods.md)<br />-   [Sammeln von Leistungsstatistiken durch Sampling](../profiling/collecting-performance-statistics-by-using-sampling.md)<br />-   [Sammeln von Daten zur .NET-Speicherbelegung und -lebensdauer](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Sammeln ausführlicher Zeitsteuerungsdaten mithilfe der Instrumentierung](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)<br />-   [Vorgehensweise: Profilerstellung für JavaScript-Code in Webseiten](../profiling/how-to-profile-javascript-code-in-web-pages.md)<br />-   [Sammeln von Parallelitätsdaten zu Threads und Prozessen](../profiling/collecting-thread-and-process-concurrency-data.md)<br />-   [Sammeln zusätzlicher Leistungsdaten](../profiling/collecting-additional-performance-data.md) |
| **Festlegen von erweiterten Konfigurationsoptionen:** Wenn Sie das Profil von .NET Framework-Anwendungen anlegen, die mehrere CLR-Versionen laden, können Sie angeben, für welche Version Sie das Profil anlegen möchten. Wenn Ihre Leistungssitzung mehrere EXE-Dateien umfasst, können Sie die Startreihenfolge der Binärdateien festlegen. | -   [Vorgehensweise: Angeben der .NET Framework-Laufzeit](../profiling/how-to-specify-the-dotnet-framework-runtime.md)<br />-   [Vorgehensweise: Angeben der zu startenden Binärdatei](../profiling/how-to-specify-the-binary-to-start.md) |
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Steuerung der Datensammlung](../profiling/controlling-data-collection.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Leistungs-Explorer](../profiling/performance-explorer.md)