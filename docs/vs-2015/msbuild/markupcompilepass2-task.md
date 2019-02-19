---
title: MarkupCompilePass2-Aufgabe | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- performing second-pass markup [WPF MSBuild], MarkupCompilePass2 task
- MarkupCompilePass2 task [WPF MSBuild]
- MarkupCompilePass2 task [WPF MSBuild], parameters
ms.assetid: 1d25689a-d21f-4b05-be26-95aa0ed4fd03
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 87c31551541bc949a98ec2dd7a15da5a86b36d21
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2019
ms.locfileid: "54777091"
---
# <a name="markupcompilepass2-task"></a>MarkupCompilePass2-Aufgabe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Der [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)]-Task führt den zweiten Markupkompilierungsschritt für <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2>-Dateien aus, die auf Typen im selben Projekt verweisen.  
  
## <a name="task-parameters"></a>Aufgabenparameter  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|`AlwaysCompileMarkupFilesInSeparateDomain`|Optionaler **Boolean**-Parameter.<br /><br /> Gibt an, ob der Task in einer separaten <xref:System.AppDomain> ausgeführt wird. Wenn dieser Parameter **FALSE** zurückgibt, wird der Task in derselben <xref:System.AppDomain> wie [!INCLUDE[TLA#tla_msbuild](../includes/tlasharptla-msbuild-md.md)] und schneller ausgeführt. Wenn der Parameter **TRUE** zurückgibt, wird der Task in einer zweiten <xref:System.AppDomain>, die von [!INCLUDE[TLA2#tla_msbuild](../includes/tla2sharptla-msbuild-md.md)] isoliert ist, und langsamer ausgeführt.|  
|`AssembliesGeneratedDuringBuild`|Optionaler **String[]**-Parameter.<br /><br /> Gibt Verweise auf Assemblys an, die sich während des Buildprozesses ändern. Eine [!INCLUDE[TLA#tla_visualstu2005](../includes/tlasharptla-visualstu2005-md.md)]-Lösung kann möglicherweise ein Projekt enthalten, das auf die kompilierte Ausgabe eines anderen Projekts verweist. In diesem Fall kann die kompilierte Ausgabe des zweiten Projekts **AssembliesGeneratedDuringBuild** hinzugefügt werden.<br /><br /> Hinweis: **AssembliesGeneratedDuringBuild** muss Verweise auf den vollständigen Satz von Assemblys enthalten, die von einer Projektmappe generiert werden.|  
|`AssemblyName`|Erforderlicher **String**-Parameter.<br /><br /> Gibt den Kurznamen der Assembly an, die für ein Projekt generiert wird. Wenn ein Projekt z.B. eine ausführbare [!INCLUDE[TLA#tla_win](../includes/tlasharptla-win-md.md)]-Datei mit dem Namen **WinExeAssembly.exe** generiert, hat der **AssemblyName**-Parameter den Wert **WinExeAssembly**.|  
|`GeneratedBaml`|Optionaler **ITaskItem[]**-Ausgabeparameter.<br /><br /> Enthält die Liste der generierten Dateien im [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)]-Binärformat.|  
|`KnownReferencePaths`|Optionaler **String[]**-Parameter.<br /><br /> Gibt Verweise auf Assemblys an, die während des Buildprozesses niemals geändert werden. Enthält Assemblys, die in einem [!INCLUDE[TLA#tla_gac](../includes/tlasharptla-gac-md.md)] gespeichert sind, in einem [!INCLUDE[TLA#tla_netframewk](../includes/tlasharptla-netframewk-md.md)]-Installationsverzeichnis usw.|  
|`Language`|Erforderlicher **String**-Parameter.<br /><br /> Gibt die verwaltete Sprache an, die der Compiler unterstützt. Die gültigen Optionen sind **C#**, **VB**, **JScript** und **C++**.|  
|`LocalizationDirectivesToLocFile`|Optionaler **String**-Parameter.<br /><br /> Gibt an, wie Lokalisierungsinformationen für jede Quell-[!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)]-Datei generiert werden. Die gültigen Optionen sind **None**, **CommentsOnly** und **All**.|  
|`OutputPath`|Erforderlicher **String**-Parameter.<br /><br /> Gibt das Verzeichnis an, in dem die generierten [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)]-Binärformatdateien generiert werden.|  
|`OutputType`|Erforderlicher **String**-Parameter.<br /><br /> Gibt den Typ der Assembly an, die von einem Projekt generiert wird. Die gültigen Optionen sind **winexe**, **wxe**, **library** und **netmodule**.|  
|`References`|Optionaler **ITaskItem[]**-Parameter.<br /><br /> Gibt die Liste der Verweise aus Dateien auf Assemblys an, die die Typen enthalten, die in den [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)]-Dateien verwendet werden. Ein Verweis zeigt auf die Assembly, die vom <xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly>-Task generiert wurde, der vor dem <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2>-Task ausgeführt werden muss.|  
|`RootNamespace`|Optionaler **String**-Parameter.<br /><br /> Gibt den Stammnamespace für Klassen innerhalb des Projekts an. **RootNamespace** wird auch als Standardnamespace für eine generierte Datei mit verwaltetem Code verwendet, wenn die entsprechende [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)]-Datei nicht das `x:Class`-Attribut enthält.|  
|`XAMLDebuggingInformation`|Optionaler **Boolean**-Parameter.<br /><br /> Wenn **true**, werden Diagnoseinformationen generiert und in die kompilierte [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)]-Datei einbezogen, um das Debuggen zu unterstützen.|  
  
## <a name="remarks"></a>Anmerkungen  
 Vor dem Ausführen von **MarkupCompilePass2** müssen Sie eine temporäre Assembly generieren, die die Typen enthält, die von den [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)]-Dateien verwendet werden, deren Markupkompilierungsschritt aufgeschoben wurde. Sie generieren die temporäre Assembly durch Ausführen der **GenerateTemporaryTargetAssembly**-Aufgabe.  
  
 Ein Verweis auf die generierte temporäre Assembly wird bei der Ausführung an <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> bereitgestellt, sodass die [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)]-Dateien, deren Kompilierung im ersten Markupkompilierungsschritt aufgeschoben wurde, nun zur Kompilierung in das binäre Format übergeben werden.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird gezeigt, wie mit dem <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2>-Task ein zweiter Kompilierungsschritt durchgeführt wird.  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [WPF-MSBuild-Referenz](../msbuild/wpf-msbuild-reference.md)   
 [Task Reference](../msbuild/wpf-msbuild-task-reference.md)  (MSBuild-Aufgabenreferenz)  
 [MSBuild Reference](../msbuild/msbuild-reference.md)  (MSBuild-Referenz)  
 [Task Reference](../msbuild/msbuild-task-reference.md)  (MSBuild-Aufgabenreferenz)  
 [Erstellen einer WPF-Anwendung (WPF)](http://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)   
 [Übersicht über WPF-XAML-Browseranwendungen](http://msdn.microsoft.com/library/3a7a86a8-75d5-4898-96b9-73da151e5e16)
