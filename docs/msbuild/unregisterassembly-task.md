---
title: "UnregisterAssembly Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#UnregisterAssembly"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, UnregisterAssembly task"
  - "UnregisterAssembly task [MSBuild]"
ms.assetid: 04f549dd-3591-4dda-9c3a-cf6ede9df2c3
caps.latest.revision: 21
caps.handback.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# UnregisterAssembly Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Hebt die Registrierung der angegebenen Assemblys für COM\-Interop\-Zwecke auf.  Ihr Zweck ist dem der [RegisterAssembly\-Aufgabe](../msbuild/registerassembly-task.md) entgegengesetzt.  
  
## Parameter  
 In der folgenden Tabelle werden die Parameter der `UnregisterAssembly`\-Aufgabe beschrieben.  
  
|Parameter|Description|  
|---------------|-----------------|  
|`Assemblies`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Parameter.<br /><br /> Gibt die Assemblys an, deren Registrierung aufgehoben werden soll.|  
|`AssemblyListFile`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>\-Parameter.<br /><br /> Enthält Informationen über den Zustand zwischen der `RegisterAssembly`\-Aufgabe und der `UnregisterAssembly`\-Aufgabe.  Dadurch wird verhindert, dass die Aufgabe versucht, die Registrierung einer Assembly aufzuheben, die in der `RegisterAssembly`\-Aufgabe nicht registriert werden konnte.<br /><br /> Wenn dieser Parameter angegeben wird, werden der `Assemblies`\-Parameter und der `TypeLibFiles`\-Parameter ignoriert.|  
|`TypeLibFiles`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Ausgabeparameter.<br /><br /> Hebt die Registrierung der angegebenen Typbibliothek in der angegebenen Assembly auf. **Note:**  Dieser Parameter ist nur erforderlich, wenn der Name der Typbibliotheksdatei nicht mit dem Assemblynamen übereinstimmt.|  
  
## Hinweise  
 Für eine erfolgreiche Ausführung dieser Aufgabe muss die Assembly nicht unbedingt vorhanden sein.  Wenn Sie versuchen, die Registrierung einer nicht vorhandenen Assembly aufzuheben, wird die Aufgabe erfolgreich ausgeführt und eine Warnung ausgegeben.  Der Zweck dieser Aufgabe ist es nämlich, die Assemblyregistrierung aus der Registrierung zu entfernen, und  wenn die Assembly nicht vorhanden ist, ist sie auch nicht in der Registrierung enthalten, weshalb die Aufgabe erfolgreich ausgeführt wird.  
  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.AppDomainIsolatedTaskExtension>\-Klasse, die selbst von der <xref:System.MarshalByRefObject>\-Klasse erbt.  Die `MarshalByRefObject`\-Klasse stellt die gleichen Funktionen wie die <xref:Microsoft.Build.Utilities.Task>\-Klasse bereit, kann jedoch in einer eigenen Anwendungsdomäne instanziiert werden kann.  
  
## Beispiel  
 Im folgenden Beispiel wird mithilfe der `UnregisterAssembly`\-Aufgabe die Registrierung der Assembly aufgehoben, die sich möglicherweise in dem von der `OutputPath`\-Eigenschaft und der `FileName`\-Eigenschaft angegebenen Pfad befindet.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <PropertyGroup>  
        <OutputPath>\Output\</OutputPath>  
        <FileName>MyFile.dll</FileName>  
    </PropertyGroup>  
    <Target Name="UnregisterAssemblies">  
        <UnregisterAssembly  
            Condition="Exists('$(OutputPath)$(FileName)')"  
            Assemblies="$(OutputPath)$(FileName)" />  
    </Target>  
  
</Project>  
```  
  
## Siehe auch  
 [RegisterAssembly Task](../msbuild/registerassembly-task.md)   
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)