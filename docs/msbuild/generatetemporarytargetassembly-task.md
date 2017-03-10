---
title: GenerateTemporaryTargetAssembly-Aufgabe | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- build process [WPF MSBuild], XAML page refers to a locally declared type
- GenerateTemporaryTargetAssembly task [WPF MSBuild]
- GenerateTemporaryTargetAssembly task [WPF MSBuild], parameters
- creating an assembly [WPF MSBuild], XAML page refers to a locally declared type
ms.assetid: 92b6539c-6897-45e0-8989-0c234bbfe782
caps.latest.revision: 7
author: kempb
ms.author: kempb
manager: ghogen
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
translationtype: Human Translation
ms.sourcegitcommit: 79460291e91f0659df0a4241e17616e55187a0e2
ms.openlocfilehash: 97370aa7301442a6f7f416b92204461177acdc5a
ms.lasthandoff: 02/22/2017

---
# <a name="generatetemporarytargetassembly-task"></a>GenerateTemporaryTargetAssembly-Aufgabe
Die <xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly>-Aufgabe generiert eine Assembly, wenn mindestens eine [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)]-Seite in einem Projekt auf einen Typ verweist, der lokal in diesem Projekt deklariert ist. Die generierte Assembly wird entfernt, nachdem der Build abgeschlossen ist, oder wenn beim Buildprozess ein Fehler auftritt.  
  
## <a name="task-parameters"></a>Aufgabenparameter  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|`AssemblyName`|Erforderlicher **String**-Parameter.<br /><br /> Gibt den Kurznamen der Assembly an, die für ein Projekt generiert wird, und ist auch der Name der temporär generierten Zielassembly. Wenn ein Projekt z.B. eine ausführbare [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)]-Datei mit dem Namen **WinExeAssembly.exe** generiert, hat der **AssemblyName**-Parameter den Wert **WinExeAssembly**.|  
|`CompileTargetName`|Erforderlicher **String**-Parameter.<br /><br /> Gibt den Namen des [!INCLUDE[TLA#tla_msbuild](../msbuild/includes/tlasharptla_msbuild_md.md)]-Ziels an, das zum Generieren von Assemblys aus Quellcodedateien verwendet wird. Der typische Wert für **CompileTargetName** ist **CoreCompile**.|  
|`CompileTypeName`|Erforderlicher **String**-Parameter.<br /><br /> Gibt den Typ der Kompilierung an, die vom Ziel ausgeführt wird, das durch den **CompileTargetName**-Parameter angegeben wird. Für das **CoreCompile**-Ziel ist dieser Wert **Compile**.|  
|`CurrentProject`|Erforderlicher **String**-Parameter.<br /><br /> Gibt den vollständigen Pfad der [!INCLUDE[TLA2#tla_msbuild](../msbuild/includes/tla2sharptla_msbuild_md.md)]-Projektdatei für das Projekt an, das eine temporäre Zielassembly erfordert.|  
|`GeneratedCodeFiles`|Optionaler **ITaskItem[]**-Parameter.<br /><br /> Gibt die Liste der sprachspezifischen verwalteten Codedateien an, die mit der [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md)-Aufgabe generiert wurden.|  
|`IntermediateOutputPath`|Erforderlicher **String**-Parameter.<br /><br /> Gibt das Verzeichnis an, in dem die temporäre Zielassembly generiert wird.|  
|`MSBuildBinPath`|Erforderlicher **String**-Parameter.<br /><br /> Gibt den Speicherort von **MSBuild.exe** an, die zum Kompilieren der temporären Zielassembly erforderlich ist.|  
|`ReferencePath`|Optionaler **ITaskItem[]**-Parameter.<br /><br /> Gibt eine Liste von Assemblys nach Pfad und Namen an, auf die die Typen verweisen, die in die temporäre Zielassembly kompiliert werden.|  
|`ReferencePathTypeName`|Erforderlicher **String**-Parameter.<br /><br /> Gibt den Parameter an, der vom Kompilierungszielparameter (**CompileTargetName**) verwendet wird, der die Liste der Assemblyverweise (**ReferencePath**) angibt. Der entsprechende Wert ist **ReferencePath**.|  
  
## <a name="remarks"></a>Hinweise  
 Im ersten Markupkompilierungsschritt, der von [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md) ausgeführt wird, kompiliert [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] Dateien in das Binärformat. Folglich benötigt der Compiler eine Liste der referenzierten Assemblys, die die Typen enthalten, die von den [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]-Dateien verwendet werden. Wenn jedoch eine [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]-Datei einen Typ verwendet, der im gleichen Projekt definiert ist, wird eine entsprechende Assembly für das Projekt erst dann erstellt, wenn das Projekt erstellt wird. Aus diesem Grund kann ein Assemblyverweis nicht beim ersten Markupkompilierungsschritt bereitgestellt werden.  
  
 Stattdessen verschiebt **MarkupCompilePass1** die Konvertierung von [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]-Dateien, die Verweise auf Typen im gleichen Projekt enthalten, auf einen zweiten Markupkompilierungsschritt, der von [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md) ausgeführt wird. Bevor **MarkupCompilePass2** ausgeführt wird, wird eine temporäre Assembly generiert. Diese Assembly enthält die Typen, die von den [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]-Dateien verwendet werden, deren Markupkompilierungsschritt aufgeschoben wurde. Ein Verweis auf die generierte Assembly wird **MarkupCompilePass2** während der Ausführung bereitgestellt, um die Konvertierung der Kompilierungs-[!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]-Dateien, deren Konvertierung aufgeschoben wurde, in das binäre Format zu ermöglichen.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird eine temporäre Assembly generiert, da `Page1.xaml` einen Verweis auf einen Typ im gleichen Projekt enthält.  
  
```xml  
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
  
## <a name="see-also"></a>Siehe auch  
 [WPF-MSBuild-Referenz](../msbuild/wpf-msbuild-reference.md)   
 [Task Reference](../msbuild/wpf-msbuild-task-reference.md)  (MSBuild-Aufgabenreferenz)  
 [MSBuild Reference](../msbuild/msbuild-reference.md)  (MSBuild-Referenz)  
 [Task Reference](../msbuild/msbuild-task-reference.md)  (MSBuild-Aufgabenreferenz)  
 [Erstellen einer WPF-Anwendung (WPF)](http://msdn.microsoft.com/Library/a58696fd-bdad-4b55-9759-136dfdf8b91c)   
 [Übersicht über WPF-XAML-Browseranwendungen](http://msdn.microsoft.com/Library/3a7a86a8-75d5-4898-96b9-73da151e5e16)
