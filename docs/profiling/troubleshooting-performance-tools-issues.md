---
title: "Behandeln von Problemen bei Profilerstellungstools | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0b61cdf7-75b7-4abd-aff2-7bd997717626
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Behandeln von Problemen bei Profilerstellungstools
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Bei der Verwendung der Profilerstellungstools tritt möglicherweise eines der folgenden Probleme auf:  
  
-   [Von den Profilerstellungstools werden keine Daten gesammelt](#NoDataCollected)  
  
-   [Leistungsansichten und Berichte zeigen Nummern für Funktionsnamen an](#NoSymbols)  
  
##  <a name="NoDataCollected"></a> Von den Profilerstellungstools werden keine Daten gesammelt  
 Wenn Sie ein Profil für eine Anwendung erstellt haben, wird keine Profilerstellungsdatendatei \(.vsp\) erstellt, und Sie erhalten im Ausgabefenster oder im Befehlsfenster die folgende Warnung:  
  
 PRF0025: Es wurden keine Daten aufgeführt.  
  
 Für dieses Problem kommen mehrere Ursachen in Frage:  
  
-   Prozesse, die mit der Sampling\- oder der .NET\-Arbeitsspeichermethode profiliert wurden, starten einen untergeordneten Prozess, von dem die Anwendungsarbeit ausgeführt wird.  Manche Anwendungen lesen z. B. die Befehlszeile, um zu bestimmen, ob sie als Windows\-Anwendung oder Befehlszeilenanwendung gestartet wurden.  Wenn eine Windows\-Anwendung angefordert wurde, startet der ursprüngliche Prozess einen neuen, als Windows\-Anwendung konfigurierten Prozess, und der ursprüngliche Prozess wird dann beendet.  Da die Profilerstellungstools Daten für untergeordnete Prozesse nicht automatisch sammeln, werden keine Daten gesammelt.  
  
     Zum Sammeln von Profilerstellungsdaten in einer solchen Situation starten Sie die Anwendung nicht mit dem Profiler, sondern fügen Sie den Profiler an den untergeordneten Prozess an.  Weitere Informationen finden Sie unter [Gewusst wie: Anfügen eines Profilers an einen laufenden Prozess und Trennen eines Profilers von einem laufenden Prozess](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md) und [Attach \(VSPerfCmd\)](../profiling/attach.md).  
  
##  <a name="NoSymbols"></a> Leistungsansichten und Berichte zeigen Nummern für Funktionsnamen an  
 Wenn Sie für eine Anwendung ein Profil erstellt haben, werden in Berichten und Ansichten statt der Funktionsnamen Nummern angezeigt.  
  
 Dieses Problem wird durch das Analysemodul des Profilerstellungstools verursacht, das die PDB\-Dateien mit den Symbolinformationen nicht finden kann, durch die Quellcodeinformationen, z. B. Funktionsnamen und Zeilennummern, der kompilierten Datei zugeordnet werden.  Standardmäßig erstellt der Compiler die PDB\-Datei beim Build der Anwendungsdatei.  Ein Verweis auf das lokale Verzeichnis der PDB\-Datei wird in der kompilierten Anwendung gespeichert.  Das Analysemodul sucht nach der PDB\-Datei in dem Verzeichnis, auf das verwiesen wird, und dann in der Datei, die derzeit die Anwendungsdatei enthält.  Wenn die PDB\-Datei nicht gefunden wird, werden vom Analysemodul statt der Funktionsnamen die Funktionsoffsets verwendet.  
  
 Sie können das Problem mit zwei Methoden beheben:  
  
-   Suchen Sie die PDB\-Dateien, und fügen Sie diese in demselben Verzeichnis wie die Anwendungsdateien ein.  
  
-   Betten Sie die Symbolinformationen in die Profilerstellungsdatendatei \(.vsp\) ein.  Weitere Informationen finden Sie unter [Speichern von symbolischen Informationen mittels Profilerstellungsdatendateien](../profiling/saving-symbol-information-with-performance-data-files.md).  
  
> [!NOTE]
>  Für das Analysemodul muss die PDB\-Datei die gleiche Version wie die kompilierte Anwendungsdatei aufweisen.  PDB\-Dateien aus einem früheren oder späteren Build der Anwendungsdatei können nicht verwendet werden.