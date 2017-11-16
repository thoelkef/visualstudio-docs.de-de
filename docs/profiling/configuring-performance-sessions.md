---
title: Konfigurieren von Leistungssitzungen | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- common tasks, performance
- common tasks, profiling tools
- profiling tools, common tasks
- performance, gathering data
ms.assetid: e1c3ba41-ffca-4edf-9a7f-8a5a9244ef9b
caps.latest.revision: "36"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9bc896429c3d9e9307fd17a7727228770735af64
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="configuring-performance-sessions"></a>Konfigurieren von Leistungssitzungen
Mithilfe von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profilerstellungstools können Sie eine Vielzahl von Leistungsdaten für eine große Anzahl von Anwendungstypen sammeln. In diesem Abschnitt erfahren Sie, wie Sie den Leistungsassistententen und die Eigenschaften der Leistungssitzung sowie der Zielbinärdatei einsetzen, um Profilerstellungstools für das Sammeln von für Sie interessanten Daten zu konfigurieren. Die Konfigurationseigenschaften von Profilerstellungstools lassen sich außerdem dazu verwenden, um zu steuern, wie viele Daten während einer Profilerstellung gesammelt werden. Weitere Informationen finden Sie unter [Steuern der Datensammlung](../profiling/controlling-data-collection.md).  
  
> [!NOTE]
>  In vielen Fällen können Sie mithilfe der Standardeigenschaften des Leistungsassistenten das Sammeln von Profilerstellungsdaten effizient steuern. Weitere Informationen finden Sie unter [Beginners Guide to Performance Profiling (Einführung in die Leistungsprofilerstellung)](../profiling/beginners-guide-to-performance-profiling.md) und [Getting Started (Erste Schritte)](../profiling/getting-started-with-performance-tools.md).  
  
## <a name="common-tasks"></a>Allgemeine Aufgaben  
  
|Aufgabe|Verwandter Inhalt|  
|----------|---------------------|  
|**Festlegen der grundlegenden Profilerstellungsoptionen:** Konfigurieren Sie [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], um den Microsoft-Symbolserver zu verwenden. So stellen Sie sicher, dass Sie für die aktuelle Version von Windows und für andere Microsoft-Anwendungen Zugriff auf Symbole wie Funktions- und Parameternamen haben. Sie können auch andere allgemeinen Optionen angeben, bevor Sie mit einer Profilerstellungssitzung beginnen, wie z.B. Systemberechtigungen für die Profilerstellungstools und die Namen von Profilerstellungs-Datendateien.|-   [How to: Reference Windows Symbol Information (Vorgehensweise: Verweisen auf Windows-Symbolinformationen)](../profiling/how-to-reference-windows-symbol-information.md)<br />-   [How to: Serialize Symbol Information (Vorgehensweise: Serialisieren von Symbolinformationen)](../profiling/how-to-serialize-symbol-information.md)<br />-   [How to: Set the Current Session (Vorgehensweise: Festlegen der aktuellen Sitzung)](../profiling/how-to-set-the-current-session.md)<br />-   [How to: Set Permissions (Festlegen von Berechtigungen)](../profiling/how-to-set-permissions.md)<br />-   [How to: Set Performance Data File Name Option (Vorgehensweise: Festlegen von Dateinamenoptionen für Profilerstellungsdaten)](../profiling/how-to-set-performance-data-file-name-options.md)|  
|**Festlegen der zu erfassenden Daten:** Die Prozeduren zur Konfigurierung einer Profilerstellungssitzung sind abhängig vom Typ der Zielanwendung, für die Sie ein Profil erstellen möchten, sowie vom Typ der Leistungsdaten, die Sie sammeln möchten.|-   [How to: Choose Collection Methods (Vorgehensweise: Auswählen von Sammlungsmethoden)](../profiling/how-to-choose-collection-methods.md)<br />-   [Collecting Performance Statistics by Using Sampling (Sammeln von Leistungsstatistiken durch Sampling)](../profiling/collecting-performance-statistics-by-using-sampling.md)<br />-   [Collecting .NET Memory Allocation and Lifetime Data (Sammeln von Daten zur .NET-Speicherbelegung und Lebensdauer)](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Collecting Detailed Timing Data by Using Instrumentation (Sammeln ausführlicher Zeitsteuerungsdaten mithilfe der Instrumentierung) ](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)<br />-   [How to: Profile JavaScript Code in Web Pages (Vorgehensweise: Profilerstellung für JavaScript-Code in Webseiten)](../profiling/how-to-profile-javascript-code-in-web-pages.md)<br />-   [Collecting Thread and Process Concurrency Data (Sammeln von Nebenläufigkeitsdaten zu Threads und Prozessen) ](../profiling/collecting-thread-and-process-concurrency-data.md)<br />-   [Collecting Additional Performance Data (Sammeln zusätzlicher Leistungsdaten)](../profiling/collecting-additional-performance-data.md)|  
|**Festlegen von erweiterten Konfigurationsoptionen:** Wenn Sie das Profil von .NET Framework-Anwendungen anlegen, die mehrere CLR-Versionen laden, können Sie angeben, für welche Version Sie das Profil anlegen möchten. Wenn Ihre Leistungssitzung mehrere EXE-Dateien umfasst, können Sie die Startreihenfolge der Binärdateien festlegen.|-   [How to: Specify the .NET Framework Runtime (Vorgehensweise: Angeben der .NET Framework-Laufzeit)](../profiling/how-to-specify-the-dotnet-framework-runtime.md)<br />-   [How to: Specify the Binary to Start (Vorgehensweise: Angeben der zu startenden Binärdatei)](../profiling/how-to-specify-the-binary-to-start.md)|  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Steuern der Datensammlung](../profiling/controlling-data-collection.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Performance Explorer (Leistungs-Explorer)](../profiling/performance-explorer.md)