---
title: "Speichern und Exportieren von Daten aus Leistungstools | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Leistungstools, Speichern und Exportieren von Berichten"
ms.assetid: 2e9b28fe-3ed2-4e1d-b9cb-0a5e384380b0
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Speichern und Exportieren von Daten aus Leistungstools
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dieses Thema beschreibt das Speichern und Exportieren von Dateien, die Leistungsdaten enthalten.  
  
##  <a name="BKMK_Save_Profiler_Data_Files_As_Analyzed_Report_Files"></a> Vorgehensweise: Speichern von Leistungsdatendateien als analysierte Berichtsdateien  
 Sie können gefilterte oder ungefilterte Ansichten der Profilerstellungsdaten\-Dateien \(.vsp\) als analysierte Berichtsdateien \(.vsps\) speichern. Eine analysierte Berichtsdatei kann im Berichtsansichtsfenster angezeigt werden und ist erheblich kleiner als die ursprüngliche VSP\-Datei. Sie können jedoch keine Filter auf die Daten einer VSPS\-Datei anwenden. Sie können über den Leistungs\-Explorer eine analysierte Berichtsdatei erstellen, ohne die Datei in der integrierten Entwicklungsumgebung \(integrated development environment; IDE\) zu müssen, oder Sie öffnen und filtern die VSP\-Datei und speichern anschließend die Ergebnisse.  
  
#### Speichern eines analysierten Leistungsberichts über den Leistungs\-Explorer  
  
1.  Klicken Sie unter **Berichte** mit der rechten Maustaste auf die Profilerstellungs\-Datendatei, die Sie analysieren möchten, und klicken Sie anschließend auf **Analysierte Daten speichern**.  
  
2.  Legen Sie im Dialogfeld **Analysierte Daten speichern** das Verzeichnis fest und geben Sie den Dateinamen ein.  
  
3.  Klicken Sie auf **Speichern**.  
  
#### Speichern eines analysierten Leistungsberichts über das Fenster „Berichtsansicht“  
  
1.  Öffnen Sie die Profilerstellungs\-Datendatei \(.vsp\) im Fenster „Berichtsansicht“.  
  
2.  \(Optional\) Wenden Sie einen Filter auf die Daten an. Weitere Informationen finden Sie unter [Filter für die Berichtsansicht der Profilerstellungstools](../profiling/performance-report-view-filter.md).  
  
3.  Klicken Sie auf der Symbolleiste der Berichtsanzeige auf **Analysierte Daten speichern**.  
  
4.  Legen Sie im Dialogfeld **Analysierte Daten speichern** das Verzeichnis fest und geben Sie den Dateinamen ein.  
  
5.  Klicken Sie auf **Speichern**.  
  
## Vorgehensweise: Exportieren Berichte für Profilerstellungstools zu einer XML\- oder CSV\-Datei  
 Sie können eine oder mehrere Berichtsansichten aus einer VSP\-Datei oder einer VSP\-Profilerstellungsdatendatei als eine durch Trennzeichen getrennte Datei oder als XML\-Datei exportieren. Sie können die Daten im Fenster „Berichtsansicht“ filtern, bevor Sie exportieren, oder Sie können Berichtsansichten der gesamten Datendatei aus dem Fenster **Leistungs\-Explorer** exportieren.  
  
> [!NOTE]
>  Sie können auch ausgewählte Zeilen aus dem Fenster „Berichtsanzeige“ als durch Tabstopps getrennte Werte kopieren und einfügen.  
  
#### Exportieren von Leistungsberichten aus dem Fenster „Leistungs\-Explorer“  
  
1.  Wählen Sie im **Leistungs\-Explorer** den Bericht aus, klicken Sie mit der rechten Maustaste, und wählen Sie **Exportieren** aus.  
  
     Das Dialogfeld **Bericht exportieren** wird angezeigt.  
  
2.  Wählen Sie die Berichtsansichten aus, die Sie exportieren möchten.  
  
3.  Geben Sie unter **Prefix report with** \(Präfixreport mit\) das Präfix an, dass Sie dem Berichtsnamen hinzufügen möchten.  
  
4.  Geben Sie unter **Speicherort des exportierten Berichts** das Verzeichnis an.  
  
5.  Wählen Sie unter **Format des exportierten Berichts**\(durch Trennzeichen getrennt\) \(\*.csv\) oder XML\-Daten \(\*.xml\) aus.  
  
6.  Klicken Sie auf **Exportieren**.  
  
     Jede Berichtsansicht wird in einer separaten Datei mit dem Namen \<Präfix\>\_\<Berichtsansichtsname\>.\<csv&#124;xml\> gespeichert.  
  
#### So exportieren Sie Leistungsberichte aus dem Fenster „Berichtsansicht“  
  
1.  Öffnen Sie die VSP\-Datei im Fenster „Berichtsansicht“.  
  
2.  \(Optional\) Wenden Sie einen Filter auf die Daten an. Weitere Informationen finden Sie unter [Filter für die Berichtsansicht der Profilerstellungstools](../profiling/performance-report-view-filter.md).  
  
3.  Klicken Sie auf der Symbolleiste der Berichtsanzeige auf **Bericht exportieren**.  
  
4.  Wählen Sie die Berichtsansichten aus, die Sie exportieren möchten.  
  
5.  Geben Sie unter **Prefix report with** \(Präfixreport mit\) das Präfix an, dass Sie dem Berichtsnamen hinzufügen möchten.  
  
6.  Geben Sie unter **Speicherort des exportierten Berichts** das Verzeichnis an.  
  
7.  Wählen Sie unter **Format des exportierten Berichts**\(durch Trennzeichen getrennt\) \(\*.csv\) oder XML\-Daten \(\*.xml\) aus.  
  
8.  Klicken Sie auf **Exportieren**.  
  
     Jede Berichtsansicht wird in einer separaten Datei mit dem Namen \<Präfix\>\_\<Berichtsansichtsname\>.\<csv&#124;xml\> gespeichert.  
  
## Siehe auch  
 [Verwenden von Profilerstellungstools](../profiling/performance-explorer.md)   
 [Analysieren der durch Profilerstellungstools erstellten Daten](../profiling/analyzing-performance-tools-data.md)   
 [Vergleichen der durch Profilerstellungstools erstellten Datendateien](../profiling/comparing-performance-data-files.md)   
 [VSPerfReport](../profiling/vsperfreport.md)