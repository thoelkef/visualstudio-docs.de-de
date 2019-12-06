---
title: 'Visual Studio-Containertools: Übersicht über den Build- und Debugprozess'
author: ghogen
description: Übersicht über den Build- und Debugprozess für Containertools
ms.author: ghogen
ms.date: 11/20/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: e1b2f332563503dcb4d63faf301000db83eed5ea
ms.sourcegitcommit: 49ebf69986713e440fd138fb949f1c0f47223f23
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2019
ms.locfileid: "74706794"
---
# <a name="how-visual-studio-builds-containerized-apps"></a>Wie Visual Studio Containeranwendungen erstellt

Wenn Sie Projekte erstellen, müssen Sie wissen wie Visual Studio das Dockerfile nutzt: ganz egal, ob Sie Visual Studio oder die Befehlszeile für Builds verwenden.  Aus Leistungsgründen führt Visual Studio einen speziellen Prozess für Container-Apps aus. Wenn Sie den Buildprozess durch die Bearbeitung des Dockerfile anpassen, ist es besonders wichtig, zu verstehen, wie Visual Studio Ihre Projekte erstellt.

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

In den ersten Dockerfile-Zeilen wird das Nano Server-Image in der Microsoft-Containerregistrierung (mcr.microsoft.com) angegeben. Außerdem wird das temporäre Image `base` erstellt, das die Ports 80 und 443 verfügbar macht und das Arbeitsverzeichnis auf `/app` festlegt.

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

## <a name="building-from-the-command-line"></a>Ausführen des Builds über die Befehlszeile

Wenn Sie Builds außerhalb von Visual Studio erstellen möchten, können Sie `docker build` oder `MSBuild` verwenden, um Builds über die Befehlszeile zu erstellen.

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

