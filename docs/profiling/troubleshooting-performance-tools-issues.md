---
title: Problembehandlung bei Leistungstools | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 0b61cdf7-75b7-4abd-aff2-7bd997717626
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: db48b940fecb27dd4f41b5fc56f32ee2cc4f5f02
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/01/2018
ms.locfileid: "34572344"
---
# <a name="troubleshoot-performance-tools-issues"></a>Problembehandlung bei Leistungstools
Bei der Verwendung der Profilerstellungstools tritt möglicherweise eines der folgenden Probleme auf:  
  
-   [Von den Profilerstellungstools werden keine Daten gesammelt.](#NoDataCollected)  
  
-   [Leistungsansichten und Berichte zeigen Nummern für Funktionsnamen an.](#NoSymbols)  
  
## <a name="no-data-is-collected-by-the-profiling-tools"></a>Von den Profilerstellungstools werden keine Daten gesammelt  
 Nachdem Sie ein Profil für eine Anwendung erstellt haben, wird keine Profilerstellungsdatendatei (*VSP*) erstellt, und Sie erhalten im **Ausgabefenster** oder im Befehlsfenster die folgende Warnung:  
  
 PRF0025: Es wurden keine Daten gesammelt.  
  
 Dieses Problem kann mehrere Ursachen haben:  
  
-   Ein Prozess, der mit der Sampling- oder der .NET-Arbeitsspeichermethode profiliert wurde, startet einen untergeordneten Prozess, der die Anwendungsarbeit ausführt. Einige Anwendungen lesen z.B. die Befehlszeile, um festzustellen, ob sie als Windows-Anwendung oder Befehlszeilenanwendung gestartet wurden. Wenn eine Windows-Anwendung angefordert wurde, startet der ursprüngliche Prozess einen neuen, als Windows-Anwendung konfigurierten Prozess, und der ursprüngliche Prozess wird beendet. Da die Profilerstellungstools nicht automatisch Daten für untergeordnete Prozesse erfassen, werden keine Daten gesammelt.  
  
     Zum Sammeln von Profilerstellungsdaten in einem solchen Fall starten Sie die Anwendung nicht mit dem Profiler, sondern fügen Sie den Profiler an den untergeordneten Prozess an. Weitere Informationen finden Sie unter [Vorgehensweise: Anfügen von Leistungstools an einen laufenden Prozess und Trennen von Leistungstools von einem laufenden Prozess](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md) und [Attach (VSPerfCmd)](../profiling/attach.md).  
  
## <a name="performance-views-and-reports-display-numbers-for-function-names"></a>Leistungsansichten und Berichte zeigen Nummern für Funktionsnamen an  
 Nachdem Sie für eine Anwendung ein Profil erstellt haben, werden in Berichten und Ansichten statt der Funktionsnamen Nummern angezeigt.  
  
 Dieses Problem wird durch die Analyse-Engine des Profilerstellungstools verursacht, die die *PDB-Dateien* mit den Symbolinformationen nicht finden kann, durch die Quellcodeinformationen wie z.B. Funktionsnamen und Zeilennummern der kompilierten Datei zugeordnet werden. Standardmäßig erstellt der Compiler bei der Erstellung der Anwendungsdatei die *PDB-Datei*. Ein Verweis auf das lokale Verzeichnis der *PDB-Datei* wird in der kompilierten Anwendung gespeichert. Die Analyse-Engine sucht nach der *PDB-Datei* in dem Verzeichnis, auf das verwiesen wird, und dann in der Datei, die derzeit die Anwendungsdatei enthält. Wenn die *PDB-Datei* nicht gefunden wird, verwendet die Analyse-Engine statt der Funktionsnamen die Funktionsoffsets.  
  
 Sie können das Problem auf zwei Arten beheben:  
  
-   Suchen Sie die *PDB-Dateien*, und platzieren Sie sie im selben Verzeichnis wie die Anwendungsdateien.  
  
-   Betten Sie die Symbolinformationen in die Profilerstellungsdatendatei (*VSP*) ein. Weitere Informationen finden Sie unter [Speichern von Symbolinformationen mittels Leistungsdatendateien](../profiling/saving-symbol-information-with-performance-data-files.md).  
  
> [!NOTE]
>  Für die Analyse-Engine muss die *PDB-Datei* die gleiche Version wie die kompilierte Anwendungsdatei aufweisen. Eine *PDB-Datei* aus einem früheren oder späteren Build der Anwendungsdatei kann nicht verwendet werden.