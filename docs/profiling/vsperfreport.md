---
title: "VSPerfReport | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Befehlszeile, Tools"
  - "Befehlszeilentools, VSPerfReport-Tool"
  - "Instrumentierung, VSPerfReport-Tool"
  - "Leistungstools, VSPerfReport-Tool"
  - "Profilerstellungstools, VSPerfReport"
  - "VSPerfReport-Tool"
ms.assetid: dbfd8d91-4430-4b82-81b9-97ac61412a6c
caps.latest.revision: 32
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 32
---
# VSPerfReport
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Mit dem Befehlszeilentool VSPerfReport können Sie unter Verwendung von Profilerstellungsdatendateien der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Profilerstellungstools Berichte erstellen.  Das Standardberichtsformat entspricht einer .csv\-Datei.  
  
 VSPerfReport verwendet die folgende Syntax:  
  
```  
VSPerfReport [/U] vspfilename [/options]  
```  
  
 Beachten Sie, dass `filename` eine gültige .vsp\- oder .vsps\-Datei sein muss.  
  
 Das Befehlszeilentool VSPerfReport wird auch zum Vergleichen von VSP\- oder VSPS\-Dateien verwendet.  Um einen Unterschiedsbericht \("diff"\) zu generieren, verwenden Sie die folgende Syntax:  
  
```  
VSPerfReport [/U] /diff vspfilename1 vspfilename2 [/options]  
```  
  
 `vspfilename1 and vspfilename2` müssen gültige .vsp\- oder .vsps\-Dateien sein.  
  
## Symboldateien  
 Um Symbolinformationen, wie z. B. Funktionsnamen und Zeilennummern, anzuzeigen, benötigt VSPerfReport Zugriff auf die Symboldateien \(.PDB\) der profilierten Komponenten und auf die Windows\-Symboldateien.  Weitere Informationen finden Sie unter [Gewusst wie: Angeben von Symboldateispeicherorten über die Befehlszeile](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md).  
  
## Allgemeine Berichtsoptionen  
 In der folgenden Tabelle werden die allgemeinen Optionen der Berichtsformatierung sowie die Optionen für die Auswahl der Daten beschrieben, auf deren Grundlage ein Bericht erstellt wird.  
  
|Optionen|**Beschreibung**|  
|--------------|----------------------|  
|**U**|Berichtsausgabe und umgeleitete Konsolenausgabe werden als Unicode geschrieben.  Muss die erste angegebene Option sein.|  
|**Summary:**\[*types*\]|Erstellt mindestens einen Berichtstyp.<br /><br /> -   `All` – Alle Berichtstypen werden generiert.<br />-   `CallerCallee` – Über\- und untergeordnete Beziehungen zwischen Funktionen.<br />-   `Function` – Aufgerufene Funktionen.<br />-   `CallTree` – Hierarchie der aufgerufenen Funktionen.<br />-   `Counter` – Alle Markierungen zusammen mit Windows\-Leistungsindikatorwerten.<br />-   `Ip` – Profilierte Anweisungen.<br />-   `Life` – Lebensdauer belegter Objekte \(verfügbar, sofern Speicherbelegungsdaten gesammelt wurden\).<br />-   `Line` – Profildaten zu Quellcodezeilen.<br />-   `Header` – Bericht enthält Dateiheaderinformationen.<br />-   `Mark` – Alle Markierungen.<br />-   `Module` – Profilierte Module.<br />-   `Process` – Profilierte Prozesse.<br />-   `Thread` – Profilierte Threads.<br />-   `Type` – Belegte Typen.<br />-   `Contention` – Ressourcenkonflikte.<br />-   `RuleWarnings` – Leistungsregelprobleme<br />-   `ETW` – Alle während der Profilerstellungsausführung erfassten Ereignisse der Ereignisablaufverfolgung für Windows \(ETW\).  Die ETL\-Datendatei muss an ihrem ursprünglichen Speicherort oder in dem Verzeichnis abgelegt sein, das die VSP\- oder VSPS\-Datei enthält.|  
|**Xml**|Ausgabe des Berichts im XML\-Format.|  
|**CallTrace**|Erstellt eine Liste mit Werten für den Eintritt in bzw. das Verlassen von Funktionen, ETW\-Ereignissen und Markierungen.|  
|**ClearPackedSymbols**|Entfernt zuvor eingebettete Symbole aus einer Profilerdatendatei.  Führen Sie diesen Befehl aus, bevor Sie PackSymbols erneut ausführen.|  
|**SymbolPath:** `path`|Gibt einen oder mehr Suchpfade oder Symbolserver an, die Symbole für die Profilerdatendatei enthalten.|  
|**DebugSymPath**|Listet die Speicherorte, in denen nach Symbolen gesucht wird, und Hinweise zu gefundenen Symbole auf.  Diese Option ist hilfreich, um Symbolauflösungsprobleme zu beheben.|  
|**PackSymbols**|Speichert Symbole in der Profilerstellungs\-Datendatei \(.vsp\), damit Symboldateien \(.pdb\) für die Analyse nicht erforderlich sind.|  
|**Output:** *path* &#124;*filename*|Gibt einen alternativen Speicherort für die generierten Berichtdateien an.  Standardmäßig werden Berichte im aktuellen Verzeichnis erstellt.|  
|**SummaryFile**|Analysiert und speichert die analysierten Informationen in einer .vsps\-Zusammenfassungsdatei.|  
|**PrintMarks**|Zeigt die Namen und Timestamps für alle Markierungen in der angegebenen Berichtsdatei an.|  
|**?**|Zeigt Informationen zur Verwendung an.|  
|**NoLogo**|Blendet Versionsinformationen aus, wenn der Bericht ausgeführt wird.|  
|**UserRulesDirectory**|Gibt das Verzeichnis an, das benutzerdefinierte Leistungsregeln enthält \[Noch nicht implementiert\].|  
  
