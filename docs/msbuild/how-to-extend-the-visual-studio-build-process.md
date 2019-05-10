---
title: Erweitern des Buildprozesses
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, overriding predefined targets
- MSBuild, overriding DependsOn properties
- MSBuild, extending Visual Studio builds
- MSBuild, DependsOn properties
ms.assetid: cb077613-4a59-41b7-96ec-d8516689163c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d22bf8af86605d414d933d16cd5dd7f8d24a6154
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62946094"
---
# <a name="how-to-extend-the-visual-studio-build-process"></a>Vorgehensweise: Erweitern des Visual Studio-Buildprozesses
Der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Buildprozess wird durch eine Reihe von *TARGETS*-Dateien von [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] definiert, die in die Projektdatei importiert werden. Eine dieser importierten Dateien (*Microsoft.Common.targets*) kann erweitert werden, um Ihnen das Ausführen benutzerdefinierter Aufgaben in unterschiedlichen Phasen während des Buildprozesses zu ermöglichen. In diesem Artikel werden die zwei Methoden erläutert, mit denen der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Buildprozess erweitert werden kann:

- Überschreiben bestimmter, in *Microsoft.Common.targets* vordefinierter Ziele

- Überschreiben der DependsOn-Eigenschaften, die in *Microsoft.Common.targets* definiert sind

## <a name="override-predefined-targets"></a>Überschreiben vordefinierter Ziele
Die Datei *Microsoft.Common.targets* enthält eine Reihe vordefinierter, leerer Ziele, die vor und nach einigen der wichtigsten Ziele im Buildprozess aufgerufen werden. Beispielsweise ruft [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] das `BeforeBuild`-Ziel vor dem `CoreBuild`-Hauptziel und das `AfterBuild`-Ziel nach dem `CoreBuild`-Ziel auf. Die leeren Ziele in *Microsoft.Common.targets* führen standardmäßig keine Aktionen aus. Sie können aber ihr Standardverhalten überschreiben, indem Sie die Ziele definieren, die eine Projektdatei enthalten soll, die *Microsoft.Common.targets* importiert. Durch das Überschreiben der vordefinierten Ziele können Sie den Buildprozess mit [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]-Aufgaben besser steuern.

#### <a name="to-override-a-predefined-target"></a>So überschreiben Sie ein vordefiniertes Ziel

1. Identifizieren Sie ein vordefiniertes Ziel in *Microsoft.Common.targets*, das Sie überschreiben möchten. In der Tabelle unten finden Sie die vollständige Liste der Ziele, die Sie bedenkenlos überschreiben können.

2. Definieren Sie das Ziel bzw. die Ziele am Ende der Projektdatei, unmittelbar vor dem `</Project>`-Tag. Beispiel:

    ```xml
    <Project>
        ...
        <Target Name="BeforeBuild">
            <!-- Insert tasks to run before build here -->
        </Target>
        <Target Name="AfterBuild">
            <!-- Insert tasks to run after build here -->
        </Target>
    </Project>
    ```

3. Erstellen Sie die Projektdatei.

Die folgende Tabelle zeigt alle Ziele in *Microsoft.Common.targets*, die Sie bedenkenlos überschreiben können.

|Zielname|Beschreibung|
|-----------------|-----------------|
|`BeforeCompile`, `AfterCompile`|Aufgaben, die in eines dieser Ziele eingefügt wurden, werden vor oder nach Abschluss der Kompilierung ausgeführt. Die meisten Anpassungen werden in einem dieser beiden Ziele ausgeführt.|
|`BeforeBuild`, `AfterBuild`|Aufgaben, die in eines dieser Ziele eingefügt wurden, werden ausgeführt, bevor oder nachdem alles Weitere erstellt wurde. **Hinweis**:  Die Ziele `BeforeBuild` und `AfterBuild` wurden bereits in Kommentaren am Ende der meisten Projektdateien definiert. Dadurch können Sie ohne großen Aufwand Pre- und Postbuildereignisse zu Ihrer Projektdatei hinzufügen.|
|`BeforeRebuild`, `AfterRebuild`|Aufgaben, die in eines dieser Ziele eingefügt wurden, werden ausgeführt, bevor oder nachdem die Funktion zum Neuerstellen von Kernen aufgerufen wurde. Die Reihenfolge der Ausführung der Ziele in *Microsoft.Common.targets* lautet wie folgt: `BeforeRebuild`, `Clean`, `Build` und anschließend `AfterRebuild`.|
|`BeforeClean`, `AfterClean`|Aufgaben, die in eines dieser Ziele eingefügt wurden, werden ausgeführt, bevor oder nachdem die Funktion zum Löschen von Kernen aufgerufen wurde.|
|`BeforePublish`, `AfterPublish`|Aufgaben, die in eines dieser Ziele eingefügt wurden, werden ausgeführt, bevor oder nachdem die Funktion zum Veröffentlichen von Kernen aufgerufen wurde.|
|`BeforeResolveReferences`, `AfterResolveReferences`|Aufgaben, die in eines dieser Ziele eingefügt wurden, werden ausgeführt, bevor oder nachdem die Assemblyverweise aufgelöst wurden.|
|`BeforeResGen`, `AfterResGen`|Aufgaben, die in eines dieser Ziele eingefügt wurden, werden ausgeführt, bevor oder nachdem Ressourcen generiert wurden.|

