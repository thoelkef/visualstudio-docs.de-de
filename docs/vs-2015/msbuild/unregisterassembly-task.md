---
title: UnregisterAssembly-Aufgabe | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#UnregisterAssembly
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, UnregisterAssembly task
- UnregisterAssembly task [MSBuild]
ms.assetid: 04f549dd-3591-4dda-9c3a-cf6ede9df2c3
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2ef7ef7f4ec930b8aa338a8be33c4009b3009b20
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68193233"
---
# <a name="unregisterassembly-task"></a>UnregisterAssembly-Aufgabe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Hebt die Registrierung der angegebenen Assemblys für COM-Interop-Zwecke auf Führt den umgekehrten Vorgang der [RegisterAssembly-Aufgabe](../msbuild/registerassembly-task.md) aus  
  
## <a name="parameters"></a>Parameter  
 In der folgenden Tabelle werden die Parameter der `UnregisterAssembly` -Aufgabe beschrieben.  
  
|Parameter|BESCHREIBUNG|  
|---------------|-----------------|  
|`Assemblies`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter<br /><br /> Legt die Assemblys fest, deren Registrierung aufgehoben werden soll|  
|`AssemblyListFile`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem> -Parameter.<br /><br /> Enthält Informationen zum Zustand zwischen der `RegisterAssembly`- und der `UnregisterAssembly`-Aufgabe. Dies verhindert, dass die Aufgabe versucht, die Registrierung einer Assembly aufzuheben, die in der `RegisterAssembly`-Aufgabe nicht registriert werden konnte.<br /><br /> Wenn dieser Parameter angegeben wird, werden die Parameter `Assemblies` und `TypeLibFiles` ignoriert.|  
|`TypeLibFiles`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Ausgabeparameter.<br /><br /> Hebt die angegebene Typbibliothek in der angegebenen Assembly auf. **Hinweis:** Dieser Parameter ist nur erforderlich, wenn der Name der Typbibliotheksdatei und der Name der Assembly sich unterscheiden.|  
  
## <a name="remarks"></a>Anmerkungen  
 Zum erfolgreichen Ausführen der Aufgabe muss die Assembly nicht vorhanden sein. Wenn Sie versuchen, die Registrierung einer Assembly aufzuheben, die nicht vorhanden ist, wird die Aufgabe mit einer Warnung abgeschlossen. Dies liegt daran, dass die Aufgabe dafür verantwortlich ist, die Assemblyregistrierung aus der Registrierung zu entfernen. Wenn die Assembly nicht vorhanden ist, befindet sie sich nicht in der Registrierung, und der Task wird erfolgreich abgeschlossen.  
  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.AppDomainIsolatedTaskExtension>-Klasse, die selbst von der <xref:System.MarshalByRefObject>-Klasse erbt. Die Klasse `MarshalByRefObject` stellt die gleichen Funktionen wie die Klasse <xref:Microsoft.Build.Utilities.Task> bereit, kann aber in ihrer eigenen Anwendungsdomäne instanziiert werden.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die `UnregisterAssembly`-Aufgabe verwendet, um die Registrierung der Assembly unter dem von den Eigenschaften `OutputPath` und `FileName` festgelegten Pfad (falls vorhanden) aufzuheben.  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [RegisterAssembly-Aufgabe](../msbuild/registerassembly-task.md)   
 [Tasks (Aufgaben)](../msbuild/msbuild-tasks.md)   
 [Aufgabenreferenz](../msbuild/msbuild-task-reference.md)
