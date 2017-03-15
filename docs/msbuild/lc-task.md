---
title: LC-Aufgabe | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 15
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
ms.openlocfilehash: 7b4ae3bba069cb1218b4ff1cf0b78877d10dfd34
ms.lasthandoff: 02/22/2017

---
# <a name="lc-task"></a>LC-Aufgabe
Umschließt „LC.exe“, womit eine LICENSE-Datei aus einer LICX-Datei generiert wird. Weitere Informationen zu „LC.exe“ finden Sie unter [Lc.exe (License Compiler)](http://msdn.microsoft.com/Library/2de803b8-495e-4982-b209-19a72aba0460) (Lc.exe [Lizenzcompiler]).  
  
## <a name="parameters"></a>Parameter  
 In der folgenden Tabelle werden die Parameter für die `LC`-Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|`LicenseTarget`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>-Parameter.<br /><br /> Gibt die ausführbare Datei an, für die die LICENSES-Dateien generiert werden.|  
|`NoLogo`|Optionaler `Boolean` -Parameter.<br /><br /> Unterdrückt die Anzeige des Startbanners von Microsoft.|  
|`OutputDirectory`|Optionaler `String` -Parameter.<br /><br /> Gibt das Verzeichnis an, in dem die LICENSES-Ausgabedatei gespeichert werden soll.|  
|`OutputLicense`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>-Ausgabeparameter.<br /><br /> Gibt den Namen der LICENSES-Datei an. Wenn Sie keinen Namen angeben, wird der Name der LICX-Datei verwendet, und die LICENSES-Datei wird in dem Verzeichnis gespeichert, das die LICX-Datei enthält.|  
|`ReferencedAssemblies`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter<br /><br /> Gibt die referenzierten Komponenten an, die beim Generieren der LICENSE-Datei geladen werden.|  
|`SdkToolsPath`|Optionaler `String` -Parameter.<br /><br /> Legt den Pfad zu den SDK-Tools wie z.B. „resgen.exe“ fest.|  
|`Sources`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem> `[]`-Parameter<br /><br /> Gibt die Elemente mit lizenzierten Komponenten an, die in die LICENSES-Datei aufgenommen werden sollen. Weitere Informationen finden Sie in der Dokumentation zum `/complist`-Schalter in [Lc.exe (License Compiler)](http://msdn.microsoft.com/Library/2de803b8-495e-4982-b209-19a72aba0460) (Lc.exe [Lizenzcompiler]).|  
  
 Neben den oben genannten Parametern übernimmt diese Aufgabe Parameter von der Klasse <xref:Microsoft.Build.Tasks.ToolTaskExtension>, die diese wiederum von der Klasse <xref:Microsoft.Build.Utilities.ToolTask> übernimmt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [ToolTaskExtension-Basisklasse](../msbuild/tooltaskextension-base-class.md).  
  
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
 [Task Reference](../msbuild/msbuild-task-reference.md) (MSBuild-Aufgabenreferenz)