## <a name="override-dependson-properties"></a>Überschreiben von DependsOn-Eigenschaften
Mit dem Überschreiben von vordefinierten Zielen lässt sich der Buildprozess leicht erweitern. Da [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] die Definition von Zielen aber nacheinander auswertet, können Sie ein anderes Projekt, das Ihr Projekt importiert, nicht daran hindern, die bereits überschriebenen Ziele noch einmal zu überschreiben. Das letzte in der Projektdatei definierte `AfterBuild`-Ziel wird z.B. während des Buildprozesses verwendet, nachdem alle anderen Projekte importiert wurden.

Sie können sich vor dem unbeabsichtigten Überschreiben von Zielen schützen, indem Sie die DependsOn-Eigenschaften überschreiben, die in `DependsOnTargets`-Attributen in der gesamten Datei *Microsoft.Common.targets* verwendet werden. So enthält das `Build`-Ziel z.B. einen `DependsOnTargets`-Attributwert von `"$(BuildDependsOn)"`. Betrachten Sie das folgende Beispiel:

```xml
<Target Name="Build" DependsOnTargets="$(BuildDependsOn)"/>
```

Dieser XML-Codeausschnitt gibt an, dass vor der Ausführung des `Build`-Ziels alle in der `BuildDependsOn`-Eigenschaft angegebenen Ziele zuerst ausgeführt werden müssen. Die `BuildDependsOn`-Eigenschaft ist definiert als:

```xml
<PropertyGroup>
    <BuildDependsOn>
        BeforeBuild;
        CoreBuild;
        AfterBuild
    </BuildDependsOn>
</PropertyGroup>
```

Sie können diesen Eigenschaftswert überschreiben, indem Sie eine andere Eigenschaft mit dem Namen `BuildDependsOn` am Ende der Projektdatei deklarieren. Durch Einschließen der vorherigen `BuildDependsOn`-Eigenschaft in die neue Eigenschaft können Sie neue Ziele am Anfang und Ende der Zielliste hinzufügen. Beispiel:

```xml
<PropertyGroup>
    <BuildDependsOn>
        MyCustomTarget1;
        $(BuildDependsOn);
        MyCustomTarget2
    </BuildDependsOn>
</PropertyGroup>

<Target Name="MyCustomTarget1">
    <Message Text="Running MyCustomTarget1..."/>
</Target>
<Target Name="MyCustomTarget2">
    <Message Text="Running MyCustomTarget2..."/>
</Target>
```

Projekte, in die Ihre Projektdateien importiert werden, können diese Eigenschaften überschreiben, ohne die von Ihnen vorgenommenen Anpassungen zu überschreiben.

#### <a name="to-override-a-dependson-property"></a>So überschreiben Sie eine DependsOn-Eigenschaft

1. Identifizieren Sie eine vordefiniertes DependsOn-Eigenschaft in *Microsoft.Common.targets*, die Sie überschreiben möchten. In der folgenden Tabelle finden Sie eine Liste der Eigenschaften der häufig überschriebenen DependsOn-Eigenschaften.

2. Definieren Sie eine andere Instanz der Eigenschaft oder Eigenschaften am Ende der Projektdatei. Schließen Sie die ursprüngliche Eigenschaft, z.B. `$(BuildDependsOn)`, in die neue Eigenschaft ein.

3. Definieren Sie Ihre benutzerdefinierten Ziele vor oder nach der Eigenschaftsdefinition.

4. Erstellen Sie die Projektdatei.

### <a name="commonly-overridden-dependson-properties"></a>Häufig überschriebene DependsOn-Eigenschaften

|Name der Eigenschaft|Beschreibung|
|-------------------|-----------------|
|`BuildDependsOn`|Die zu überschreibende Eigenschaft, wenn Sie benutzerdefinierte Ziele vor oder nach dem gesamten Buildprozess einfügen möchten|
|`CleanDependsOn`|Die zu überschreibende Eigenschaft, wenn Sie die Ausgabe Ihres benutzerdefinierten Buildprozesses bereinigen möchten|
|`CompileDependsOn`|Die zu überschreibende Eigenschaft, wenn Sie benutzerdefinierte Prozesse vor oder nach dem Kompilieren einfügen möchten|

## <a name="see-also"></a>Siehe auch
- [Integration von Visual Studio](../msbuild/visual-studio-integration-msbuild.md)
- [MSBuild-Grundlagen](../msbuild/msbuild-concepts.md)
- [TARGETS-Dateien](../msbuild/msbuild-dot-targets-files.md)
