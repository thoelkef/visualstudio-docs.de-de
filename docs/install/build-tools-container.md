---
title: Installieren von Build Tools in einem Container | Microsoft-Dokumentation
ms.custom: 
ms.date: 10/18/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d5c038e2-e70d-411e-950c-8a54917b578a
author: heaths
ms.author: heaths
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 95f9c69ebca7dbdc7e576279b4e1ad3f17d2be25
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="install-build-tools-into-a-container"></a>Installieren von Build Tools in einem Container

Sie können Visual Studio Build Tools in einem Windows-Container installieren, um CI/CD-Workflows (Continuous Integration und Continuous Delivery) zu unterstützen. In diesem Artikel erfahren Sie, welche Docker-Konfigurationsänderungen erforderlich sind, sowie welche [Workloads und Komponenten](workload-component-id-vs-build-tools.md) Sie in einem Container installieren können.

[Container](https://www.docker.com/what-container) stellen eine hervorragende Möglichkeit dar, aus einem konsistenten Buildsystem ein Paket zu erstellen, welches Sie nicht nur in einer CI/CD-Serverumgebung, sondern auch in Entwicklungsumgebungen nutzen können. Sie können z.B. Ihren Quellcode in einen Container einbinden, der von einer benutzerdefinierten Umgebung erstellt werden soll, und parallel Visual Studio oder andere Tools verwenden, um Code zu schreiben. Wenn Ihr CI/CD-Workflow das gleiche Containerimage verwendet, können Sie sicher sein, dass Ihr Code konsistent erstellt wird. Sie können Container auch zum Erreichen von Runtime-Konsistenz nutzen, was bei Microservices üblich ist, die mithilfe eines Orchestrierungssystems mehrere Container nutzen. Dieser Aspekt wird in diesem Artikel jedoch nicht behandelt.

Wenn Sie Ihren Quellcode mithilfe von Visual Studio Build Tools nicht erstellen können, können Sie die gleichen Schritte auch auf andere Visual Studio-Produkte anwenden. Beachten Sie allerdings, dass Windows-Container keine interaktiven Benutzeroberflächen unterstützen und daher alle Befehle automatisiert werden müssen.

## <a name="overview"></a>Übersicht

Mithilfe von [Docker](https://www.docker.com/what-docker) erstellen Sie ein Image, auf Basis dessen Sie Container erstellen können, die Ihren Quellcode erstellen. Mithilfe der Dockerfile-Beispieldatei werden die neueste Version von Visual Studio Build Tools 2017 und einige andere nützliche Programme installiert, die häufig zum Erstellen von Quellcode verwendet werden. Sie können Ihre eigene Dockerfile-Datei dahingehend verändern, dass sie unter anderem andere Tools und Skripts zum Ausführen von Tests und zum Veröffentlichen von Buildausgaben einbezieht.

Wenn Sie Docker für Windows bereits installiert haben, können Sie direkt mit Schritt 3 weitermachen.

## <a name="step-1-enable-hyper-v"></a>Schritt 1. Aktivieren von Hyper-V

Hyper-V ist standardmäßig nicht aktiviert. Hyper-V muss aktiviert sein, damit Docker für Windows gestartet werden kann, da unter Windows 10 derzeit nur Hyper-V-Isolation unterstützt wird.

* [Hyper-V unter Windows 10 aktivieren](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v)
* [Hyper-V unter Windows Server 2016 aktivieren](https://docs.microsoft.com/windows-server/virtualization/hyper-v/get-started/install-the-hyper-v-role-on-windows-server)

> [!NOTE]
> Auf Ihrem Computer muss die Virtualisierung aktiviert sein. Diese ist in der Regel standardmäßig aktiviert. Wenn bei der Installation von Hyper-V jedoch ein Fehler auftritt, können Sie in der Dokumentation Ihres Betriebssystems nachlesen, wie Sie die Virtualisierung aktivieren.

## <a name="step-2-install-docker-for-windows"></a>Schritt 2 Installieren von Docker für Windows

Wenn Sie Windows 10 verwenden, können Sie die [Docker Community Edition für Windows](https://www.docker.com/docker-windows) herunterladen und installieren. Wenn Sie eine einzelne Installation vornehmen möchten, können Sie zum [Installieren der Docker Enterprise Edition für Windows Server 2016](https://docs.docker.com/engine/installation/windows/docker-ee) PowerShell in Verbindung mit Desired State Configuration (DSC) oder einem [Paketanbieter](https://docs.microsoft.com/virtualization/windowscontainers/deploy-containers/deploy-containers-on-server) verwenden.

## <a name="step-3-switch-to-windows-containers"></a>Schritt 3 Wechseln zu Windows-Containern

Da Sie Build Tools 2017 nur unter Windows installieren können, müssen Sie [auf Windows-Container umsteigen](https://docs.docker.com/docker-for-windows/#getting-started-with-windows-containers). Unter Windows 10 unterstützen Windows-Container nur [Hyper-V-Isolation](https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/hyperv-container), unter Windows Server 2016 dagegen sowohl Hyper-V-, als auch Prozessisolation.

## <a name="step-4-expand-maximum-container-disk-size"></a>Schritt 4. Erweitern der maximalen Datenträgergröße des Containers

Visual Studio Build Tools – und in größerem Umfang auch Visual Studio – erfordern viel Speicherplatz, da bei der Installation auch eine Vielzahl an Tools installiert wird. Obwohl der Paketcache durch die Dockerfile-Beispieldatei deaktiviert wird, muss die Größe, die Containerimages auf dem Datenträger haben dürfen, entsprechend des erforderlichen Speicherplatzes angepasst werden. Unter Windows können Sie derzeit nur die Datenträgergröße erhöhen, indem Sie die Docker-Konfiguration ändern.

**So gehen Sie unter Windows 10 vor**:

1. Klicken Sie in der Taskleiste mit der rechten Maustaste auf das Symbol [„Docker für Windows“](https://docs.docker.com/docker-for-windows/#docker-settings) und anschließend auf **Settings...** (Einstellungen...).
2. [Klicken Sie auf den Daemon](https://docs.docker.com/docker-for-windows/#docker-daemon)-Abschnitt.
3. [Schalten Sie die Schaltfläche **Basic**](https://docs.docker.com/docker-for-windows/#edit-the-daemon-configuration-file) auf **Erweitert** um.
4. Fügen Sie die folgende JSON-Array-Eigenschaft hinzu, um den Speicherplatz auf 120 GB zu erhöhen. Dann steht Build Tools auch bei erhöhtem Speicherplatzbedarf genug Speicherplatz zur Verfügung.

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

5. Klicken Sie auf **Übernehmen**.

**So gehen Sie unter Windows Server 2016 vor**:

1. Beenden Sie den Docker-Dienst:

   ```shell
   sc.exe stop docker
   ```

2. Bearbeiten Sie mithilfe einer Eingabeaufforderung mit erhöhten Rechten „%ProgramData%\Docker\config\daemon.json“ bzw. was Sie in der Datei `dockerd --config-file` festgelegt haben.
3. Fügen Sie die folgende JSON-Array-Eigenschaft hinzu, um den Speicherplatz auf 120 GB zu erhöhen. Dann steht Build Tools auch bei erhöhtem Speicherplatzbedarf genug Speicherplatz zur Verfügung.

   ```json
   {
     "storage-opts": [
       "size=120GB"
     ]
   }
   ```

   Diese Eigenschaft wird zu allen bereits vorhandenen Standardkonfigurationsdateien hinzugefügt.
4. Speichern und schließen Sie die Datei.
5. Starten Sie den Docker-Dienst:

   ```shell
   sc.exe start docker
   ```

## <a name="step-5-create-and-build-the-dockerfile"></a>Schritt 5. Erstellen und Kompilieren der Dockerfile-Datei

Sie müssen folgende Dockerfile-Beispieldatei auf dem Datenträger in einer neuen Datei speichern. Wenn Sie die Datei einfach „Dockerfile“ nennen, wird sie standardmäßig erkannt.

> [!NOTE]
> Diese Dockerfile-Beispieldatei kann lediglich bei älteren Windows SDKs nicht verwendet werden, die nicht in Containern installiert werden können. Bei älteren Releases schlägt der Buildbefehl fehl.

1. Öffnen Sie eine Eingabeaufforderung.
2. Erstellen Sie ein neues Verzeichnis (empfohlen):

   ```shell
   mkdir C:\BuildTools
   ```

3. Ändern Sie die Verzeichnisse auf dieses neue Verzeichnis:

   ```shell
   cd C:\BuildTools
   ```

3. Speichern Sie den folgenden Inhalt unter C:\BuildTools\Dockerfile.

   ```dockerfile
   # Use the latest Windows Server Core image.
   FROM microsoft/windowsservercore

   # Download useful tools to C:\Bin.
   ADD https://dist.nuget.org/win-x86-commandline/v4.1.0/nuget.exe C:\\Bin\\nuget.exe

   # Download the Build Tools bootstrapper outside of the PATH.
   ADD https://aka.ms/vs/15/release/vs_buildtools.exe C:\\TEMP\\vs_buildtools.exe

   # Add C:\Bin to PATH and install Build Tools excluding workloads and components with known issues.
   RUN setx /m PATH "%PATH%;C:\Bin" \
    && C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache --installPath C:\BuildTools --all \
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 \
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 \
       --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 \
       --remove Microsoft.VisualStudio.Component.Windows81SDK \
    || IF "%ERRORLEVEL%"=="3010" EXIT 0

   # Start developer command prompt with any other commands specified.
   ENTRYPOINT C:\BuildTools\Common7\Tools\VsDevCmd.bat &&

   # Default to PowerShell if no other command specified.
   CMD ["powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
   ```

4. Führen Sie den folgenden Befehl innerhalb jenes Verzeichnisses aus.

   ```shell
   docker build -t buildtools2017:latest -m 2GB .
   ```

   Dieser Befehl erstellt die Dockerfile-Datei im aktuellen Verzeichnis. Dies erfordert 2 GB an Arbeitsspeicher. Standardmäßig steht dafür 1 GB zur Verfügung. Dies ist jedoch zum Installieren einiger Workloads nicht ausreichend. Abhängig von Ihren Build-Anforderungen reicht dies möglicherweise dennoch aus.

   Das endgültige Image trägt die Markierung „buildtools2017:latest“, sodass Sie es problemlos als „buildtools2017“ in einem Container ausführen können, da das Tag „latest“ standardmäßig verwendet wird, wenn kein Tag angegeben wurde. Wenn Sie eine bestimmte Version von Visual Studio Build Tools 2017 in einem [komplexeren Szenario](advanced-build-tools-container.md) verwenden möchten, können Sie den Container stattdessen mit einer bestimmten Visual Studio-Buildnummer sowie dem Tag „latest“ markieren, damit die Container eine bestimmte Version konsistent verwenden.

## <a name="step-6-using-the-built-image"></a>Schritt 6. Verwenden des erstellten Images

Da Sie bereits ein Image erstellt haben, können Sie dieses nun in einem Container ausführen, um sowohl interaktive, als auch automatisierte Builds abzudecken. Im Beispiel wird die Developer-Eingabeaufforderung verwendet, damit Ihre PATH-Variable und andere Umgebungsvariablen bereits konfiguriert sind.

1. Öffnen Sie eine Eingabeaufforderung.
2. Führen Sie den Container aus, um eine PowerShell-Umgebung zu starten, in der alle Entwicklerumgebungsvariablen festgelegt sind:

   ```shell
   docker run -it buildtools2017
   ```

Wenn Sie dieses Image für Ihren CI/CD-Workflow verwenden möchten, können Sie es in Ihrer eigenen [Azure Container Registry](https://azure.microsoft.com/services/container-registry) oder in einer anderen internen [Docker-Registrierung](https://docs.docker.com/registry/deploying) veröffentlichen, damit die Server es nur abrufen müssen.

## <a name="get-support"></a>Support aufrufen
Manchmal kann etwas schiefgehen. Wenn bei der Installation von Visual Studio ein Fehler auftritt, lesen Sie den Artikel [Problembehandlung bei Visual Studio 2017-Installations- und -Upgradefehlern](troubleshooting-installation-issues.md). Wenn keiner der Schritte zur Problembehandlung hilfreich ist, können Sie uns per Livechat kontaktieren, um Hilfe bei der Installation zu erhalten (nur in englischer Sprache). Einzelheiten finden Sie auf der [Visual Studio-Supportseite](https://www.visualstudio.com/vs/support/#talktous).

Hier sind einige weitere Supportoptionen:
* Sie können uns über Produktprobleme mit dem Tool [Problem melden](../ide/how-to-report-a-problem-with-visual-studio-2017.md) informieren, das sowohl im Visual Studio-Installer als auch in der Visual Studio-IDE angezeigt wird.
* Sie können uns einen Produktvorschlag unter [UserVoice](https://visualstudio.uservoice.com/forums/121579) mitteilen.
* Sie können Probleme mit Produkten im Portal [Visual Studio Developer Community](https://developercommunity.visualstudio.com/) im Blick behalten, Fragen stellen und Antworten finden.
* Über die [Visual Studio-Unterhaltung in der Gitter-Community](https://gitter.im/Microsoft/VisualStudio) können Sie auch Kontakt zu uns oder zu anderen Visual Studio-Entwicklern aufnehmen.  (Diese Option erfordert ein [GitHub](https://github.com/)-Konto.)

## <a name="see-also"></a>Siehe auch

* [Erweitertes Beispiel für Container](advanced-build-tools-container.md)
* [Bekannte Probleme für Container](build-tools-container-issues.md)
* [Workload- und Komponenten-IDs in Visual Studio Build Tools 2017](workload-component-id-vs-build-tools.md)
