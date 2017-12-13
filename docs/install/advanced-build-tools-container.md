---
title: "Erweitertes Beispiel für Container | Microsoft-Dokumentation"
ms.custom: 
ms.date: 10/18/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e03835db-a616-41e6-b339-92b41d0cfc70
author: heaths
ms.author: heaths
manager: ghogen
ms.openlocfilehash: 8ab92d3936306ac47a59df33b4a1131341b28d44
ms.sourcegitcommit: eb954434c34b4df6fd2264266381b23ce9e6204a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/22/2017
---
# <a name="advanced-example-for-containers"></a>Erweitertes Beispiel für Container

Die Docker-Beispieldatei in [Install Build Tools into a Container (Installieren von Build Tools in einem Container)](build-tools-container.md) verwendet immer das aktuelle microsoft/windowsservercore-Image und den aktuellen Visual Studio Build Tools 2017-Installer. Wenn Sie dieses Image in einer [Docker-Registrierung](https://azure.microsoft.com/services/container-registry) veröffentlichen, sodass andere dieses herunterladen können, kann das Image für viele Szenarios geeignet sein. In der Praxis ist es allerdings üblich, ein spezifisches Basisimage zu verwenden, spezifische Binärdateien herunterzuladen und spezifische Tools zu installieren.

Die folgende Docker-Beispieldatei verwendet ein spezifisches Versionstag des microsoft/windowsservercore-Images. Das Verwenden eines spezifischen Tags für ein Basisimage ist üblich und erleichtert es, daran zu denken, dass das Erstellen und Neuerstellen von Images immer die gleiche Grundlage hat.

> [!NOTE]
> Sie können Visual Studio nicht in microsoft/windowsservercore:10.0.14393.1593 installieren, da dort bekannte Probleme beim Starten des Installers in einem Container vorliegen. Weitere Informationen finden Sie unter [Bekannte Probleme](build-tools-container-issues.md).

Das Beispiel verwendet ebenfalls einen Build Tools 2017-Bootstrapper, der eine spezifische Version installiert, die zur selben Zeit wie der Bootstrapper erstellt wurde. Das Produkt kann weiterhin über den Releasekanal aktualisiert werden. Dies ist jedoch kein praxisnahes Szenario für Container, die Sie in der Regel neu erstellen würden. Wenn Sie die URLs für einen bestimmten Kanal abrufen möchten, können Sie diesen von https://aka.ms/vs/15/release/channel herunterladen, die JSON-Datei öffnen und die Bootstrapper-URLs überprüfen. Weitere Informationen finden Sie unter [Erstellen einer Netzwerkinstallation von Visual Studio](create-a-network-installation-of-visual-studio.md).

```dockerfile
# Use a specific tagged image. Tags can be changed, though that is unlikely for most images.
# You could also use the immutable tag @sha256:d841bd78721c74f9b88e2700f5f3c2d66b54cb855b8acb4ab2c627a76a46301d
FROM microsoft/windowsservercore:10.0.14393.1770

# Use PowerShell commands to download, validate hashes, etc.
SHELL ["powershell.exe", "-ExecutionPolicy", "Bypass", "-Command", "$ErrorActionPreference='Stop'; $ProgressPreference='SilentlyContinue'; $VerbosePreference = 'Continue';"]

# Download Build Tools 15.4.27004.2005 and other useful tools.
ENV VS_BUILDTOOLS_URI=https://aka.ms/vs/15/release/6e8971476/vs_buildtools.exe \
    VS_BUILDTOOLS_SHA256=D482171C7F2872B6B9D29B116257C6102DBE6ABA481FAE4983659E7BF67C0F88 \
    NUGET_URI=https://dist.nuget.org/win-x86-commandline/v4.1.0/nuget.exe \
    NUGET_SHA256=4C1DE9B026E0C4AB087302FF75240885742C0FAA62BD2554F913BBE1F6CB63A0

# Download tools to C:\Bin and install Build Tools excluding workloads and components with known issues.
RUN New-Item -Path C:\Bin, C:\TEMP -Type Directory | Out-Null; \
    [System.Environment]::SetEnvironmentVariable('PATH', "\"${env:PATH};C:\Bin\"", 'Machine'); \
    function Fetch ([string] $Uri, [string] $Path, [string] $Hash) { \
      Invoke-RestMethod -Uri $Uri -OutFile $Path; \
      if ($Hash -and ((Get-FileHash -Path $Path -Algorithm SHA256).Hash -ne $Hash)) { \
        throw "\"Download hash for '$Path' incorrect\""; \
      } \
    }; \
    Fetch -Uri $env:NUGET_URI -Path C:\Bin\nuget.exe -Hash $env:NUGET_SHA256; \
    Fetch -Uri $env:VS_BUILDTOOLS_URI -Path C:\TEMP\vs_buildtools.exe -Hash $env:VS_BUILDTOOLS_SHA256; \
    Fetch -Uri 'https://aka.ms/vscollect.exe' -Path C:\TEMP\collect.exe; \
    $p = Start-Process -Wait -PassThru -FilePath C:\TEMP\vs_buildtools.exe -ArgumentList '--quiet --wait --norestart --nocache --installPath C:\BuildTools --all --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 --remove Microsoft.VisualStudio.Component.Windows81SDK'; \
    if (($ret = $p.ExitCode) -and ($ret -ne 3010)) { C:\TEMP\collect.exe; throw ('Install failed with exit code 0x{0:x}' -f $ret) }

# Restore default shell for Windows containers.
SHELL ["cmd.exe", "/s", "/c"]

# Start developer command prompt with any other commands specified.
ENTRYPOINT C:\BuildTools\Common7\Tools\VsDevCmd.bat &&

# Default to PowerShell if no other command specified.
CMD ["powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
```

Dieses Beispiel lädt spezifische Tools herunter und überprüft, dass die Hashwerte übereinstimmen. Es lädt ebenfalls die aktuellen Visual Studio- und .NET-Hilfsprogramme für die Protokollauflistung herunter, sodass Sie diese im Fall einer fehlgeschlagenen Installation auf Ihren Hostcomputer kopieren können, um den Fehler zu analysieren.

```shell
> docker build -t buildtools:15.4.27004.2005 -t buildtools:latest -m 2GB .
Sending build context to Docker daemon
...
Step 4/7 : RUN New-Item -Path C:\Bin, C:\TEMP -Type Directory | Out-Null; ...
 ---> Running in 4b62b4ce3a3c
Install failed with exit code 0x643
At line:1 char:1
+ throw ('Install failed with exit code 0x{0:x}' -f 1603)
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : OperationStopped: (Install failed with exit code 0x643:String) [], RuntimeException
    + FullyQualifiedErrorId : Install failed with exit code 0x643

> docker cp 4b62b4ce3a3c:C:\Users\ContainerAdministrator\AppData\Local\TEMP\vslogs.zip "%TEMP%\vslogs.zip"
```

Nachdem die Ausführung der letzten Zeile abgeschlossen ist, öffnen Sie „%TEMP%\vslogs.zip“ auf Ihrem Computer, oder melden Sie ein Problem auf der Website der [Entwicklercommunity](https://developercommunity.visualstudio.com).

## <a name="get-support"></a>Support aufrufen
Manchmal kann etwas schiefgehen. Wenn bei der Installation von Visual Studio ein Fehler auftritt, lesen Sie den Artikel [Problembehandlung bei Visual Studio 2017-Installations- und -Upgradefehlern](troubleshooting-installation-issues.md). Wenn keiner der Schritte zur Problembehandlung hilfreich ist, können Sie uns per Livechat kontaktieren, um Hilfe bei der Installation zu erhalten (nur in englischer Sprache). Einzelheiten finden Sie auf der [Visual Studio-Supportseite](https://www.visualstudio.com/vs/support/#talktous).

Hier sind einige weitere Supportoptionen:
* Sie können uns über Produktprobleme mit dem Tool [Problem melden](../ide/how-to-report-a-problem-with-visual-studio-2017.md) informieren, das sowohl im Visual Studio-Installer als auch in der Visual Studio-IDE angezeigt wird.
* Sie können uns einen Produktvorschlag unter [UserVoice](https://visualstudio.uservoice.com/forums/121579) mitteilen.
* Sie können Probleme mit Produkten im Portal [Visual Studio Developer Community](https://developercommunity.visualstudio.com/) im Blick behalten, Fragen stellen und Antworten finden.
* Über die [Visual Studio-Unterhaltung in der Gitter-Community](https://gitter.im/Microsoft/VisualStudio) können Sie auch Kontakt zu uns oder zu anderen Visual Studio-Entwicklern aufnehmen.  (Diese Option erfordert ein [GitHub](https://github.com/)-Konto).

## <a name="see-also"></a>Siehe auch
* [Installieren von Build Tools in einem Container](build-tools-container.md)
* [Bekannte Probleme für Container](build-tools-container-issues.md)
