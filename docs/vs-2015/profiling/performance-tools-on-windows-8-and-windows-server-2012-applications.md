---
title: Leistungstools für Windows 8- und Windows Server 2012-Anwendungen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: a704215d-d252-4087-921b-ac81ebe2a9c9
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c65561f9a9a2ca287232b7a61bb0e07ca07a769d
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299663"
---
# <a name="performance-tools-on-windows-8-and-windows-server-2012-applications"></a>Leistungstools für Windows 8- und Windows Server 2012-Anwendungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Verbesserte Sicherheitsfunktionen in Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung der Visual Studio-Leistungstools auf diesen Plattformen. Außerdem benötigen Windows Store-Apps neue Erfassungsmethoden. In diesem Thema werden die Änderungen für die Leistungstools auf Windows 8- und Windows Server 2012-Plattformen beschrieben.  
  
> [!NOTE]
> Leistungstools für andere unterstützte Versionen von Windows (Windows 7, Windows Server 2008 R2) haben sich nicht geändert.  
  
## <a name="BKMK_In_this_topic"></a> In diesem Thema  
 [Sammeln von Daten für Windows Store-Apps in Visual Studio-IDE](#BKMK_Profiling_Windows_Store_apps_from_the_Visual_Studio_IDE)  
  
 [Sammeln von Daten aus der Visual Studio-IDE für Apps, die auf dem Windows 8-Desktop oder unter Windows Server 2012 ausgeführt werden](#BKMK_Profiling_apps_running_on_the_Windows_8_desktop_or_on_Windows_Server_2012_from_the_Visual_Studio_IDE)  
  
- [Sammeln von Daten für Apps, die auf dem Windows 8-Desktop oder unter Windows Server 2012 ausgeführt werden, unter Verwendung von Sampling aus der Visual Studio-IDE](#BKMK_Profiling_apps_running_on_the_Windows_8_desktop_or_on_Windows_Server_2012_by_using_sampling_from_the_Visual_Studio_IDE)  
  
  [Profilerstellung mithilfe der Befehlszeile](#BKMK_Profiling_from_the_command_line)  
  
  [Sammeln von Ebeneninteraktionsdaten (TIP-Daten)](#BKMK_Collecting_tier_interaction__TIP__data)  
  
## <a name="BKMK_Profiling_Windows_Store_apps_from_the_Visual_Studio_IDE"></a> Sammeln von Daten für Windows Store-Apps in Visual Studio-IDE  
 Wenn Sie das Profil für eine Windows Store-App erstellen, die in JavaScript und HTML 5 geschrieben ist, erfassen Sie Instrumentationsdaten für den JavaScript-Code. Wenn Sie das Profil für eine Windows Store-App oder -Komponente erstellen, die in Visual C++, Visual C# oder Visual Basic geschrieben ist, erfassen Sie Samplingdaten für den systemeigenen und verwalteten Code. Sie können das Profil für die App lokal oder auf einem Remotecomputer erstellen.  
  
 Diese Funktionen und Optionen für die Profilerstellung werden nicht unterstützt, wenn Profile für Windows Store-Apps erstellt werden:  
  
- Die Profilerstellung von JavaScript-Apps mit der Samplingmethode.  
  
- Die Profilerstellung für verwalteten und systemeigenen Code mit der Instrumentationsmethode.  
  
- Parallelitätsprofilerstellung  
  
- Profilerstellung für .NET-Arbeitsspeicher  
  
- Profilerstellung für Ebeneninteraktion  
  
- Samplingoptionen, z. B. das Festlegen des Samplingereignis- und -steuerungsintervalls oder das Sammeln zusätzlicher Leistungsindikatordaten.  
  
- Instrumentationsoptionen, z. B. das Sammeln von Leistungs- und Fensterindikatordaten oder das Angeben zusätzlicher Befehlszeilenoptionen.  
  
  Weitere Informationen zur Profilerstellung für Windows Store-Apps finden Sie in den folgenden Themen im Windows Developer Center:  
  
  [Ausführen von Windows Store-Apps auf einem lokalen Computer](../debugger/run-windows-store-apps-on-the-local-machine.md)  
  
  [Ausführen von Windows Store-Apps auf einem Remotecomputer](../debugger/run-windows-store-apps-on-a-remote-machine.md)  
  
  [Analysieren der App-Leistung](https://msdn.microsoft.com/library/58acb30b-8428-41a6-b195-b0fdedb89575)  
  
- [JavaScript-Funktionstiming](https://msdn.microsoft.com/library/b2bf49fc-aea7-4d9c-8fcf-cff8b8dd0c03)  
  
- [Zeitliche Steuerung von JavaScript-Funktionen auf einem Remote Gerät](https://msdn.microsoft.com/library/d78812b6-a97e-46dc-8d99-e724d1d725d8)  
  
- [Analysieren von JavaScript-Funktionstimingdaten](https://msdn.microsoft.com/library/b5aea8d8-36df-47ba-a7ca-95406700ca9b)  
  
- [Profilerstellung für Visual C++-, Visual C#- und Visual Basic-Code in Windows Store-Apps auf einem lokalen Computer](https://msdn.microsoft.com/2d0c939e-0bac-48c5-b727-46f6c6113060)  
  
- [Erstellen eines Profils von Visual C++-, Visual C#- und Visual Basic-Code in Windows Store-Apps auf einem Remotegerät](https://msdn.microsoft.com/b932a2be-11b0-40fd-b996-75c6b6a79d22)  
  
- [Analysieren von Leistungsdaten für Visual C++-, Visual C#- und Visual Basic-Code in Windows Store-Apps](https://msdn.microsoft.com/5de4a413-d924-425f-afc4-e1ecfb0fca18)  
  
  [In diesem Thema](#BKMK_In_this_topic)  
  
## <a name="BKMK_Profiling_apps_running_on_the_Windows_8_desktop_or_on_Windows_Server_2012_from_the_Visual_Studio_IDE"></a> Sammeln von Daten aus der Visual Studio-IDE für Apps, die auf dem Windows 8-Desktop oder unter Windows Server 2012 ausgeführt werden  
 Die Profilerstellung mithilfe der Instrumentationsmethode hat sich unter Windows 8 nicht geändert.  
  
 Die Profilerstellung für die Ebeneninteraktion wird nicht mit der Samplingmethode unterstützt.  
  
### <a name="BKMK_Profiling_apps_running_on_the_Windows_8_desktop_or_on_Windows_Server_2012_by_using_sampling_from_the_Visual_Studio_IDE"></a> Sammeln von Daten für Apps, die auf dem Windows 8-Desktop oder unter Windows Server 2012 ausgeführt werden, unter Verwendung von Sampling aus der Visual Studio IDE  
 Diese Funktionen und Optionen für die Profilerstellung werden nicht unterstützt, wenn Profile für Windows 8-Desktopanwendungen oder Windows Server 2012-Anwendungen mithilfe der Samplingmethode erstellt werden:  
  
- Profilerstellung für Ebeneninteraktion. Das Sammeln von Daten für die Profilerstellung für die Ebeneninteraktion mithilfe der Instrumentation wird unterstützt.  
  
- Samplingoptionen, z. B. das Festlegen des Samplingereignis- und -steuerungsintervalls oder das Sammeln zusätzlicher Leistungsindikatordaten.  
  
## <a name="BKMK_Profiling_from_the_command_line"></a> Profilerstellung mithilfe der Befehlszeile  
 Sie verwenden zwei Befehlszeilentools, um Profilerstellungsdaten auf Windows 8- und Windows Server 2012-Geräten zu erfassen, einschließlich Geräte, auf denen kein Visual Studio installiert ist:  
  
|Toolname|Beschreibung|  
|---------------|-----------------|  
|[VSPerf](../profiling/vsperf.md)|Sammelt Profilerstellungsdaten von Windows Store-Apps und Beispielprofilerstellungsdaten von Windows 8-Desktopanwendungen und Windows Server 2012-Anwendungen.|  
|[VSPerfCmd](../profiling/vsperfcmd.md)|Sammelt Instrumentations-, Parallelitäts- und Ebeneninteraktionsprofilerstellungsdaten von Apps, die unter Windows 8-Desktop oder Windows Server 2012 ausgeführt werden. Sammelt alle Arten von Profilerstellungsdaten von früheren Versionen von Windows.|  
  
 Beide Tools werden mit Visual Studio zur Verwendung auf dem lokalen Computer installiert.  
  
 Um Profile für Anwendungen auf Geräten zu erstellen, auf denen Visual Studio nicht installiert ist, führen Sie eines der folgenden Verfahren aus:  
  
- Laden Sie die Tools als Teil der Remotetools für Visual Studio von der [MSDN-Website](https://go.microsoft.com/fwlink/?LinkID=219549)herunter.  
  
- Kopieren Sie das Installationsprogramm für die eigenständigen Profilertools, und führen Sie es von Ihrem Visual Studio-Computer aus. Die Installationsprogramme befinden sich im Ordner *%VSInstallDir%* **\Team Tools\Performance Tools\Setups** . Wählen Sie das Setupprogramm für das Betriebssystem (x86/x64) des Remotecomputers aus.  
  
> [!NOTE]
> Um Profilerstellungsdaten für die Ebeneninteraktion (TIP-Daten) zu erfassen, müssen Sie den eigenständigen Profiler vom Visual Studio-Computer auf dem Remotecomputer installieren.  
  
 Diese Funktionen und Optionen für die Profilerstellung werden nicht unterstützt, wenn Profile für Windows 8- und Windows Server 2012-Anwendungen von der Befehlszeile erstellt werden:  
  
- Erfassen von Daten von Windows 8- und Windows Server 2012-Web-Apps mithilfe des Samplingmodus mit [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md).  
  
- Erfassen von Samplingdaten mit VsPerfCmd.exe.  
  
- Samplingoptionen, z. B. das Festlegen des Samplingereignis- und -steuerungsintervalls oder das Sammeln zusätzlicher Leistungsindikatordaten.  
  
## <a name="BKMK_Collecting_tier_interaction__TIP__data"></a> Sammeln von Ebeneninteraktionsdaten (TIP-Daten)  
 Die Profilerstellung für Ebeneninteraktion stellt weitere Informationen zu den Ausführungszeiten der Funktionen von Anwendungen mit mehreren Ebenen, die über ADO.NET-Dienste mit Datenbanken kommunizieren, bereit. Es werden nur Daten für synchrone Funktionsaufrufe gesammelt.  
  
 **Visual Studio-Editionen**  
  
 Profilerstellungsdaten für die Ebeneninteraktion können mit [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]oder [!INCLUDE[vs_pro_current_short](../includes/vs-pro-current-short-md.md)]erfasst werden. Allerdings können Profilerstellungsdaten für die Ebeneninteraktion nur in [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] und [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]angezeigt werden.  
  
 **Windows 8 und Windows Server 2012**  
  
1. Um Ebeneninteraktionsdaten von Apps zu sammeln, die unter Windows 8 Desktop oder Windows Server 2012 ausgeführt werden, müssen Sie die Instrumentationsmethode verwenden.  
  
2. Sie können Ebeneninteraktionsdaten nicht für Windows Store-Apps sammeln.  
  
3. Sie können Ebeneninteraktionsdaten in alle Profilerstellungsmethoden einer anderen unterstützten Version von Windows einschließen.  
  
   **Leistungs-Assistent und Leistungs-Explorer**  
  
   Sie müssen die Ebeneninteraktions-Datensammlungsoption einer laufenden Profilerstellung vom Leistungs-Explorer hinzufügen. Sie müssen das Projekt, die ausführbare Datei oder die Website außerdem dem Zielknoten des Leistungs-Explorers hinzufügen. Informationen hierzu finden Sie unter [Erfassen von Ebeneninteraktionsdaten](../profiling/collecting-tier-interaction-data.md).  
  
   **Sammeln von TIP-Daten auf einem Remotecomputer**  
  
   Sie müssen Sie die Datei **vs\_profiler\_** _\<Plattform>_ **\_** _\<Sprache>_ **.exe** aus dem Ordner _%VInstallDir%_ **\Team Tools\Performance Tools\Setups** eines Visual Studio-Computers auf den Remotecomputer kopieren und dort installieren, um Ebeneninteraktionsdaten auf einem Remotecomputer zu erfassen. Sie können nicht die Profilerstellungstools im Downloadpaket der [Visual Studio-Remotetools](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c) verwenden.  
  
   Sie können [VSPerfCmd](../profiling/vsperfcmd.md) oder [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md) verwenden, um die Profilerstellungsdaten zu erfassen.  
  
   **TIP-Berichte**  
  
   Ebeneninteraktionsdaten können nur in der [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] - oder [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] -IDE angezeigt werden. Dateibasierte Ebeneninteraktionsberichte über [VSPerfReport](../profiling/vsperfreport.md) sind nicht verfügbar.  
  
## <a name="see-also"></a>Siehe auch  
 [Performance Explorer (Leistungs-Explorer)](../profiling/performance-explorer.md)   
 [Konfigurieren von Leistungssitzungen](../profiling/configuring-performance-sessions.md)   
 [Profilerstellung mithilfe der Befehlszeile](../profiling/using-the-profiling-tools-from-the-command-line.md)
