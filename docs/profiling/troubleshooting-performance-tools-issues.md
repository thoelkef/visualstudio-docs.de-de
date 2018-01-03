---
title: Problembehandlung bei Leistungstools | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b61cdf7-75b7-4abd-aff2-7bd997717626
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 748f642e4bd150c8ec5819057b4ee3f7768893f0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="troubleshooting-performance-tools-issues"></a>Problembehandlung bei Leistungstools
Bei der Verwendung der Profilerstellungstools tritt möglicherweise eines der folgenden Probleme auf:  
  
-   [Von den Profilerstellungstools werden keine Daten gesammelt](#NoDataCollected)  
  
-   [Leistungsansichten und Berichte zeigen Nummern für Funktionsnamen an](#NoSymbols)  
  
##  <a name="NoDataCollected"></a> Von den Profilerstellungstools werden keine Daten gesammelt  
 Nachdem Sie ein Profil für eine Anwendung erstellt haben, wird keine Profilerstellungsdatendatei (.vsp) erstellt, und Sie erhalten im Ausgabefenster oder im Befehlsfenster die folgende Warnung:  
  
 PRF0025: Es wurden keine Daten gesammelt.  
  
 Dieses Problem kann mehrere Ursachen haben:  
  
-   Ein Prozess, der mit der Sampling- oder der .NET-Arbeitsspeichermethode profiliert wurde, startet einen untergeordneten Prozess, der die Anwendungsarbeit ausführt. Einige Anwendungen lesen z.B. die Befehlszeile, um festzustellen, ob sie als Windows-Anwendung oder Befehlszeilenanwendung gestartet wurden. Wenn eine Windows-Anwendung angefordert wurde, startet der ursprüngliche Prozess einen neuen, als Windows-Anwendung konfigurierten Prozess, und der ursprüngliche Prozess wird beendet. Da die Profilerstellungstools nicht automatisch Daten für untergeordnete Prozesse erfassen, werden keine Daten gesammelt.  
  
     Zum Sammeln von Profilerstellungsdaten in einem solchen Fall starten Sie die Anwendung nicht mit dem Profiler, sondern fügen Sie den Profiler an den untergeordneten Prozess an. Weitere Informationen finden Sie unter [Vorgehensweise: Anfügen von Leistungstools an einen laufenden Prozess und Trennen von Leistungstools von einem laufenden Prozess](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md) und [Attach (VSPerfCmd)](../profiling/attach.md).  
  
##  <a name="NoSymbols"></a> Leistungsansichten und Berichte zeigen Nummern für Funktionsnamen an  
 Nachdem Sie für eine Anwendung ein Profil erstellt haben, werden in Berichten und Ansichten statt der Funktionsnamen Nummern angezeigt.  
  
 Dieses Problem wird durch das Analysemodul des Profilerstellungstools verursacht, das die PDB-Dateien mit den Symbolinformationen nicht finden kann, durch die Quellcodeinformationen wie z.B. Funktionsnamen und Zeilennummern der kompilierten Datei zugeordnet werden. Standardmäßig erstellt der Compiler bei der Erstellung der Anwendungsdatei die PDB-Datei. Ein Verweis auf das lokale Verzeichnis der PDB-Datei wird in der kompilierten Anwendung gespeichert. Das Analysemodul sucht nach der PDB-Datei in dem Verzeichnis, auf das verwiesen wird, und dann in der Datei, die derzeit die Anwendungsdatei enthält. Wenn die PDB-Datei nicht gefunden wird, verwendet das Analysemodul statt der Funktionsnamen die Funktionsoffsets.  
  
 Sie können das Problem auf zwei Arten beheben:  
  
-   Suchen Sie die PDB-Dateien und platzieren Sie sie im selben Verzeichnis wie die Anwendungsdateien.  
  
-   Betten Sie die Symbolinformationen in die Profilerstellungsdatendatei (.vsp) ein. Weitere Informationen finden Sie unter [Speichern von Symbolinformationen mittels Leistungsdatendateien](../profiling/saving-symbol-information-with-performance-data-files.md).  
  
> [!NOTE]
>  Für das Analysemodul muss die PDB-Datei die gleiche Version wie die kompilierte Anwendungsdatei aufweisen. Eine PDB-Datei aus einem früheren oder späteren Build der Anwendungsdatei kann nicht verwendet werden.