## Filteroptionen  
 In der folgenden Tabelle werden die Optionen zum Filtern der verfügbaren Daten beschrieben.  
  
|Optionen|**Beschreibung**|  
|--------------|----------------------|  
|**JustMyCode**\[**:**\[`caller`\]\[,`callee`\]\]|Nur Funktionsaufrufe durch Benutzeranwendungen zeigen; Systemaufrufe ausblenden.<br /><br /> -   Keine Parameter – Alle Systemfunktionen ausblenden.<br />-   `caller` – Eine Ebene von Systemfunktionen anzeigen, die Anwendungsfunktionen aufrufen.<br />-   `callee` – Eine Ebene von Systemfunktionen anzeigen, die von Benutzeranwendungsfunktionen aufgerufen werden.|  
|**StartTime:**\[*value*\]|Zeigt nur nach einem Wert \(in Millisekunden\) erfasste Daten an.|  
|**EndTime:**\[*value*\]|Zeigt nur vor einem Wert \(in Millisekunden\) erfasste Daten an.|  
|**FilterFile:** `VSPFFile`|Gibt den Speicherort einer Filterdatei an, die im Visual Studio\-Fenster Leistungsbericht generiert wurde.|  
|**MsFilter:**\[*starttime,duration*\]|Nur Daten ab `starttime` und für die Dauer von `duration` \(in Millisekunden\) anzeigen.|  
|**Process:**\[*pid*\]|Zeigt nur Daten zum angegebenen Prozess an.|  
|**Thread:**\[*threadid*\]|Zeigt nur Daten zum angegebenen Thread an.|  
|**Thread:**\[*threadid,processid*\]|Zeigt nur Daten zum angegebenen Thread an, der mit dem angegebenen Prozess verknüpft ist.|  
  
## Optionen für Unterschiedsberichte  
 In der folgenden Tabelle werden die Optionen zum Vergleichen von Berichtsdateien beschrieben.  
  
|Optionen|**Beschreibung**|  
|--------------|----------------------|  
|**Diff**  `vspfile1 vspfile2`|Vergleicht zwei Berichtsdateien \(.vsp oder .vsps\).  Zusammenfassungsoptionen werden mit der diff\-Option ignoriert.|  
|**Diff:**\[*value*\]|Unterschiede zwischen zwei Werten, die unter diesem Schwellenwert liegen, werden ignoriert.  Außerdem werden auch keine neuen Daten mit Werten unter diesem Schwellenwert angezeigt.|  
|**DiffTable:**\[*tablename*\]|Verwendet diese bestimmte Tabelle, um Dateien zu vergleichen.  Standardmäßig wird die Funktionstabelle verwendet.|  
|**DiffColumn:**\[*columnname*\]|Verwendet diese bestimmte Spalte, um Werte zu vergleichen.  Standardmäßig wird die Spalte mit dem prozentualen Wert der exklusiven Samplings verwendet.|  
|**QueryDiffTables**|Listet die gültigen Tabellen und Spalten für die beiden bereitgestellten Berichtsdateien auf.|  
  
## Siehe auch  
 [Berichtsansichten für Profilerstellungstools](../profiling/performance-report-views.md)