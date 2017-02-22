---
title: "VSInstr | Microsoft Docs"
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
  - "Leistungstools, Instrumentation"
  - "Instrumentation, VSInstr-Tool"
  - "Profilerstellungstools, VSInstr"
  - "Befehlszeilentools, Instrumentation"
  - "Befehlszeile, Tools"
  - "VSInstr"
  - "VSInstr-Tool"
  - "Leistungstools, VSInstr-Tool"
ms.assetid: 7b1334f7-f9b0-4a82-a145-d0607bfa8467
caps.latest.revision: 44
caps.handback.revision: 44
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# VSInstr
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Mithilfe des VSInstr\-Tools werden Binärdateien instrumentiert.  Das Tool wird über diese Syntax aufgerufen:  
  
```  
VSInstr [/U] filename [/options]  
```  
  
 In der folgenden Tabelle werden die Optionen des VSInstr\-Tools beschrieben:  
  
|Optionen|**Beschreibung**|  
|--------------|----------------------|  
|**Help** oder **?**|Zeigt die Hilfe an.|  
|**U**|Umgeleitete Konsolenausgaben werden als Unicode geschrieben.  Diese Option muss zuerst angegeben werden.|  
|`@filename`|Legt den Namen einer Antwortdatei fest, die eine Befehlsoption pro Zeile enthält.  Verwenden Sie keine Anführungszeichen.|  
|**OutputPath** `:path`|Gibt ein Zielverzeichnis für das instrumentierte Image an.  Wird kein Ausgabepfad angegeben, wird die ursprüngliche Binärdatei umbenannt, indem im selben Verzeichnis "Orig" an den Dateinamen angehängt wird, und eine Kopie der ursprünglichen Binärdatei wird instrumentiert.|  
|**Exclude** `:funcspec`|Gibt eine Funktionsspezifikation an, die mithilfe von Überprüfungen von der Instrumentation ausgeschlossen werden soll.  Dies ist hilfreich, wenn das Einfügen von Profilerstellungsüberprüfungen in eine Funktion zu unvorhersehbaren und unerwünschten Ergebnissen führt.<br /><br /> Geben Sie keine **Exclude**\-Option oder **Include**\-Option an, die auf Funktionen in derselben Binärdatei verweist.<br /><br /> Geben Sie die **Exclude**\-Option mehrmals an, wenn Sie mehrere Funktionen ausschließen möchten.<br /><br /> `funcspec` wird folgendermaßen definiert:<br /><br /> \[namespaceseparator1\<\>\] \[classseparator2\<\>\] Funktion<br /><br /> \<separator1\> ist `::` für systemeigenen Code und `.` für verwalteten Code.<br /><br /> \<separator2\> ist immer `::`<br /><br /> **Exclude** wird mit Codeabdeckung unterstützt.<br /><br /> Das Platzhalterzeichen \* wird unterstützt.  Zum Beispiel können Sie alle Funktionen in einem Namespace ausschließen:<br /><br /> MyNamespace::\*<br /><br /> Sie können die vollständigen Namen von Funktionen in der angegebenen Binärdatei mithilfe von **VSInstr \/DumpFuncs** aufführen.|  
|**Include** `:funcspec`|Gibt eine Funktionsspezifikation in einer Binärdatei an, die mit Überprüfungen instrumentiert werden soll.  Alle anderen Funktionen in den Binärdateien werden nicht instrumentiert.<br /><br /> Geben Sie die **Include**\-Option mehrmals an, wenn Sie mehrere Funktionsspezifikationen angeben möchten.<br /><br /> Geben Sie keine **Include**\-Option oder **Exclude**\-Option an, die auf Funktionen in derselben Binärdatei verweist.<br /><br /> **Include** wird nicht mit Codeabdeckung unterstützt.<br /><br /> `funcspec` wird folgendermaßen definiert:<br /><br /> \[namespaceseparator1\<\>\] \[classseparator2\<\>\] Funktion<br /><br /> \<separator1\> ist `::` für systemeigenen Code und `.` für verwalteten Code.<br /><br /> \<separator2\> ist immer `::`<br /><br /> Das Platzhalterzeichen \* wird unterstützt.  Zum Beispiel können Sie alle Funktionen in einem Namespace einschließen:<br /><br /> MyNamespace::\*<br /><br /> Sie können die vollständigen Namen von Funktionen in der angegebenen Binärdatei mithilfe von **VSInstr \/DumpFuncs** aufführen.|  
|**DumpFuncs**|Listet die Funktionen im angegebenen Image auf.  Es wird keine Instrumentation durchgeführt.|  
|**ExcludeSmallFuncs**|Schließt kleine Funktionen aus der Instrumentation aus. Hierbei handelt es sich um kurze Funktionen, die keine Funktionsaufrufe ausführen.  Die **ExcludeSmallFuncs**\-Option bietet einen geringeren Instrumentationsmehraufwand und damit eine verbesserte Instrumentationsgeschwindigkeit.<br /><br /> Durch den Ausschluss kleiner Funktionen wird auch die Größe von VSP\-Dateien und die für die Analyse erforderliche Zeit reduziert.|  
|**Mark:**{**Before** `&#124;`  **After** `&#124;`  **Top** `&#124;` **Bottom**}`,funcname,markid`|Fügt eine Profilmarkierung \(einen Bezeichner zum Unterteilen der Daten in Berichten\) ein, mit der der Beginn und das Ende eines Datenbereichs in einer VSP\-Berichtsdatei identifiziert werden können.<br /><br /> **Before**  ``  – Unmittelbar vor dem Aufrufen der Zielfunktion.<br /><br /> **After**  ``  – Unmittelbar nach dem Verlassen der Zielfunktion.<br /><br /> **Top**  ``  – Unmittelbar nach dem Aufrufen der Zielfunktion.<br /><br /> **Bottom**  ``  – Unmittelbar vor jeder Rückkehr in der Zielfunktion.<br /><br /> `funcname` – Der Name der Zielfunktion.<br /><br /> `Markid`\- Eine positive ganze Zahl \(lang\), die als Bezeichner für die Profilmarkierung verwendet wird.|  
|**Coverage**|Führt eine Abdeckungsinstrumentation durch.  Es kann nur mit den folgenden Optionen verwendet werden: **Verbose**, **OutputPath**, **Exclude** und **Logfile**.|  
|**Verbose**|Die **Verbose**\-Option wird zum Anzeigen detaillierter Informationen zum Instrumentationsvorgang verwendet.|  
|**NoWarn** `[:[Message Number[;Message Number]]]`|Unterdrückt alle oder bestimmte Warnungen.<br /><br /> `Message Number` – Die Warnnummer.  Wenn die `Message Number` weggelassen wird, werden alle Warnungen unterdrückt.<br /><br /> Weitere Informationen finden Sie unter [VSInstr\-Warnungen](../profiling/vsinstr-warnings.md).|  
|**Control** `:{` **Thread** `&#124;`  **Process** `&#124;` **Global** `}`|Gibt die Profilebene der folgenden VSInstr\-Optionen für die Steuerung der Datensammlung an:<br /><br /> **Start**<br /><br /> **StartOnly**<br /><br /> **Suspend**<br /><br /> **StopOnly**<br /><br /> **SuspendOnly**<br /><br /> **ResumeOnly**<br /><br /> **Thread**  ``  – Gibt die Steuerungsfunktionen für die Datensammlung auf Threadebene an.  Die Profilerstellung wird nur für den aktuellen Thread gestartet oder beendet.  Der Profilerstellungszustand anderer Threads wird nicht beeinflusst.  Der Standardwert ist thread.<br /><br /> **Process**  ``  – Gibt die Steuerungsfunktionen für die Sammlung von Profilerstellungsdaten auf Prozessebene an.  Die Profilerstellung wird für alle Threads im aktuellen Prozess gestartet oder beendet.  Der Profilerstellungszustand für andere Prozesse wird nicht beeinflusst.<br /><br /> **Global**  ``  – Gibt die Steuerungsfunktionen für die Datensammlung auf globaler Ebene \(prozessübergreifend\) an.<br /><br /> Wenn Sie keine Profilebene angeben, tritt ein Fehler auf.|  
|**Start** `:{` **Inside** `&#124;` **Outside** `},funcname`|Beschränkt die Datensammlung auf die Zielfunktion sowie die von dieser Funktion aufgerufenen untergeordneten Funktionen.<br /><br /> **Inside**  ``  – Fügt die StartProfile\-Funktion unmittelbar nach dem Aufrufen der Zielfunktion ein.  Fügt die StopProfile\-Funktion unmittelbar vor jeder Rückkehr in die Zielfunktion ein.<br /><br /> **Outside**  ``  – Fügt die StartProfile\-Funktion unmittelbar vor jedem Aufruf der Zielfunktion ein.  Fügt die StopProfile\-Funktion unmittelbar nach einem Aufruf in die Zielfunktion ein.<br /><br /> `funcname` – Der Name der Zielfunktion.|  
|**Suspend** `:{` **Inside** `&#124;` **Outside** `},funcname`|Schließt die Datensammlung für die Zielfunktion und untergeordnete von der Funktion aufgerufene Funktionen aus.<br /><br /> **Inside**  ``  – Fügt die SuspendProfile\-Funktion unmittelbar nach dem Aufrufen der Zielfunktion ein.  Fügt die ResumeProfile\-Funktion unmittelbar vor jeder Rückkehr in die Zielfunktion ein.<br /><br /> **Outside**  ``  – Fügt die SuspendProfile\-Funktion unmittelbar vor dem Aufrufen der Zielfunktion ein.  Fügt die ResumeProfile\-Funktion unmittelbar nach dem Verlassen der Zielfunktion ein.<br /><br /> `funcname` – Der Name der Zielfunktion.<br /><br /> Wenn die Zielfunktion eine StartProfile\-Funktion enthält, wird die SuspendProfile\-Funktion davor eingefügt.  Wenn die Zielfunktion eine StopProfile\-Funktion enthält, wird die ResumeProfile\-Funktion danach eingefügt.|  
|**StartOnly:** `{` **Before** `&#124;`  **After** `&#124;`  **Top** `&#124;` **Bottom** `},funcname`|Startet während einer Profilerstellungsausführung die Datensammlung.  Diese Option fügt die StartProfile\-API\-Funktion an der angegebenen Stelle ein.<br /><br /> **Before**  `` – Unmittelbar vor dem Aufrufen der Zielfunktion.<br /><br /> **After**  `` – Unmittelbar nach dem Verlassen der Zielfunktion.<br /><br /> **Top**  ``  – Unmittelbar nach dem Aufrufen der Zielfunktion.<br /><br /> **Bottom**  `` – Unmittelbar vor jeder Rückkehr in der Zielfunktion.<br /><br /> `funcname` – Der Name der Zielfunktion.|  
|**StopOnly:**{**Before** `&#124;`  **After** `&#124;`  **Top** `&#124;` **Bottom**}`,funcname`|Stoppt während einer Profilerstellungsausführung die Datensammlung.  Die Option fügt die StopProfile\-Funktion an der angegebenen Stelle ein.<br /><br /> **Before**  `` – Unmittelbar vor dem Aufrufen der Zielfunktion.<br /><br /> **After**  `` – Unmittelbar nach dem Verlassen der Zielfunktion.<br /><br /> **Top**  ``  – Unmittelbar nach dem Aufrufen der Zielfunktion.<br /><br /> **Bottom**  `` – Unmittelbar vor jeder Rückkehr in der Zielfunktion.<br /><br /> `funcname` – Der Name der Zielfunktion.|  
|**SuspendOnly:**{**Before** `&#124;`  **After** `&#124;`  **Top** `&#124;` **Bottom**}`,funcname`|Stoppt während einer Profilerstellungsausführung die Datensammlung.  Die Option fügt die SuspendProfile\-API\-Funktion an der angegebenen Stelle ein.<br /><br /> **Before**  `` – Unmittelbar vor dem Aufrufen der Zielfunktion.<br /><br /> **After**  `` – Unmittelbar nach dem Verlassen der Zielfunktion.<br /><br /> **Top**  ``  – Unmittelbar nach dem Aufrufen der Zielfunktion.<br /><br /> **Bottom**  `` – Unmittelbar vor jeder Rückkehr in der Zielfunktion.<br /><br /> `funcname` – Der Name der Zielfunktion.<br /><br /> Wenn die Zielfunktion eine StartProfile\-Funktion enthält, wird die SuspendProfile\-Funktion davor eingefügt.|  
|**ResumeOnly:**{**Before** `&#124;`  **After** `&#124;`  **Top** `&#124;` **Bottom**}`,funcname`|Beginnt oder setzt während einer Profilerstellungsausführung die Datensammlung fort.<br /><br /> Normalerweise wird sie verwendet, um die Profilerstellung zu starten, wenn durch eine **SuspendOnly**\-Option die Profilerstellung angehalten wurde.  Die Option fügt eine ResumeProfile\-API\-Funktion an der angegebenen Stelle ein.<br /><br /> **Before**  `` – Unmittelbar vor dem Aufrufen der Zielfunktion.<br /><br /> **After**  `` – Unmittelbar nach dem Verlassen der Zielfunktion.<br /><br /> **Top**  ``  – Unmittelbar nach dem Aufrufen der Zielfunktion.<br /><br /> **Bottom**  `` – Unmittelbar vor jeder Rückkehr in der Zielfunktion.<br /><br /> `funcname` – Der Name der Zielfunktion.<br /><br /> Wenn die Zielfunktion eine StopProfile\-Funktion enthält, wird die ResumeProfile\-Funktion danach eingefügt.|  
  
## Siehe auch  
 [VSPerfMon](../profiling/vsperfmon.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [VSPerfReport](../profiling/vsperfreport.md)   
 [VSInstr\-Warnungen](../profiling/vsinstr-warnings.md)   
 [Berichtsansichten für Profilerstellungstools](../profiling/performance-report-views.md)