---
title: VSPerf | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: b5854e62-279e-4850-bfeb-0c6ef82f4805
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0a32de469c5b58ca2bf58901e30b81cfb70ed84b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54803526"
---
# <a name="vsperf"></a>VSPerf
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Verwenden Sie das Befehlszeilentool **VsPerf** für Folgendes:  
  
1. Erstellen Sie von der Befehlszeile aus Profile für Windows Store-Apps, wenn Visual Studio nicht auf dem Gerät installiert ist.  
  
2. Erstellen Sie Profile für Windows 8-Desktopanwendungen und Windows Server 2012-Anwendungen mithilfe der Sampling-Profilerstellungsmethode.  
  
   Weitere Informationen zu Ihren Profilerstellungsoptionen finden Sie unter [Profilerstellung für Windows 8- und Windows Server 2012-Anwendungen](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
##  <a name="BKMK_In_this_topic"></a> In diesem Thema  
 Dieses Thema beschreibt die Optionen, die Sie mit dem Befehlszeilentool `vsperf.exe` verwenden können. Dieses Thema enthält folgende Abschnitte:  
  
 [Nur Windows Store-Apps](#BKMK_windows_store_apps_only)  
  
 [Nur Windows 8-Desktopanwendungen und Windows Server 2012-Anwendungen](#BKMK_Windows_8_classic_applications_and_Windows_Server_2012_applications_only)  
  
 [Alle Anwendungen](#BKMK_All_applications)  
  
##  <a name="BKMK_windows_store_apps_only"></a> Nur Windows Store-Apps  
 Diese Optionen gelten nur für Windows Store-Apps.  
  
|||  
|-|-|  
|**/app:{AppName}**|Startet den Profiler und wartet darauf, dass die angegebene App vom Startmenü aus gestartet wird.<br /><br /> Führen Sie `vsperf /listapps` aus, um den App-Namen und PackageFullName der installierten Apps anzuzeigen.|  
|**/package:{PackageFullName}**|Startet den Profiler und wartet darauf, dass die angegebene App vom Startmenü aus gestartet wird.<br /><br /> Führen Sie `vsperf /listapps` aus, um den App-Namen und PackageFullName der installierten Apps anzuzeigen.|  
|**/js**|Erforderlich für die Profilerstellung von JavaScript-Apps.<br /><br /> Es werden Leistungsdaten von JavaScript-Apps gesammelt.<br /><br /> Nur mit „/package“ oder „/attach“ verwenden.|  
|**/noclr**|Dies ist optional. Es werden keine CLR-Daten gesammelt.<br /><br /> Nur mit „/package“ oder „/attach“ verwenden.<br /><br /> Optimierung, es werden keine verwalteten Symbole aufgelöst.|  
|**/listapps**|Listet Namen installierter Apps und PackageFullNames auf.|  
  
##  <a name="BKMK_Windows_8_classic_applications_and_Windows_Server_2012_applications_only"></a> Nur Windows 8-Desktopanwendungen und Windows Server 2012-Anwendungen  
 Diese Optionen funktionieren nicht mit Windows Store-Apps.  
  
|||  
|-|-|  
|**/launch:{Executable}**|Startet und beginnt die Profilerstellung für die angegebene ausführbare Datei.|  
|**/args:{ExecutableArguments}**|Gibt Befehlszeilenargumente an, um das **/launch**-Ziel zu erreichen.|  
|**/console**|Führt das **/launch**-Ziel in einem neuen Befehlsfenster aus.|  
  
##  <a name="BKMK_All_applications"></a> Alle Anwendungen  
 Diese Option gilt für jede Windows 8- oder Windows Server 2012-Anwendung.  
  
|||  
|-|-|  
|**/attach:{PID&#124;ProcessName}[,PID&#124;ProcessName]...**|Sammelt Daten aus den angegebenen Prozessen.<br /><br /> Verwenden Sie Task-Manager, um die Prozess-ID (PID) anzuzeigen und Namen von ausgeführten Apps zu verarbeiten.|  
|**/file:{ReportName}**|Dies ist optional. Gibt die Ausgabedatei an (überschreibt die vorhandene Datei).<br /><br /> Nur mit „/package“ oder „/attach“ verwenden.|  
|**/pause**|Hält die Datensammlung an.|  
|**/resume**|Führt die Datensammlung fort.|  
|**/stop**|Beendet die Datensammlung und die Zielprozesse.|  
|**/detach**|Beendet die Datensammlung, erlaubt jedoch die weitere Ausführung von Zielprozessen.|  
|**/status**|Zeit den Profiler-Status an.|  
  
## <a name="see-also"></a>Siehe auch  
 [Profilerstellung für Windows 8- und Windows Server 2012-Anwendungen](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)   
 [Profilerstellung mithilfe der Befehlszeile](../profiling/using-the-profiling-tools-from-the-command-line.md)
