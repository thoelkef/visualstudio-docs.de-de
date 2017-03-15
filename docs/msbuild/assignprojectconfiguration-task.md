---
title: AssignProjectConfiguration-Aufgabe | Microsoft-Dokumentation
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
ms.assetid: 09633a0b-8f6f-4aba-8058-7cb4d13ce2c0
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 80fe9e734dd8af527fad318df17f9c456129d660
ms.lasthandoff: 02/22/2017

---
# <a name="assignprojectconfiguration-task"></a>AssignProjectConfiguration-Aufgabe
Diese Aufgabe akzeptiert eine Liste von Konfigurationszeichenfolgen und weist sie angegebenen Projekten zu.  
  
## <a name="task-parameters"></a>Aufgabenparameter  
 In der folgenden Tabelle werden die Parameter der `AssignProjectConfiguration`-Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|`SolutionConfigurationContents`|Optionaler `string`-Ausgabeparameter.<br /><br /> Enthält eine XML-Zeichenfolge mit einer Projektkonfiguration für jedes Projekt. Die Konfigurationen werden den benannten Projekten zugewiesen.|  
|`DefaultToVcxPlatformMapping`|Optionaler `string`-Ausgabeparameter.<br /><br /> Enthält eine durch Semikolons getrennte Liste der Zuordnungen zwischen den von den meisten Typen verwendeten Plattformnamen<br /><br /> und den Namen, die von .vcxproj-Dateien verwendet werden.<br /><br /> Zum Beispiel:<br /><br /> `"AnyCPU=Win32;X86=Win32;X64=X64"`|  
|`VcxToDefaultPlatformMapping`|Optional<br /><br /> `string`-Ausgabeparameter.<br /><br /> Enthält eine durch Semikolons getrennte Liste mit Zuordnungen zwischen .vcxproj-Plattformnamen und den von den meisten Typen verwendeten Plattformnamen.<br /><br /> Zum Beispiel:<br /><br /> `"Win32=AnyCPU;X64=X64"`|  
|`CurrentProjectConfiguration`|Optionaler `string`-Ausgabeparameter.<br /><br /> Enthält die Konfiguration für das aktuelle Projekt.|  
|`CurrentProjectPlatform`|Optionaler `string`-Ausgabeparameter.<br /><br /> Enthält die Plattform für das aktuelle Projekt.|  
|`OnlyReferenceAndBuildProjectsEnabledInSolutionConfiguration`|Optionaler `bool`-Ausgabeparameter.<br /><br /> Enthält ein Flag, das angibt, dass Verweise erstellt werden sollen, auch wenn sie in der Projektkonfiguration deaktiviert wurden.|  
|`ShouldUnsetParentConfigurationAndPlatform`|Optionaler `bool`-Ausgabeparameter.<br /><br /> Enthält ein Flag, das angibt, ob die übergeordnete Konfiguration und Plattform gelöscht werden sollen.|  
|`OutputType`|Optionaler `string`-Ausgabeparameter.<br /><br /> Enthält den Ausgabetyp für das Projekt.|  
|`ResolveConfigurationPlatformUsingMappings`|Optionaler `bool`-Ausgabeparameter.<br /><br /> Enthält ein Flag, das angibt, ob der Build die Standardzuordnungen verwenden soll, um die Konfiguration und Plattform der übergebenen Projektverweise aufzulösen.|  
|`AssignedProjects`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Ausgabeparameter.<br /><br /> Enthält die Liste der aufgelösten Verweispfade.|  
|`UnassignedProjects`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Ausgabeparameter.<br /><br /> Enthält die Liste der Projektverweiselemente, die nicht mithilfe der Liste vorab aufgelöster Ausgaben aufgelöst werden konnten.|  
  
## <a name="remarks"></a>Hinweise  
 Neben den oben genannten Parametern übernimmt diese Aufgabe Parameter von der Klasse <xref:Microsoft.Build.Tasks.TaskExtension>, die diese wiederum von der Klasse <xref:Microsoft.Build.Utilities.Task> übernimmt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension-Basisklasse](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Tasks (Aufgaben)](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md) (MSBuild-Aufgabenreferenz)
