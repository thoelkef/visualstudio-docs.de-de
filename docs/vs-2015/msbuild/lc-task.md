---
title: LC-Aufgabe | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
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
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d151f99aec8f752a64e2dae965321e4ef54eb734
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47522412"
---
# <a name="lc-task"></a>LC-Aufgabe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [LC-Aufgabe](https://docs.microsoft.com/visualstudio/msbuild/lc-task).  
  
  
Umschließt „LC.exe“, womit eine LICENSE-Datei aus einer LICX-Datei generiert wird. Weitere Informationen zu „LC.exe“ finden Sie unter [Lc.exe (License Compiler)](http://msdn.microsoft.com/library/2de803b8-495e-4982-b209-19a72aba0460) (Lc.exe [Lizenzcompiler]).  
  
## <a name="parameters"></a>Parameter  
 In der folgenden Tabelle werden die Parameter für die `LC`-Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|`LicenseTarget`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem> -Parameter.<br /><br /> Gibt die ausführbare Datei an, für die die LICENSES-Dateien generiert werden.|  
|`NoLogo`|Optionaler `Boolean` -Parameter.<br /><br /> Unterdrückt die Anzeige des Startbanners von Microsoft.|  
|`OutputDirectory`|Optionaler `String` -Parameter.<br /><br /> Gibt das Verzeichnis an, in dem die LICENSES-Ausgabedatei gespeichert werden soll.|  
|`OutputLicense`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>-Ausgabeparameter.<br /><br /> Gibt den Namen der LICENSES-Datei an. Wenn Sie keinen Namen angeben, wird der Name der LICX-Datei verwendet, und die LICENSES-Datei wird in dem Verzeichnis gespeichert, das die LICX-Datei enthält.|  
|`ReferencedAssemblies`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter<br /><br /> Gibt die referenzierten Komponenten an, die beim Generieren der LICENSE-Datei geladen werden.|  
|`SdkToolsPath`|Optionaler `String` -Parameter.<br /><br /> Legt den Pfad zu den SDK-Tools wie z.B. „resgen.exe“ fest.|  
|`Sources`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter.<br /><br /> Gibt die Elemente mit lizenzierten Komponenten an, die in die LICENSES-Datei aufgenommen werden sollen. Weitere Informationen finden Sie in der Dokumentation zum `/complist`-Schalter in [Lc.exe (License Compiler)](http://msdn.microsoft.com/library/2de803b8-495e-4982-b209-19a72aba0460) (Lc.exe [Lizenzcompiler]).|  
  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.ToolTaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.ToolTask>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [ToolTaskExtension-Basisklasse](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die `LC`-Aufgabe zum Kompilieren von Lizenzen verwendet.  
  
```  
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



