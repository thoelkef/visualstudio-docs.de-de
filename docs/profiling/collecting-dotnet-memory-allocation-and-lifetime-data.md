---
title: "Sammeln von Daten zur .NET-Speicherbelegung und Lebensdauer | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - ".NET-Arbeitsspeicher-Profilerstellungsmethode"
  - "Profilerstellungstools, .NET-Arbeitsspeichermethode"
ms.assetid: 62a6dd5f-db66-4456-9d57-f8913dbfe4d5
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Sammeln von Daten zur .NET-Speicherbelegung und Lebensdauer
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Von den [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Profilerstellungstools wird das Sammeln von Daten zur .NET\-Speicherbelegung und zur Objektlebensdauer unterstützt, damit Leistungsprobleme im Zusammenhang mit dem Arbeitsspeicher in der Anwendung erkannt werden können.  
  
-   Informationen zur .NET\-Speicherbelegung enthalten die Größe und die Anzahl von .NET Framework\-Arbeitsspeicherobjekten, die zugeordnet wurden.  
  
-   Objektlebensdauerdaten enthalten die Größe und die Anzahl von .NET Framework\-Arbeitsspeicherobjekten, die in den drei Garbage Collection\-Generierungen freigegeben wurden.  
  
 **Voraussetzungen**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
> [!NOTE]
>  Verbesserte Sicherheitsfeatures in Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung des Visual Studio\-Profilers auf diesen Plattformen.  Außerdem benötigen Windows Store\-Apps neue Erfassungsmethoden.  Siehe [Profilerstellung für Windows 8\- und Windows Server 2012\-Anwendungen](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 Daten können mit der Sampling\- oder der Instrumentationsmethode zur Profilerstellung gesammelt werden.  
  
-   Wenn Sie die Samplingmethode verwenden, verfolgt der Profiler alle .NET\-Speicherbelegungen und Objekte, die von dem Prozess generiert werden, der gestartet oder an den der Profiler angefügt wurde.  
  
-   Wenn Sie die Instrumentationsmethode verwenden, verfolgt der Profiler nur die .NET\-Speicherbelegungen und die Objekte nach, die von den instrumentierten Modulen generiert werden.  
  
> [!IMPORTANT]
>  Wenn Sie .NET\-Arbeitsspeicherdaten \(Belegungen und\/oder Objektlebensdauern\) mithilfe der Samplingmethode sammeln, werden alle vom Benutzer angegebenen Samplingereignisse ignoriert, und die entsprechenden Speicherbelegungsereignisse werden verwendet, um Daten zu sammeln.  
  
 Wenn Sie die Profilerstellung für die .NET\-Speicherbelegung aktivieren, aktivieren Sie auch die Zuordnungsansicht.  Wenn Sie die Profilerstellung für .NET\-Lebensdauerdaten aktivieren, aktivieren Sie auch die Objektlebensdaueransicht.  Weitere Informationen finden Sie unter [Zuordnungsansicht](../profiling/dotnet-memory-allocations-view.md) und [Objektlebensdaueransicht](../profiling/object-lifetime-view.md).  
  
 Informationen zum Sammeln von .NET\-Arbeitsspeicherdaten mit den Befehlszeilentools der Profilerstellungstools finden Sie unter [Verwenden von Profilerstellungsmethoden über die Befehlszeile](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md) im Thema "Verwenden von .NET\-Arbeitsspeichermethoden zum Sammeln von Daten zur Speicherbelegung und der Objektlebensdauer".  
  
### So sammeln Sie .NET\-Speicherdaten  
  
1.  Klicken Sie im **Leistungs\-Explorer** mit der rechten Maustaste auf die Leistungssitzung, und klicken Sie dann auf **Eigenschaften**.  
  
2.  Klicken Sie im Dialogfeld *Performance Session***Eigenschaftenseiten**  klicken Sie auf die Registerkarte **Allgemein** und aktivieren Sie das Kontrollkästchen **.NET\-ObjektSpeicherbelegungsinformationen auflisten**.  
  
3.  Aktivieren Sie das Kontrollkästchen **Lebensdauerinformationen für .NET\-Objekt auflisten**, um Lebensdauerinformationen für .NET\-Objekte zu sammeln.  
  
## Allgemeine Aufgaben  
 Sie können Optionen im Dialogfeld *Performance Session***Eigenschaftenseiten** der Leistungssitzung angeben.  So öffnen Sie dieses Dialogfeld  
  
-   Klicken Sie im **Leistungs\-Explorer** mit der rechten Maustaste auf den Namen der Leistungssitzung, und klicken Sie dann auf **Eigenschaften**.  
  
 Die Aufgaben in der folgenden Tabelle beschreiben Optionen, die Sie im Dialogfeld *Performance Session***Eigenschaftenseiten** angeben können, wenn Sie .NET\-Arbeitsspeicherdaten sammeln.  
  
|Aufgabe|Verwandter Inhalt|  
|-------------|-----------------------|  
|Geben Sie auf der Seite **Allgemein** Namensdetails für die generierte Profilerstellungs\-Datendatei \(.vsp\) an.|-   [Collecting .NET Memory Allocation and Lifetime Data](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Gewusst wie: Dateinamenoptionen für Profilerstellungsdaten](../profiling/how-to-set-performance-data-file-name-options.md)|  
|Wählen Sie auf der Seite **Starten** die Anwendung aus, die gestartet werden soll, wenn mehrere EXE\-Projekte in der Codeprojektmappe vorhanden sind.|-   [Erfassen von Ebeneninteraktionsdaten](../profiling/collecting-tier-interaction-data.md)|  
|Fügen Sie der Profilerstellung auf der Seite **Ebeneninteraktionen** ADO.NET\-Aufrufdaten hinzu.|-   [Erfassen von Ebeneninteraktionsdaten](../profiling/collecting-tier-interaction-data.md)|  
|Geben Sie auf der Seite **Windows\-Ereignisse** ein oder mehrere ETW\-Ereignisse \(Ereignisse der Ereignisablaufverfolgung für Windows\) an, die mit den Samplingdaten erfasst werden sollen.|-   [Gewusst wie: Sammeln von Daten der Ereignisablaufverfolgung für Windows \(ETW\)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|  
|Geben Sie auf der Seite **Windows\-Indikatoren** einen oder mehrere Betriebssystem\-Leistungsindikatoren an, die den Profilerstellungsdaten als Markierungen hinzugefügt werden sollen.|-   [Gewusst wie: Sammeln von Windows\-Indikatordaten](../profiling/how-to-collect-windows-counter-data.md)|  
|Geben Sie auf der Seite **Erweitert** die Version der .NET Framework\-Laufzeit für die Profilerstellung an, wenn die Anwendungsmodule mehrere Versionen verwenden.  Standardmäßig wird die zuerst geladene Version für die Profilerstellung verwendet.|-   [Gewusst wie: Angeben der .NET Framework\-Laufzeit für die Profilerstellung in parallelen Szenarios](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|  
  
## Instrumentationsaufgaben  
 Die Aufgaben in der folgenden Tabelle sind Optionen im Dialogfeld **Eigenschaftenseiten**, die für die Profilerstellung mit der Instrumentationsmethode spezifisch sind.  
  
|Aufgabe|Verwandter Inhalt|  
|-------------|-----------------------|  
|Geben Sie auf der Seite **Binärdateien** einen Speicherort für die instrumentierten Kopien der Module an.  Standardmäßig werden die ursprünglichen Binärdateien in einen Sicherungsordner verschoben.|-   [Gewusst wie: Verschieben instrumentierter Binärdateien](../profiling/how-to-relocate-instrumented-binaries.md)|  
|Schließen Sie auf der Seite **Instrumentation** kleine Funktionen von der Profilerstellung aus, um den Profilerstellungsaufwand zu reduzieren, erstellen Sie für JavaScript\-Code in ASP.NET\-Webseiten ein Profil, und geben Sie Befehle an, die vor und nach der Instrumentation über eine Eingabeaufforderung ausgeführt werden sollen.|-   [Gewusst wie: Ausschließen oder Einschließen kurzer Funktionen in die Instrumentation](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)<br />-   [Gewusst wie: Profilerstellung für JavaScript\-Code \(ECMA\) in Webseiten](../profiling/how-to-profile-javascript-code-in-web-pages.md)<br />-   [Gewusst wie: Festlegen von Präinstrumentations\- und Postinstrumentationsbefehlen](../profiling/how-to-specify-pre-and-post-instrument-commands.md)|  
|Geben Sie auf der Seite **CPU\-Indikatoren** einen oder mehrere Prozessorleistungsindikatoren an, die den Profilerstellungsdaten hinzugefügt werden sollen.|-   [Gewusst wie: Sammeln von CPU\-Indikatordaten](../profiling/how-to-collect-cpu-counter-data.md)|  
|Geben Sie auf der Seite **Erweitert** zusätzliche gewünschte VSInstr.exe\-Optionen an, z. B. Optionen zum Ein\- oder Ausschließen bestimmter Funktionen.  Weitere Informationen zu diesen VSInstr\-Optionen finden Sie unter [VSInstr](../profiling/vsinstr.md).|-   [Gewusst wie: Angeben zusätzlicher Instrumentationsoptionen](../profiling/how-to-specify-additional-instrumentation-options.md)<br />-   [Gewusst wie: Beschränken der Instrumentation auf bestimmte Funktionen](../profiling/how-to-limit-instrumentation-to-specific-functions.md)|  
  
## Siehe auch  
 [Konfigurieren von Leistungssitzungen](../profiling/configuring-performance-sessions.md)   
 [Gewusst wie: Auswählen von Sammlungsmethoden](../profiling/how-to-choose-collection-methods.md)   
 [Eigenschaften von Leistungssitzungen](../profiling/performance-session-properties.md)