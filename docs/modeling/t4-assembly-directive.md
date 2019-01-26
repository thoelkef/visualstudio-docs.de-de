---
title: T4-Assemblyanweisung
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: d2777f48f4038bfea889e7e85d6cf9c37c1778f3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55000951"
---
# <a name="t4-assembly-directive"></a>T4-Assemblyanweisung

In einer Textvorlage von Visual Studio zur Entwurfszeit die `assembly` Richtlinie lädt eine Assembly, damit im Vorlagencode die Typen verwenden kann. Der Effekt ist vergleichbar mit dem Hinzufügen eines Assemblyverweises in einem Visual Studio-Projekt.

 Eine allgemeine Übersicht über das Schreiben von Textvorlagen finden Sie unter [Schreiben einer T4-Textvorlage](../modeling/writing-a-t4-text-template.md).

> [!NOTE]
>  Die `assembly`-Anweisung ist in einer Laufzeitvorlage (vorverarbeiteten Vorlage) nicht erforderlich. Fügen Sie stattdessen die notwendigen Assemblys hinzu. die **Verweise** von Visual Studio-Projekt.

## <a name="using-the-assembly-directive"></a>Verwenden der Assemblyanweisung
 Die Syntax der Direktive lautet wie folgt:

```
<#@ assembly name="[assembly strong name|assembly file name]" #>
```

 Folgende Optionen stehen zum Angeben des Assemblynamens zur Verfügung:

- Der starke Name einer Assembly im GAC, z. B. `System.Xml.dll`. Sie können auch das lange Formular verwenden, z. B. `name="System.Xml, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"`. Weitere Informationen finden Sie unter <xref:System.Reflection.AssemblyName>.

- Absoluter Pfad der Assembly

  Sie können die `$(variableName)` Syntax, um Visual Studio-Variablen verweisen, z. B. `$(SolutionDir)`, und `%VariableName%` auf Umgebungsvariablen verweisen. Zum Beispiel:

```
<#@ assembly name="$(SolutionDir)\MyProject\bin\Debug\SomeLibrary.Dll" #>
```

 Die assembly-Anweisung hat in einer vorverarbeiteten Textvorlage keinerlei Auswirkungen. Fügen Sie stattdessen die notwendigen Verweise in die **Verweise** Abschnitt der Visual Studio-Projekt. Weitere Informationen finden Sie unter [Run-Time-Textgenerierung mithilfe von T4-Textvorlagen](../modeling/run-time-text-generation-with-t4-text-templates.md).

## <a name="standard-assemblies"></a>Standardassemblys
 Die folgenden Assemblys werden automatisch geladen, damit Sie keine Assemblyanweisungen dafür schreiben müssen:

- `Microsoft.VisualStudio.TextTemplating.1*.dll`

- `System.dll`

- `WindowsBase.dll`

  Wenn Sie eine benutzerdefinierte Anweisung verwenden, lädt der Anweisungsprozessor möglicherweise zusätzliche Assemblys. Wenn Sie z. B. Vorlagen für eine domänenspezifische Sprache (DSL) schreiben, müssen Sie keine Assemblyanweisungen für die folgenden Assemblys schreiben:

- `Microsoft.VisualStudio.Modeling.Sdk.1*.dll`

- `Microsoft.VisualStudio.Modeling.Sdk.Diagrams.1*.dsl`

- `Microsoft.VisualStudio.TextTemplating.Modeling.1*.dll`

- Die Assembly mit der DSL.

## <a name="msbuild"></a> Verwenden von Projekteigenschaften in MSBuild und Visual Studio
 Visual Studio-Makros wie $ (SolutionDir) funktionieren nicht in MSBuild. Wenn Sie Vorlagen im Buildcomputer transformieren möchten, müssen Sie dies mithilfe von Projekteigenschaften tun.

 Bearbeiten Sie die CSPROJ- oder VBPROJ-Datei, und definieren Sie eine Projekteigenschaft. In folgendem Beispiel wird eine Eigenschaft mit dem Namen `myLibFolder` definiert:

```xml
<!-- Define a project property, myLibFolder: -->
<PropertyGroup>
    <myLibFolder>$(MSBuildProjectDirectory)\..\libs</myLibFolder>
</PropertyGroup>

<!-- Tell the MSBuild T4 task to make the property available: -->
<ItemGroup>
    <T4ParameterValues Include="myLibFolder">
      <Value>$(myLibFolder)</Value>
    </T4ParameterValues>
  </ItemGroup>
```

 Nun können Sie die Projekteigenschaft in Textvorlagen verwenden, die sowohl in Visual Studio als auch in MSBuild ordnungsgemäß transformiert werden:

```
<#@ assembly name="$(myLibFolder)\MyLib.dll" #>
```

## <a name="see-also"></a>Siehe auch

- [T4-Include-Direktive](../modeling/t4-include-directive.md)