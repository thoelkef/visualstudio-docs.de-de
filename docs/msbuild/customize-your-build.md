---
title: Anpassen Ihres Builds | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, transforms
- transforms [MSBuild]
ms.assetid: d0bceb3b-14fb-455c-805a-63acefa4b3ed
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 31856366712da0a2287f73906c6e3a5f81f63a00
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49857587"
---
# <a name="customize-your-build"></a>Anpassen Ihres Builds

MSBuild-Projekte, die den Standardbuildprozess verwenden und *Microsoft.Common.props* und *Microsoft.Common.targets* importieren, beinhalten einige Erweiterungsmöglichkeiten, die zum Anpassen Ihres Buildprozesses verwendet werden können.

## <a name="add-arguments-to-command-line-msbuild-invocations-for-your-project"></a>Hinzufügen von Argumenten zu MSBuild-Aufrufen Ihres Projekts über die Befehlszeile

Es wird eine *Directory.Build.rsp*-Datei innerhalb oder oberhalb des Quellverzeichnisses auf die Builds des Projekts über die Befehlszeile angewendet. Weitere Einzelheiten finden Sie unter [MSBuild-Antwortdateien](../msbuild/msbuild-response-files.md#directorybuildrsp).

## <a name="directorybuildprops-and-directorybuildtargets"></a>„Directory.Build.props“ und „Directory.Build.targets“

Wenn Sie vor Version 15 von MSBuild eine neue benutzerdefinierte Eigenschaft für Projekte in Ihrer Projektmappe bereitstellen wollten, mussten Sie zu jeder Projektdatei in der Projektmappe manuell einen Verweis auf diese Eigenschaft hinzufügen. Alternativ dazu konnten Sie unter anderem die Eigenschaft in einer *PROPS*-Datei definieren und diese dann explizit in jedes Projekt der Projektmappe importieren.

Jetzt hingegen können Sie in einem Schritt jedem Projekt eine neue Eigenschaft hinzufügen, indem Sie sie in einer einzigen Datei mit dem Namen *Directory.Build.props* im Stammverzeichnis der Quelle definieren. Beim Ausführen von MSBuild durchsucht *Microsoft.Common.props* die Verzeichnisstruktur nach der Datei *Directory.Build.props* (und *Microsoft.Common.targets* sucht nach *Directory.Build.targets*). Wenn eine Datei gefunden wird, wird die Eigenschaft importiert. Bei *Directory.Build.props* handelt es sich um eine benutzerdefinierte Datei, die Anpassungen für Projekte in einem Verzeichnis bereitstellt.

> [!NOTE]
> Bei Linux-basierten Dateisystemen wird zwischen Groß- und Kleinschreibung unterschieden. Stellen Sie sicher, dass die Schreibweise des Dateinamens „Directory.Build.props“ genau übereinstimmt, sonst wird die Datei während des Buildvorgangs nicht erkannt.
>
> Weitere Informationen finden Sie in [diesem GitHub-Problem](https://github.com/dotnet/core/issues/1991#issue-368441031).

### <a name="directorybuildprops-example"></a>Beispiel für „Directory.Build.props“

Wenn Sie beispielsweise für alle Ihre Projekte den Zugriff auf die neue Roslyn-Funktion **/deterministic** (die im `CoreCompile`-Ziel von Roslyn durch die Eigenschaft `$(Deterministic)` verfügbar gemacht wird) aktivieren möchten, können Sie wie folgt vorgehen.

1. Erstellen Sie im Stammverzeichnis Ihres Repositorys eine neue Datei mit dem Namen *Directory.Build.props*.
2. Fügen Sie der Datei das folgende XML hinzu.

   ```xml
   <Project>
    <PropertyGroup>
      <Deterministic>true</Deterministic>
    </PropertyGroup>
   </Project>
   ```
3. Führen Sie MSBuild aus. Die vorhandenen Importe des Projekts von *Microsoft.Common.props* und *Microsoft.Common.targets* finden die Datei und importieren sie.

### <a name="search-scope"></a>Suchbereich

Bei der Suche nach einer Datei *Directory.Build.props* durchläuft MSBuild die Verzeichnisstruktur vom Speicherort des Projekts (`$(MSBuildProjectFullPath)`) aufwärts und stoppt, wenn eine Datei *Directory.Build.props* gefunden wird. Wenn `$(MSBuildProjectFullPath)` zum Beispiel *C:\users\username\code\test\case1* lautet, beginnt MSBuild an dieser Stelle und durchsucht die Verzeichnisstruktur aufwärts, bis wie in der folgenden Verzeichnisstruktur eine Datei *Directory.Build.props* gefunden wird.

```
c:\users\username\code\test\case1
c:\users\username\code\test
c:\users\username\code
c:\users\username
c:\users
c:\
```

Der Speicherort der Projektmappendatei ist für *Directory.Build.props* ohne Bedeutung.

### <a name="import-order"></a>Importreihenfolge

*Directory.Build.props* wird zu einem frühen Zeitpunkt in *Microsoft.Common.props* importiert, und später definierte Eigenschaften sind dafür nicht verfügbar. Vermeiden Sie deshalb das Verweisen auf Eigenschaften, die noch nicht definiert sind (und als leer ausgewertet werden).

*Directory.Build.targets* wird aus *Microsoft.Common.targets* importiert, nachdem *TARGETS*-Dateien aus NuGet-Paketen importiert wurden. Deshalb kann es zum Überschreiben der meisten in der Buildlogik definierten Eigenschaften und Ziele verwendet werden. In manchen Fällen kann es jedoch erforderlich sein, dass Sie nach dem abschließenden Import Anpassungen an der Projektdatei vornehmen.

### <a name="use-case-multi-level-merging"></a>Anwendungsfall: Zusammenführen mehrerer Ebenen

Für diesen Anwendungsfall wird beispielhaft davon ausgegangen, dass Sie die folgende Standard-Projektmappenstruktur verwenden:

```
\
  MySolution.sln
  Directory.Build.props     (1)
  \src
    Directory.Build.props   (2-src)
    \Project1
    \Project2
  \test
    Directory.Build.props   (2-test)
    \Project1Tests
    \Project2Tests
```

Es kann sinnvoll sein, gemeinsame Eigenschaften für alle Projekte *(1)*, für *src*-Projekte *(2-src)* und für *test*-Projekte *(2-test)* zu verwenden.

Damit MSBuild die „inneren“ Dateien (*2-src* und *2-test*) mit der „äußeren“ Datei (*1*) korrekt zusammenführen kann, müssen Sie berücksichtigen, dass MSBuild nach der ersten gefundenen Datei *Directory.Build.props* den Suchvorgang abbricht. Zum Fortsetzen des Suchvorgangs und des Zusammenführens in der äußeren Datei ist es erforderlich, diesen Code in beide inneren Dateien einzufügen:

`<Import Project="$([MSBuild]::GetPathOfFileAbove('Directory.Build.props', '$(MSBuildThisFileDirectory)../'))" />`

Der allgemeine Ansatz von MSBuild lässt sich folgendermaßen zusammenfassen:

- MSBuild sucht die erste Datei *Directory.Build.props*, die in der Projektmappenstruktur oberhalb der aktuellen Datei gefunden wird, führt diese mit den Standardeinstellungen zusammen und beendet anschließend den Suchvorgang.
- Wenn mehrere Ebenen gefunden und zusammengeführt werden sollen, importieren Sie wie oben gezeigt mit [`<Import...>`](../msbuild/property-functions.md#msbuild-getpathoffileabove) die äußere Datei aus der inneren.
- Wenn die äußere Datei nicht ebenfalls Dateien importiert, die sich in der Projektstruktur oberhalb der äußeren Datei befinden, wird der Suchvorgang an dieser Stelle beendet.
- Verwenden Sie zum Konfigurieren des Such- und Zusammenführungsprozesses `$(DirectoryBuildPropsPath)` und `$(ImportDirectoryBuildProps)`.

Oder in einem Satz ausgedrückt: MSBuild beendet den Suchvorgang, sobald eine *Directory.Build.props*-Datei gefunden wurde, durch die keine weiteren Dateien importiert werden.

## <a name="msbuildprojectextensionspath"></a>MSBuildProjectExtensionsPath

Standardmäßig importiert *Microsoft.Common.props* `$(MSBuildProjectExtensionsPath)$(MSBuildProjectFile).*.props`, und *Microsoft.Common.targets* importiert `$(MSBuildProjectExtensionsPath)$(MSBuildProjectFile).*.targets`. Der Standardwert von `MSBuildProjectExtensionsPath` ist `$(BaseIntermediateOutputPath)`, `obj/`. NuGet verwendet diesen Mechanismus, um einen Verweis auf die mit Paketen bereitgestellte Buildlogik herzustellen. D.h., NuGet erstellt während der Wiederherstellung `{project}.nuget.g.props`-Dateien, die auf die Paketinhalte verweisen.

Sie können diesen Erweiterbarkeitsmechanismus deaktivieren, indem Sie die Eigenschaft `ImportProjectExtensionProps` in einer *Directory.Build.props*-Datei oder vor dem Import von *Microsoft.Common.props* auf `false` festlegen.

> [!NOTE]
> Wenn Sie MSBuildProjectExtensionsPath-Importe deaktivieren, wird die Buildlogik, die in NuGet-Paketen enthalten ist, nicht auf Ihr Projekt angewendet. Für einige NuGet-Pakete ist es erforderlich, dass die Buildlogik ausgeführt wird. Sie werden daher unnötig gerendert, wenn diese Option deaktiviert ist.

## <a name="user-file"></a>USER-Datei

*Microsoft.Common.CurrentVersion.targets* importiert `$(MSBuildProjectFullPath).user`, sofern vorhanden, damit Sie neben Ihrem Projekt eine Datei mit dieser zusätzlichen Erweiterung erstellen können. Für längerfristig geplante Änderungen, die Sie in die Quellcodeverwaltung integrieren möchten, ändern Sie besser das Projekt direkt, damit spätere Verwalter diesen Erweiterungsmechanismus nicht unbedingt kennen müssen.

## <a name="msbuildextensionspath-and-msbuilduserextensionspath"></a>MSBuildExtensionsPath und MSBuildUserExtensionsPath

> [!WARNING]
> Wenn Sie diesen Erweiterungsmechanismus verwenden, ist es schwieriger, wiederholbare Builds für mehrere Computer zu gewährleisten. Verwenden Sie stattdessen am besten eine Konfiguration, die in Ihr Quellcodeverwaltungssystem integriert werden und für alle Entwickler Ihrer Codebasis freigegeben werden kann.

Standardmäßig importieren viele wichtige Buildlogikdateien

```xml
$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\{TargetFileName}\ImportBefore\*.targets
```

vor ihrem Inhalt und

```xml
$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\{TargetFileName}\ImportAfter\*.targets
```

danach. Dadurch können installierte SDKs die Buildlogik häufig verwendeter Projekttypen erweitern.

In `$(MSBuildUserExtensionsPath)` wird nach der gleichen Verzeichnisstruktur (je nach Benutzerordner *%LOCALAPPDATA%\Microsoft\MSBuild*) gesucht. Dateien, die in diesem Ordner platziert werden, werden für alle Builds des jeweiligen Projekttyps importiert, die mit den Anmeldeinformationen des Benutzers ausgeführt werden. Sie können die Benutzererweiterungen deaktivieren, indem Sie die Eigenschaften festlegen, die nach der Importdatei im Muster `ImportUserLocationsByWildcardBefore{ImportingFileNameWithNoDots}` benannt werden. Wenn Sie beispielsweise `ImportUserLocationsByWildcardBeforeMicrosoftCommonProps` auf `false` festlegen, wird `$(MSBuildUserExtensionsPath)\$(MSBuildToolsVersion)\Imports\Microsoft.Common.props\ImportBefore\*` nicht importiert.

## <a name="customize-the-solution-build"></a>Anpassen des Projektmappenbuilds

> [!IMPORTANT]
> Wenn auf diese Weise der Projektmappenbuild angepasst wird, werden die Änderungen nur auf Builds mit *MSBuild.exe* über die Befehlszeile angewendet. Sie werden **nicht** auf Builds innerhalb von Visual Studio angewendet.

Wenn MSBuild eine Projektmappendatei erstellt, wird diese zuerst intern in eine Projektdatei übersetzt, die dann erstellt wird. Die generierte Projektdatei importiert `before.{solutionname}.sln.targets`, bevor sie Ziele definiert und `after.{solutionname}.sln.targets` nachdem sie Ziele importiert hat. Dazu gehören auch die Ziele, die in den Verzeichnissen `$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\SolutionFile\ImportBefore` und `$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\SolutionFile\ImportAfter` installiert sind.

Sie können beispielsweise ein neues Ziel definieren, um eine benutzerdefinierte Protokollmeldung zu schreiben, nachdem *MyCustomizedSolution.sln* erstellt wurde, indem Sie eine Datei in demselben Verzeichnis mit dem Namen *after.MyCustomizedSolution.sln.targets* erstellen, die Folgendes enthält:

```xml
<Project>
 <Target Name="EmitCustomMessage" AfterTargets="Build">
   <Message Importance="High" Text="The solution has completed the Build target" />
 </Target>
</Project>
```

## <a name="see-also"></a>Siehe auch

[MSBuild-Grundlagen](../msbuild/msbuild-concepts.md)

[MSBuild-Referenz](../msbuild/msbuild-reference.md)
