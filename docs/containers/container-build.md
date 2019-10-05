---
title: 'Visual Studio-Containertools: Buildübersicht'
author: ghogen
description: Übersicht über den Buildprozess für Containertools
ms.author: ghogen
ms.date: 06/06/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: edc4674e2468124ecb46b25a1411043ed4b66a2a
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253116"
---
# <a name="building-containerized-apps-using-visual-studio-or-the-command-line"></a>Erstellen von Container-Apps mithilfe von Visual Studio oder der Befehlszeile

Wenn Sie Projekte erstellen, müssen Sie wissen wie Visual Studio das Dockerfile für den Buildvorgang nutzt: ganz egal, ob Sie Visual Studio oder die Befehlszeile für Builds verwenden.  Aus Leistungsgründen führt Visual Studio einen speziellen Prozess für Container-Apps aus. Wenn Sie den Buildprozess durch die Bearbeitung des Dockerfile anpassen, ist es besonders wichtig, zu verstehen, wie Visual Studio Ihre Projekte erstellt.

Wenn Visual Studio ein Projekt erstellt, das keine Docker-Container verwendet, ruft die IDE MSBuild auf dem lokalen Computer auf und generiert die Ausgabedateien in einem Ordner (in der Regel `bin`) innerhalb Ihres lokalen Projektmappenordners. Bei einem Containerprojekt berücksichtigt der Buildprozess jedoch die Anweisungen des Dockerfile zum Erstellen der Container-App. Das von Visual Studio verwendete Dockerfile ist in mehrere Stages unterteilt. Dieser Prozess basiert auf den *Multistagebuilds* von Docker.

## <a name="multistage-build"></a>Multistagebuilds

Multistagebuilds sorgen für die effizientere Erstellung von Containern. Außerdem werden die Container damit kleiner, da sie nur die Komponenten enthalten, die Ihre App zur Laufzeit benötigt. Multistagebuilds werden für .NET Core-, nicht aber für .NET Framework-Projekte verwendet.

Durch einen Multistagebuild können Containerimages in Stages erstellt werden, die temporäre Images generieren. Sehen Sie sich als Beispiel ein typisches Dockerfile an, das von Visual Studio generiert wird. Die erste Stage ist `base`:

```
FROM mcr.microsoft.com/dotnet/core/aspnet:2.2-stretch-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443
```

In der ersten Dockerfile-Zeile wird das Nanoserver-Image der Microsoft-Containerregistrierung (mcr.microsoft.com) angegeben. Außerdem wird das temporäre Image `base` erstellt, das die Ports 80 und 443 verfügbar macht und das Arbeitsverzeichnis auf `/app` festlegt.

Die nächste Stage ist `build` und sieht wie folgt aus:

```
FROM mcr.microsoft.com/dotnet/core/sdk:2.2-stretch AS build
WORKDIR /src
COPY ["WebApplication43/WebApplication43.csproj", "WebApplication43/"]
RUN dotnet restore "WebApplication43/WebApplication43.csproj"
COPY . .
WORKDIR "/src/WebApplication43"
RUN dotnet build "WebApplication43.csproj" -c Release -o /app
```

Als Startpunkt für die Stage `build` wird offensichtlich ein anderes ursprüngliches Image aus der Registrierung verwendet (`sdk` anstelle von `aspnet`). „base“ wird hingegen nicht genutzt.  Das `sdk`-Image verfügt über alle Buildtools und ist aus diesem Grund deutlich größer als das Image „aspnet“, das nur Laufzeitkomponenten enthält. Der Grund für die Verwendung eines separaten Images wird deutlich, wenn Sie sich den Rest des Dockerfile ansehen:

```
FROM build AS publish
RUN dotnet publish "WebApplication43.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "WebApplication43.dll"]
```

Die letzte Stage beginnt erneut bei `base` und enthält `COPY --from=publish`, um die veröffentlichte Ausgabe in das finale Image zu kopieren. Durch diesen Prozess wird das finale Image deutlicher kleiner, da es nicht alle Buildtools enthalten muss, die im `sdk`-Image vorhanden waren.

## <a name="faster-builds-for-the-debug-configuration"></a>Schnellere Builds für die Debugkonfiguration

Visual Studio führt mehrere Optimierungen durch, um die Leistung des Buildprozesses für Containerprojekte zu erhöhen. Wenn Sie mit dem Debuggen beginnen (F5), wird ein zuvor erstelltes Image nach Möglichkeit wiederverwendet. Wenn Sie den vorherigen Container nicht wiederverwenden möchten, können Sie in Visual Studio die Befehle **Rebuild** (Neu erstellen) oder **Bereinigen** verwenden, um zu erzwingen, dass Visual Studio einen neuen Container verwendet.

Zur Verbesserung der Leistung werden während des Buildprozesses für Container-Apps nicht einfach die Schritte im Dockerfile ausgeführt. Ein Build in einem Container ist deutlich langsamer als ein Build auf einem lokalen Computer.  Wenn Sie also für den Build die **Debugkonfiguration** nutzen, erstellt Visual Studio Ihre Projekte auf dem lokalen Computer und gibt den Ausgabeordner dann für den Container frei, indem das Volume eingebunden wird. Ein Build mit dieser Optimierung wird auch als *Schnellmodusbuild* bezeichnet.

