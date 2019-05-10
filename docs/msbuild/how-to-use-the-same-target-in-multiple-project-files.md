---
title: 'Vorgehensweise: Verwenden eines Ziels in mehreren Projektdateien | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, importing
- MSBuild, using the same target in multiple project files
ms.assetid: 163734bd-1bfd-4093-a730-7741fc21742d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8674f0c8ed833ac8db80f30f616aa8b0dbf4cf9f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977176"
---
# <a name="how-to-use-the-same-target-in-multiple-project-files"></a>Vorgehensweise: Verwenden desselben Ziels in mehreren Projektdateien
Wenn Sie mehrere [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]-Projektdateien autorisiert haben, haben Sie möglicherweise festgestellt, dass Sie die gleichen Aufgaben und Ziele in verschiedenen Projektdateien verwenden müssen. Statt die vollständige Beschreibung dieser Aufgaben oder Ziele in jede Projektdatei einzuschließen, können Sie ein Ziel in einer separaten Projektdatei speichern und dieses Projekt anschließend in einem beliebigen anderen Projekt importieren, in dem das Ziel verwendet werden muss.

## <a name="use-the-import-element"></a>Verwenden des Import-Elements
 Das `Import`-Element wird verwendet, um eine Projektdatei in eine andere Projektdatei einzufügen. Die Projektdatei, die importiert wird, muss eine gültige [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]-Projektdatei sein, die wohlgeformtes XML enthält. Das Attribut `Project` gibt den Pfad zur importierten Projektdatei an. Weitere Informationen zu dem `Import`-Element finden Sie unter [Import-Element (MSBuild)](../msbuild/import-element-msbuild.md).

#### <a name="to-import-a-project"></a>So importieren Sie ein Projekt

1. Definieren Sie in der importierten Projektdatei alle Eigenschaften und Elemente, die als Parameter für Eigenschaften und Elemente im importierten Projekt verwendet werden.

2. Verwenden Sie das `Import`-Element zum Importieren des Projekts. Beispiel:

     `<Import Project="MyCommon.targets"/>`

3. Definieren Sie nach dem `Import`-Element alle Eigenschaften und Elemente, mit denen Standarddefinitionen von Eigenschaften und Elementen im importierten Projekt überschrieben werden müssen.

## <a name="order-of-evaluation"></a>Reihenfolge der Auswertung
 Wenn [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] ein `Import`-Element erreicht, wird das importierte Projekt effektiv in das importierte Projekt an den Speicherort des `Import`-Elements eingefügt. Aus diesem Grund kann der Speicherort des `Import`-Elements Auswirkungen auf die Werte der Eigenschaften und Elemente haben. Die Eigenschaften und Elemente, die durch das importierte Projekt festgelegt wurden, und die Eigenschaften und Elemente, die vom importierten Projekt verwendet werden, müssen bekannt sein.

 Wenn das Projekt erstellt wird, werden zunächst alle Eigenschaften ausgewertet, gefolgt von den Elementen. Folgendes XML definiert z.B. die importierte Projektdatei *MyCommon.targets*:

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
        <Name>MyCommon</Name>
    </PropertyGroup>

    <Target Name="Go">
        <Message Text="Name=$(Name)"/>
    </Target>
</Project>
```

 Folgendes XML definiert *MyApp.proj*, worüber *MyCommon.targets* importiert wird:

```xml
<Project
    DefaultTargets="Go"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
        <Name>MyApp</Name>
    </PropertyGroup>
    <Import Project="MyCommon.targets"/>
</Project>
```

 Wenn das Projekt erstellt wird, wird die folgende Nachricht angezeigt:

 `Name="MyCommon"`

 Da der Import des Projekts nach der Definition der Eigenschaft `Name` in *MyApp.proj* erfolgt ist, wird mit der Definition von `Name` in *MyCommon.targets* die Definition in *MyApp.proj* überschrieben. Wenn der Import des Projekts vor der Definition der Eigenschaft „Name“ erfolgt, würde die folgende Nachricht im Build angezeigt werden:

 `Name="MyApp"`

#### <a name="use-the-following-approach-when-importing-projects"></a>Gehen Sie beim Importieren von Projekten wie folgt vor

1. Definieren Sie in der Projektdatei alle Eigenschaften und Elemente, die als Parameter für Eigenschaften und Elemente im importierten Projekt verwendet werden.

2. Importieren Sie das Projekt.

3. Definieren Sie in der Projektdatei alle Eigenschaften und Elemente, mit denen Standarddefinitionen von Eigenschaften und Elementen im importierten Projekt überschrieben werden müssen.

## <a name="example"></a>Beispiel
 Im folgenden Codebeispiel wird die Datei *MyCommon.targets* dargestellt, die im zweiten Codebeispiel importiert wird. Die *TARGETS*-Datei wertet Eigenschaften des importierten Projekts für die Konfiguration des Builds aus.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
        <Flavor Condition="'$(Flavor)'==''">DEBUG</Flavor>
        <Optimize Condition="'$(Flavor)'=='RETAIL'">yes</Optimize>
        <appname>$(MSBuildProjectName)</appname>
    <PropertyGroup>
    <Target Name="Build">
        <Csc Sources="hello.cs"
            Optimize="$(Optimize)"
            OutputAssembly="$(appname).exe"/>
    </Target>
</Project>
```

## <a name="example"></a>Beispiel
 Im folgenden Codebeispiel wird die Datei *MyCommon.targets* importiert.

```xml
<Project DefaultTargets="Build"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
        <Flavor>RETAIL</Flavor>
    </PropertyGroup>
    <Import Project="MyCommon.targets"/>
</Project>
```

## <a name="see-also"></a>Siehe auch
- [Import-Element (MSBuild)](../msbuild/import-element-msbuild.md)
- [Ziele](../msbuild/msbuild-targets.md)