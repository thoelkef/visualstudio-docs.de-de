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
ms.openlocfilehash: dae51959313a7108c54466dff08b3641525818cd
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="customize-your-build"></a>Anpassen Ihres Builds
Wenn Sie in Versionen von MSBuild vor Version 15 eine neue benutzerdefinierte Eigenschaft für Projekte in Ihrer Projektmappe bereitstellen wollten, mussten Sie jeder Projektdatei in der Projektmappe manuell einen Verweis auf diese Eigenschaft hinzufügen. Alternativ dazu konnten Sie unter anderem die Eigenschaft in einer *PROPS*-Datei definieren und diese dann explizit in jedes Projekt der Projektmappe importieren.

Jetzt hingegen können Sie in einem Schritt jedem Projekt eine neue Eigenschaft hinzufügen, indem Sie sie in einer einzigen Datei mit dem Namen *Directory.Build.props* im Stammverzeichnis des Repositorys definieren. Beim Ausführen von MSBuild durchsucht *Microsoft.Common.props* die Verzeichnisstruktur nach der Datei *Directory.Build.props* (und *Microsoft.Common.targets* sucht nach *Directory.Build.targets*). Wenn eine Datei gefunden wird, wird die Eigenschaft importiert. Bei *Directory.Build.props* handelt es sich um eine benutzerdefinierte Datei, die Anpassungen für Projekte in einem Verzeichnis bereitstellt.

## <a name="directorybuildprops-example"></a>Beispiel für „Directory.Build.props“
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

## <a name="search-scope"></a>Suchbereich
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

## <a name="import-order"></a>Importreihenfolge

*Directory.Build.props* wird zu einem frühen Zeitpunkt in *Microsoft.Common.props* importiert, sodass später definierte Eigenschaften dafür nicht verfügbar sind. Vermeiden Sie deshalb das Verweisen auf Eigenschaften, die noch nicht definiert sind (und daher als leer ausgewertet werden).

*Directory.Build.targets* wird aus *Microsoft.Common.targets* importiert, nachdem *TARGETS*-Dateien aus NuGet-Paketen importiert wurden. Deshalb kann es zum Überschreiben der meisten in der Buildlogik definierten Eigenschaften und Ziele verwendet werden, aber in einigen Fällen kann es erforderlich sein, nach dem abschließenden Import Anpassungen in der Projektdatei vorzunehmen.

## <a name="use-case-multi-level-merging"></a>Anwendungsfall: Zusammenführen mehrerer Ebenen

Für diesen Anwendungsfall wird beispielhaft davon ausgegangen, dass Sie die folgende Standard-Projektmappenstruktur verwenden:

````
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
````

Es kann sinnvoll sein, gemeinsame Eigenschaften für alle Projekte *(1)*, für *src*-Projekte *(2-src)* und für *test*-Projekte *(2-test)* zu verwenden.

Damit MSBuild die „inneren“ Dateien (*2-src* und *2-test*) mit der „äußeren“ Datei (*1*) korrekt zusammenführen kann, müssen Sie berücksichtigen, dass MSBuild nach der ersten gefundenen Datei *Directory.Build.props* den Suchvorgang abbricht. Zum Fortsetzen des Suchvorgangs und Zusammenführen mit der äußeren Datei ist es erforderlich, den folgenden Code in beide inneren Dateien einzufügen:

`<Import Project="$([MSBuild]::GetPathOfFileAbove('Directory.Build.props', '$(MSBuildThisFileDirectory)../'))" />`

Der allgemeine Ansatz von MSBuild lässt sich folgendermaßen zusammenfassen:

- MSBuild sucht die erste Datei *Directory.Build.props*, die in der Projektmappenstruktur oberhalb der aktuellen Datei gefunden wird, führt diese mit den Standardeinstellungen zusammen und beendet anschließend den Suchvorgang.
- Wenn mehrere Ebenen gefunden und zusammengeführt werden sollen, importieren Sie wie oben gezeigt mit [`<Import...>`](../msbuild/property-functions.md#msbuild-getpathoffileabove) die äußere Datei aus der inneren.
- Wenn die äußere Datei nicht ebenfalls Dateien importiert, die sich in der Projektstruktur oberhalb der äußeren Datei befinden, wird der Suchvorgang an dieser Stelle beendet.
- Verwenden Sie zum Konfigurieren des Such- und Zusammenführungsprozesses `$(DirectoryBuildPropsPath)` und `$(ImportDirectoryBuildProps)`.

Oder in einem Satz ausgedrückt: MSBuild beendet den Suchvorgang, sobald eine Datei *Directory.Build.props* gefunden wurde, durch die keine weiteren Dateien importiert werden.

## <a name="see-also"></a>Siehe auch  
 [MSBuild Concepts](../msbuild/msbuild-concepts.md)  (MSBuild-Grundlagen)  
 [MSBuild-Referenz](../msbuild/msbuild-reference.md)   
