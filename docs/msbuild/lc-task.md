---
title: LC-Aufgabe | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#LC
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, LC task
- LC task [MSBuild]
ms.assetid: d5a53472-6f2a-42b8-a6db-593ca99c9790
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6b80d43a291f5afaf9be34ad5b7f1f7a474ba93e
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="lc-task"></a>LC-Aufgabe
Umschließt „LC.exe“, womit eine LICENSE-Datei aus einer LICX-Datei generiert wird. Weitere Informationen zu „LC.exe“ finden Sie unter [Lc.exe (License Compiler)](/dotnet/framework/tools/lc-exe-license-compiler) (Lc.exe [Lizenzcompiler]).  
  
## <a name="parameters"></a>Parameter  
 In der folgenden Tabelle werden die Parameter für die `LC`-Aufgabe beschrieben.  
  
|Parameter|description|  
|---------------|-----------------|  
|`LicenseTarget`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem> -Parameter.<br /><br /> Gibt die ausführbare Datei an, für die die LICENSES-Dateien generiert werden.|  
|`NoLogo`|Optionaler `Boolean` -Parameter.<br /><br /> Unterdrückt die Anzeige des Startbanners von Microsoft.|  
|`OutputDirectory`|Optionaler `String` -Parameter.<br /><br /> Gibt das Verzeichnis an, in dem die LICENSES-Ausgabedatei gespeichert werden soll.|  
|`OutputLicense`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>-Ausgabeparameter.<br /><br /> Gibt den Namen der LICENSES-Datei an. Wenn Sie keinen Namen angeben, wird der Name der LICX-Datei verwendet, und die LICENSES-Datei wird in dem Verzeichnis gespeichert, das die LICX-Datei enthält.|  
|`ReferencedAssemblies`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter<br /><br /> Gibt die referenzierten Komponenten an, die beim Generieren der LICENSE-Datei geladen werden.|  
|`SdkToolsPath`|Optionaler `String` -Parameter.<br /><br /> Legt den Pfad zu den SDK-Tools wie z.B. „resgen.exe“ fest.|  
|`Sources`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter.<br /><br /> Gibt die Elemente mit lizenzierten Komponenten an, die in die LICENSES-Datei aufgenommen werden sollen. Weitere Informationen finden Sie in der Dokumentation zum `/complist`-Schalter in [Lc.exe (License Compiler)](/dotnet/framework/tools/lc-exe-license-compiler) (Lc.exe [Lizenzcompiler]).|  
  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.ToolTaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.ToolTask>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [ToolTaskExtension-Basisklasse](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die `LC`-Aufgabe zum Kompilieren von Lizenzen verwendet.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
<!-- Item declarations, etc -->  
  
    <Target Name="CompileLicenses">  
        <LC  
            Sources="@(LicxFile)"  
            LicenseTarget="$(TargetFileName)"  
            OutputDirectory="$(IntermediateOutputPath)"  
            OutputLicenses="$(IntermediateOutputPath)$(TargetFileName).licenses"  
            ReferencedAssemblies="@(ReferencePath);@(ReferenceDependencyPaths)">  
  
            <Output  
                TaskParameter="OutputLicenses"  
                ItemName="CompiledLicenseFile"/>  
        </LC>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Tasks (Aufgaben)](../msbuild/msbuild-tasks.md)   
 [Aufgabenreferenz](../msbuild/msbuild-task-reference.md)