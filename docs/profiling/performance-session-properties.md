---
title: "Eigenschaften von Leistungssitzungen | Microsoft Docs"
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
  - "Profilerstellungstools, Eigenschaften"
  - "Eigenschaftenseiten, Profilerstellungstools"
  - "Leistungstools, Eigenschaften von Leistungssitzungen"
ms.assetid: c3a86913-172b-488f-a31a-cea01a71b2ea
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Eigenschaften von Leistungssitzungen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Mithilfe einer **Leistungssitzung** können Sie Einstellungen für die Profilerstellung der Anwendung konfigurieren.  Zudem werden in einer Leistungssitzung die für eine Profilerstellungssitzung generierten Berichte gespeichert.  
  
 **Voraussetzungen**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 Sie können eine **Leistungssitzung** entweder durch Ausführen des **Leistungs\-Assistenten** oder durch manuelles Erstellen einer Sitzung erstellen.  Die **Leistungssitzung** wird im **Leistungs\-Explorer** angezeigt, nachdem die **Leistungssitzung** erstellt wurde.  
  
 Um die Eigenschaften der **Leistungssitzung** anzuzeigen, klicken Sie im **Leistungs\-Explorer** mit der rechten Maustaste auf den Sitzungsnamen und wählen dann **Eigenschaften** aus.  
  
 Die Leistungssitzung verfügt über die folgenden Eigenschaftenseiten:  
  
## Allgemein  
 Diese Einstellungen ermöglichen, dass die Profilerstellungsmethode wählen, .NET\-Objektauflistungs\- und Lebensdauerinformationen hinzufügen, und den Standardspeicherort für Berichte und Namenskonventionen angeben.  
  
 Weitere Informationen finden Sie unter:  
  
 [Gewusst wie: Auswählen von Sammlungsmethoden](../profiling/how-to-choose-collection-methods.md)  
  
 [Sammeln von Daten zur .NET\-Speicherbelegung und Lebensdauer](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)  
  
 [Gewusst wie: Dateinamenoptionen für Profilerstellungsdaten](../profiling/how-to-set-performance-data-file-name-options.md)  
  
## Starten  
 Hier können Sie aus einer Liste Binärdateien zum Starten auswählen und die Startreihenfolge für die Binärdateien definieren.  
  
 Weitere Informationen finden Sie unter [Gewusst wie: Angeben der zu startenden Binärdatei](../profiling/how-to-specify-the-binary-to-start.md)  
  
## Sampling  
 Hier können Sie das Samplingereignis und Samplingintervall auswählen, wenn die Samplingmethode für die Profilerstellung verwendet wird.  Mithilfe eines Samplingereignisses werden Profilerstellungsdaten entsprechend dem festgelegten Intervall erfasst.  Lautet das Samplingereignis beispielsweise Taktzyklen und ist das Samplingintervall auf 10.000.000 festgelegt, werden jeweils nach 10 Millionen Taktzyklen Profilerstellungsdaten erfasst.  Die folgenden vier Typen von Samplingereignissen sind verfügbar:  
  
-   Taktzyklen – bei Problemen im Zusammenhang mit der CPU  
  
-   Seitenfehler – bei Problemen im Zusammenhang mit dem Arbeitsspeicher  
  
-   Systemaufrufe – bei E\/A\-Problemen  
  
-   Leistungsindikatoren – bei Problemen im Zusammenhang mit niedriger Leistung  
  
-   Zusätzliche Samplingereignisse können auf Grundlage verfügbarer Leistungsindikatoren angegeben werden.  
  
 Weitere Informationen finden Sie unter [Gewusst wie: Auswählen von Samplingereignissen](../profiling/how-to-choose-sampling-events.md)  
  
## Binär  
 Hier können Sie festlegen, ob instrumentierte Binärdateien an einen anderen Speicherort verschoben werden sollen.  Wenn Sie beispielsweise eine Profilerstellung für My.DLL durchführen und festlegen, dass die instrumentierte Binärdatei nicht verschoben werden soll, wird eine Sicherungskopie von My.DLL mit der Bezeichnung My.Orig.DLL erstellt.  Anschließend wird die My.DLL durch Einfügen von Überprüfungen zum Erfassen von Daten verändert.  Legen Sie hingegen fest, dass die instrumentierte Binärdatei verschoben werden soll, wird die ursprüngliche Binärdatei nicht umbenannt, und die instrumentierte Binärdatei wird für die Dauer der Instrumentation an den angegebenen Speicherort kopiert.  
  
 Weitere Informationen finden Sie unter [Gewusst wie: Angeben der zu startenden Binärdatei](../profiling/how-to-specify-the-binary-to-start.md)  
  
