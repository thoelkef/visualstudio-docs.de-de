---
title: Messen der CPU-Auslastung über die Befehlszeile
description: Messen Sie die CPU-Auslastung in Ihrer Anwendung über die Befehlszeile.
ms.custom: ''
ms.date: 02/19/2019
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
ms.openlocfilehash: 87bf0c236f34e753866ea114dfc7f45e8f16a979
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62972416"
---
# <a name="measure-application-performance-from-the-command-line"></a>Messen der Anwendungsleistung über die Befehlszeile

Über die Befehlszeilentools können Sie Leistungsinformationen zu einer Anwendung sammeln.

In dem Beispiel, das in diesem Artikel beschrieben wird, sammeln Sie Leistungsinformationen zum Microsoft Notepad. Dieselbe Methode kann aber auch verwendet werden, um jeden anderen Prozess zu profilen.

## <a name="prerequisites"></a>Erforderliche Komponenten

* Visual Studio 2019 Preview 3 oder höhere Versionen

* Kenntnisse im Umgang mit Befehlszeilentools

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

## <a name="config_file"></a> Agent-Konfigurationsdateien

Sammlungs-Agents sind austauschbare Komponenten, die verschiedene Datentypen sammeln, je nachdem, was gemessen werden soll.

Der Bequemlichkeit halber können Sie diese Informationen in einer Agent-Konfigurationsdatei speichern. Die Konfigurationsdatei ist eine *.json*-Datei, die mindestens den Namen der *.dll*-Datei und deren COM-CLSID enthält. Hier sehen Sie die Beispielkonfigurationsdateien, die Sie im folgenden Ordner finden können:

```<Visual Studio installation folder>\2019\Preview\Team Tools\DiagnosticsHub\Collector\AgentConfigs\```

* Konfigurationen für die CPU-Nutzung (CpuUsage) (Standard/Hoch/Niedrig). Dies entspricht den Daten, die für das Profilerstellungstool für die [CPU-Auslastung](../profiling/cpu-usage.md) gesammelt wurden.
* DotNetObjectAlloc-Konfigurationen (Standard/Niedrig). Dies entspricht den Daten, die für das [.NET-Objektzuteilungstool](https://devblogs.microsoft.com/visualstudio/visual-studio-2017-version-15-8-preview-3/#tooling) gesammelt wurden.

Die Konfigurationen „Standard“, „Niedrig“ und „Hoch“ beziehen sich auf die Stichprobenentnahmerate. So bedeutet „Niedrig“ z.B. 100 Stichproben pro Sekunde, und „Hoch“ 4000 Stichproben pro Sekunde.

Damit das *VSDiagnostics.exe*-Tool mit einem Sammlungs-Agent zusammenarbeitet, werden für den entsprechenden Agent sowohl eine DLL als auch eine COM-CLSID benötigt, und für den Agent gibt es möglicherweise auch zusätzliche Konfigurationsoptionen. Wenn Sie einen Agent ohne Konfigurationsdatei verwenden, verwenden Sie das Format im folgenden Befehl.

```cmd
VSDiagnostics.exe start <id> /attach:<pid> /loadAgent:<agentCLSID>;<agentName>[;<config>]
```

## <a name="permissions"></a>Berechtigungen

Um eine Anwendung zu profilen, die erweiterte Berechtigungen benötigt, müssen Sie eine Eingabeaufforderung mit erhöhten Rechten verwenden.
