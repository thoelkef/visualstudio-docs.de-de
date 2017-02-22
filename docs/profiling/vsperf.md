---
title: "VSPerf | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b5854e62-279e-4850-bfeb-0c6ef82f4805
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# VSPerf
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Verwenden Sie das Befehlszeilentool **VsPerf**:  
  
1.  Erstellen Sie Windows Store\-Apps aus der Befehlszeile ein Profil, wenn Visual Studio nicht auf dem Gerät installiert ist.  
  
2.  Erstellen Sie Windows 8\-Desktopanwendungen und Windows Server 2012\-Anwendungen mithilfe der Samplingmethode ein Profil.  
  
 Weitere Informationen über die Profilerstellungsoptionen, finden Sie unter [Profilerstellung für Windows 8\- und Windows Server 2012\-Anwendungen](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
##  <a name="BKMK_In_this_topic"></a> In diesem Thema  
 In diesem Thema werden die Optionen, die Sie mit dem `vsperf.exe` \- Befehlszeilentool verwenden können.  Dieses Thema enthält folgende Abschnitte:  
  
 [Nur Windows Store-Apps](#BKMK_windows_store_apps_only)  
  
 [Windows 8-Desktopanwendungen und nur Windows Server 2012-Anwendungen](#BKMK_Windows_8_classic_applications_and_Windows_Server_2012_applications_only)  
  
 [Alle Anwendungen](#BKMK_All_applications)  
  
##  <a name="BKMK_windows_store_apps_only"></a> Nur Windows Store\-Apps  
 Diese Optionen gelten nur für Windows Store\-Apps zu.  
  
|||  
|-|-|  
|**\/app:{AppName}**|Startet den Profiler und die Wartung die angegebene App, gestartetes von Startmenü zu sein.<br /><br /> Ausführung `vsperf /listapps`, das App Namens und des PackageFullName installierter Apps anzuzeigen.|  
|**\/package:{PackageFullName}**|Startet den Profiler und die Wartung die angegebene App, gestartetes von Startmenü zu sein.<br /><br /> Ausführung `vsperf /listapps`, das App Namens und des PackageFullName installierter Apps anzuzeigen.|  
|**\/js**|Erforderlich für die Profilerstellung von JavaScript\-Apps.<br /><br /> Sammeln von Leistungsdaten von JavaScript\-Apps.<br /><br /> Verwenden Sie nur mit \/package oder \/attach.|  
|**\/noclr**|Optional.  Sammeln Sie nicht CLR\-Daten.<br /><br /> Verwenden Sie nur mit \/package oder \/attach.<br /><br /> Optimierung, keine verwalteten Symbole wird für.|  
|**\/listapps**|Liste installierte App Namen und PackageFullNames.|  
  
##  <a name="BKMK_Windows_8_classic_applications_and_Windows_Server_2012_applications_only"></a> Windows 8\-Desktopanwendungen und nur Windows Server 2012\-Anwendungen  
 Diese Optionen funktionieren nicht auf Windows Store\-Apps.  
  
|||  
|-|-|  
|**\/launch:{Executable}**|Startet und startet, die angegebene ausführbare Datei ein Profil erstellen.|  
|**\/args:{ExecutableArguments}**|Legt Befehlszeilenargumente an, um das Ziel **\/launch** zu übergeben.|  
|**\/console**|Führt das **\/launch** ein neues Ziel in Befehlsfenster aus.|  
  
##  <a name="BKMK_All_applications"></a> Alle Anwendungen  
 Dadurch gelten Option beliebige Windows 8 oder Windows Server 2012\-Anwendung zu.  
  
|||  
|-|-|  
|**\/attach:{PID&#124;ProcessName}\[,PID&#124;ProcessName\]...**|Sammelt Daten aus angegebenen Prozesse.<br /><br /> Verwenden Sie Task\-Manager, um die Prozess\-ID \(PID\) anzuzeigen und verarbeiten Sie Namen von ausgeführten App.|  
|**\/file:{ReportName}**|Optional.  Gibt Ausgabedatei an \(überschreiben vorhandene Datei\).<br /><br /> Verwenden Sie nur mit \/package oder \/attach.|  
|**\/pause**|PAUSE\-Datensammlung.|  
|**\/resume**|Zusammenfassungsdatensammlung.|  
|**\/stop**|Beenden Sie die Datensammlung und beenden Sie Zielprozesse.|  
|**\/detach**|Beenden Sie die Datensammlung, aber lassen Sie Zielprozesse fortfahren, um ausgeführt zu werden.|  
|**\/status**|Zeigen Sie Profilerstatus an.|  
  
## Siehe auch  
 [Profilerstellung für Windows 8\- und Windows Server 2012\-Anwendungen](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)   
 [Profilerstellung mithilfe der Befehlszeile](../profiling/using-the-profiling-tools-from-the-command-line.md)