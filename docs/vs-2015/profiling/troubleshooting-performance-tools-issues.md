---
title: Problembehandlung bei Leistungstools | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0b61cdf7-75b7-4abd-aff2-7bd997717626
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 93e9f75ad953ff9c6cd08e8eb78bcfbf01542223
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51787925"
---
# <a name="troubleshooting-performance-tools-issues"></a>Problembehandlung bei Leistungstools
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
  
 Dieses Problem wird durch die Analyse-Engine des Profilerstellungstools verursacht, die die PDB-Dateien mit den Symbolinformationen nicht finden kann, durch die Quellcodeinformationen wie z.B. Funktionsnamen und Zeilennummern der kompilierten Datei zugeordnet werden. Standardmäßig erstellt der Compiler bei der Erstellung der Anwendungsdatei die PDB-Datei. Ein Verweis auf das lokale Verzeichnis der PDB-Datei wird in der kompilierten Anwendung gespeichert. Die Analyse-Engine sucht nach der PDB-Datei in dem Verzeichnis, auf das verwiesen wird, und dann in der Datei, die derzeit die Anwendungsdatei enthält. Wenn die PDB-Datei nicht gefunden wird, verwendet die Analyse-Engine statt der Funktionsnamen die Funktionsoffsets.  
  
 Sie können das Problem auf zwei Arten beheben:  
  
-   Suchen Sie die PDB-Dateien und platzieren Sie sie im selben Verzeichnis wie die Anwendungsdateien.  
  
-   Betten Sie die Symbolinformationen in die Profilerstellungsdatendatei (.vsp) ein. Weitere Informationen finden Sie unter [Speichern von Symbolinformationen mittels Leistungsdatendateien](../profiling/saving-symbol-information-with-performance-data-files.md).  
  
> [!NOTE]
>  Für die Analyse-Engine muss die PDB-Datei die gleiche Version wie die kompilierte Anwendungsdatei aufweisen. Eine PDB-Datei aus einem früheren oder späteren Build der Anwendungsdatei kann nicht verwendet werden.



