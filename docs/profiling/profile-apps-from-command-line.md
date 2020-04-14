---
title: Messen der Leistung über die Befehlszeile
description: Messen Sie die CPU-Leistung und die Nutzung des verwalteten Speichers in Ihrer Anwendung über die Befehlszeile.
ms.custom: ''
ms.date: 02/21/2020
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools, command-line
- Diagnostics Tools, command-line
- CPU Usage, command-line
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: 18850a6e365988abd33b7e2e2a3972ba5cb0a91a
ms.sourcegitcommit: 9c1cecaff4d9955276eee7865b78d47679dd1e2a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/03/2020
ms.locfileid: "80638690"
---
# <a name="measure-application-performance-from-the-command-line"></a>Messen der Anwendungsleistung über die Befehlszeile

Über die Befehlszeilentools können Sie Leistungsinformationen zu einer Anwendung sammeln.

In dem Beispiel, das in diesem Artikel beschrieben wird, sammeln Sie Leistungsinformationen zum Microsoft Notepad. Dieselbe Methode kann aber auch verwendet werden, um jeden anderen Prozess zu profilen.

## <a name="prerequisites"></a>Voraussetzungen

* Visual Studio 2019 oder höher

* Kenntnisse im Umgang mit Befehlszeilentools

* Installieren Sie die [Leistungstools für Visual Studio](https://visualstudio.microsoft.com/downloads#performance-tools-for-visual-studio-2019) auf dem Remotecomputer, um Leistungsinformationen auf einem Remotecomputer zu erfassen, auf dem Visual Studio nicht installiert ist. Die Version der Tools muss mit Ihrer Version von Visual Studio übereinstimmen.

## <a name="collect-performance-data"></a>Sammeln von Leistungsdaten

Bei der Profilerstellung mithilfe der CLI-Diagnosetools von Visual Studio wird das Profilerstellungstool zusammen mit einem der Collector-Agenten an einen Prozess angefügt. Wenn Sie das Profilerstellungstool anfügen, beginnen Sie eine Diagnosesitzung, die solange Profilerstellungsdaten aufnimmt und speichert, bis das Tool beendet wird. Dann werden die Daten in eine *.diagsession*-Datei exportiert. Diese Datei können Sie dann in Visual Studio öffnen, um die Ergebnisse zu analysieren.

1. Starten Sie das Notepad, und öffnen Sie dann den Taskmanager, um seine Prozess-ID (PID) zu erhalten. Im Taskmanager finden Sie die PID in der Registerkarte **Details**.

1. Öffnen Sie eine Eingabeaufforderung, und wechseln Sie zum Verzeichnis mit dem ausführbaren Sammlungs-Agent, das sich normalerweise hier befindet:

   ```<Visual Studio installation folder>\2019\Preview\Team Tools\DiagnosticsHub\Collector\```

1. Starten Sie *VSDiagnostics.exe*, indem Sie den folgenden Befehl ausführen.

   ```cmd
   VSDiagnostics.exe start <id> /attach:<pid> /loadConfig:<configFile>
   ```

   Folgende Argumente müssen eingeschlossen werden:

   * \<*id*> Identifiziert die Sammlungssitzung. Die ID muss eine Zahl zwischen 1 und 255 sein.
   * \<*pid*>, Die PID des Prozesses, den Sie profilen möchten. Hier also die PID, die Sie in Schritt 1 abgerufen haben.
   * \<*configFile*>, Konfigurationsdatei des Sammlungs-Agents, den Sie starten möchten. Weitere Informationen finden Sie unter [Runtime Configuration Files (Konfigurationsdateien der Runtime)](#config_file).

1. Ändern Sie die Größe des Notepads, oder geben Sie etwas ein, damit einige aussagekräftige Profilerstellungsinformationen gesammelt werden können.

1. Halten Sie die Sammlungssitzung an, und senden Sie die Ausgabe an eine Datei, indem Sie den folgenden Befehl eingeben.

   ```cmd
   VSDiagnostics.exe stop <id> /output:<path to file>
   ```

1. Wechseln Sie zur Dateiausgabe des vorherigen Befehls, und öffnen Sie sie in Visual Studio, um die gesammelten Informationen zu untersuchen.

## <a name="agent-configuration-files"></a><a name="config_file"></a> Agent-Konfigurationsdateien

Sammlungs-Agents sind austauschbare Komponenten, die verschiedene Datentypen sammeln, je nachdem, was gemessen werden soll.

Der Bequemlichkeit halber können Sie diese Informationen in einer Agent-Konfigurationsdatei speichern. Die Konfigurationsdatei ist eine *.json*-Datei, die mindestens den Namen der *.dll*-Datei und deren COM-CLSID enthält. Hier sehen Sie die Beispielkonfigurationsdateien, die Sie im folgenden Ordner finden können:

```<Visual Studio installation folder>\2019\Preview\Team Tools\DiagnosticsHub\Collector\AgentConfigs\```

* Konfigurationen für die CPU-Nutzung (CpuUsage) (Standard/Hoch/Niedrig). Dies entspricht den Daten, die für das Profilerstellungstool für die [CPU-Auslastung](../profiling/cpu-usage.md) gesammelt wurden.
* DotNetObjectAlloc-Konfigurationen (Standard/Niedrig). Dies entspricht den Daten, die für das [.NET-Objektzuteilungstool](../profiling/dotnet-alloc-tool.md) gesammelt wurden.

Die Konfigurationen „Standard“, „Niedrig“ und „Hoch“ beziehen sich auf die Stichprobenentnahmerate. So bedeutet „Niedrig“ z.B. 100 Stichproben pro Sekunde, und „Hoch“ 4000 Stichproben pro Sekunde.

Damit das *VSDiagnostics.exe*-Tool mit einem Sammlungs-Agent zusammenarbeitet, werden für den entsprechenden Agent sowohl eine DLL als auch eine COM-CLSID benötigt, und für den Agent gibt es möglicherweise auch zusätzliche Konfigurationsoptionen. Wenn Sie einen Agent ohne Konfigurationsdatei verwenden, verwenden Sie das Format im folgenden Befehl.

```cmd
VSDiagnostics.exe start <id> /attach:<pid> /loadAgent:<agentCLSID>;<agentName>[;<config>]
```

## <a name="permissions"></a>Berechtigungen

Um eine Anwendung zu profilen, die erweiterte Berechtigungen benötigt, müssen Sie eine Eingabeaufforderung mit erhöhten Rechten verwenden.
