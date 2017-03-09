---
title: "GenerateTemporaryTargetAssembly Task | Microsoft Docs"
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
  - "build process [WPF MSBuild], XAML page refers to a locally declared type"
  - "GenerateTemporaryTargetAssembly task [WPF MSBuild]"
  - "GenerateTemporaryTargetAssembly task [WPF MSBuild], parameters"
  - "creating an assembly [WPF MSBuild], XAML page refers to a locally declared type"
ms.assetid: 92b6539c-6897-45e0-8989-0c234bbfe782
caps.latest.revision: 7
caps.handback.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# GenerateTemporaryTargetAssembly Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die <xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly>\-Aufgabe generiert eine Assembly, wenn mindestens eine [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)]\-Seite eines Projekts auf einen Typ verweist, der lokal in diesem Projekt deklariert ist.  Die generierte Assembly wird entfernt, sobald der Buildprozess abgeschlossen ist oder wenn Fehler im Buildprozess auftreten.  
  
## Aufgabenparameter  
  
|Parameter|Beschreibung|  
|---------------|------------------|  
|`AssemblyName`|Erforderlicher **String**\-Parameter.<br /><br /> Gibt den Kurznamen der für ein Projekt generierten Assembly an, bei dem es sich gleichzeitig um den Namen der temporär generierten Zielassembly handelt.  Wenn beispielsweise ein Projekt eine ausführbare [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)]\-Datei mit dem Namen **WinExeAssembly.exe** generiert, hat der **AssemblyName**\-Parameter den Wert **WinExeAssembly**.|  
|`CompileTargetName`|Erforderlicher **String**\-Parameter.<br /><br /> Gibt den Namen des [!INCLUDE[TLA#tla_msbuild](../msbuild/includes/tlasharptla_msbuild_md.md)]\-Ziels an, das zum Generieren von Assemblys aus Quellcodedateien verwendet wird.  Der typische Wert für **CompileTargetName** ist **CoreCompile**.|  
|`CompileTypeName`|Erforderlicher **String**\-Parameter.<br /><br /> Gibt den Typ der Kompilierung an, die von dem Ziel ausgeführt wird, das mit dem **CompileTargetName**\-Parameter angegeben wird.  Für das **CoreCompile**\-Ziel lautet dieser Wert **Compile**.|  
|`CurrentProject`|Erforderlicher **String**\-Parameter.<br /><br /> Gibt den vollständigen Pfad der [!INCLUDE[TLA2#tla_msbuild](../msbuild/includes/tla2sharptla_msbuild_md.md)]\-Projektdatei für das Projekt an, für das eine temporäre Zielassembly erforderlich ist.|  
|`GeneratedCodeFiles`|Optionaler **ITaskItem\[\]**\-Parameter.<br /><br /> Gibt die Liste der sprachspezifischen verwalteten Codedateien an, die von der [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md)\-Aufgabe generiert wurden.|  
|`IntermediateOutputPath`|Erforderlicher **String**\-Parameter.<br /><br /> Gibt das Verzeichnis an, in dem die temporäre Zielassembly generiert wird.|  
|`MSBuildBinPath`|Erforderlicher **String**\-Parameter.<br /><br /> Gibt den Speicherort von **MSBuild.exe** an, die zum Kompilieren der temporären Zielassembly erforderlich ist.|  
|`ReferencePath`|Optionaler **ITaskItem\[\]**\-Parameter.<br /><br /> Gibt eine Liste der Assemblys mit Pfad und Dateinamen an, auf die von den Typen verwiesen wird, die in die temporäre Zielassembly kompiliert werden.|  
|`ReferencePathTypeName`|Erforderlicher **String**\-Parameter.<br /><br /> Gibt den Parameter an, der von dem Parameter des Kompilierungsziels \(**CompileTargetName**\) verwendet wird, der die Liste der Assemblyverweise \(**ReferencePath**\) angibt.  Der geeignete Wert ist **ReferencePath**.|  
  
## Hinweise  
 Im ersten Markupkompilierungsdurchlauf, der von der [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md) ausgeführt wird, werden [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]\-Dateien in das Binärformat kompiliert.  Folglich benötigt der Compiler eine Liste der Assemblys, auf die verwiesen wird und in denen die in den [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]\-Dateien verwendeten Typen enthalten sind.  Wenn eine [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]\-Datei jedoch einen Typ verwendet, der im gleichen Projekt definiert ist, wird eine entsprechende Assembly für das Projekt erst erstellt, nachdem das Projekt erstellt wurde.  Deshalb kann ein Assemblyverweis nicht während des ersten Markupkompilierungsdurchlaufs bereitgestellt werden.  
  
 Stattdessen verschiebt **MarkupCompilePass1** die Konvertierung von [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]\-Dateien, die Verweise auf Typen im gleichen Projekt enthalten, in den zweiten Markupkompilierungsdurchlauf, der von der [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md) ausgeführt wird.  Vor dem Ausführen von **MarkupCompilePass2** wird eine temporäre Assembly generiert.  Diese Assembly enthält die von den [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]\-Dateien verwendeten Typen, deren Markupkompilierungsdurchlauf verschoben wurde.  Während der Ausführung wird dem **MarkupCompilePass2** ein Verweis auf die generierte Assembly bereitgestellt, sodass die [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]\-Dateien, deren Kompilierung verschoben wurde, in das Binärformat konvertiert werden können.  
  
## Beispiel  
 Im folgenden Beispiel wird eine temporäre Assembly generiert, da `Page1.xaml` einen Verweis auf einen Typ im gleichen Projekt enthält.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask  
    TaskName="Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="GenerateTemporaryTargetAssemblyTask">  
    <GenerateTemporaryTargetAssembly  
      AssemblyName="WPFMSBuildSample"  
      CompileTargetName="CoreCompile"  
      CompileTypeName="Compile"  
      CurrentProject="FullBuild.proj"  
      GeneratedCodeFiles="obj\debug\app.g.cs;obj\debug\Page1.g.cs;obj\debug\Page2.g.cs"  
      ReferencePath="c:\windows\Microsoft.net\Framework\v2.0.50727\System.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationCore.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationFramework.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\WindowsBase.dll"  
      IntermediateOutputPath=".\obj\debug\"  
      MSBuildBinPath="$(MSBuildBinPath)"  
      ReferencePathTypeName="ReferencePath"/>  
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