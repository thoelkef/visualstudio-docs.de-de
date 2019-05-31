---
title: Leistungstools für Windows 8- und Windows Server 2012-Apps
ms.date: 06/19/2017
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 69b817af15b782ebd1e281d51855d62b11e8f470
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/28/2019
ms.locfileid: "66262956"
---
# <a name="performance-tools-on-windows-8-and-windows-server-2012-applications"></a>Leistungstools für Windows 8- und Windows Server 2012-Anwendungen

Verbesserte Sicherheitsfunktionen ab Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung der Visual Studio-Leistungstools auf diesen Plattformen. Außerdem benötigen UWP-Apps neue Erfassungsmethoden. In diesem Thema werden die Änderungen für die Leistungstools auf Windows 8- und Windows Server 2012-Plattformen beschrieben.

> [!NOTE]
> Leistungstools für andere unterstützte Versionen von Windows (Windows 7, Windows Server 2008 R2) haben sich nicht geändert.

## <a name="collect-data-on-uwp-apps-from-the-visual-studio-ide"></a>Erfassen von Daten für UWP-Apps in der Visual Studio-IDE

Wenn Sie das Profil für eine UWP-App erstellen, die in JavaScript und HTML 5 geschrieben ist, erfassen Sie Instrumentationsdaten für den JavaScript-Code. Wenn Sie das Profil für eine UWP-App oder -Komponente erstellen, die in Visual C++, Visual C# oder Visual Basic geschrieben ist, erfassen Sie Samplingdaten für den nativen und verwalteten Code. Sie können das Profil für die App lokal oder auf einem Remotecomputer erstellen.

Diese Funktionen und Optionen für die Profilerstellung werden nicht unterstützt, wenn Profile für UWP-Apps erstellt werden:

- Die Profilerstellung von JavaScript-Apps mit der Samplingmethode.
- Die Profilerstellung für verwalteten und systemeigenen Code mit der Instrumentationsmethode.
- Parallelitätsprofilerstellung
- Profilerstellung für .NET-Arbeitsspeicher
- Profilerstellung für Ebeneninteraktion
- Samplingoptionen, z. B. das Festlegen des Samplingereignis- und -steuerungsintervalls oder das Sammeln zusätzlicher Leistungsindikatordaten.
- Instrumentationsoptionen, z. B. das Sammeln von Leistungs- und Fensterindikatordaten oder das Angeben zusätzlicher Befehlszeilenoptionen.

Weitere Informationen zur Profilerstellung für UWP-Apps finden Sie in den folgenden Artikeln:

