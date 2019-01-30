---
title: MarkupCompilePass1-Aufgabe | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- converting XAML to binary format [WPF MSBuild]
- MarkupCompilePass1 task [WPF MSBuild], parameters
- converting XAML projects to compiled binary format [WPF MSBuild]
- MarkupCompilePass1 task [WPF MSBuild], converting XAML to binary format
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cb5f9ec3f2db14369cf8f469b718b027fd394649
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55027333"
---
# <a name="markupcompilepass1-task"></a>MarkupCompilePass1-Aufgabe

Der <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1>-Task konvertiert nicht lokalisierte [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)]-Projektdateien in kompiliertes Binärformat.

## <a name="task-parameters"></a>Aufgabenparameter

| Parameter | Beschreibung |
| - | - |
| `AllGeneratedFiles` | Optionaler **ITaskItem[]**-Ausgabeparameter.<br /><br /> Enthält eine vollständige Liste von Dateien, die vom <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1>-Task generiert werden. |
| `AlwaysCompileMarkupFilesInSeparateDomain` | Optionaler **Boolean**-Parameter.<br /><br /> Gibt an, ob der Task in einer separaten <xref:System.AppDomain> ausgeführt werden soll. Wenn dieser Parameter **FALSE** zurückgibt, wird der Task in der gleichen <xref:System.AppDomain> wie [!INCLUDE[TLA#tla_msbuild](../msbuild/includes/tlasharptla_msbuild_md.md)] und schneller ausgeführt. Wenn der Parameter **TRUE** zurückgibt, wird der Task in einer zweiten <xref:System.AppDomain>, die von [!INCLUDE[TLA2#tla_msbuild](../msbuild/includes/tla2sharptla_msbuild_md.md)] isoliert ist, und langsamer ausgeführt. |
| `ApplicationMarkup` | Optionaler **ITaskItem[]**-Parameter.<br /><br /> Gibt den Namen der Anwendungsdefinitions-[!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]-Datei an. |
| `AssembliesGeneratedDuringBuild` | Optionaler **String[]**-Parameter.<br /><br /> Gibt Verweise auf Assemblys an, die sich während des Buildprozesses ändern. Eine Visual Studio-Projektmappe kann möglicherweise ein Projekt enthalten, das auf die kompilierte Ausgabe eines anderen Projekts verweist. In diesem Fall kann die kompilierte Ausgabe des zweiten Projekts dem **AssembliesGeneratedDuringBuild**-Parameter hinzugefügt werden.<br /><br /> Hinweis: Der **AssembliesGeneratedDuringBuild**-Parameter muss Verweise auf den vollständigen Satz von Assemblys enthalten, die von einer Projektmappe generiert werden. |
| `AssemblyName` | Erforderlicher **String**-Parameter.<br /><br /> Gibt den Kurznamen der Assembly an, die für ein Projekt generiert wird. Wenn ein Projekt z.B. eine ausführbare [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)]-Datei mit dem Namen *WinExeAssembly.exe* generiert, hat der **AssemblyName**-Parameter den Wert **WinExeAssembly**. |
| `AssemblyPublicKeyToken` | Optionaler **String**-Parameter.<br /><br /> Gibt das öffentliche Schlüsseltoken für die Assembly an. |
| `AssemblyVersion` | Optionaler **String**-Parameter.<br /><br /> Gibt die Versionsnummer der Assembly an. |
| `ContentFiles` | Optionaler **ITaskItem[]**-Parameter.<br /><br /> Gibt die Liste loser Inhaltsdateien an. |
| `DefineConstants` | Optionaler **String**-Parameter.<br /><br /> Gibt an, dass der aktuelle Wert von **DefineConstants** beibehalten wird. Dies betrifft die Generierung der Zielassembly. Wenn dieser Parameter geändert wird, könnte die öffentliche API in der Zielassembly geändert und die Kompilierung der [!INCLUDE[TLA2#tla_titlexaml](../msbuild/includes/tla2sharptla_titlexaml_md.md)]-Dateien, die auf lokale Typen verweisen, beeinträchtigt werden. |
| `ExtraBuildControlFiles` | Optionaler **ITaskItem[]**-Parameter.<br /><br /> Gibt eine Liste der Dateien an, die steuern, ob ein erneutes Erstellen ausgelöst wird, wenn der <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1>-Task erneut ausgeführt wird. Ein erneutes Erstellen wird ausgelöst, wenn eine dieser Dateien geändert wird. |
| `GeneratedBamlFiles` | Optionaler **ITaskItem[]**-Ausgabeparameter.<br /><br /> Enthält die Liste der generierten Dateien im [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]-Binärformat. |
| `GeneratedCodeFiles` | Optionaler **ITaskItem[]**-Ausgabeparameter.<br /><br /> Enthält die Liste der generierten Dateien mit verwaltetem Code. |
| `GeneratedLocalizationFiles` | Optionaler **ITaskItem[]**-Ausgabeparameter.<br /><br /> Enthält die Liste der Lokalisierungsdateien, die für jede lokalisierbare [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]-Datei generiert wurden. |
| `HostInBrowser` | Optionaler **String**-Parameter.<br /><br /> Gibt an, ob die generierte Assembly eine [!INCLUDE[TLA#tla_xbap](../msbuild/includes/tlasharptla_xbap_md.md)] ist. Die gültigen Optionen sind **true** und **false**. Wenn **true**, wird Code generiert, um das Hosten in einem Browser zu unterstützen. |
| `KnownReferencePaths` | Optionaler **String[]**-Parameter.<br /><br /> Gibt Verweise auf Assemblys an, die sich während des Buildprozesses nicht ändern. Enthält Assemblys, die in einem [!INCLUDE[TLA#tla_gac](../msbuild/includes/tlasharptla_gac_md.md)] gespeichert sind, in einem [!INCLUDE[TLA#tla_netframewk](../misc/includes/tlasharptla_netframewk_md.md)]-Installationsverzeichnis usw. |
| `Language` | Erforderlicher **String**-Parameter.<br /><br /> Gibt die verwaltete Sprache an, die der Compiler unterstützt. Die gültigen Optionen sind **C#**, **VB**, **JScript** und **C++**. |
| `LanguageSourceExtension` | Optionaler **String**-Parameter.<br /><br /> Gibt die Erweiterung an, die der Erweiterung der generierten Datei mit verwaltetem Code angefügt wird:<br /><br /> `<Filename>.g<LanguageSourceExtension>`<br /><br /> Wenn für den **LanguageSourceExtension**-Parameter kein bestimmter Wert festgelegt ist, wird die standardmäßige Quelldateinamen-Erweiterung für eine Sprache verwendet: *.vb* für [!INCLUDE[TLA#tla_visualb](../msbuild/includes/tlasharptla_visualb_md.md)], *.csharp* für [!INCLUDE[TLA#tla_cshrp](../data-tools/includes/tlasharptla_cshrp_md.md)]. |
| `LocalizationDirectivesToLocFile` | Optionaler **String**-Parameter.<br /><br /> Gibt an, wie Lokalisierungsinformationen für jede Quell-[!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]-Datei generiert werden. Die gültigen Optionen sind **None**, **CommentsOnly** und **All**. |
| `OutputPath` | Erforderlicher **String**-Parameter.<br /><br /> Gibt das Verzeichnis an, in dem die generierten Dateien mit verwaltetem Code und [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]-Binärformatdateien generiert werden. |
| `OutputType` | Erforderlicher **String**-Parameter.<br /><br /> Gibt den Typ der Assembly an, die von einem Projekt generiert wird. Die gültigen Optionen sind **winexe**, **wxe**, **library** und **netmodule**. |
| `PageMarkup` | Optionaler **ITaskItem[]**-Parameter.<br /><br /> Gibt eine Liste der zu verarbeitenden [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]-Dateien an. |
| `References` | Optionaler **ITaskItem[]**-Parameter.<br /><br /> Gibt die Liste der Verweise aus Dateien auf Assemblys an, die die Typen enthalten, die in den [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]-Dateien verwendet werden. |
| `RequirePass2ForMainAssembly` | Optionaler **boolescher** Ausgabeparameter.<br /><br /> Gibt an, ob das Projekt nicht lokalisierbare [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]-Dateien enthält, die auf lokale Typen verweisen, die in die Hauptassembly eingebettet sind. |
| `RequirePass2ForSatelliteAssembly` | Optionaler **boolescher** Ausgabeparameter.<br /><br /> Gibt an, ob das Projekt lokalisierbare [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]-Dateien enthält, die auf lokale Typen verweisen, die in die Hauptassembly eingebettet sind. |
| `RootNamespace` | Optionaler **String**-Parameter.<br /><br /> Gibt den Stammnamespace für Klassen innerhalb des Projekts an. **RootNamespace** wird auch als Standardnamespace für eine generierte Datei mit verwaltetem Code verwendet, wenn die entsprechende [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]-Datei nicht das `x:Class`-Attribut enthält. |
| `SourceCodeFiles` | Optionaler **ITaskItem[]**-Parameter.<br /><br /> Gibt die Liste der Codedateien für das aktuelle Projekt an. Die Liste enthält keine generierten sprachspezifischen Dateien mit verwaltetem Code. |
| `UICulture` | Optionaler **String**-Parameter.<br /><br /> Gibt die Satellitenassembly für die Benutzeroberflächenkultur an, in die die generierten [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]-Binärformatdateien eingebettet werden. Wenn **UICulture** nicht festgelegt ist, werden die generierten [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]-Binärformatdateien in die Hauptassembly eingebettet. |
| `XAMLDebuggingInformation` | Optionaler **Boolean**-Parameter.<br /><br /> Wenn **true**, werden Diagnoseinformationen generiert und in die kompilierte [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]-Datei einbezogen, um das Debuggen zu unterstützen. |

## <a name="remarks"></a>Hinweise

Der <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1>-Task kompiliert [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] normalerweise in Binärformat und generiert Codedateien. Wenn eine [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]-Datei Verweise auf Typen enthält, die im gleichen Projekt definiert sind, wird ihre Kompilierung in das Binärformat durch **MarkupCompilePass1** auf einen zweiten Markupkompilierungsschritt (**MarkupCompilePass2**) aufgeschoben. Die Kompilierung solcher Dateien muss aufgeschoben werden, weil sie warten müssen, bis die referenzierten lokal definierten Typen kompiliert sind. Wenn eine [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]-Datei allerdings ein `x:Class`-Attribut aufweist, generiert <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> die sprachspezfiische Codedatei für diese.

Eine [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]-Datei ist lokalisierbar, wenn sie Elemente enthält, die das `x:Uid`-Attribut verwenden:

```xml
<Page x:Class="WPFMSBuildSample.Page1"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Uid="Page1Uid"
    >
  ...
</Page>
```

Eine [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]-Datei verweist auf einen lokal definierten Typ , wenn sie einen [!INCLUDE[TLA#tla_xml](../msbuild/includes/tlasharptla_xml_md.md)]-Namespace deklariert, der mit dem `clr-namespace`-Wert auf einen Namespace im aktuellen Projekt verweist:

```xml
<Page x:Class="WPFMSBuildSample.Page1"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:localNamespace="clr-namespace:WPFMSBuildSample"
    >
    <Grid>
      <Grid.Resources>
        <localNameSpace:LocalType x:Key="localType" />
      </Grid.Resources>
      ...
    </Grid>
</Page>
```

Wenn eine beliebige [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]-Datei lokalisierbar ist oder auf einen lokal definierten Typ verweist, ist ein zweiter Markupkompilierungsschritt erforderlich, was die Ausführung von [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md) und dann [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md) erfordert.

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt, wie drei [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]-*Seite*-Dateien ins Binärformat konvertiert werden. *Seite1* enthält einen Verweis auf einen Typ (`Class1`), der sich im Stammnamespace des Projekts befindet und daher nicht in diesem Markupkompilierungsschritt in Binärformatdateien konvertiert wird. Stattdessen wird [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md) ausgeführt und anschließend [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md).

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask 
    TaskName="Microsoft.Build.Tasks.Windows.MarkupCompilePass1" 
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="MarkupCompilePass1Task">
    <MarkupCompilePass1 
      AssemblyName="WPFMSBuildSample"
      Language="C#"
      OutputType="WinExe"
      OutputPath="obj\Debug\"
      ApplicationMarkup="App.xaml"
      PageMarkup="Page1.xaml;Page2.xaml;Page3.xaml"
      SourceCodeFiles="Class1.cs"
      References="c:\windows\Microsoft.net\Framework\v2.0.50727\System.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationCore.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationFramework.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\WindowsBase.dll" />
  </Target>
</Project>
```

## <a name="see-also"></a>Siehe auch

[WPF-MSBuild-Referenz](../msbuild/wpf-msbuild-reference.md)  
[Referenz zu MSBuild-Tasks für WPF](../msbuild/wpf-msbuild-task-reference.md)  
[MSBuild-Referenz](../msbuild/msbuild-reference.md)  
[Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)  
[Erstellen einer WPF-Anwendung (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)  
[Übersicht über WPF-XAML-Browseranwendungen](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)