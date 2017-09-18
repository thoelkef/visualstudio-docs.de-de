---
title: "Sammeln von Leistungsstatistiken durch Sampling | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Profilerstellungstools, Sampling"
  - "Sampling-Profilerstellungsmethode"
ms.assetid: 8e36361b-bb3d-40c6-b286-0e68c0ecb915
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# Sammeln von Leistungsstatistiken durch Sampling
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Standardmäßig werden mit der Samplingmethode der [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)]\-Profilerstellungstools nach jeweils 10.000.000 Prozessorzyklen Profilerstellungsinformationen gesammelt \(etwa jede Hundertstelsekunde auf einem 1\-GHz\-Computer\).  Die Samplingmethode ist nützlich für das Auffinden von Prozessornutzungsproblemen und ist die vorgeschlagene Methode zum Starten der meisten Leistungsuntersuchungen.  
  
 **Voraussetzungen**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
> [!NOTE]
>  Verbesserte Sicherheitsfeatures in Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung des Visual Studio\-Profilers auf diesen Plattformen.  Außerdem benötigen Windows Store\-Apps neue Erfassungsmethoden.  Siehe [Profilerstellung für Windows 8\- und Windows Server 2012\-Anwendungen](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 Zum Angeben der Samplingmethode haben Sie folgende Möglichkeiten:  
  
-   Klicken Sie auf der ersten Seite des Profilerstellungs\-Assistenten auf **CPU\-Sampling \(empfohlen\)**.  
  
-   Klicken Sie in der Symbolleiste **Leistungs\-Explorer** in der Liste **Methode** auf **Sampling**.  
  
-   Klicken Sie im Eigenschaftendialogfeld der Leistungssitzung auf der Seite **Allgemein** auf **Sampling**.  
  
## Allgemeine Aufgaben  
 Sie können Optionen im Dialogfeld *Performance Session***Eigenschaftenseiten** der Leistungssitzung angeben.  So öffnen Sie dieses Dialogfeld  
  
-   Klicken Sie im **Leistungs\-Explorer** mit der rechten Maustaste auf den Namen der Leistungssitzung, und klicken Sie dann auf **Eigenschaften**.  
  
 Die Aufgaben in der folgenden Tabelle beschreiben Optionen, die Sie im Dialogfeld *Performance Session***Eigenschaftenseiten** angeben können, wenn Sie ein Profil erstellen, indem Sie die Samplingmethode.  
  
|Aufgabe|Verwandter Inhalt|  
|-------------|-----------------------|  
|Fügen Sie auf der Seite **Allgemein** gesammelte Daten zur .NET\-Speicherbelegung und Lebensdauer hinzu, und geben Sie Namensdetails für die generierte Profilerstellungs\-Datendatei \(.vsp\) an.|-   [Sammeln von Daten zur .NET\-Speicherbelegung und Lebensdauer](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Gewusst wie: Dateinamenoptionen für Profilerstellungsdaten](../profiling/how-to-set-performance-data-file-name-options.md)|  
|Ändern Sie auf der Seite **Sampling** die Samplingrate, ändern Sie das Samplingereignis von Prozessortaktzyklen in einen anderen Prozessorleistungsindikator, oder ändern Sie beide Werte.|-   [Gewusst wie: Auswählen von Samplingereignissen](../profiling/how-to-choose-sampling-events.md)|  
|Wenn sich in der Codeprojektmappe mehrere EXE\-Projekte befinden, geben Sie auf der Seite **Starten** die zu startenden Anwendungen sowie die Startreihenfolge an.|-   [Erfassen von Ebeneninteraktionsdaten](../profiling/collecting-tier-interaction-data.md)|  
|Fügen Sie auf der Seite **Ebeneninteraktionen** ADO.NET\-Aufrufinformationen zu den Daten hinzu, die während der Profilerstellung gesammelt wurden.|-   [Erfassen von Ebeneninteraktionsdaten](../profiling/collecting-tier-interaction-data.md)|  
|Geben Sie auf der Seite **Windows\-Ereignisse** ein oder mehrere ETW\-Ereignisse \(Ereignisse der Ereignisablaufverfolgung für Windows\) an, die mit den Samplingdaten erfasst werden sollen.|-   [Gewusst wie: Sammeln von Daten der Ereignisablaufverfolgung für Windows \(ETW\)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|  
|Geben Sie auf der Seite **Windows\-Indikatoren** einen oder mehrere Betriebssystem\-Leistungsindikatoren an, die den Profilerstellungsdaten als Markierungen hinzugefügt werden sollen.|-   [Gewusst wie: Sammeln von Windows\-Indikatordaten](../profiling/how-to-collect-windows-counter-data.md)|  
|Geben Sie auf der Seite **Erweitert** die Version der .NET Framework\-Laufzeit für die Profilerstellung an, wenn die Anwendungsmodule mehrere Versionen verwenden.  Standardmäßig wird die zuerst geladene Version für die Profilerstellung verwendet.|-   [Gewusst wie: Angeben der .NET Framework\-Laufzeit für die Profilerstellung in parallelen Szenarios](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|