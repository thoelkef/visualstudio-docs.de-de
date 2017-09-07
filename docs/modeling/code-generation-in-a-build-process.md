---
title: Codegenerierung in einem Buildprozess mit | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text templates, build tasks
- text templates, transforming by using msbuild
ms.assetid: 4da43429-2a11-4d7e-b2e0-9e4af7033b5a
caps.latest.revision: 28
author: alancameronwills
ms.author: awills
manager: douge
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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 6cfdd28afbfb88f83d7931b57adbedfb88bf93bf
ms.contentlocale: de-de
ms.lasthandoff: 09/06/2017

---
# <a name="code-generation-in-a-build-process"></a>Codegenerierung in einem Buildprozess
[TextTransformation](../modeling/code-generation-and-t4-text-templates.md) ausgerufen werden als Teil der [Buildprozess](http://msdn.microsoft.com/Library/a971b0f9-7c28-479d-a37b-8fd7e27ef692) von einer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Lösung. Es gibt Buildaufgaben, die für die Texttransformation angegeben wurden. Die T4-Buildaufgaben führen Entwurfszeittextvorlagen aus und kompilieren gleichzeitig Laufzeitvorlagen (vorverarbeitete Textvorlagen.)  
  
 Je nachdem, welches Buildmodul Sie verwenden, können die Buildaufgaben unterschiedliche Ergebnisse haben. Wenn Sie die Projektmappe in Visual Studio erstellen, eine Textvorlage kann zugreifen, die Visual Studio-API (EnvDTE) Wenn die [Hostspecific = "true"](../modeling/t4-template-directive.md) -Attribut festgelegt ist. Jedoch, die nicht "true", wenn Sie die Projektmappe über die Befehlszeile erstellen oder wenn Sie einen Serverbuild mit Visual Studio starten. In diesen Fällen wird der Build von MSBuild ausgeführt, und ein anderer T4-Host wird verwendet.  
  
 Dies bedeutet, dass Sie Elemente wie Projektdateinamen nicht genauso zugreifen können, bei der Erstellung einer Textvorlage in MSBuild. Sie können jedoch [übergeben Sie Umgebungsinformationen mit Buildparametern in Textvorlagen und Direktivenprozessoren](#parameters).  
  
##  <a name="buildserver"></a>Konfigurieren des Computers  
 Um Buildaufgaben auf dem Entwicklungscomputer zu ermöglichen, installieren Sie Modellierungs-SDK für Visual Studio.
 
[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

 Wenn [dem Buildserver](http://msdn.microsoft.com/Library/788443c3-0547-452e-959c-4805573813a9) ausgeführt wird, auf einem Computer, auf dem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ist nicht installiert, die folgenden Dateien vom Entwicklungscomputer auf den Buildcomputer kopieren. Ersetzen Sie die aktuellste Versionsnummer für "*".  
  
-   $(ProgramFiles)\MSBuild\Microsoft\VisualStudio\v*.0\TextTemplating  
  
    -   Microsoft.VisualStudio.TextTemplating.Sdk.Host.*.0.dll  
  
    -   Microsoft.TextTemplating.Build.Tasks.dll  
  
    -   Microsoft.TextTemplating.targets  
  
-   $(ProgramFiles)\Microsoft Visual Studio *.0\VSSDK\VisualStudioIntegration\Common\Assemblies\v4.0  
  
    -   Microsoft.VisualStudio.TextTemplating.*.0.dll  
  
    -   Microsoft.VisualStudio.TextTemplating.Interfaces.*.0.dll (mehrere Dateien)  
  
    -   Microsoft.VisualStudio.TextTemplating.VSHost.*.0.dll  
  
-   $(ProgramFiles)\Microsoft Visual Studio *.0\Common7\IDE\PublicAssemblies\  
  
    -   Microsoft.VisualStudio.TextTemplating.Modeling.*.0.dll  
  
## <a name="to-edit-the-project-file"></a>So bearbeiten Sie die Projektdatei  
 Sie müssen zum Bearbeiten der Projektdatei, um einige der Funktionen in MSBuild zu konfigurieren.  
  
 Wählen Sie im Projektmappen-Explorer **entladen** aus dem Kontextmenü des Projekts. Damit können Sie die CSPROJ- oder VBPROJ-Datei im XML-Editor zu bearbeiten.  
  
 Wenn Sie die Bearbeitung abgeschlossen haben, wählen Sie **zum erneuten Laden**.  
  
## <a name="import-the-text-transformation-targets"></a>Importieren der Texttransformationsziele  
 Suchen Sie wie folgt eine Zeile in der VBPROJ-Datei oder in der CSPROJ-Datei:  
  
 `<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />`  
  
 \- oder –  
  
 `<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />`  
  
 Fügen Sie nach dieser Zeile den Textvorlagenimport ein:  
  
```xml  
<!-- Optionally make the import portable across VS versions -->  
  <PropertyGroup>  
    <!-- Get the Visual Studio version - defaults to 10: -->  
    <VisualStudioVersion Condition="'$(VisualStudioVersion)' == ''">10.0</VisualStudioVersion>  
    <!-- Keep the next element all on one line: -->  
    <VSToolsPath Condition="'$(VSToolsPath)' == ''">$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)</VSToolsPath>  
  </PropertyGroup>  
  
<!-- This is the important line: -->  
  <Import Project="$(VSToolsPath)\TextTemplating\Microsoft.TextTemplating.targets" />  
```  
  
## <a name="transforming-templates-in-a-build"></a>Transformieren von Vorlagen in einem Build  
 Einige Eigenschaften, die Sie in die Projektdatei einfügen können, um die Transformationsaufgabe zu steuern:  
  
-   Führen Sie die Transformationsaufgabe am Anfang jedes Builds aus:  
  
    ```xml  
    <PropertyGroup>  
        <TransformOnBuild>true</TransformOnBuild>  
    </PropertyGroup>  
    ```  
  
-   Überschreiben Sie Dateien, die schreibgeschützt sind, weil sie z. B. nicht ausgecheckt sind:  
  
    ```xml  
    <PropertyGroup>  
        <OverwriteReadOnlyOutputFiles>true</OverwriteReadOnlyOutputFiles>  
    </PropertyGroup>  
    ```  
  
-   Transformieren Sie jede Vorlage jedes Mal:  
  
    ```xml  
    <PropertyGroup>  
        <TransformOutOfDateOnly>false</TransformOutOfDateOnly>  
    </PropertyGroup>  
    ```  
  
     Standardmäßig generiert die Aufgabe T4 MSBuild erneut eine Ausgabedatei, wenn diese älter als die entsprechende Vorlagendatei oder alle Dateien ist, auf die die Vorlage oder ein Direktivenprozessor, der die Datei verwendet, zuvor zugegriffen hat. Beachten Sie, dass hierbei ein viel leistungsstärkerer Abhängigkeitstest durchgeführt wird als mit dem Befehl zur Transformation aller Vorlagen in Visual Studio, bei dem nur die Daten der Vorlage und der Ausgabedatei verglichen werden.  
  
 Wenn Sie nur die Texttransformationen im Projekt ausführen möchten, rufen Sie die Aufgabe "TransformAll" auf:  
  
 `msbuild myProject.csproj /t:TransformAll`  
  
 Zur Transformation einer bestimmten Textvorlage:  
  
 `msbuild myProject.csproj /t:Transform /p:TransformFile="Template1.tt"`  
  
 In TransformFile können Sie Platzhalter verwenden:  
  
 `msbuild dsl.csproj /t:Transform /p:TransformFile="GeneratedCode\**\*.tt"`  
  
## <a name="source-control"></a>Quellcodeverwaltung  
 Es besteht keine spezifische integrierte Integration in ein Quellcodeverwaltungssystem. Sie können jedoch auch eigene Erweiterungen z. B. zum Einchecken oder Auschecken einer generierten Datei hinzufügen. Standardmäßig wird durch die Texttransformationsaufgabe vermieden, dass eine als schreibgeschützt markierte Datei überschrieben wird. Wenn eine solche Datei erkannt wird, wird ein Fehler in der Fehlerliste von Visual Studio protokolliert, und die Aufgabe schlägt fehl.  
  
 Fügen Sie die folgende Eigenschaft ein, um anzugeben, dass schreibgeschützte Dateien überschrieben werden sollen:  
  
 `<OverwriteReadOnlyOuputFiles>true</OverwriteReadOnlyOuputFiles>`  
  
 Sofern Sie den Nachverarbeitungsschritt nicht anpassen, wird eine Warnung in der Fehlerliste protokolliert, wenn eine Datei überschrieben wird.  
  
## <a name="customizing-the-build-process"></a>Anpassen des Buildprozesses  
 Texttransformation geschieht vor anderen Aufgaben im Buildprozess. Sie können Aufgaben definieren, die vor und nach der Transformation aufgerufen werden, indem Sie die Eigenschaften `$(BeforeTransform)` und `$(AfterTransform)` festlegen:  
  
```  
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
  
-   GeneratedFiles – Eine Liste von Dateien, die vom Prozess geschrieben werden. Für die Dateien, durch die vorhandene schreibgeschützte Dateien überschrieben wurden, ist %(GeneratedFiles.ReadOnlyFileOverwritten) true. Diese Dateien können aus der Quellcodeverwaltung ausgecheckt werden.  
  
-   NonGeneratedFiles– Eine Liste von schreibgeschützten Dateien, die nicht überschrieben wurden.  
  
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
  
 Wenn Sie einen Ausgabedateinamen angeben, hat dieser Vorrang vor der Erweiterung, die in der output-Anweisung in den Vorlagen angegeben ist.  
  
```xml  
<ItemGroup>  
  <None Include="MyTemplate.tt">  
    <Generator>TextTemplatingFileGenerator</Generator>  
    <OutputFileName>MyOutputFileName.cs</OutputFileName>  
    <LastGenOutput>MyTemplate.cs</LastGenOutput>  
  </None>  
</ItemGroup>  
```  
  
 Eine OutputFileName oder OutputFilePath angeben, wird nicht empfohlen, wenn Sie auch Vorlagen in VS mit allen zu transformieren, einzelner Dateien ausgeführt werden. Je nachdem, wie Sie die Transformation ausgelöst haben, erhalten Sie dann unterschiedliche Dateipfade. Dies kann sehr verwirrend sein.  
  
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
  
##  <a name="parameters"></a>Übergeben der buildkontextdaten in die Vorlagen  
 Sie können Parameterwerte in der Projektdatei festlegen. Sie können z. B. übergeben [erstellen](../msbuild/msbuild-properties.md) Eigenschaften und [Umgebungsvariablen](../msbuild/how-to-use-environment-variables-in-a-build.md):  
  
```xml  
<ItemGroup>  
  <T4ParameterValues Include="ProjectFolder">  
    <Value>$(ProjectDir)</Value>  
    <Visible>false</Visible>  
  </T4ParameterValues>  
</ItemGroup>  
```  
  
 Legen Sie in einer Textvorlage `hostspecific` in der template-Direktive fest. Verwenden der [Parameter](../modeling/t4-parameter-directive.md) Richtlinie, um Werte zu erhalten:  
  
```  
<#@template language="c#" hostspecific="true"#>  
<#@ parameter type="System.String" name="ProjectFolder" #>  
The project folder is: <#= ProjectFolder #>  
  
```  
  
 In einem Direktivenprozessor können Sie <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost.ResolveParameterValue%2A> aufrufen:  
  
```csharp  
string value = Host.ResolveParameterValue("-", "-", "parameterName");  
```  
  
```vb  
Dim value = Host.ResolveParameterValue("-", "-", "parameterName")  
```  
  
> [!NOTE]
>  `ResolveParameterValue` ruft Daten nur dann aus `T4ParameterValues` ab, wenn Sie MSBuild verwenden. Wenn Sie die Vorlage mit Visual Studio transformieren, haben die Parameter Standardwerte.  
  
##  <a name="msbuild"></a>Verwenden von Projekteigenschaften in der Assembly- und Includedirektive  
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
 **Warum sollte ich Vorlagen im Buildserver transformieren? Ich habe haben bereits Vorlagen in Visual Studio transformiert, bevor ich meinen Code eingecheckt.**  
  
 Wenn Sie eine eingeschlossene Datei oder eine andere Datei, die von der Vorlage gelesen wird, aktualisieren, nicht auf Visual Studio die Datei automatisch transformiert werden. Transformieren von Vorlagen im Rahmen des Build wird sichergestellt ist, dass alle auf dem neuesten Stand.  
  
 **Welche anderen Optionen gibt es zur Transformation von Textvorlagen?**  
  
-   Die [Hilfsprogramm "TextTransform"](../modeling/generating-files-with-the-texttransform-utility.md) in den Befehlsskripten verwendet werden können. In den meisten Fällen ist es einfacher, MSBuild zu verwenden.  
  
-   [Aufrufen von Texttransformation in einer VS-Erweiterung](../modeling/invoking-text-transformation-in-a-vs-extension.md)  
  
-   [Während der Entwurfszeit-Textvorlagen](../modeling/design-time-code-generation-by-using-t4-text-templates.md) werden von Visual Studio transformiert.  
  
-   [Laufzeittextvorlagen](../modeling/run-time-text-generation-with-t4-text-templates.md) werden zur Laufzeit in der Anwendung transformiert.  
  
## <a name="read-more"></a>Weitere Informationen  
 Hier finden Sie eine gute Anleitung zur T4 MSbuild-Vorlage, $(VSToolsPath)\TextTemplating\Microsoft.TextTemplating.targets  
  
 [Schreiben einer T4-Textvorlage](../modeling/writing-a-t4-text-template.md)  
  
 [Oleg Sych: Grundlegendes T4:MSBuild-Integration](http://www.olegsych.com/2010/04/understanding-t4-msbuild-integration/)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]


