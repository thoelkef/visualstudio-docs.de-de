---
title: Anpassen Ihres Builds | Microsoft-Dokumentation
ms.custom: 
ms.date: 06/14/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, transforms
- transforms [MSBuild]
ms.assetid: d0bceb3b-14fb-455c-805a-63acefa4b3ed
caps.latest.revision: 13
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 3fb5627d2cc92c36e9dcf34f4b94796b6620321f
ms.openlocfilehash: 86f7fef0365a47e8ea88bc3fc46cb0016efd4628
ms.contentlocale: de-de
ms.lasthandoff: 06/15/2017

---
# <a name="customize-your-build"></a>Anpassen Ihres Builds
Wenn Sie in Versionen von MSBuild vor Version 15 eine neue benutzerdefinierte Eigenschaft für Projekte in Ihrer Projektmappe bereitstellen wollten, mussten Sie jeder Projektdatei in der Projektmappe manuell einen Verweis auf diese Eigenschaft hinzufügen. Alternativ dazu konnten Sie unter anderem die Eigenschaft in einer PROPS-Datei definieren und diese dann explizit in jedes Projekt der Projektmappe importieren.

Nun hingegen können Sie in einem Schritt jedem Projekt eine neue Eigenschaft hinzufügen, indem Sie sie in einer einzigen Datei mit dem Namen „Directory.Build.props“ im Stammverzeichnis des Repositorys definieren. Beim Ausführen von MSBuild durchsucht „Microsoft.Common.props“ die Verzeichnisstruktur nach der Datei „Directory.Build.props“ (und „Microsoft.Common.targets“ sucht nach „Directory.Build.targets“). Wenn eine Datei gefunden wird, wird die Eigenschaft importiert. Bei „Directory.Build.props“ handelt es sich um eine benutzerdefinierte Datei, die Anpassungen für Projekte in einem Verzeichnis bereitstellt.

## <a name="directorybuildprops-example"></a>Beispiel für „Directory.Build.props“
Wenn Sie beispielsweise für alle Ihre Projekte den Zugriff auf die neue Roslyn-Funktion **/deterministic** (die im CoreCompile-Ziel von Roslyn durch die Eigenschaft `$(Deterministic)` verfügbar gemacht wird) aktivieren möchten, können Sie wie folgt vorgehen.

1. Erstellen Sie im Stammverzeichnis Ihres Repositorys eine neue Datei mit dem Namen „Directory.Build.props“.
2. Fügen Sie der Datei das folgende XML hinzu.

  ```xml
  <Project>
    <PropertyGroup>
      <Deterministic>true</Deterministic>
    </PropertyGroup>
  </Project>
  ```
3. Führen Sie MSBuild aus. Die vorhandenen Importe des Projekts von „Microsoft.Common.props“ und „Microsoft.Common.targets“ finden die Datei und importieren sie.

## <a name="search-scope"></a>Suchbereich
Bei der Suche nach einer „Directory.Build.props“-Datei durchläuft MSBuild die Verzeichnisstruktur vom Speicherort des Projekts ($(MSBuildProjectFullPath)) aufwärts und stoppt, wenn es eine „Directory.Build.props“-Datei findet. Wenn $(MSBuildProjectFullPath) zum Beispiel „c:\users\username\code\test\case1“ ist, beginnt MSBuild an dieser Stelle und durchsucht die Verzeichnisstruktur aufwärts, bis es wie in der folgenden Verzeichnisstruktur eine „Directory.Build.props“-Datei findet.

```
c:\users\username\code\test\case1
c:\users\username\code\test
c:\users\username\code
c:\users\username
c:\users
c:\
```
Der Speicherort der Projektmappendatei ist für „Directory.Build.props“ ohne Bedeutung.

## <a name="import-order"></a>Importreihenfolge

„Directory.Build.props“ wird zu einem frühen Zeitpunkt in „Microsoft.Common.props“ importiert, sodass später definierte Eigenschaften dafür nicht verfügbar sind. Vermeiden Sie deshalb das Verweisen auf Eigenschaften, die noch nicht definiert sind (und daher als leer ausgewertet werden).

„Directory.Build.targets“ wird aus „Microsoft.Common.targets“ importiert, nachdem TARGETS-Dateien aus NuGet-Paketen importiert wurden. Deshalb kann es zum Überschreiben der meisten in der Buildlogik definierten Eigenschaften und Ziele verwendet werden, aber in einigen Fällen kann es erforderlich sein, nach dem abschließenden Import Anpassungen in der Projektdatei vorzunehmen.

## <a name="see-also"></a>Siehe auch  
 [MSBuild Concepts](../msbuild/msbuild-concepts.md)  (MSBuild-Grundlagen)  
 [MSBuild-Referenz](../msbuild/msbuild-reference.md)   

