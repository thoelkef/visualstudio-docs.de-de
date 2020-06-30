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
ms.openlocfilehash: a8042b228a481dc3d720d8b422963db41abbddcd
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85533834"
---
# <a name="vsperf"></a>VSPerf
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Verwenden Sie das Befehlszeilentool **VsPerf** für Folgendes:  
  
1. Erstellen Sie von der Befehlszeile aus Profile für Windows Store-Apps, wenn Visual Studio nicht auf dem Gerät installiert ist.  
  
2. Erstellen Sie Profile für Windows 8-Desktopanwendungen und Windows Server 2012-Anwendungen mithilfe der Sampling-Profilerstellungsmethode.  
  
   Weitere Informationen zu Ihren Profilerstellungsoptionen finden Sie unter [Profilerstellung für Windows 8- und Windows Server 2012-Anwendungen](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> In diesem Thema  
 Dieses Thema beschreibt die Optionen, die Sie mit dem Befehlszeilentool `vsperf.exe` verwenden können. Dieses Thema enthält folgende Abschnitte:  
  
 [Nur Windows Store-Apps](#BKMK_windows_store_apps_only)  
  
 [Nur Windows 8-Desktop Anwendungen und Windows Server 2012-Anwendungen](#BKMK_Windows_8_classic_applications_and_Windows_Server_2012_applications_only)  
  
 [Alle Anwendungen](#BKMK_All_applications)  
  
## <a name="windows-store-apps-only"></a><a name="BKMK_windows_store_apps_only"></a> Nur Windows Store-Apps  
 Diese Optionen gelten nur für Windows Store-Apps.  
  
|Option|BESCHREIBUNG|  
|-|-|  
|**/app:{AppName}**|Startet den Profiler und wartet darauf, dass die angegebene App vom Startmenü aus gestartet wird.<br /><br /> Führen Sie `vsperf /listapps` aus, um den App-Namen und PackageFullName der installierten Apps anzuzeigen.|  
|**/package:{PackageFullName}**|Startet den Profiler und wartet darauf, dass die angegebene App vom Startmenü aus gestartet wird.<br /><br /> Führen Sie `vsperf /listapps` aus, um den App-Namen und PackageFullName der installierten Apps anzuzeigen.|  
|**/js**|Erforderlich für die Profilerstellung von JavaScript-Apps.<br /><br /> Es werden Leistungsdaten von JavaScript-Apps gesammelt.<br /><br /> Nur mit „/package“ oder „/attach“ verwenden.|  
|**/noclr**|Optional. Es werden keine CLR-Daten gesammelt.<br /><br /> Nur mit „/package“ oder „/attach“ verwenden.<br /><br /> Optimierung, es werden keine verwalteten Symbole aufgelöst.|  
|**/listapps**|Listet Namen installierter Apps und PackageFullNames auf.|  
  
## <a name="windows-8-desktop-applications-and-windows-server-2012-applications-only"></a><a name="BKMK_Windows_8_classic_applications_and_Windows_Server_2012_applications_only"></a> Nur Windows 8-Desktopanwendungen und Windows Server 2012-Anwendungen  
 Diese Optionen funktionieren nicht mit Windows Store-Apps.  
  
|Option|BESCHREIBUNG|  
|-|-|  
|**/launch:{Executable}**|Startet und beginnt die Profilerstellung für die angegebene ausführbare Datei.|  
|**/args:{ExecutableArguments}**|Gibt Befehlszeilenargumente an, um das **/launch**-Ziel zu erreichen.|  
|**/Console**|Führt das **/launch**-Ziel in einem neuen Befehlsfenster aus.|  
  
## <a name="all-applications"></a><a name="BKMK_All_applications"></a>Alle Anwendungen  
 Diese Option gilt für jede Windows 8- oder Windows Server 2012-Anwendung.  
  
|Option|BESCHREIBUNG|  
|-|-|  
|**/attach:{PID&#124;ProcessName}[,PID&#124;ProcessName]...**|Sammelt Daten aus den angegebenen Prozessen.<br /><br /> Verwenden Sie Task-Manager, um die Prozess-ID (PID) anzuzeigen und Namen von ausgeführten Apps zu verarbeiten.|  
|**/file:{ReportName}**|Optional. Gibt die Ausgabedatei an (überschreibt die vorhandene Datei).<br /><br /> Nur mit „/package“ oder „/attach“ verwenden.|  
|**/Pause**|Hält die Datensammlung an.|  
|**/Resume**|Führt die Datensammlung fort.|  
|**/Stop**|Beendet die Datensammlung und die Zielprozesse.|  
|**/Detach**|Beendet die Datensammlung, erlaubt jedoch die weitere Ausführung von Zielprozessen.|  
|**/Status**|Zeit den Profiler-Status an.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Leistungs Tools für Windows 8-und Windows Server 2012-Anwendungen](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)   
 [Profilerstellung mithilfe der Befehlszeile](../profiling/using-the-profiling-tools-from-the-command-line.md)
