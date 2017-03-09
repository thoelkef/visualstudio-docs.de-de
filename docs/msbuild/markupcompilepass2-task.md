---
title: "MarkupCompilePass2 Task | Microsoft Docs"
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
  - "performing second-pass markup [WPF MSBuild], MarkupCompilePass2 task"
  - "MarkupCompilePass2 task [WPF MSBuild]"
  - "MarkupCompilePass2 task [WPF MSBuild], parameters"
ms.assetid: 1d25689a-d21f-4b05-be26-95aa0ed4fd03
caps.latest.revision: 7
caps.handback.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# MarkupCompilePass2 Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2>\-Aufgabe führt einen weiteren Markupkompilierungsdurchlauf für [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)]\-Dateien aus, die auf Typen im gleichen Projekt verweisen.  
  
## Aufgabenparameter  
  
|Parameter|Beschreibung|  
|---------------|------------------|  
|`AlwaysCompileMarkupFilesInSeparateDomain`|Optionaler **Boolean** Parameter.<br /><br /> Gibt an, ob die Aufgabe in einer separaten <xref:System.AppDomain> ausgeführt werden soll.  Wenn der Parameter **false** zurückgibt, wird die Aufgabe in derselben <xref:System.AppDomain> wie [!INCLUDE[TLA#tla_msbuild](../msbuild/includes/tlasharptla_msbuild_md.md)] und schneller ausgeführt.  Wenn der Parameter **true** zurückgibt, wird die Aufgabe in einer anderen <xref:System.AppDomain>, die von [!INCLUDE[TLA2#tla_msbuild](../msbuild/includes/tla2sharptla_msbuild_md.md)] getrennt ist, und langsamer ausgeführt.|  
|`AssembliesGeneratedDuringBuild`|Optionaler **String\[\]**\-Parameter.<br /><br /> Gibt Verweise auf Assemblys an, die sich während des Buildprozesses ändern.  Beispielsweise enthält eine [!INCLUDE[TLA#tla_visualstu2005](../msbuild/includes/tlasharptla_visualstu2005_md.md)]\-Projektmappe möglicherweise ein Projekt, das auf die kompilierte Ausgabe eines anderen Projekts verweist.  In diesem Fall kann dem **AssembliesGeneratedDuringBuild**\-Parameter die kompilierte Ausgabe des zweiten Projekts hinzugefügt werden.<br /><br /> Hinweis: **AssembliesGeneratedDuringBuild** muss Verweise auf den vollständigen Satz der Assemblys enthalten, die von einer Buildprojektmappe generiert werden.|  
|`AssemblyName`|Erforderlicher **String**\-Parameter.<br /><br /> Gibt den Kurznamen der Assembly an, die für ein Projekt generiert wird.  Wenn beispielsweise ein Projekt eine ausführbare [!INCLUDE[TLA#tla_win](../msbuild/includes/tlasharptla_win_md.md)]\-Datei mit dem Namen **WinExeAssembly.exe** generiert, hat der **AssemblyName**\-Parameter den Wert **WinExeAssembly**.|  
|`GeneratedBaml`|Optionaler **ITaskItem\[\]**\-Ausgabeparameter.<br /><br /> Enthält die Liste der generierten Dateien im [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]\-Binärformat.|  
|`KnownReferencePaths`|Optionaler **String\[\]**\-Parameter.<br /><br /> Gibt Verweise auf Assemblys an, die sich während des Buildprozesses nicht ändern.  Schließt Assemblys ein, die im [!INCLUDE[TLA#tla_gac](../msbuild/includes/tlasharptla_gac_md.md)], in einem [!INCLUDE[TLA#tla_netframewk](../misc/includes/tlasharptla_netframewk_md.md)]\-Installationsverzeichnis usw. gesucht werden.|  
|`Language`|Erforderlicher **String**\-Parameter.<br /><br /> Gibt die verwaltete Sprache an, die der Compiler unterstützt.  Die gültigen Optionen sind **C\#**, **VB**, **JScript**und **C\+\+**.|  
|`LocalizationDirectivesToLocFile`|Optionaler **String**\-Parameter.<br /><br /> Gibt an, wie Lokalisierungsinformationen für jede [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]\-Quelldatei generiert werden.  Die gültigen Optionen sind **None**, **CommentsOnly** und **All**.|  
|`OutputPath`|Erforderlicher **String**\-Parameter.<br /><br /> Gibt das Verzeichnis an, in dem die Dateien im [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]\-Binärformat generiert werden.|  
|`OutputType`|Erforderlicher **String**\-Parameter.<br /><br /> Gibt den Typ der Assembly an, die von einem Projekt generiert wird.  Die gültigen Optionen sind **winexe**, **exe**, **library** und **netmodule**.|  
|`References`|Optionaler **ITaskItem\[\]**\-Parameter.<br /><br /> Gibt die Liste der Verweise aus Dateien auf Assemblys an, in denen die in den [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]\-Dateien verwendeten Typen enthalten sind.  Ein Verweis zeigt auf die von der <xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly>\-Aufgabe generierte Assembly, die vor der <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2>\-Aufgabe ausgeführt werden muss.|  
|`RootNamespace`|Optionaler **String**\-Parameter.<br /><br /> Gibt den Stammnamespace für Klassen an, die sich im Projekt befinden.  **RootNamespace** wird auch als Standardnamespace für eine generierte verwaltete Codedatei verwendet, wenn die entsprechende [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]\-Datei das `x:Class`\-Attribut nicht enthält.|  
|`XAMLDebuggingInformation`|Optionaler **Boolean** Parameter.<br /><br /> Bei **true** werden Diagnoseinformationen generiert und in die kompilierte [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] integriert, um das Debuggen zu unterstützen.|  
  
## Hinweise  
 Vor dem Ausführen von **MarkupCompilePass2** müssen Sie eine temporäre Assembly mit den Typen generieren, die von den [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]\-Dateien verwendet wurden, deren Markupkompilierungsdurchlauf verschoben wurde.  Sie generieren die temporäre Assembly, indem Sie die **GenerateTemporaryTargetAssembly**\-Aufgabe ausführen.  
  
 Ein Verweis auf die generierte temporäre Assembly wird dem <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> während der Ausführung bereitgestellt, sodass die [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]\-Dateien, deren Kompilierung im ersten Markupkompilierungsdurchlauf verschoben wurde, nun im Binärformat kompiliert werden können.  
  
## Beispiel  
 Im folgenden Beispiel wird veranschaulicht, wie mit der <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2>\-Aufgabe ein zweiter Kompilierungsdurchlauf ausgeführt wird.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.MarkupCompilePass2"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="MarkupCompilePass2Task">  
    <MarkupCompilePass2   
      AssemblyName="WPFMSBuildSample"  
      Language="C#"  
      OutputType="WinExe"  
      OutputPath="obj\Debug\"  
      References=".\obj\debug\WPFMSBuildSample.exe;c:\windows\Microsoft.net\Framework\v2.0.50727\System.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationCore.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationFramework.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\WindowsBase.dll" />  
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