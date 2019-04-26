---
title: Installieren von Visual Studio Build Tools in einem Container
titleSuffix: ''
description: Erfahren Sie, wie Sie Visual Studio Build Tools in einem Windows-Container installieren können, um CI/CD-Workflows (Continuous Integration und Continuous Delivery) zu unterstützen.
ms.date: 04/18/2018
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: d5c038e2-e70d-411e-950c-8a54917b578a
author: heaths
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: cd2294d3018aba3d2e7ff8a0c0737b32a05214c0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62974253"
---
# <a name="install-build-tools-into-a-container"></a>Installieren von Build Tools in einem Container

Sie können Visual Studio Build Tools in einem Windows-Container installieren, um CI/CD-Workflows (Continuous Integration und Continuous Delivery) zu unterstützen. In diesem Artikel erfahren Sie, welche Docker-Konfigurationsänderungen erforderlich sind, sowie welche [Workloads und Komponenten](workload-component-id-vs-build-tools.md) Sie in einem Container installieren können.

[Container](https://www.docker.com/what-container) stellen eine hervorragende Möglichkeit dar, aus einem konsistenten Buildsystem ein Paket zu erstellen, welches Sie nicht nur in einer CI/CD-Serverumgebung, sondern auch in Entwicklungsumgebungen nutzen können. Sie können z.B. Ihren Quellcode in einen Container einbinden, der von einer benutzerdefinierten Umgebung erstellt werden soll, und parallel Visual Studio oder andere Tools verwenden, um Code zu schreiben. Wenn Ihr CI/CD-Workflow das gleiche Containerimage verwendet, können Sie sicher sein, dass Ihr Code konsistent erstellt wird. Sie können Container auch zum Erreichen von Runtime-Konsistenz verwenden, was bei Microservices üblich ist, die mithilfe eines Orchestrierungssystems mehrere Container nutzen. Dieser Aspekt wird in diesem Artikel jedoch nicht behandelt.

Wenn Sie Ihren Quellcode mithilfe von Visual Studio Build Tools nicht erstellen können, können Sie die gleichen Schritte auch auf andere Visual Studio-Produkte anwenden. Beachten Sie allerdings, dass Windows-Container keine interaktiven Benutzeroberflächen unterstützen und daher alle Befehle automatisiert werden müssen.

## <a name="overview"></a>Übersicht

Mithilfe von [Docker](https://www.docker.com/what-docker) erstellen Sie ein Image, auf Basis dessen Sie Container erstellen können, die Ihren Quellcode erstellen. Mithilfe der Dockerfile-Beispieldatei werden die neueste Version von Visual Studio Build Tools und einige andere nützliche Programme installiert, die häufig zum Erstellen von Quellcode verwendet werden. Sie können Ihre eigene Dockerfile-Datei dahingehend verändern, dass sie unter anderem andere Tools und Skripts zum Ausführen von Tests und zum Veröffentlichen von Buildausgaben einbezieht.

Wenn Sie Docker für Windows bereits installiert haben, können Sie direkt mit Schritt 3 weitermachen.

## <a name="step-1-enable-hyper-v"></a>Schritt 1. Aktivieren von Hyper-V

Hyper-V ist standardmäßig nicht aktiviert. Hyper-V muss aktiviert sein, damit Docker für Windows gestartet werden kann, da unter Windows 10 derzeit nur Hyper-V-Isolation unterstützt wird.

* [Hyper-V unter Windows 10 aktivieren](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v)
* [Hyper-V unter Windows Server 2016 aktivieren](https://docs.microsoft.com/windows-server/virtualization/hyper-v/get-started/install-the-hyper-v-role-on-windows-server)

> [!NOTE]
> Auf Ihrem Computer muss die Virtualisierung aktiviert sein. Diese ist in der Regel standardmäßig aktiviert. Wenn bei der Installation von Hyper-V jedoch ein Fehler auftritt, können Sie in der Dokumentation Ihres Betriebssystems nachlesen, wie Sie die Virtualisierung aktivieren.

## <a name="step-2-install-docker-for-windows"></a>Schritt 2 Installieren von Docker für Windows

Wenn Sie Windows 10 verwenden, können Sie die [Docker Community Edition](https://docs.docker.com/docker-for-windows/install) herunterladen und installieren. Wenn Sie Windows Server 2016 verwenden, führen Sie die Anweisungen unter [instructions to install Docker Enterprise Edition (Anweisungen zur Installation von Docker Enterprise Edition)](https://docs.docker.com/install/windows/docker-ee) aus.

## <a name="step-3-switch-to-windows-containers"></a>Schritt 3 Wechseln zu Windows-Containern

Da Sie Build Tools nur unter Windows installieren können, müssen Sie [auf Windows-Container umsteigen](https://docs.docker.com/docker-for-windows/#getting-started-with-windows-containers). Unter Windows 10 unterstützen Windows-Container nur [Hyper-V-Isolation](https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/hyperv-container), unter Windows Server 2016 dagegen sowohl Hyper-V-, als auch Prozessisolation.

## <a name="step-4-expand-maximum-container-disk-size"></a>Schritt 4. Erweitern der maximalen Datenträgergröße des Containers

Visual Studio Build Tools – und in größerem Umfang auch Visual Studio – erfordern viel Speicherplatz, da bei der Installation auch eine Vielzahl an Tools installiert wird. Obwohl der Paketcache durch die Dockerfile-Beispieldatei deaktiviert wird, muss die Größe, die Containerimages auf dem Datenträger haben dürfen, entsprechend des erforderlichen Speicherplatzes angepasst werden. Unter Windows können Sie derzeit nur die Datenträgergröße erhöhen, indem Sie die Docker-Konfiguration ändern.

**So gehen Sie unter Windows 10 vor**:

1. [Klicken Sie in der Taskleiste mit der rechten Maustaste auf das Symbol „Docker für Windows“](https://docs.docker.com/docker-for-windows/#docker-settings) und anschließend auf **Einstellungen**.

1. [Klicken Sie auf den Daemon](https://docs.docker.com/docker-for-windows/#docker-daemon)-Abschnitt.

1. [Schalten Sie die Schaltfläche **Basic**](https://docs.docker.com/docker-for-windows/#edit-the-daemon-configuration-file) auf **Erweitert** um.

1. Fügen Sie die folgende JSON-Array-Eigenschaft hinzu, um den Speicherplatz auf 120 GB zu erhöhen. Dann steht Build Tools auch bei erhöhtem Speicherplatzbedarf genug Speicherplatz zur Verfügung.

   ```json
   {
     "storage-opts": [
       "size=120GB"
     ]
   }
   ```

   Diese Eigenschaft wird zu allen bereits vorhandenen Standardkonfigurationsdateien hinzugefügt. Wenn diese Änderungen beispielsweise auf die Daemon-Standardkonfigurationsdatei angewendet wurden, sollte Ihnen jetzt Folgendes angezeigt werden:

   ```json
   {
     "registry-mirrors": [],
     "insecure-registries": [],
     "debug": true,
     "experimental": true,
     "storage-opts": [
       "size=120GB"
     ]
   }
   ```

1. Klicken Sie auf **Übernehmen**.

**So gehen Sie unter Windows Server 2016 vor**:

1. Beenden Sie den Docker-Dienst:

   ```shell
   sc.exe stop docker
   ```

1. Bearbeiten Sie mithilfe einer Eingabeaufforderung mit erhöhten Rechten „%ProgramData%\Docker\config\daemon.json“ bzw. was Sie in der Datei `dockerd --config-file` festgelegt haben.

1. Fügen Sie die folgende JSON-Array-Eigenschaft hinzu, um den Speicherplatz auf 120 GB zu erhöhen. Dann steht Build Tools auch bei erhöhtem Speicherplatzbedarf genug Speicherplatz zur Verfügung.

   ```json
   {
     "storage-opts": [
       "size=120GB"
     ]
   }
   ```

   Diese Eigenschaft wird zu allen bereits vorhandenen Standardkonfigurationsdateien hinzugefügt.
 
1. Speichern und schließen Sie die Datei.

1. Starten Sie den Docker-Dienst:

   ```shell
   sc.exe start docker
   ```

## <a name="step-5-create-and-build-the-dockerfile"></a>Schritt 5. Erstellen und Kompilieren der Dockerfile-Datei

Speichern Sie die folgende Dockerfile-Beispieldatei in einer neuen Datei auf Ihrem Datenträger. Wenn Sie die Datei einfach „Dockerfile“ nennen, wird sie standardmäßig erkannt.

> [!WARNING]
> Diese Dockerfile-Beispieldatei kann lediglich bei älteren Windows SDKs nicht verwendet werden, die nicht in Containern installiert werden können. Bei älteren Releases schlägt der Buildbefehl fehl.

1. Öffnen Sie eine Eingabeaufforderung.

1. Erstellen Sie ein neues Verzeichnis (empfohlen):

   ```shell
   mkdir C:\BuildTools
   ```

1. Ändern Sie die Verzeichnisse auf dieses neue Verzeichnis:

   ```shell
   cd C:\BuildTools
   ```

1. Speichern Sie den folgenden Inhalt unter C:\BuildTools\Dockerfile.
 
   ::: moniker range="vs-2017"

   ```dockerfile
   # escape=`

   # Use the latest Windows Server Core image with .NET Framework 4.7.1.
   FROM microsoft/dotnet-framework:4.7.1

   # Restore the default Windows shell for correct batch processing.
   SHELL ["cmd", "/S", "/C"]

   # Download the Build Tools bootstrapper.
   ADD https://aka.ms/vs/15/release/vs_buildtools.exe C:\TEMP\vs_buildtools.exe

   # Install Build Tools excluding workloads and components with known issues.
   RUN C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache `
       --installPath C:\BuildTools `
       --all `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
       --remove Microsoft.VisualStudio.Component.Windows81SDK `
    || IF "%ERRORLEVEL%"=="3010" EXIT 0

   # Start developer command prompt with any other commands specified.
   ENTRYPOINT C:\BuildTools\Common7\Tools\VsDevCmd.bat &&

   # Default to PowerShell if no other command specified.
   CMD ["powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
   ```

   > [!WARNING]
   > Wenn Sie Ihr Image direkt auf der Grundlage von microsoft/windowsservercore erstellen, wird .NET Framework möglicherweise nicht ordnungsgemäß installiert, ohne dass ein Installationsfehler ausgegeben wird. Es kann sein, dass verwalteter Code nach Abschluss der Installation nicht ausgeführt wird. Erstellen Sie Ihr Image stattdessen auf der Grundlage von [microsoft/dotnet-framework:4.7.1](https://hub.docker.com/r/microsoft/dotnet-framework) oder höher. Beachten Sie außerdem, dass Images der Version 4.7.1 oder höher ggf. PowerShell als Standard-`SHELL` verwenden, wodurch die Anweisungen `RUN` und `ENTRYPOINT` fehlschlagen.
   >
   > Visual Studio 2017 Version 15.8 und früher (alle Produkte) werden unter mcr\.microsoft\.com\/windows\/servercore:1809 oder höher nicht ordnungsgemäß installiert. Es wird keine Fehlermeldung angezeigt.
   >
   > Weitere Informationen finden Sie unten unter [Bekannte Probleme bei Containern](build-tools-container-issues.md).

   ::: moniker-end

   ::: moniker range="vs-2019"

   ```dockerfile
   # escape=`

   # Use the latest Windows Server Core image with .NET Framework 4.7.1.
   FROM microsoft/dotnet-framework:4.7.1

   # Restore the default Windows shell for correct batch processing.
   SHELL ["cmd", "/S", "/C"]

   # Download the Build Tools bootstrapper.
   ADD https://aka.ms/vs/16/release/vs_buildtools.exe C:\TEMP\vs_buildtools.exe

   # Install Build Tools excluding workloads and components with known issues.
   RUN C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache `
       --installPath C:\BuildTools `
       --all `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
       --remove Microsoft.VisualStudio.Component.Windows81SDK `
    || IF "%ERRORLEVEL%"=="3010" EXIT 0

   # Start developer command prompt with any other commands specified.
   ENTRYPOINT C:\BuildTools\Common7\Tools\VsDevCmd.bat &&

   # Default to PowerShell if no other command specified.
   CMD ["powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
   ```

   > [!WARNING]
   > Wenn Sie Ihr Image direkt auf der Grundlage von microsoft/windowsservercore erstellen, wird .NET Framework möglicherweise nicht ordnungsgemäß installiert, ohne dass ein Installationsfehler ausgegeben wird. Es kann sein, dass verwalteter Code nach Abschluss der Installation nicht ausgeführt wird. Erstellen Sie Ihr Image stattdessen auf der Grundlage von [microsoft/dotnet-framework:4.7.1](https://hub.docker.com/r/microsoft/dotnet-framework) oder höher. Beachten Sie außerdem, dass Images der Version 4.7.1 oder höher ggf. PowerShell als Standard-`SHELL` verwenden, wodurch die Anweisungen `RUN` und `ENTRYPOINT` fehlschlagen.
   >
   > Weitere Informationen finden Sie unten unter [Bekannte Probleme bei Containern](build-tools-container-issues.md).

   ::: moniker-end

1. Führen Sie den folgenden Befehl innerhalb jenes Verzeichnisses aus.

   ::: moniker range="vs-2017"

   ```shell
   docker build -t buildtools2017:latest -m 2GB .
   ```

   Dieser Befehl erstellt die Dockerfile-Datei im aktuellen Verzeichnis. Dies erfordert 2 GB an Arbeitsspeicher. Standardmäßig steht dafür 1 GB zur Verfügung. Dies ist jedoch zum Installieren einiger Workloads nicht ausreichend. Abhängig von Ihren Buildanforderungen reicht dies möglicherweise dennoch aus.

   Das endgültige Image trägt die Markierung „buildtools2017:latest“, sodass Sie es problemlos als „buildtools2017“ in einem Container ausführen können, da das Tag „latest“ standardmäßig verwendet wird, wenn kein Tag angegeben wurde. Wenn Sie eine bestimmte Version von Visual Studio Build Tools 2017 in einem [komplexeren Szenario](advanced-build-tools-container.md) verwenden möchten, können Sie den Container stattdessen mit einer bestimmten Visual Studio-Buildnummer sowie dem Tag „latest“ markieren, damit die Container eine bestimmte Version konsistent verwenden.

   ::: moniker-end

   ::: moniker range="vs-2019"

   ```shell
   docker build -t buildtools2019:latest -m 2GB .
   ```

   Dieser Befehl erstellt die Dockerfile-Datei im aktuellen Verzeichnis. Dies erfordert 2 GB an Arbeitsspeicher. Standardmäßig steht dafür 1 GB zur Verfügung. Dies ist jedoch zum Installieren einiger Workloads nicht ausreichend. Abhängig von Ihren Buildanforderungen reicht dies möglicherweise dennoch aus.

   Das endgültige Image trägt die Markierung „buildtools2019:latest“, sodass Sie es problemlos als „buildtools2019“ in einem Container ausführen können, da das Tag „latest“ standardmäßig verwendet wird, wenn kein Tag angegeben wurde. Wenn Sie eine bestimmte Version von Visual Studio Build Tools 2019 in einem [komplexeren Szenario](advanced-build-tools-container.md) verwenden möchten, können Sie den Container stattdessen mit einer bestimmten Visual Studio-Buildnummer sowie dem Tag „latest“ markieren, damit die Container eine bestimmte Version konsistent verwenden.

   ::: moniker-end

## <a name="step-6-using-the-built-image"></a>Schritt 6. Verwenden des erstellten Images

Da Sie bereits ein Image erstellt haben, können Sie dieses nun in einem Container ausführen, um sowohl interaktive, als auch automatisierte Builds abzudecken. Im Beispiel wird die Developer-Eingabeaufforderung verwendet, damit Ihre PATH-Variable und andere Umgebungsvariablen bereits konfiguriert sind.

1. Öffnen Sie eine Eingabeaufforderung.

1. Führen Sie den Container aus, um eine PowerShell-Umgebung zu starten, in der alle Entwicklerumgebungsvariablen festgelegt sind:

   ::: moniker range="vs-2017"

   ```shell
   docker run -it buildtools2017
   ```

   ::: moniker-end

   ::: moniker range="vs-2019"

   ```shell
   docker run -it buildtools2019
   ```

   ::: moniker-end

Wenn Sie dieses Image für Ihren CI/CD-Workflow verwenden möchten, können Sie es in Ihrer eigenen [Azure Container Registry](https://azure.microsoft.com/services/container-registry) oder in einer anderen internen [Docker-Registrierung](https://docs.docker.com/registry/deploying) veröffentlichen, damit die Server es nur abrufen müssen.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Siehe auch

* [Erweitertes Beispiel für Container](advanced-build-tools-container.md)
* [Bekannte Probleme für Container](build-tools-container-issues.md)
* [Workload- und Komponenten-IDs in Visual Studio Build Tools](workload-component-id-vs-build-tools.md)
