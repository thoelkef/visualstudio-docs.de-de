---
title: Erweitertes Beispiel für Container
description: ''
ms.custom: ''
ms.date: 04/18/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: e03835db-a616-41e6-b339-92b41d0cfc70
author: heaths
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c941928495dc39dc6b6ecbe9600f39dad969fec2
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/20/2018
ms.locfileid: "31621144"
---
# <a name="advanced-example-for-containers"></a>Erweitertes Beispiel für Container

Die Docker-Beispieldatei unter [Installieren von Build Tools in einem Container](build-tools-container.md) verwendet immer das [microsoft/dotnet-framework:4.7.1](https://hub.docker.com/r/microsoft/dotnet-framework)-Image, das auf dem aktuellen microsoft/windowsservercore-Image und dem aktuellen Visual Studio Build Tools 2017-Installer basiert. Wenn Sie dieses Image in einer [Docker-Registrierung](https://azure.microsoft.com/services/container-registry) veröffentlichen, sodass andere dieses herunterladen können, kann das Image für viele Szenarios geeignet sein. In der Praxis ist es allerdings üblich, ein spezifisches Basisimage zu verwenden, spezifische Binärdateien herunterzuladen und spezifische Tools zu installieren.

Die folgende Docker-Beispieldatei verwendet ein spezifisches Versionstag des microsoft/dotnet-framework-Images. Das Verwenden eines spezifischen Tags für ein Basisimage ist üblich und erleichtert es, daran zu denken, dass das Erstellen und Neuerstellen von Images immer die gleiche Grundlage hat.

> [!NOTE]
> Sie können Visual Studio nicht in microsoft/windowsservercore:10.0.14393.1593 oder in einem auf microsoft/windowsservercore:10.0.14393.1593 basierenden Image installieren, da dort bekannte Probleme beim Starten des Installers in einem Container entstehen können. Weitere Informationen finden Sie unter [Bekannte Probleme](build-tools-container-issues.md).

Über das untenstehende Beispiel wird das neuste Build Tools 2017-Release heruntergeladen. Wenn Sie eine ältere Build Tools-Version verwenden möchten, können Sie die Installation in einem Container zu einem späteren Zeitpunkt durchführen. Zuerst müssen Sie jedoch ein Layout [erstellen](create-an-offline-installation-of-visual-studio.md) und [verwalten](update-a-network-installation-of-visual-studio.md).

## <a name="install-script"></a>Installieren eines Skripts

Erstellen Sie im Arbeitsverzeichnis ein Batchskript mit dem Namen „Install.cmd“ und dem folgenden Inhalt, um Protokolle zu erfassen, wenn bei der Installation ein Fehler auftritt:

```shell
@if not defined _echo echo off
setlocal enabledelayedexpansion

call %*
if "%ERRORLEVEL%"=="3010" (
    exit /b 0
) else (
    if not "%ERRORLEVEL%"=="0" (
        set ERR=%ERRORLEVEL%
        call C:\TEMP\collect.exe -zip:C:\vslogs.zip

        exit /b !ERR!
    )
)
```

## <a name="dockerfile"></a>Docker-Datei

Erstellen Sie im Arbeitsverzeichnis die Docker-Datei mit dem folgenden Inhalt:

```dockerfile
# escape=`

# Use a specific tagged image. Tags can be changed, though that is unlikely for most images.
# You could also use the immutable tag @sha256:1a66e2b5f3a5b8b98ac703a8bfd4902ae60d307ed9842978df40dbc04ac86b1b
ARG FROM_IMAGE=microsoft/dotnet-framework:4.7.1-20180410-windowsservercore-1709
FROM ${FROM_IMAGE}

# Copy our Install script.
COPY Install.cmd C:\TEMP\

# Download collect.exe in case of an install failure.
ADD https://aka.ms/vscollect.exe C:\TEMP\collect.exe

# Use the latest release channel. For more control, specify the location of an internal layout.
ARG CHANNEL_URL=https://aka.ms/vs/15/release/channel
ADD ${CHANNEL_URL} C:\TEMP\VisualStudio.chman

# Download and install Build Tools excluding workloads and components with known issues.
ADD https://aka.ms/vs/15/release/vs_buildtools.exe C:\TEMP\vs_buildtools.exe
RUN C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache `
    --installPath C:\BuildTools `
    --channelUri C:\TEMP\VisualStudio.chman `
    --installChannelUri C:\TEMP\VisualStudio.chman `
    --all `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
    --remove Microsoft.VisualStudio.Component.Windows81SDK

# Start developer command prompt with any other commands specified.
ENTRYPOINT C:\BuildTools\Common7\Tools\VsDevCmd.bat &&

# Default to PowerShell if no other command specified.
CMD ["powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
```

Führen Sie den folgenden Befehl aus, um das Image im aktuellen Arbeitsverzeichnis zu erstellen:

```shell
docker build -t buildtools2017:15.6.27428.2037 -t buildtools2017:latest -m 2GB .
```

Sie können entweder eins der Argumente `FROM_IMAGE` und `CHANNEL_URL` oder beide Argumente gleichzeitig übergeben, indem Sie die Befehlszeilenoption `--build-arg` verwenden, um ein anderes Basisimage oder den Speicherort des internen Layouts anzugeben, wenn Sie ein bestimmtes Image verwalten möchten.

## <a name="diagnosing-install-failures"></a>Analysieren von Fehlern bei der Installation

Dieses Beispiel lädt spezifische Tools herunter und überprüft, dass die Hashwerte übereinstimmen. Es lädt ebenfalls die aktuellen Visual Studio- und .NET-Hilfsprogramme für die Protokollsammlung herunter, sodass Sie diese im Fall einer fehlgeschlagenen Installation auf Ihren Hostcomputer kopieren können, um den Fehler zu analysieren.

```shell
> docker build -t buildtools2017:15.6.27428.2037 -t buildtools2017:latest -m 2GB .
Sending build context to Docker daemon
...
Step 8/10 : RUN C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache ...
 ---> Running in 4b62b4ce3a3c
The command 'cmd /S /C C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe ...' returned a non-zero code: 1603

> docker cp 4b62b4ce3a3c:C:\vslogs.zip "%TEMP%\vslogs.zip"
```

Nachdem die Ausführung der letzten Zeile abgeschlossen ist, öffnen Sie „%TEMP%\vslogs.zip“ auf Ihrem Computer, oder melden Sie ein Problem auf der Website der [Entwicklercommunity](https://developercommunity.visualstudio.com).

## <a name="get-support"></a>Support aufrufen

Manchmal kann etwas schiefgehen. Wenn bei der Installation von Visual Studio ein Fehler auftritt, lesen Sie den Artikel [Problembehandlung bei der Visual Studio 2017-Installation und Upgradefehlern](troubleshooting-installation-issues.md). Wenn keiner der Schritte zur Problembehandlung hilfreich ist, können Sie uns per Livechat kontaktieren, um Hilfe bei der Installation zu erhalten (nur in englischer Sprache). Einzelheiten finden Sie auf der [Visual Studio-Supportseite](https://www.visualstudio.com/vs/support/#talktous).

Hier sind einige weitere Supportoptionen:

* Sie können uns über Produktprobleme mit dem Tool [Problem melden](../ide/how-to-report-a-problem-with-visual-studio-2017.md) informieren, das sowohl im Visual Studio-Installer als auch in der Visual Studio-IDE angezeigt wird.
* Sie können uns einen Produktvorschlag unter [UserVoice](https://visualstudio.uservoice.com/forums/121579) mitteilen.
* Sie können Probleme mit Produkten und Antworten in der [Visual Studio-Entwicklercommunity](https://developercommunity.visualstudio.com/) finden.
* Sie können auch über die [Visual Studio-Unterhaltung in der Gitter-Community](https://gitter.im/Microsoft/VisualStudio) Kontakt zu uns oder zu anderen Visual Studio-Entwicklern aufnehmen. (Diese Option erfordert ein [GitHub](https://github.com/)-Konto.)

## <a name="see-also"></a>Siehe auch

* [Installieren von Build Tools in einem Container](build-tools-container.md)
* [Bekannte Probleme für Container](build-tools-container-issues.md)
* [Workload- und Komponenten-IDs in Visual Studio Build Tools 2017](workload-component-id-vs-build-tools.md)