Die Ausgabe ähnelt der, die im Fenster **Ausgabe** angezeigt wird, wenn Sie eine Projektmappe mit der IDE Visual Studio erstellen. Verwenden Sie immer `/p:Configuration=Release`, da die Ergebnisse beim Erstellen mit der **Debugkonfiguration** möglicherweise nicht Ihren Erwartungen entsprechen, wenn Visual Studio die Multistageoptimierung für Builds verwendet. Siehe [Debuggen](#debugging).

Wenn Sie ein Docker Compose-Projekt verwenden, nutzen Sie den Befehl zum Erstellen von Images:

```cmd
msbuild /p:SolutionPath=<solution-name>.sln /p:Configuration=Release docker-compose.dcproj
```

## <a name="project-warmup"></a>Projektaufwärmphase

Als *Projektaufwärmphase* wird eine Reihe von Schritten bezeichnet, die erfolgen, wenn das Docker-Profil für ein Projekt ausgewählt wird (d. h. wenn ein Projekt geladen oder Docker-Unterstützung hinzugefügt wird), um die Leistung nachfolgender Läufe zu verbessern (**F5** oder **STRG**+**F5**). Dies kann unter **Tools** > **Optionen** > **Containertools** konfiguriert werden. Es folgen die Aufgaben aufgeführt, die im Hintergrund ausgeführt werden:

- Überprüfen, ob Docker Desktop installiert ist und ausgeführt wird
- Sicherstellen, dass Docker Desktop auf das Betriebssystem des Projekts festgelegt ist
- Pullen der Images in der ersten Phase der Dockerfile (der Phase `base` in den meisten Dockerfiles)  
- Erstellen der Dockerfile und Starten des Containers

Die Aufwärmphase findet nur im Modus **Schnell** statt, sodass für den aktiven Container das Volume des App-Ordners bereitgestellt wird. Das heißt, dass Änderungen an der App den Container nicht ungültig machen sollten. Dadurch wird die Debugleistung deutlich verbessert und die Wartezeit für zeitintensiv Aufgaben wie das Pullen großer Images verkürzt.

## <a name="volume-mapping"></a>Volumezuordnung

Damit das Debuggen in Containern funktioniert, verwendet Visual Studio die Volumezuordnung, um den Debugger und die NuGet-Ordner vom Hostcomputer zuzuordnen. Hier sind die Volumes, die in Ihrem Container bereitgestellt werden:

|||
|-|-|
| **Remotedebugger** | Enthält die Bits, die abhängig vom Projekttyp erforderlich sind, um den Debugger im Container auszuführen. Dies wird im Abschnitt |[Debuggen](#debugging) ausführlicher beschrieben.
| **App-Ordner** | Enthält den Projektordner, in dem sich die Dockerfile befindet.|
| **Quellordner** | Enthält den Buildkontext, der an Docker-Befehle übergeben wird.|
| **Ordner mit NuGet-Paketen** | Enthalten die NuGet-Pakete und Fallbackordner, die aus der Datei *obj\{project}.csproj.nuget.g.reps* in das Projekt eingelesen werden. |

Für ASP.NET Core-Web-Apps kann es zwei zusätzliche Ordner für das SSL-Zertifikat und die Benutzergeheimnisse geben, was im nächsten Abschnitt näher erläutert wird.

## <a name="ssl-enabled-aspnet-core-apps"></a>SSL-fähige ASP.NET Core-Apps

Containertools in Visual Studio unterstützen das Debuggen einer SSL-fähigen ASP.NET Core-App mit einem Entwicklungszertifikat, so wie Sie es auch ohne Container erwarten würden. Um dies zu erreichen, fügt Visual Studio einige weitere Schritte hinzu, um das Zertifikat zu exportieren und dem Container zur Verfügung zu stellen. Der Ablauf ist wie folgt:

1. Stellen Sie mit dem Tool `dev-certs` sicher, dass das lokale Entwicklungszertifikat auf dem Hostcomputer vorhanden und vertrauenswürdig ist.
2. Exportieren Sie das Zertifikat in %APPDATA%\ASP.NET\Https mit einem sicheren Kennwort, das im Speicher für Benutzergeheimnisse für diese bestimmte App gespeichert ist.
3. Verwenden Sie für das Bereitstellen von Volumes die folgenden Verzeichnisse:

   - *%APPDATA%\Microsoft\UserSecrets*
   - *%APPDATA%\ASP.NET\Https*

ASP.NET Core sucht nach einem Zertifikat, das dem Assemblynamen im Ordner *Https* entspricht, weshalb es dem Container in diesem Pfad zugeordnet wird. Pfad und Kennwort des Zertifikats können alternativ über Umgebungsvariablen (d. h. `ASPNETCORE_Kestrel__Certificates__Default__Path` und `ASPNETCORE_Kestrel__Certificates__Default__Password`) oder in der JSON-Datei mit Benutzergeheimnissen definiert werden. Beispiel:

```json
{
  "Kestrel": {
    "Certificates": {
      "Default": {
        "Path": "c:\\app\\mycert.pfx",
        "Password": "strongpassword"
      }
    }
  }
}
```

Weitere Informationen zur Verwendung von SSL mit ASP.NET Core-Apps in Containern finden Sie unter [Hosten von ASP.NET Core-Images mit Docker über HTTPS](https://docs.microsoft.com/aspnet/core/security/docker-https).

## <a name="debugging"></a>Debuggen

Beim Erstellen von Builds in der Konfiguration **Debuggen** führt Visual Studio mehrere Optimierungen durch, um die Leistung des Buildprozesses für Containerprojekte zu erhöhen. Der Buildprozess für Container-Apps ist komplexer, sodass nicht einfach die in der Dockerfile beschriebenen Schritte ausgeführt werden können. Ein Build in einem Container ist deutlich langsamer als ein Build auf einem lokalen Computer.  Wenn Sie also für den Build die **Debugkonfiguration** nutzen, erstellt Visual Studio Ihre Projekte auf dem lokalen Computer und gibt den Ausgabeordner dann für den Container frei, indem das Volume eingebunden wird. Ein Build mit dieser Optimierung wird auch als *Schnellmodusbuild* bezeichnet.

Im **Schnellmodus** ruft Visual Studio `docker build` mit einem Argument auf, das Docker anweist, nur die `base`-Stage zu erstellen.  Die restlichen Schritte führt Visual Studio durch, ohne den Inhalt des Dockerfile zu beachten. Wenn Sie das Dockerfile ändern, um beispielsweise die Containerumgebung anzupassen oder zusätzliche Abhängigkeiten zu installieren, sollten Sie die Änderungen in der ersten Stage ablegen.  Wenn benutzerdefinierte Schritte in den Stages `build`, `publish` und `final` des Dockerfile hinterlegt werden, werden diese nicht ausgeführt.

Diese Leistungsoptimierung wird nur durchgeführt, wenn Sie für den Build die **Debugkonfiguration** verwenden. In der **Releasekonfiguration** findet der Build wie im Dockerfile angegeben im Container statt.

Wenn Sie die Leistungsoptimierung deaktivieren und den Build wie im Dockerfile angegeben ausführen möchten, legen Sie die Eigenschaft **ContainerDevelopmentMode** in der Projektdatei wie folgt auf **Regular** fest:

```xml
<PropertyGroup>
   <ContainerDevelopmentMode>Regular</ContainerDevelopmentMode>
</PropertyGroup>
```

Wenn Sie die Leistungsoptimierung wiederherstellen möchten, entfernen Sie die Eigenschaft aus der Projektdatei.

 Wenn Sie mit dem Debuggen beginnen (**F5**), wird nach Möglichkeit ein zuvor gestarteter Container wiederverwendet. Wenn Sie den vorherigen Container nicht wiederverwenden möchten, können Sie in Visual Studio die Befehle **Rebuild** (Neu erstellen) oder **Bereinigen** verwenden, um zu erzwingen, dass Visual Studio einen neuen Container verwendet.

Die Ausführung des Debuggers hängt von der Art des Projekts und dem Containerbetriebssystem ab:

|||
|-|-|
| **.NET Core-Apps (Linux-Container)**| Visual Studio lädt `vsdbg` herunter und ordnet es dem Container zu. Dann wird es mit Ihrem Programm und Argumenten (d. h. `dotnet webapp.dll`) aufgerufen, und anschließend wird der Debugger an den Prozess angefügt. |
| **.NET Core-Apps (Windows-Container)**| Visual Studio verwendet `onecoremsvsmon`, ordnet es dem Container zu und führt es als Einstiegspunkt aus. Dann stellt Visual Studio eine Verbindung damit her und fügt es an Ihr Programm an. Dies ähnelt der Vorgehensweise beim Einrichten des Remotedebuggens auf einem anderen oder virtuellen Computer.|
| **.NET Framework-Apps** | Visual Studio verwendet `msvsmon`, ordnet es dem Container zu, führt es als Einstiegspunkt aus, an dem sich Visual Studio damit verbinden kann, und fügt es an Ihr Programm an.|

Informationen zu `vsdbg.exe` finden Sie unter [Offroad-Debuggen von .NET Core unter Linux und OSX in Visual Studio](https://github.com/Microsoft/MIEngine/wiki/Offroad-Debugging-of-.NET-Core-on-Linux---OSX-from-Visual-Studio).

## <a name="container-entry-point"></a>Containereinstiegspunkt

Visual Studio verwendet einen benutzerdefinierten Containereinstiegspunkt abhängig vom Projekttyp und Containerbetriebssystem. Es folgen die verschiedenen Kombinationen:

|||
|-|-|
| **Linux-Container** | Der Einstiegspunkt ist `tail -f /dev/null`. Dabei handelt es sich um eine unbegrenzte Wartezeit, um den Container aktiv zu halten. Wenn die App über den Debugger gestartet wird, ist der Debugger für die Ausführung der App verantwortlich (d. h. `dotnet webapp.dll`). Bei Starten ohne Debuggen führt das Tool `docker exec -i {containerId} dotnet webapp.dll` aus, um die App auszuführen.|
| **Windows-Container**| Der Einstiegspunkt ist so etwas wie `C:\remote_debugger\x64\msvsmon.exe /noauth /anyuser /silent /nostatus`, womit der Debugger so ausgeführt wird, dass er auf Verbindungen lauscht. Gleiches gilt für die Ausführung der App durch den Debugger und den Befehl `docker exec` beim Starten ohne Debuggen. Bei .NET Framework-Web-Apps ist der Einstiegspunkt etwas anders, da `ServiceMonitor` zum Befehl hinzugefügt wird.|

Der Containereinstiegspunkt kann nur in Docker-Compose-Projekten, nicht in Einzelcontainerprojekten geändert werden.

## <a name="next-steps"></a>Nächste Schritte

Erfahren Sie, wie Sie Ihre Builds weiter anpassen, indem Sie zusätzliche MSBuild-Eigenschaften in Ihren Projektdateien festlegen. Weitere Informationen finden Sie unter [MSBuild-Eigenschaften für Containerprojekte](container-msbuild-properties.md).

## <a name="see-also"></a>Siehe auch

[MSBuild](../msbuild/msbuild.md)
[Dockerfile unter Windows](/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
[Linux-Container unter Windows](/virtualization/windowscontainers/deploy-containers/linux-containers)
