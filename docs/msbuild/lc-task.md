---
title: "LC Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#LC"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, LC task"
  - "LC task [MSBuild]"
ms.assetid: d5a53472-6f2a-42b8-a6db-593ca99c9790
caps.latest.revision: 15
caps.handback.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# LC Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Umschließt LC.exe, womit eine LICENSES\-Datei aus einer LICX\-Datei generiert wird.  Weitere Informationen zu LC.exe finden Sie unter [Lc.exe \(License Compiler\)](../Topic/Lc.exe%20\(License%20Compiler\).md).  
  
## Parameter  
 In der folgenden Tabelle werden die Parameter für die `LC`\-Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|------------------|  
|`LicenseTarget`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>\-Parameter.<br /><br /> Gibt die ausführbare Datei an, für die die LICENSES\-Dateien generiert werden.|  
|`NoLogo`|Optionaler `Boolean`\-Parameter.<br /><br /> Unterdrückt die Anzeige des Startbanners von Microsoft.|  
|`OutputDirectory`|Optionaler `String`\-Parameter.<br /><br /> Gibt das Verzeichnis an, in dem die LICENSES\-Ausgabedateien gespeichert werden sollen.|  
|`OutputLicense`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>\-Ausgabeparameter.<br /><br /> Gibt den Namen der LICENSES\-Datei an.  Wenn Sie keinen Namen angeben, wird der Name der LICX\-Datei verwendet, und die LICENSES\-Datei wird in dem Verzeichnis gespeichert, in dem sich auch die LICX\-Datei befindet.|  
|`ReferencedAssemblies`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Parameter.<br /><br /> Gibt die Komponenten an, auf die verwiesen wird und die geladen werden sollen, wenn die LICENSES\-Datei generiert wird.|  
|`SdkToolsPath`|Optionaler `String`\-Parameter.<br /><br /> Gibt den Pfad zu den SDK\-Tools, wie z. B. resgen.exe an.|  
|`Sources`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Parameter.<br /><br /> Gibt die Elemente an, die lizenzierte Komponenten enthalten, die in die LICENSES\-Datei eingeschlossen werden sollen.  Weitere Informationen finden Sie in der Dokumentation zum `/complist`\-Schalter unter [Lc.exe \(License Compiler\)](../Topic/Lc.exe%20\(License%20Compiler\).md).|  
  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.ToolTaskExtension>\-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.ToolTask>\-Klasse erbt.  Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [ToolTaskExtension Base Class](../msbuild/tooltaskextension-base-class.md).  
  
## Beispiel  
 Im folgenden Beispiel wird die `LC`\-Aufgabe verwendet, um Lizenzen zu kompilieren.  
  
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
  
## Siehe auch  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)