- [Run UWP apps on the local machine (Ausführen von UWP-Apps auf einem lokalen Computer)](/visualstudio/debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml)
- [Run UWP apps on a remote machine (Ausführen von UWP-Apps auf einem Remotecomputer)](../debugger/run-windows-store-apps-on-a-remote-machine.md)
- [Einführung in Profilerstellungstools](profiling-feature-tour.md)
- [JavaScript memory (JavaScript-Arbeitsspeicher)](../profiling/javascript-memory.md)
- [Profilerstellung für Visual C++-, Visual C#- und Visual Basic-Code in UWP-Apps auf einem lokalen Computer](https://msdn.microsoft.com/2d0c939e-0bac-48c5-b727-46f6c6113060)
- [Erstellen eines Profils von Visual C++-, Visual C#- und Visual Basic-Code in UWP-Apps auf einem Remotegerät](https://msdn.microsoft.com/b932a2be-11b0-40fd-b996-75c6b6a79d22)
- [Analysieren von Leistungsdaten für Visual C++-, Visual C#- und Visual Basic-Code in UWP-Apps](https://msdn.microsoft.com/5de4a413-d924-425f-afc4-e1ecfb0fca18)

## <a name="collect-data-on-apps-running-on-the-windows-8-desktop-or-on-windows-server-2012-from-the-visual-studio-ide"></a>Verwenden der Visual Studio-IDE zum Sammeln von Daten für Apps, die auf dem Windows 8-Desktop oder unter Windows Server 2012 ausgeführt werden

Die Profilerstellung mithilfe der Instrumentationsmethode hat sich unter Windows 8 nicht geändert.

Die Profilerstellung für die Ebeneninteraktion wird nicht mit der Samplingmethode unterstützt.

## <a name="collect-data-on-apps-running-on-the-windows-8-desktop-or-on-windows-server-2012-by-using-sampling-from-the-visual-studio-ide"></a>Verwenden von Sampling in der Visual Studio-IDE zum Sammeln von Daten für Apps, die auf dem Windows 8-Desktop oder unter Windows Server 2012 ausgeführt werden

Diese Funktionen und Optionen für die Profilerstellung werden nicht unterstützt, wenn Profile für Windows 8-Desktopanwendungen oder Windows Server 2012-Anwendungen mithilfe der Samplingmethode erstellt werden:

- Profilerstellung für Ebeneninteraktion. Das Sammeln von Daten für die Profilerstellung für die Ebeneninteraktion mithilfe der Instrumentation wird unterstützt.

- Samplingoptionen, z. B. das Festlegen des Samplingereignis- und -steuerungsintervalls oder das Sammeln zusätzlicher Leistungsindikatordaten.

## <a name="profile-from-the-command-line"></a>Profilen über die Befehlszeile

Sie verwenden zwei Befehlszeilentools, um Profilerstellungsdaten auf Windows 8- und Windows Server 2012-Geräten zu erfassen, einschließlich Geräte, auf denen kein Visual Studio installiert ist:

|Toolname|Beschreibung|
|---------------|-----------------|
|[VSPerf](../profiling/vsperf.md)|Erfasst Profilerstellungsdaten von UWP-Apps und Beispielprofilerstellungsdaten von Windows 8-Desktopanwendungen und Windows Server 2012-Anwendungen.|
|[VSPerfCmd](../profiling/vsperfcmd.md)|Sammelt Instrumentations-, Parallelitäts- und Ebeneninteraktionsprofilerstellungsdaten von Apps, die unter Windows 8-Desktop oder Windows Server 2012 ausgeführt werden. Sammelt alle Arten von Profilerstellungsdaten von früheren Versionen von Windows.|

Beide Tools werden mit Visual Studio zur Verwendung auf dem lokalen Computer installiert.

Um Profile für Anwendungen auf Geräten zu erstellen, auf denen Visual Studio nicht installiert ist, führen Sie eines der folgenden Verfahren aus:

- Laden Sie die Tools als Teil der Remotetools für Visual Studio von der [MSDN-Website](http://go.microsoft.com/fwlink/?LinkID=219549)herunter.

- Kopieren Sie das Installationsprogramm für die eigenständigen Profilertools, und führen Sie es von Ihrem Visual Studio-Computer aus. Informationen zum Abrufen des Pfads zu den Profilerstellungstools finden Sie unter [Angeben des Pfads zu Befehlszeilentools](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Wählen Sie das Setupprogramm für das Betriebssystem (x86/x64) des Remotecomputers aus.

> [!NOTE]
> Um Profilerstellungsdaten für die Ebeneninteraktion (TIP-Daten) zu erfassen, müssen Sie den eigenständigen Profiler vom Visual Studio-Computer auf dem Remotecomputer installieren.

Diese Funktionen und Optionen für die Profilerstellung werden nicht unterstützt, wenn Profile für Windows 8- und Windows Server 2012-Anwendungen von der Befehlszeile erstellt werden:

- Erfassen von Daten von Windows 8- und Windows Server 2012-Web-Apps mithilfe des Samplingmodus mit [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md).

- Erfassen von Samplingdaten mit VsPerfCmd.exe.

- Samplingoptionen, z. B. das Festlegen des Samplingereignis- und -steuerungsintervalls oder das Sammeln zusätzlicher Leistungsindikatordaten.

## <a name="collect-tier-interaction-tip-data"></a>Sammeln von Ebeneninteraktionsdaten (TIP-Daten)

Die Profilerstellung für Ebeneninteraktion stellt weitere Informationen zu den Ausführungszeiten der Funktionen von Anwendungen mit mehreren Ebenen, die über ADO.NET-Dienste mit Datenbanken kommunizieren, bereit. Es werden nur Daten für synchrone Funktionsaufrufe gesammelt.

**Visual Studio-Editionen**

Profilerstellungsdaten für die Ebeneninteraktion können mit einer beliebigen Visual Studio-Edition erfasst werden. Allerdings können Profilerstellungsdaten für die Ebeneninteraktion nur in Visual Studio Enterprise angezeigt werden.

**Windows 8 und Windows Server 2012**

1. Um Ebeneninteraktionsdaten von Apps zu sammeln, die unter Windows 8 Desktop oder Windows Server 2012 ausgeführt werden, müssen Sie die Instrumentationsmethode verwenden.

2. Sie können Ebeneninteraktionsdaten nicht für UWP-Apps erfassen.

3. Sie können Ebeneninteraktionsdaten in alle Profilerstellungsmethoden einer anderen unterstützten Version von Windows einschließen.

**Leistungs-Assistent und Leistungs-Explorer**

Sie müssen die Ebeneninteraktions-Datensammlungsoption einer laufenden Profilerstellung vom Leistungs-Explorer hinzufügen. Sie müssen das Projekt, die ausführbare Datei oder die Website außerdem dem Zielknoten des Leistungs-Explorers hinzufügen. Siehe [Erfassen von Ebeneninteraktionsdaten](../profiling/collecting-tier-interaction-data.md).

**Sammeln von TIP-Daten auf einem Remotecomputer**

Um Ebeneninteraktionsdaten auf einem Remotecomputer zu sammeln, müssen Sie die Datei **vs\_profiler\_** _\<Plattform>_ **\_** _\<Sprache>_ **.exe** aus dem Ordner *%VSInstallDir%\Team Tools\Performance Tools\Setups* eines Visual Studio-Computers auf den Remotecomputer kopieren und dort installieren. Sie können nicht die Profilerstellungstools im Downloadpaket [Remotedebuggen](../debugger/remote-debugging.md) verwenden.

Sie können [VSPerfCmd](../profiling/vsperfcmd.md) oder [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md) verwenden, um die Profilerstellungsdaten zu erfassen.

**TIP-Berichte**

Ebeneninteraktionsdaten können nur in Visual Studio Enterprise angezeigt werden. Dateibasierte Ebeneninteraktionsberichte über [VSPerfReport](../profiling/vsperfreport.md) sind nicht verfügbar.

## <a name="see-also"></a>Siehe auch

[Leistungs-Explorer](../profiling/performance-explorer.md)
[Konfigurieren von Leistungssitzungen](../profiling/configuring-performance-sessions.md)
[Profilen über die Befehlszeile](../profiling/using-the-profiling-tools-from-the-command-line.md)