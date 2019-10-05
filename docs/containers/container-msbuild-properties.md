---
title: 'Visual Studio-Containertools: Buildeigenschaften'
author: ghogen
description: Übersicht über den Buildprozess für Containertools
ms.author: ghogen
ms.date: 06/06/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: 4bc6cb4221d85bd43b98b2ac36c34c919937960b
ms.sourcegitcommit: 3cda0d58c5cf1985122b8977b33a171c7359f324
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/29/2019
ms.locfileid: "71126058"
---
# <a name="container-tools-build-properties"></a>Buildeigenschaften für Containertools

Sie können den Buildprozess für Ihre Containerprojekte in Visual Studio anpassen, indem Sie die Eigenschaften festlegen, die MSBuild zum Erstellen Ihres Projekts nutzt. Beispielsweise können Sie den Namen der Dockerfile ändern, Tags und Bezeichnungen für Ihre Images festlegen, zusätzliche an Docker-Befehle übergebene Argumente angeben und steuern, ob Visual Studio bestimmte Leistungsoptimierungen vornimmt, z. B. das Erstellen außerhalb der Containerumgebung. Sie können auch Debuggingeigenschaften wie den Namen der zu startenden ausführbaren Datei und die bereitzustellenden Befehlszeilenargumente festlegen.

Bearbeiten Sie die Projektdatei, um den Wert einer Eigenschaft festzulegen. Angenommen der Name Ihrer Dockerfile lautet *MyDockerfile*. Sie können die `DockerfileFile`-Eigenschaft dann wie folgt in der Projektdatei festlegen:

```xml
<PropertyGroup>
   <DockerfileFile>MyDockerfile</DockerfileFile>
</PropertyGroup>
```

Sie können die Eigenschaftseinstellung einem vorhandenen `PropertyGroup`-Element hinzufügen oder ein neues `PropertyGroup`-Element erstellen, falls noch keines vorhanden ist.

In der folgenden Tabelle werden die MSBuild-Eigenschaften aufgeführt, die für Containerprojekte verfügbar sind.

| Name der Eigenschaft | BESCHREIBUNG | Standardwert  |
|---------------|-------------|----------------|
| DockerfileFile | Beschreibt die standardmäßige Dockerfile, die zum Erstellen oder Ausführen des Containers für das Projekt verwendet wird. Hierfür kann auch ein Pfad angegeben werden. | Docker-Datei |
| DockerfileTag | Das Tag, das beim Erstellen des Docker-Images verwendet wird. Beim Debuggen wird „.dev“ an das Tag angehängt. | Der Assemblyname, nachdem nicht alphanumerische Zeichen gemäß der folgenden Regeln entfernt wurden: <br/> Wenn das resultierende Tag nur aus numerischen Zeichen besteht, wird „image“ als Präfix eingefügt (z. B. „image2314“). <br/> Wenn das resultierende Tag eine leere Zeichenfolge ist, wird „image“ als Tag verwendet. |
| DockerContext | Der Standardkontext, der beim Erstellen des Docker-Images verwendet wird. | Wird von Visual Studio festgelegt. |
| ContainerDevelopmentMode | Steuert, ob die Optimierung „build-on-host“ (Debugging im schnellen Modus) aktiviert ist.  Zulässige Werte sind: **Fast** (Schnell) und **Regular** (Normal). | Fast |
| DockerDefaultTargetOS | Das standardmäßige Zielbetriebssystem, das beim Erstellen des Docker-Images verwendet wird. | Wird von Visual Studio festgelegt. |
| DockerImageLabels | Die Standardbezeichnungen, die auf das Docker-Image angewendet werden. | com.microsoft.created-by=visual-studio;com.microsoft.visual-studio.project-name=$(MSBuildProjectName) |
| ContainerVsDbgPath | Der Pfad für den VSDBG-Debugger. | `%USERPROFILE%\vsdbg\vs2017u5` |
| DockerfileBuildArguments | Zusätzliche Argumente, die an den Docker-Buildbefehl übergeben werden. | Nicht zutreffend. |
| DockerfileRunArguments | Zusätzliche Argumente, die an den Docker-Ausführungsbefehl übergeben werden. | Nicht zutreffend. |
| DockerfileRunEnvironmentFiles | Durch Semikolons getrennte Liste von Umgebungsdateien, die während der Docker-Ausführung angewendet werden. | Nicht zutreffend. |
| DockerfileFastModeStage | Die Dockerfile-Phase (d. h. Ziel), die beim Erstellen des Images im Debugmodus verwendet werden soll. | Die erste Phase, die in der Dockerfile (Base) ermittelt wird. |
| DockerDebuggeeProgram | Beim Debuggen wird der Debugger aufgefordert, diese ausführbare Datei zu starten. | Bei .NET Core-Projekten: dotnet, bei .NET Framework-Projekten in ASP.NET: Nicht anwendbar (es wird immer IIS verwendet). |
| DockerDebuggeeArguments | Beim Debuggen wird der Debugger angewiesen, diese Argumente an die gestartete ausführbare Datei zu übergeben. | Nicht auf .NET Framework-Projekte in ASP.NET anwendbar. |
| DockerDebuggeeWorkingDirectory | Beim Debuggen wird der Debugger angewiesen, diesen Pfad als Arbeitsverzeichnis zu verwenden. | C:\app (Windows) oder /app (Linux). |
| DockerDebuggeeKillProgram | Dieser Befehl wird zum Beenden des in einem Container ausgeführten Prozess verwendet. | Nicht auf .NET Framework-Projekte in ASP.NET anwendbar. |

## <a name="next-steps"></a>Nächste Schritte

Weitere allgemeine Informationen zu MSBuild-Eigenschaften finden Sie unter [MSBuild-Eigenschaften](../msbuild/msbuild-properties.md).

## <a name="see-also"></a>Siehe auch

[Buildeigenschaften von Docker Compose](docker-compose-properties.md)

[Starteinstellungen für Containertools](container-launch-settings.md)

[Reservierte und bekannte Eigenschaften für MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md)
