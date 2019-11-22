---
title: Code Generation in a Build Process | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, build tasks
- text templates, transforming by using msbuild
ms.assetid: 4da43429-2a11-4d7e-b2e0-9e4af7033b5a
caps.latest.revision: 30
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ae28c59f9c5f19e87b833c90e7dbc6bf3b7497ea
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297932"
---
# <a name="code-generation-in-a-build-process"></a>Codegenerierung in einem Buildprozess
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Text transformation can be invoked as part of the build process of a Visual Studio solution. Es gibt Buildaufgaben, die für die Texttransformation angegeben wurden. Die T4-Buildaufgaben führen Entwurfszeittextvorlagen aus und kompilieren gleichzeitig Laufzeitvorlagen (vorverarbeitete Textvorlagen.)

Je nachdem, welche Build-Engine Sie verwenden, können die Buildaufgaben unterschiedliche Ergebnisse haben. When you build the solution in Visual Studio, a text template can access the Visual Studio API (EnvDTE) if the [hostspecific="true"](../modeling/t4-template-directive.md) attribute is set. Dies gilt jedoch nicht, wenn Sie die Projektmappe aus der Befehlszeile erstellen oder wenn Sie einen Serverbuild mit Visual Studio starten. In diesen Fällen wird der Build von MSBuild ausgeführt, und ein anderer T4-Host wird verwendet.