## Ebeneninteraktionen  
 Weitere Informationen finden Sie unter [Erfassen von Ebeneninteraktionsdaten](../profiling/collecting-tier-interaction-data.md)  
  
## Instrumentation  
 Mit diesen Einstellungen können Sie Leistungsdaten für JScript\-Code auf [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Webseiten erfassen und beliebige **Präinstrumentationsereignisse** und **Postinstrumentationsereignisse** festlegen, die vor bzw. nach dem Instrumentationsvorgang auftreten sollen.  
  
 Weitere Informationen finden Sie unter:  
  
 [Gewusst wie: Profilerstellung für JavaScript\-Code \(ECMA\) in Webseiten](../profiling/how-to-profile-javascript-code-in-web-pages.md)  
  
 [Gewusst wie: Festlegen von Präinstrumentations\- und Postinstrumentationsbefehlen](../profiling/how-to-specify-pre-and-post-instrument-commands.md)  
  
## CPU\-Indikatoren  
 Beim Verwenden der instrumentierten Profilerstellungsmethode können Sie mit diesen Einstellungen Daten zu CPU\-Leistungsindikatoren erfassen.  Portable Leistungszähler sind unabhängig von CPU\-Design oder \-Hersteller verfügbar.  Plattformereignisse sind spezifisch für CPU\-Design und \-Hersteller.  Weitere Informationen zu integrierten Leistungsindikatoren finden Sie in der Dokumentation des jeweiligen Prozessors.  
  
 Weitere Informationen finden Sie unter [Gewusst wie: Sammeln von CPU\-Indikatordaten](../profiling/how-to-collect-cpu-counter-data.md)  
  
## Windows\-Ereignisse  
 Während der Profilerstellung können Sie Daten von Ereignisablaufverfolgungsanbietern erfassen.  Sie können die Daten mithilfe der `/calltrace`\-Option des Befehlszeilentools VSPerfReport.exe anzeigen.  Weitere Informationen über Event Tracing for Windows \(ETW\), finden Sie. [Die Ereignisablaufverfolgung](http://go.microsoft.com/fwlink/?linkid=90752)  
  
 Weitere Informationen finden Sie unter:  
  
 [Gewusst wie: Sammeln von Daten der Ereignisablaufverfolgung für Windows \(ETW\)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)  
  
 [VSPerfReport](../profiling/vsperfreport.md).  
  
## Windows\-Indikatoren  
 Diese Option ermöglicht es Ihnen, Daten aus den Indikatoren des Windows\-Systemmonitors zu erfassen.  Um diese Daten zu erfassen, aktivieren Sie das Kontrollkästchen **Windows\-Leistungsindikatoren erfassen**.  Das Erfassungsintervall kann im Feld **Erfassungsintervall** festgelegt werden.  **Indikatorenkategorie** und **Instanz** sind möglicherweise auch verfügbar.  Einige Standardindikatoren des Windows\-Systemmonitors sind verfügbar.  
  
 Weitere Informationen finden Sie unter [Gewusst wie: Sammeln von Windows\-Indikatordaten](../profiling/how-to-collect-windows-counter-data.md).  
  
## Erweitert  
 Hier können Sie dem Instrumentationsprozess Optionen hinzufügen, indem Sie eine oder mehrere Optionen des [VSInstr](../profiling/vsinstr.md)\-Befehlszeilentools zur Profilerstellung angeben.  Sie können auch die Version der Common Runtime angeben, für die die Profilerstellung erfolgen soll, wenn die Anwendung mehr als eine Version verwendet.  
  
 Weitere Informationen finden Sie unter:  
  
 [Gewusst wie: Angeben der .NET Framework\-Laufzeit für die Profilerstellung in parallelen Szenarios](../profiling/how-to-specify-the-dotnet-framework-runtime.md)  
  
 [Gewusst wie: Angeben zusätzlicher Instrumentationsoptionen](../profiling/how-to-specify-additional-instrumentation-options.md)  
  
## Siehe auch  
 [Übersichten](../profiling/overviews-performance-tools.md)   
 [Konfigurieren von Leistungssitzungen](../profiling/configuring-performance-sessions.md)   
 [Steuern der Datensammlung](../profiling/controlling-data-collection.md)