---
title: MSBuild-Ziele | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, targets
ms.assetid: 8060b4d2-e4a9-48cf-a437-852649ceb417
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: afa9be494aaaf79b7235cb9af2393406a6e49abf
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56634421"
---
# <a name="msbuild-targets"></a>MSBuild-Ziele
Durch Ziele werden Aufgaben in einer bestimmten Reihenfolge gruppiert, und der Buildprozess kann in kleinere Einheiten aufgeteilt werden. Ein Ziel kann beispielsweise alle Dateien im Ausgabeverzeichnis zur Vorbereitung auf den Build löschen, während ein anderes die Eingaben für das Projekt kompiliert und diese in einem leeren Verzeichnis platziert. Weitere Informationen zu Aufgaben finden Sie unter [Aufgaben](../msbuild/msbuild-tasks.md).

## <a name="declare-targets-in-the-project-file"></a>Deklarieren von Zielen in der Projektdatei
 Ziele werden in der Projektdatei mithilfe des [Target](../msbuild/target-element-msbuild.md)-Elements deklariert. Die folgende XML erstellt beispielsweise ein Ziel namens „Construct“, das dann die Csc-Aufgabe mit dem Elementtyp „Compile“ aufruft.

```xml
<Target Name="Construct">
    <Csc Sources="@(Compile)" />
</Target>
```

 Ziele können genau wie MSBuild-Eigenschaften neu definiert werden. Ein auf ein Objekt angewendeter

```xml
<Target Name="AfterBuild" >
    <Message Text="First occurrence" />
</Target>
<Target Name="AfterBuild" >
    <Message Text="Second occurrence" />
</Target>
```

 Wenn AfterBuild ausgeführt wird, wird nur „Second occurrence“ (Zweites Vorkommen) angezeigt.

## <a name="target-build-order"></a>Buildreihenfolge für Ziele
 Ziele müssen geordnet werden, wenn die Eingabe für ein Ziel von der Ausgabe eines anderen Ziels abhängt. Es gibt mehrere Möglichkeiten, um die Reihenfolge anzugeben, in der die Ziele ausgeführt werden.

-   Ursprüngliche Ziele

-   Standardziele

-   Erstes Ziel

-   Zielabhängigkeiten

-   `BeforeTargets` und `AfterTargets` (MSBuild 4.0)

Ein Ziel wird während eines einzelnen Builds nie zweimal ausgeführt, auch wenn ein nachfolgendes Ziel im Build von diesem abhängt. Sobald ein Ziel ausgeführt wird, ist sein Beitrag zum Build abgeschlossen.

Ausführlichere Informationen zur Buildreihenfolge für Ziele finden Sie unter [Buildreihenfolge für Ziele](../msbuild/target-build-order.md).

## <a name="target-batching"></a>Zielbatchverarbeitung
Ein Zielelement kann ein `Outputs`-Attribut enthalten, das Metadaten im Format %(\<Metadaten>) angibt. Wenn dies der Fall ist, führt MSBuild das Ziel einmal für jeden eindeutigen Metadatenwert aus und gruppiert die Elemente, die diesen Metadatenwert aufweisen. Ein auf ein Objekt angewendeter

```xml
<ItemGroup>
    <Reference Include="System.Core">
      <RequiredTargetFramework>3.5</RequiredTargetFramework>
    </Reference>
    <Reference Include="System.Xml.Linq">
      <RequiredTargetFramework>3.5</RequiredTargetFramework>
    </Reference>
    <Reference Include="Microsoft.CSharp">
      <RequiredTargetFramework>4.0</RequiredTargetFramework>
    </Reference>
</ItemGroup>
<Target Name="AfterBuild"
    Outputs="%(Reference.RequiredTargetFramework)">
    <Message Text="Reference:
      @(Reference->'%(RequiredTargetFramework)')" />
</Target>
```

 Die Verweiselemente werden nach ihren RequiredTargetFramework-Metadaten gruppiert. Die Ausgabe des Ziels sieht folgendermaßen aus:

```
Reference: 3.5;3.5
Reference: 4.0
```

 Die Zielbatchverarbeitung wird in tatsächlichen Builds selten verwendet. Die Aufgabenbatchverarbeitung wird häufiger verwendet. Weitere Informationen finden Sie unter [MSBuild Batching (Batchverarbeitung)](../msbuild/msbuild-batching.md).

## <a name="incremental-builds"></a>Inkrementelle Builds
 Inkrementelle Builds sind Buildvorgänge, die so optimiert werden, dass Ziele mit Ausgabedateien, die hinsichtlich der zugehörigen Eingabedateien aktuell sind, nicht ausgeführt werden. Ein Zielelement kann über das `Inputs`- und das `Outputs`-Attribut verfügen, die angeben, welche Elemente das Ziel als Eingabe erwartet und welche es als Ausgabe erzeugt.

 Wenn alle Ausgabeelemente aktuell sind, überspringt MSBuild das Ziel, wodurch die Buildgeschwindigkeit deutlich verbessert wird. Dies wird als inkrementeller Build des Ziels bezeichnet. Wenn nur einige Dateien aktuell sind, führt MSBuild das Ziel ohne die aktuellen Elemente aus. Dies wird als partiell inkrementeller Build des Ziels bezeichnet. Weitere Informationen finden Sie unter [Incremental Builds (Inkrementelle Builds)](../msbuild/incremental-builds.md).

## <a name="see-also"></a>Siehe auch
- [MSBuild-Grundlagen](../msbuild/msbuild-concepts.md)
- [Vorgehensweise: Verwenden desselben Ziels in mehreren Projektdateien](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md)