Dies bedeutet, dass Sie auf Elemente wie Projektdateinamen nicht genauso zugreifen können, wie wenn Sie eine Textvorlage in MSBuild erstellen. However, you can [pass environment information into text templates and directive processors by using build parameters](#parameters).

## <a name="buildserver"></a> Configure your machines

To enable build tasks on your development computer, install [Modeling SDK for Visual Studio](https://www.microsoft.com/download/details.aspx?id=48148).

If [your build server](https://msdn.microsoft.com/library/788443c3-0547-452e-959c-4805573813a9) runs on a computer on which Visual Studio is not installed, copy the following files to the build computer from your development machine. Ersetzen Sie "*" durch die aktuellste Versionsnummer.

- $(ProgramFiles)\MSBuild\Microsoft\VisualStudio\v*.0\TextTemplating

  - Microsoft.VisualStudio.TextTemplating.Sdk.Host.*.0.dll

  - Microsoft.TextTemplating.Build.Tasks.dll

  - Microsoft.TextTemplating.targets

- $(ProgramFiles)\Microsoft Visual Studio *.0\VSSDK\VisualStudioIntegration\Common\Assemblies\v4.0

  - Microsoft.VisualStudio.TextTemplating.*.0.dll

  - Microsoft.VisualStudio.TextTemplating.Interfaces.*.0.dll (mehrere Dateien)

  - Microsoft.VisualStudio.TextTemplating.VSHost.*.0.dll

- $(ProgramFiles)\Microsoft Visual Studio *.0\Common7\IDE\PublicAssemblies\

  - Microsoft.VisualStudio.TextTemplating.Modeling.*.0.dll

## <a name="to-edit-the-project-file"></a>So bearbeiten Sie die Projektdatei

Sie müssen die Projektdatei bearbeiten, um einige der Funktionen in MSBuild zu konfigurieren.

In solution explorer, choose **Unload** from the context menu of your project. Damit können Sie die CSPROJ- oder VBPROJ-Datei im XML-Editor zu bearbeiten.

When you’ve finished editing, choose **Reload**.

## <a name="import-the-text-transformation-targets"></a>Importieren der Texttransformationsziele

Suchen Sie wie folgt eine Zeile in der VBPROJ-Datei oder in der CSPROJ-Datei:

`<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />`

\- oder -

`<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />`

Fügen Sie nach dieser Zeile den Textvorlagenimport ein:

```xml
<!-- Optionally make the import portable across VS versions -->
  <PropertyGroup>
    <!-- Get the Visual Studio version – defaults to 10: -->
    <VisualStudioVersion Condition="'$(VisualStudioVersion)' == ''">10.0</VisualStudioVersion>
    <!-- Keep the next element all on one line: -->
    <VSToolsPath Condition="'$(VSToolsPath)' == ''">$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)</VSToolsPath>
  </PropertyGroup>

<!-- This is the important line: -->
  <Import Project="$(VSToolsPath)\TextTemplating\Microsoft.TextTemplating.targets" />
```

## <a name="transforming-templates-in-a-build"></a>Transformieren von Vorlagen in einem Build

Einige Eigenschaften, die Sie in die Projektdatei einfügen können, um die Transformationsaufgabe zu steuern:

- Führen Sie die Transformierensaufgabe am Anfang jedes Builds aus:

    ```xml
    <PropertyGroup>
        <TransformOnBuild>true</TransformOnBuild>
    </PropertyGroup>
    ```

- Überschreiben Sie Dateien, die schreibgeschützt sind, weil sie z. B. nicht ausgecheckt sind:

    ```xml
    <PropertyGroup>
        <OverwriteReadOnlyOutputFiles>true</OverwriteReadOnlyOutputFiles>
    </PropertyGroup>
    ```

- Transformieren Sie jede Vorlage jedes Mal:

    ```xml
    <PropertyGroup>
        <TransformOutOfDateOnly>false</TransformOutOfDateOnly>
    </PropertyGroup>
    ```

     Standardmäßig generiert die Aufgabe T4 MSBuild erneut eine Ausgabedatei, wenn diese älter als die entsprechende Vorlagendatei oder alle Dateien ist, auf die die Vorlage oder ein Direktivenprozessor, der die Datei verwendet, zuvor zugegriffen hat. Beachten Sie, dass hierbei ein viel leistungsstärkerer Abhängigkeitstest durchgeführt wird als mit dem Befehl zur Transformation aller Vorlagen in Visual Studio, bei dem nur die Daten der Vorlage und der Ausgabedatei verglichen werden.

Wenn Sie nur die Texttransformationen im Projekt ausführen möchten, rufen Sie die Aufgabe „TransformAll“ auf:

`msbuild myProject.csproj /t:TransformAll`

Zur Transformation einer bestimmten Textvorlage:

`msbuild myProject.csproj /t:Transform /p:TransformFile="Template1.tt"`

In TransformFile können Sie Platzhalter verwenden:

`msbuild dsl.csproj /t:Transform /p:TransformFile="GeneratedCode\**\*.tt"`

## <a name="source-control"></a>Quellcodeverwaltung

Es besteht keine spezifische integrierte Integration in ein Quellcodeverwaltungssystem. Sie können jedoch auch eigene Erweiterungen z. B. zum Einchecken oder Auschecken einer generierten Datei hinzufügen. Standardmäßig wird durch die Texttransformationsaufgabe vermieden, dass eine als schreibgeschützt markierte Datei überschrieben wird. Wenn eine solche Datei erkannt wird, wird ein Fehler in der Fehlerliste von Visual Studio protokolliert, und die Aufgabe schlägt fehl.

Fügen Sie die folgende Eigenschaft ein, um anzugeben, dass schreibgeschützte Dateien überschrieben werden sollen:

`<OverwriteReadOnlyOutputFiles>true</OverwriteReadOnlyOutputFiles>`

Sofern Sie den Nachverarbeitungsschritt nicht anpassen, wird eine Warnung in der Fehlerliste protokolliert, wenn eine Datei überschrieben wird.

## <a name="customizing-the-build-process"></a>Anpassen des Buildprozesses

Texttransformation geschieht vor anderen Aufgaben im Buildprozess. Sie können Aufgaben definieren, die vor und nach der Transformation aufgerufen werden, indem Sie die Eigenschaften `$(BeforeTransform)` und `$(AfterTransform)` festlegen:

```xml
<PropertyGroup>
    <BeforeTransform>CustomPreTransform</BeforeTransform>
    <AfterTransform>CustomPostTransform</AfterTransform>
  </PropertyGroup>
  <Target Name="CustomPreTransform">
    <Message Text="In CustomPreTransform..." Importance="High" />
  </Target>
  <Target Name="CustomPostTransform">
    <Message Text="In CustomPostTransform..." Importance="High" />
  </Target>
```

In `AfterTransform` können Sie auf Dateilisten verweisen:

- GeneratedFiles – Eine Liste von Dateien, die vom Prozess geschrieben werden. Für die Dateien, durch die vorhandene schreibgeschützte Dateien überschrieben wurden, ist %(GeneratedFiles.ReadOnlyFileOverwritten) true. Diese Dateien können aus der Quellcodeverwaltung ausgecheckt werden.

- NonGeneratedFiles– Eine Liste von schreibgeschützten Dateien, die nicht überschrieben wurden.

  Sie definieren z. B. eine Aufgabe zum Auschecken von GeneratedFiles.

## <a name="outputfilepath-and-outputfilename"></a>OutputFilePath und OutputFileName

Diese Eigenschaften werden nur von MSBuild verwendet. Sie beeinflussen nicht die Codegenerierung in Visual Studio. Sie leiten die generierte Ausgabedatei in einen anderen Ordner oder eine andere Datei um. Der Zielordner muss bereits vorhanden sein.

```xml
<ItemGroup>
  <None Include="MyTemplate.tt">
    <Generator>TextTemplatingFileGenerator</Generator>
    <OutputFilePath>MyFolder</OutputFilePath>
    <LastGenOutput>MyTemplate.cs</LastGenOutput>
  </None>
</ItemGroup>
```

Ein hilfreicher Ordner für die Umleitung ist `$(IntermediateOutputPath).`

Wenn Sie einen Ausgabedateinamen angeben, hat dieser Vorrang vor der Erweiterung, die in der output-Direktive in den Vorlagen angegeben ist.

```xml
<ItemGroup>
  <None Include="MyTemplate.tt">
    <Generator>TextTemplatingFileGenerator</Generator>
    <OutputFileName>MyOutputFileName.cs</OutputFileName>
    <LastGenOutput>MyTemplate.cs</LastGenOutput>
  </None>
</ItemGroup>
```

Es wird nicht empfohlen, OutputFileName oder OutputFilePath anzugeben, wenn Sie außerdem in VS mit „Alle transformieren“ Vorlagen transformieren oder einen Generator einzelner Dateien ausführen. Je nachdem, wie Sie die Transformation ausgelöst haben, erhalten Sie dann unterschiedliche Dateipfade. Dies kann sehr verwirrend sein.

## <a name="adding-reference-and-include-paths"></a>Hinzufügen von Verweis- und Includepfaden

Der Host verfügt über einen Standardsatz an Pfaden, in denen er nach Assemblys sucht, auf die von Vorlagen verwiesen wird. So fügen Sie diesem Satz Pfade hinzu:

```
<ItemGroup>
    <T4ReferencePath Include="$(VsIdePath)PublicAssemblies\" />
    <!-- Add more T4ReferencePath items here -->
</ItemGroup>
```

Stellen Sie eine durch Semikolons getrennte Liste bereit, um die Ordner festzulegen, in denen nach Includedateien gesucht wird. Normalerweise fügen Sie der vorhandenen Liste Pfade hinzu.

```
<PropertyGroup>
    <IncludeFolders>
$(IncludeFolders);$(MSBuildProjectDirectory)\Include;AnotherFolder;And\Another</IncludeFolders>
</PropertyGroup>
```

## <a name="parameters"></a> Pass build context data into the templates

Sie können Parameterwerte in der Projektdatei festlegen. For example, you can pass build properties and [environment variables](../msbuild/how-to-use-environment-variables-in-a-build.md):

```xml
<ItemGroup>
  <T4ParameterValues Include="ProjectFolder">
    <Value>$(ProjectDir)</Value>
    <Visible>false</Visible>
  </T4ParameterValues>
</ItemGroup>
```

Legen Sie in einer Textvorlage `hostspecific` in der template-Direktive fest. Use the [parameter](../modeling/t4-parameter-directive.md) directive to get values:

```
<#@template language="c#" hostspecific="true"#>
<#@ parameter type="System.String" name="ProjectFolder" #>
The project folder is: <#= ProjectFolder #>
```

## <a name="msbuild"></a> Using project properties in assembly and include directives

Visual Studio-Makros wie $ (SolutionDir) funktionieren nicht in MSBuild. Sie können stattdessen Projekteigenschaften verwenden.

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

Nun können Sie die Projekteigenschaft in der Assembly- und der Includedirektive verwenden:

```
<#@ assembly name="$(myLibFolder)\MyLib.dll" #>
<#@ include file="$(myLibFolder)\MyIncludeFile.t4" #>
```

 Diese Direktiven rufen Werte von T4parameterValues in MSBuild- und Visual Studio-Hosts ab.

## <a name="q--a"></a>Fragen und Antworten

**Why would I want to transform templates in the build server? I already transformed templates in Visual Studio before I checked in my code.**

Wenn Sie eine eingeschlossene Datei oder eine andere Datei, die von der Vorlage gelesen wird, aktualisieren, wird diese Datei nicht automatisch von Visual Studio transformiert. Durch die Transformation von Vorlagen im Rahmen des Build wird sichergestellt, dass alle Teile aktuell sind.

**What other options are there for transforming text templates?**

- The [TextTransform utility](../modeling/generating-files-with-the-texttransform-utility.md) can be used in command scripts. In den meisten Fällen ist es einfacher, MSBuild zu verwenden.

- [Aufrufen von Texttransformation in einer VS-Erweiterung](../modeling/invoking-text-transformation-in-a-vs-extension.md)

- [Design-time text templates](../modeling/design-time-code-generation-by-using-t4-text-templates.md) are transformed by Visual Studio.

- [Run time text templates](../modeling/run-time-text-generation-with-t4-text-templates.md) are transformed at run time in your application.

## <a name="read-more"></a>Weitere Informationen

Hier finden Sie eine gute Anleitung zur T4 MSbuild-Vorlage, $(VSToolsPath)\TextTemplating\Microsoft.TextTemplating.targets

- [Schreiben einer T4-Textvorlage](../modeling/writing-a-t4-text-template.md)
- [Visual Studio Visualization and Modeling SDK](https://go.microsoft.com/fwlink/?LinkID=185579)
- [Oleg Sych: Understanding T4:MSBuild Integration](https://github.com/olegsych/T4Toolbox)
