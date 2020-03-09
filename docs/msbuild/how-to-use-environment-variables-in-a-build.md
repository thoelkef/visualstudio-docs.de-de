---
title: 'Vorgehensweise: Verwenden von Umgebungsvariablen in einem Build | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- environment variables, referencing
- projects [.NET Framework], environment variables
- MSBuild, environment variables
ms.assetid: 7f9e4469-8865-4b59-aab3-3ff26bd36e77
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: afc679f9b782b8bc9ed3e04a2b8fb684cdbc1a20
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633784"
---
# <a name="how-to-use-environment-variables-in-a-build"></a>Vorgehensweise: Verwenden von Umgebungsvariablen in einem Build

Wenn Sie Projekte erstellen, ist es oft erforderlich, Buildoptionen mithilfe der Informationen festzulegen, die sich nicht in der Projektdatei oder in den Dateien befinden, aus denen Ihr Projekt besteht. Diese Informationen werden normalerweise in Umgebungsvariablen gespeichert.

## <a name="reference-environment-variables"></a>Verweisen auf Umgebungsvariablen

 Alle Umgebungsvariablen stehen der Microsoft-Build-Engine (MSBuild)-Projektdatei als Eigenschaften zur Verfügung.

> [!NOTE]
> Wenn das Projekt eine Eigenschaftsdefinition enthält, die denselben Namen wie eine Umgebungsvariable hat, wird der Wert der Umgebungsvariablen von der Eigenschaft im Projekt überschrieben.

#### <a name="to-use-an-environment-variable-in-an-msbuild-project"></a>Verwenden einer Umgebungsvariable in einem MSBuild-Projekt

- Verweisen Sie auf die gleiche Art auf Umgebungsvariablen wie auf eine Variable, die in der Projektdatei deklariert ist. Beispielsweise verweist der folgende Code auf die Umgebungsvariable BIN_PATH:

   `<FinalOutput>$(BIN_PATH)\MyAssembly.dll</FinalOutput>`

  Sie können ein `Condition`-Attribut verwenden, um einen Standardwert für eine Eigenschaft anzugeben, wenn die Umgebungsvariable nicht festgelegt wurde.

#### <a name="to-provide-a-default-value-for-a-property"></a>Gibt den Standardwert für eine Eigenschaft an

- Verwenden eines `Condition`-Attributs für eine Eigenschaft, um einen Wert festzulegen, nur wenn die Eigenschaft keinen Wert hat. Im folgenden Code wird z.B. die `ToolsPath`-Eigenschaft nur auf *c:\tools* festgelegt, wenn die `ToolsPath`-Umgebungsvariable nicht festgelegt ist:

     `<ToolsPath Condition="'$(TOOLSPATH)' == ''">c:\tools</ToolsPath>`

    > [!NOTE]
    > Eigenschaftennamen unterscheiden keine Groß-/Kleinschreibung, sodass jeweils `$(ToolsPath)` und `$(TOOLSPATH)` auf die gleiche Eigenschaft oder Umgebungsvariable verweisen.

## <a name="example"></a>Beispiel

 Die folgende Projektdatei verwendet Umgebungsvariablen, um den Speicherort von Verzeichnissen anzugeben.

```xml
<Project DefaultTargets="FakeBuild">
    <PropertyGroup>
        <FinalOutput>$(BIN_PATH)\myassembly.dll</FinalOutput>
        <ToolsPath Condition=" '$(ToolsPath)' == '' ">
            C:\Tools
        </ToolsPath>
    </PropertyGroup>
    <Target Name="FakeBuild">
        <Message Text="Building $(FinalOutput) using the tools at $(ToolsPath)..."/>
    </Target>
</Project>
```

## <a name="see-also"></a>Siehe auch

- [MSBuild](../msbuild/msbuild.md)
- [MSBuild-Eigenschaften](../msbuild/msbuild-properties.md)
- [How to: Erstellen identischer Quelldateien mit unterschiedlichen Optionen](../msbuild/how-to-build-the-same-source-files-with-different-options.md)
