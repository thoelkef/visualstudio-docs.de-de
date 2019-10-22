---
title: 'Visual Studio-Containertools: Buildeinstellungen für Docker Compose'
author: ghogen
description: Übersicht über den Buildprozess für Containertools
ms.author: ghogen
ms.date: 08/12/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: 2178881c6ea0e597aef5e25074e3648162d3f6e9
ms.sourcegitcommit: 6ae0a289f1654dec63b412bfa22035511a2ef5ad
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71950640"
---
# <a name="docker-compose-build-properties"></a>Buildeigenschaften von Docker Compose

Die Eigenschaften zur Verwaltung einzelner Docker-Projekte sind unter [Buildeigenschaften von Containertools](container-msbuild-properties.md) beschrieben. Diese Eigenschaften können Sie anpassen. Zusätzlich können Sie auch festlegen, wie Visual Studio Docker-Projekte erstellt. Dazu legen Sie die Docker Compose-Eigenschaften fest, die MSBuild zur Erstellung der Projektmappe verwendet. Außerdem können Sie steuern, wie der Visual Studio-Debugger Ihre Docker Compose-Apps ausführt, indem Sie Dateibezeichnungen in Docker Compose-Konfigurationsdateien festlegen.

## <a name="how-to-set-the-msbuild-properties"></a>Festlegen der MSBuild-Eigenschaften

Den Wert einer Eigenschaft legen Sie in der Projektdatei fest. Sofern in der Tabelle im nächsten Abschnitt nicht anders angegeben, handelt es sich bei der Projektdatei für die Docker Compose-Eigenschaften um eine Datei mit der Erweiterung „.dcproj“. Angenommen, Sie möchten festlegen, dass zu Beginn des Debuggens der Browser gestartet wird. Die `DockerLaunchAction`-Eigenschaft in der DCPROJ-Projektdatei können Sie dann wie folgt festlegen:

```xml
<PropertyGroup>
   <DockerLaunchAction>LaunchBrowser</DockerLaunchAction>
</PropertyGroup>
```

Sie können die Eigenschaftseinstellung einem vorhandenen `PropertyGroup`-Element hinzufügen oder ein neues `PropertyGroup`-Element erstellen, falls noch keines vorhanden ist.

## <a name="docker-compose-msbuild-properties"></a>MSBuild-Eigenschaften für Docker Compose

In der folgenden Tabelle werden die MSBuild-Eigenschaften aufgeführt, die für Docker Compose-Projekte verfügbar sind.

| Name der Eigenschaft | Speicherort | BESCHREIBUNG | Standardwert  |
|---------------|----------|-------------|----------------|
|DockerComposeBuildArguments|dcproj|Legt die zusätzlichen Parameter fest, die dem Befehl `docker-compose build` übergeben werden sollen. Beispiel: `--parallel --pull` |
|DockerComposeDownArguments|dcproj|Legt die zusätzlichen Parameter fest, die dem Befehl `docker-compose down` übergeben werden sollen. Beispiel: `--timeout 500`|-|  
|DockerComposeProjectPath|csproj oder vbproj|Der relative Pfad zur Docker Compose-Projektdatei (mit der DCPROJ-Erweiterung). Legen Sie diese Eigenschaft fest, wenn Sie das Dienstprojekt veröffentlichen, damit die zugeordneten Imagebuildeinstellungen in der Datei „docker-compose.yml“ gefunden werden.|-|
|DockerComposeUpArguments|dcproj|Legt die zusätzlichen Parameter fest, die dem Befehl `docker-compose up` übergeben werden sollen. Beispiel: `--timeout 500`|-|
|DockerLaunchAction| dcproj | Legt die Startaktion fest, die beim Drücken von F5 oder STRG+F5 ausgeführt werden soll.  Zulässige Werte sind None, LaunchBrowser und LaunchWCFTestClient.|Keine|
|DockerLaunchBrowser| dcproj | Legt fest, ob der Browser gestartet werden soll. Wird ignoriert, wenn DockerLaunchAction festgelegt wird. | False |
|DockerServiceName| dcproj|Wenn DockerLaunchAction oder DockerLaunchBrowser festgelegt wird, ist DockerServiceName der Name des Diensts, der gestartet werden soll.  Da eine Docker Compose-Datei auf mehrere Projekte verweisen kann, können Sie mit dieser Eigenschaft festlegen, welches Projekt gestartet werden soll.|-|
|DockerServiceUrl| dcproj | Die URL, die beim Start des Browsers verwendet werden soll.  Gültige Ersetzungstoken sind „{ServiceIPAddress}“, „{ServicePort}“ und „{Scheme}“.  Beispiel: {Scheme}://{ServiceIPAddress}:{ServicePort}.|-|
|DockerTargetOS| dcproj | Das Zielbetriebssystem, das beim Erstellen des Docker-Images verwendet wird.|-|

> [!NOTE]
> DockerComposeBuildArguments, DockerComposeDownArguments und DockerComposeUpArguments sind neu in Visual Studio 2019 Version 16.3.

## <a name="docker-compose-file-labels"></a>Docker Compose-Dateibezeichnungen

Sie können bestimmte Einstellungen auch überschreiben, indem Sie eine Datei mit dem Namen *docker-compose.vs.debug.yml* (für die **Debugkonfiguration**) oder *docker-compose.vs.release.yml* (für die **Releasekonfiguration**) im selben Verzeichnis wie die Datei *docker-compose.yml* platzieren.  In dieser Datei können Sie Einstellungen wie folgt festlegen:

```yml
services:
  webapplication1:
    labels:
      com.microsoft.visualstudio.debuggee.workingdirectory: "C:\\my_app_folder"
```

Setzen Sie wie im vorherigen Beispiel die Werte in doppelte Anführungszeichen, und verwenden Sie den umgekehrten Schrägstrich als Escapezeichen für umgekehrte Schrägstriche in Pfaden.

|Bezeichnungsname|BESCHREIBUNG|
|----------|-----------|
|com.microsoft.visualstudio.debuggee.arguments|Die Argumente, die zu Beginn des Debuggens dem Programm übergeben werden. Bei .NET Core-Apps sind diese Argumente in der Regel zusätzliche Suchpfade für NuGet-Pakete, auf die der Pfad zur Ausgabeassembly des Projekts folgt.|
|com.microsoft.visualstudio.debuggee.killprogram|Mit diesem Befehl wird ggf. das Programm der zu debuggenden Komponente beendet, das im Container ausgeführt wird.|
|com.microsoft.visualstudio.debuggee.program|Das Programm, das zu Beginn des Debuggens gestartet wird. Bei .NET Core-Apps ist für diese Einstellung in der Regel **dotnet** festgelegt.|
|com.microsoft.visualstudio.debuggee.workingdirectory|Das Verzeichnis, das zu Beginn des Debuggens als Startverzeichnis verwendet wird. Bei Linux-Containern ist für diese Einstellung üblicherweise */app* festgelegt, bei Windows-Containern *C:\app*.|

## <a name="next-steps"></a>Nächste Schritte

Weitere allgemeine Informationen zu MSBuild-Eigenschaften finden Sie unter [MSBuild-Eigenschaften](../msbuild/msbuild-properties.md).

## <a name="see-also"></a>Siehe auch

[Buildeigenschaften für Containertools](container-msbuild-properties.md)

[Starteinstellungen für Containertools](container-launch-settings.md)

[Reservierte und bekannte Eigenschaften für MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md)
