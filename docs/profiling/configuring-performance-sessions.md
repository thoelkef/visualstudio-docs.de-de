---
title: "Konfigurieren von Leistungssitzungen f&#252;r Profilerstellungstools | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Allgemeine Aufgaben, Leistung"
  - "Allgemeine Aufgaben, Profilerstellungstools"
  - "Profilerstellungstools, Allgemeine Aufgaben"
  - "Leistung, Ermitteln von Daten"
ms.assetid: e1c3ba41-ffca-4edf-9a7f-8a5a9244ef9b
caps.latest.revision: 36
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 36
---
# Konfigurieren von Leistungssitzungen f&#252;r Profilerstellungstools
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Mit den [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Profilerstellungstools können Sie vielfältige Leistungsdaten für zahlreiche Anwendungstypen sammeln.  In diesem Abschnitt wird erläutert, wie Sie die Profilerstellungstools mithilfe des Leistungs\-Assistenten und der Eigenschaften der Leistungssitzung und der Zielbinärdatei so konfigurieren, dass die gewünschten Daten gesammelt werden.  Die Konfigurationseigenschaften der Profilerstellungstools können auch verwendet werden, um zu steuern, wie viele Daten bei der Profilerstellung erfasst werden.  Weitere Informationen finden Sie unter [Steuern der Datensammlung](../profiling/controlling-data-collection.md).  
  
> [!NOTE]
>  In vielen Fällen ist die Verwendung der Standardeigenschaften des Leistungs\-Assistenten ein effektives Verfahren zum Sammeln von Profilerstellungsdaten.  Weitere Informationen finden Sie unter [Einführung in die Leistungsprofilerstellung](../profiling/beginners-guide-to-performance-profiling.md) und [Erste Schritte](../profiling/getting-started-with-performance-tools.md).  
  
## Allgemeine Aufgaben  
  
|Aufgabe|Verwandter Inhalt|  
|-------------|-----------------------|  
|**Festlegen der grundlegenden Optionen für die Profilerstellung:** Sie sollten [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] für die Verwendung des Microsoft\-Symbolservers konfigurieren.  So wird sichergestellt, dass Sie Zugriff auf Symbole wie Funktions\- und Parameternamen für die aktuelle Version von Windows und andere Microsoft\-Anwendungen haben.  Sie können auch andere allgemeine Optionen angeben, bevor eine Profilerstellungssitzung startet, z. B. Systemberechtigungen für die Profilerstellungstools und die Namen von Datendateien für die Profilerstellung.|-   [Gewusst wie: Verweisen auf Windows\-Symbolinformationen](../profiling/how-to-reference-windows-symbol-information.md)<br />-   [Gewusst wie: Serialisieren von Symbolinformationen](../profiling/how-to-serialize-symbol-information.md)<br />-   [Gewusst wie: Festlegen der aktuellen Profilerstellungssitzung](../profiling/how-to-set-the-current-session.md)<br />-   [Gewusst wie: Festlegen von Berechtigungen für die Profilerstellung](../profiling/how-to-set-permissions.md)<br />-   [Gewusst wie: Dateinamenoptionen für Profilerstellungsdaten](../profiling/how-to-set-performance-data-file-name-options.md)|  
|**Eingeben der Daten, die gesammelt werden sollen:** Die Verfahren, mit denen Sie eine Profilerstellungssitzung konfigurieren, hängen vom Typ der Zielanwendung ab, für die die Profilerstellung erfolgen soll, und vom Typ der Leistungsdaten, die gesammelt werden sollen.|-   [Gewusst wie: Auswählen von Sammlungsmethoden](../profiling/how-to-choose-collection-methods.md)<br />-   [Sammeln von Leistungsstatistiken durch Sampling](../profiling/collecting-performance-statistics-by-using-sampling.md)<br />-   [Sammeln von Daten zur .NET\-Speicherbelegung und Lebensdauer](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Sammeln ausführlicher Zeitsteuerungsdaten mithilfe der Instrumentation](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)<br />-   [Gewusst wie: Profilerstellung für JavaScript\-Code \(ECMA\) in Webseiten](../profiling/how-to-profile-javascript-code-in-web-pages.md)<br />-   [Sammeln von Parallelitätsdaten zu Threads und Prozessen](../profiling/collecting-thread-and-process-concurrency-data.md)<br />-   [Sammeln zusätzlicher Leistungsdaten](../profiling/collecting-additional-performance-data.md)|  
|**Festlegen von erweiterten Konfigurationsoptionen:**  Wenn Sie Profile für .NET Framework\-Anwendungen erstellen, die mehrere Versionen der Common Language Run\-time \(CLR\) laden, können Sie angeben, für welche Version das Profil erstellt werden soll.  Wenn in einer Leistungssitzung mehrere EXE\-Dateien vorhanden sind, können Sie die Startreihenfolge der Binärdateien festlegen.|-   [Gewusst wie: Angeben der .NET Framework\-Laufzeit für die Profilerstellung in parallelen Szenarios](../profiling/how-to-specify-the-dotnet-framework-runtime.md)<br />-   [Gewusst wie: Angeben der zu startenden Binärdatei](../profiling/how-to-specify-the-binary-to-start.md)|  
  
## Verwandte Abschnitte  
 [Steuern der Datensammlung](../profiling/controlling-data-collection.md)  
  
## Siehe auch  
 [Verwenden von Profilerstellungstools](../profiling/performance-explorer.md)