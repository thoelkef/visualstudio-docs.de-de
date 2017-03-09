---
title: "MarkupCompilePass1 Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "converting XAML to binary format [WPF MSBuild]"
  - "MarkupCompilePass1 task [WPF MSBuild], parameters"
  - "converting XAML projects to compiled binary format [WPF MSBuild]"
  - "MarkupCompilePass1 task [WPF MSBuild], converting XAML to binary format"
ms.assetid: 693d6945-fd6f-4698-8f64-9dfcb71052d3
caps.latest.revision: 8
caps.handback.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# MarkupCompilePass1 Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1>\-Aufgabe konvertiert nicht lokalisierbare [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)]\-Projektdateien in ein kompiliertes Binärformat.  
  
## Aufgabenparameter  
  
|Parameter|Beschreibung|  
|---------------|------------------|  
|`AllGeneratedFiles`|Optionaler **ITaskItem\[\]**\-Ausgabeparameter.<br /><br /> Enthält eine vollständige Liste der Dateien, die von der <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1>\-Aufgabe generiert werden.|  
|`AlwaysCompileMarkupFilesInSeparateDomain`|Optionaler **Boolean** Parameter.<br /><br /> Gibt an, ob die Aufgabe in einer separaten <xref:System.AppDomain> ausgeführt werden soll.  Wenn der Parameter **false** zurückgibt, wird die Aufgabe in derselben <xref:System.AppDomain> wie [!INCLUDE[TLA#tla_msbuild](../msbuild/includes/tlasharptla_msbuild_md.md)] und schneller ausgeführt.  Wenn der Parameter **true** zurückgibt, wird die Aufgabe in einer anderen <xref:System.AppDomain>, die von [!INCLUDE[TLA2#tla_msbuild](../msbuild/includes/tla2sharptla_msbuild_md.md)] getrennt ist, und langsamer ausgeführt.|  
|`ApplicationMarkup`|Optionaler **ITaskItem\[\]**\-Parameter.<br /><br /> Gibt den Namen der [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]\-Anwendungsdefinitionsdatei an.|  
|`AssembliesGeneratedDuringBuild`|Optionaler **String\[\]**\-Parameter.<br /><br /> Gibt Verweise auf Assemblys an, die sich während des Buildprozesses ändern.  Beispielsweise enthält eine [!INCLUDE[TLA#tla_visualstu2005](../msbuild/includes/tlasharptla_visualstu2005_md.md)]\-Projektmappe möglicherweise ein Projekt, das auf die kompilierte Ausgabe eines anderen Projekts verweist.  In diesem Fall kann dem **AssembliesGeneratedDuringBuild**\-Parameter die kompilierte Ausgabe des zweiten Projekts hinzugefügt werden.<br /><br /> Hinweis: Der **AssembliesGeneratedDuringBuild**\-Parameter muss Verweise auf den vollständigen Satz der Assemblys enthalten, die von einer Buildprojektmappe generiert werden.|  
|`AssemblyName`|Erforderlicher **string**\-Parameter.<br /><br /> Gibt den Kurznamen der Assembly an, die für ein Projekt generiert wird.  Wenn beispielsweise ein Projekt eine ausführbare [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)]\-Datei mit dem Namen **WinExeAssembly.exe** generiert, hat der **AssemblyName**\-Parameter den Wert **WinExeAssembly**.|  
|`AssemblyPublicKeyToken`|Optionaler **String**\-Parameter.<br /><br /> Gibt das öffentliche Schlüsseltoken der Assembly an.|  
|`AssemblyVersion`|Optionaler **String**\-Parameter.<br /><br /> Gibt die Versionsnummer der Assembly an.|  
|`ContentFiles`|Optionaler **ITaskItem\[\]**\-Parameter.<br /><br /> Gibt die Liste loser Inhaltsdateien an.|  
|`DefineConstants`|Optionaler **String**\-Parameter.<br /><br /> Gibt an, dass der aktuelle Wert von **DefineConstants** beibehalten wird.  Dies wirkt sich auf die Generierung der Zielassembly aus. Wenn dieser Parameter geändert wird, kann die öffentliche API in der Zielassembly geändert und die Kompilierung der [!INCLUDE[TLA2#tla_titlexaml](../msbuild/includes/tla2sharptla_titlexaml_md.md)]\-Dateien, die auf lokale Typen verweisen, beeinflusst werden.|  
|`ExtraBuildControlFiles`|Optionaler **ITaskItem\[\]**\-Parameter.<br /><br /> Gibt eine Liste der Dateien an, mit denen gesteuert wird, ob beim erneuten Ausführen der <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1>\-Aufgabe eine Neuerstellung ausgelöst wird. Eine Neuerstellung wird ausgelöst, wenn sich eine dieser Dateien ändert.|  
|`GeneratedBamlFiles`|Optionaler **ITaskItem\[\]**\-Ausgabeparameter.<br /><br /> Enthält die Liste der generierten Dateien im [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]\-Binärformat.|  
|`GeneratedCodeFiles`|Optionaler **ITaskItem\[\]**\-Ausgabeparameter.<br /><br /> Enthält die Liste der generierten verwalteten Codedateien.|  
|`GeneratedLocalizationFiles`|Optionaler **ITaskItem\[\]**\-Ausgabeparameter.<br /><br /> Enthält die Liste der Lokalisierungsdateien, die für jede lokalisierbare [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]\-Datei generiert wurden.|  
|`HostInBrowser`|Optionaler **String**\-Parameter.<br /><br /> Gibt an, ob die generierte Assembly ein [!INCLUDE[TLA#tla_xbap](../msbuild/includes/tlasharptla_xbap_md.md)] ist.  Die gültigen Optionen sind **true** und **false**.  Bei **true** wird Code generiert, um das Hosten in einem Browser zu unterstützen.|  
|`KnownReferencePaths`|Optionaler **String\[\]**\-Parameter.<br /><br /> Gibt Verweise auf Assemblys an, die sich während des Buildprozesses nicht ändern.  Schließt Assemblys ein, die im [!INCLUDE[TLA#tla_gac](../msbuild/includes/tlasharptla_gac_md.md)], in einem [!INCLUDE[TLA#tla_netframewk](../misc/includes/tlasharptla_netframewk_md.md)]\-Installationsverzeichnis usw. gesucht werden.|  
|`Language`|Erforderlicher **String**\-Parameter.<br /><br /> Gibt die verwaltete Sprache an, die der Compiler unterstützt.  Die gültigen Optionen sind **C\#**, **VB**, **JScript**und **C\+\+**.|  
|`LanguageSourceExtension`|Optionaler **String**\-Parameter.<br /><br /> Gibt die Erweiterung an, die an die Erweiterung der generierten verwalteten Codedatei angefügt wird:<br /><br /> `<Filename>.g<LanguageSourceExtension>`<br /><br /> Wenn der **LanguageSourceExtension**\-Parameter auf keinen bestimmten Wert festgelegt ist, wird die Standarderweiterung für den Quelldateinamen für die jeweilige Sprache verwendet: **.vb** für [!INCLUDE[TLA#tla_visualb](../msbuild/includes/tlasharptla_visualb_md.md)] und **.csharp** für [!INCLUDE[TLA#tla_cshrp](../data-tools/includes/tlasharptla_cshrp_md.md)].|  
|`LocalizationDirectivesToLocFile`|Optionaler **String**\-Parameter.<br /><br /> Gibt an, wie Lokalisierungsinformationen für jede [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]\-Quelldatei generiert werden.  Die gültigen Optionen sind **None**, **CommentsOnly** und **All**.|  
|`OutputPath`|Erforderlicher **String**\-Parameter.<br /><br /> Gibt das Verzeichnis an, in dem die generierten verwalteten Codedateien und [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]\-Binärformatdateien generiert werden.|  
|`OutputType`|Erforderlicher **String**\-Parameter.<br /><br /> Gibt den Typ der Assembly an, die von einem Projekt generiert wird.  Die gültigen Optionen sind **winexe**, **exe**, **library** und **netmodule**.|  
|`PageMarkup`|Optionaler **ITaskItem\[\]**\-Parameter.<br /><br /> Gibt eine Liste der zu verarbeitenden [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]\-Dateien an.|  
|`References`|Optionaler **ITaskItem\[\]**\-Parameter.<br /><br /> Gibt die Liste der Verweise aus Dateien auf Assemblys an, in denen die in den [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]\-Dateien verwendeten Typen enthalten sind.|  
|`RequirePass2ForMainAssembly`|Optionaler **Boolean** Ausgabeparameter.<br /><br /> Gibt an, ob das Projekt nicht lokalisierbare [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]\-Dateien enthält, die auf lokale Typen verweisen, die in die Hauptassembly eingebettet sind.|  
|`RequirePass2ForSatelliteAssembly`|Optionaler **Boolean** Ausgabeparameter.<br /><br /> Gibt an, ob das Projekt lokalisierbare [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]\-Dateien enthält, die auf lokale Typen verweisen, die in die Hauptassembly eingebettet sind.|  
|`RootNamespace`|Optionaler **String**\-Parameter.<br /><br /> Gibt den Stammnamespace für Klassen an, die sich im Projekt befinden.  **RootNamespace** wird auch als Standardnamespace für eine generierte verwaltete Codedatei verwendet, wenn die entsprechende [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]\-Datei das `x:Class`\-Attribut nicht enthält.|  
|`SourceCodeFiles`|Optionaler **ITaskItem\[\]**\-Parameter.<br /><br /> Gibt die Liste der Codedateien für das aktuelle Projekt an.  Die Liste enthält keine generierten sprachspezifischen verwalteten Codedateien.|  
|`UICulture`|Optionaler **String**\-Parameter.<br /><br /> Gibt die Satellitenassembly für die UI\-Kultur an, in die die generierten [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]\-Binärformatdateien eingebettet sind.  Wenn **UICulture** nicht festgelegt ist, werden die generierten [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]\-Binärformatdateien in die Hauptassembly eingebettet.|  
|`XAMLDebuggingInformation`|Optionaler **Boolean** Parameter.<br /><br /> Bei **true** werden Diagnoseinformationen generiert und in die kompilierte [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] integriert, um das Debuggen zu unterstützen.|  
  
## Hinweise  
 Die <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1>\-Aufgabe kompiliert [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] normalerweise im Binärformat und generiert Codedateien.  Wenn eine [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]\-Datei Verweise auf im gleichen Projekt definierte Typen enthält, wird die Kompilierung im Binärformat von **MarkupCompilePass1** in den nächsten Markupkompilierungsschritt \(**MarkupCompilePass2**\) verschoben.  Die Kompilierung solcher Dateien muss verschoben werden, bis die lokal definierten Typen, auf die verwiesen wird, kompiliert sind.  Wenn eine [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]\-Datei jedoch über ein `x:Class`\-Attribut verfügt, generiert <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> die sprachspezifische Codedatei.  
  
 Eine [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]\-Datei ist lokalisierbar, wenn sie Elemente enthält, die das `x:Uid`\-Attribut verwenden:  
  
```  
<Page x:Class="WPFMSBuildSample.Page1"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    x:Uid="Page1Uid"  
    >  
  ...  
</Page>  
```  
  
 Eine [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]\-Datei verweist auf einen lokal definierten Typ, wenn sie einen [!INCLUDE[TLA#tla_xml](../msbuild/includes/tlasharptla_xml_md.md)]\-Namespace deklariert, der mit dem `clr-namespace`\-Wert auf einen Namespace im aktuellen Projekt verweist:  
  
```  
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
  
 Wenn eine der [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]\-Dateien lokalisierbar ist oder auf einen lokal definierten Typ verweist, ist ein zweiter Markupkompilierungsschritt erforderlich, für den die [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md) und dann die [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md) ausgeführt werden müssen.  
  
## Beispiel  
 Im folgenden Beispiel wird das Konvertieren von drei `Page` [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]\-Dateien in Dateien im Binärformat veranschaulicht.  `Page1` enthält einen Verweis auf den Typ `Class1`, der sich im Stammnamespace des Projekts befindet und in diesem Markupkompilierungsschritt daher nicht in Dateien im Binärformat konvertiert wird.  Stattdessen werden die [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md) und anschließend die [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md) ausgeführt.  
  
```  
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
  
## Siehe auch  
 [WPF MSBuild Reference](../msbuild/wpf-msbuild-reference.md)   
 [Task Reference](../msbuild/wpf-msbuild-task-reference.md)   
 [MSBuild Reference](../msbuild/msbuild-reference.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [Erstellen einer WPF\-Anwendung \(WPF\)](../Topic/Building%20a%20WPF%20Application%20\(WPF\).md)   
 [Übersicht über WPF\-XAML\-Browseranwendungen](../Topic/WPF%20XAML%20Browser%20Applications%20Overview.md)