Im **Schnellmodus** ruft Visual Studio `docker build` mit einem Argument auf, das Docker anweist, nur die `base`-Stage zu erstellen.  Die restlichen Schritte führt Visual Studio durch, ohne den Inhalt des Dockerfile zu beachten. Wenn Sie das Dockerfile ändern, um beispielsweise die Containerumgebung anzupassen oder zusätzliche Abhängigkeiten zu installieren, sollten Sie die Änderungen in der ersten Stage ablegen.  Wenn benutzerdefinierte Schritte in den Stages `build`, `publish` und `final` des Dockerfile hinterlegt werden, werden diese nicht ausgeführt.

Diese Leistungsoptimierung wird nur durchgeführt, wenn Sie für den Build die **Debugkonfiguration** verwenden. In der **Releasekonfiguration** findet der Build wie im Dockerfile angegeben im Container statt.

Wenn Sie die Leistungsoptimierung deaktivieren und den Build wie im Dockerfile angegeben ausführen möchten, legen Sie die Eigenschaft **ContainerDevelopmentMode** in der Projektdatei wie folgt auf **Regular** fest:

```xml
<PropertyGroup>
   <ContainerDevelopmentMode>Regular</ContainerDevelopmentMode>
</PropertyGroup>
```

Wenn Sie die Leistungsoptimierung wiederherstellen möchten, entfernen Sie die Eigenschaft aus der Projektdatei.

## <a name="building-from-the-command-line"></a>Ausführen des Builds über die Befehlszeile

Sie können `docker build` oder `MSBuild` verwenden, um über die Befehlszeile den Build auszuführen.

### <a name="docker-build"></a>docker build

Wenn Sie eine Projektmappe für Container über die Befehlszeile erstellen möchten, können Sie in der Regel den Befehl `docker build <context>` für jedes Projekt in der Projektmappe verwenden. Dabei müssen Sie das Argument für den *Buildkontext* angeben. Der *Buildkontext* eines Dockerfile auf dem lokalen Computer ist der Ordner, der als Arbeitsordner zum Generieren des Images verwendet wird. Das kann beispielsweise der Ordner sein, aus dem Sie Dateien kopieren und in den Container einfügen.  Verwenden Sie in .NET Core-Projekten den Ordner mit der Projektmappendatei (.sln).  Dieses Argument wird als relativer Pfad angegeben und ist in der Regel „..“ für ein Dockerfile in einem Projektordner und für die Projektmappendatei im übergeordneten Ordner.  Bei .NET Framework-Projekten ist der Buildkontext der Projektordner und nicht der Projektmappenordner.

```cmd
docker build -f Dockerfile ..
```

### <a name="msbuild"></a>MSBuild

Dockerfiles, die von Visual Studio für .NET Framework-Projekte (und für .NET Core-Projekte, die mit älteren Versionen als Update 4 von Visual Studio 2017 erstellt wurden) erstellt werden, entsprechen nicht dem Multistagetyp.  Mit den Schritten in diesen Dockerfiles wird der Code nicht kompiliert.  Wenn Visual Studio ein .NET Framework-Dockerfile erstellt, kompiliert die IDE stattdessen zuerst das Projekt mithilfe von MSBuild.  Wenn dieser Vorgang erfolgreich ist, erstellt Visual Studio anschließend das Dockerfile, wodurch einfach die Buildausgabe von MSBuild in das resultierende Docker-Image kopiert wird.  Da die Schritte zum Kompilieren des Codes nicht im Dockerfile enthalten sind, können Sie .NET Framework-Dockerfiles nicht mithilfe von `docker build` über die Befehlszeile erstellen. Sie sollten MSBuild verwenden, um diese Projekte zu erstellen.

Zum Erstellen eines Images für ein einzelnes Docker-Containerprojekt können Sie MSBuild mit der Befehlsoption `/t:ContainerBuild` verwenden. Beispiel:

```cmd
MSBuild MyProject.csproj /t:ContainerBuild /p:Configuration=Release
```

Die Ausgabe ähnelt der, die im Fenster **Ausgabe** angezeigt wird, wenn Sie eine Projektmappe mit der IDE Visual Studio erstellen. Verwenden Sie immer `/p:Configuration=Release`, da die Ergebnisse beim Erstellen mit der **Debugkonfiguration** möglicherweise nicht Ihren Erwartungen entsprechen, wenn Visual Studio die Multistageoptimierung für Builds verwendet.

Wenn Sie ein Docker Compose-Projekt verwenden, nutzen Sie den Befehl zum Erstellen von Images:

```cmd
msbuild /p:SolutionPath=<solution-name>.sln /p:Configuration=Release docker-compose.dcproj
```

## <a name="next-steps"></a>Nächste Schritte

Erfahren Sie, wie Sie Ihre Builds weiter anpassen, indem Sie zusätzliche MSBuild-Eigenschaften in Ihren Projektdateien festlegen. Weitere Informationen finden Sie unter [MSBuild-Eigenschaften für Containerprojekte](container-msbuild-properties.md).

## <a name="see-also"></a>Siehe auch

[MSBuild](../msbuild/msbuild.md)
[Dockerfile unter Windows](/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
[Linux-Container unter Windows](/virtualization/windowscontainers/deploy-containers/linux-containers)
