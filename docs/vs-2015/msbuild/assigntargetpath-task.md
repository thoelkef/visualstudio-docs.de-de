---
title: AssignTargetPath-Aufgabe | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 0e830e31-3bcf-4259-b2a8-a5df49b92d51
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: efae349037d6a826c4d267e12d901306eed7629b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54758696"
---
# <a name="assigntargetpath-task"></a>AssignTargetPath-Aufgabe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Diese Aufgabe akzeptiert Listendateien und fügt `<TargetPath>`-Attribute hinzu, wenn sie nicht bereits angegeben wurden.  
  
## <a name="task-parameters"></a>Aufgabenparameter  
 In der folgenden Tabelle werden die Parameter der `AssignTargetPath`-Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|`RootFolder`|Optionaler `string`-Eingabeparameter.<br /><br /> Enthält den Pfad zu dem Ordner, der die Ziellinks enthält.|  
|`Files`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Eingabeparameter.<br /><br /> Enthält die eingehende Liste von Dateien.|  
|`AssignedFiles`|Optional<br /><br /> <xref:Microsoft.Build.Framework.ITaskItem> `[]`-Ausgabeparameter.<br /><br /> Enthält die resultierende Liste von Dateien.|  
  
## <a name="remarks"></a>Hinweise  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel führt die `AssignTargetPath`-Aufgabe aus, um ein Projekt zu konfigurieren.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="MyProject">  
        <AssignTargetPath  
RootFolder="Resources"  
            Files="@(ResourceFiles)"  
            <Output TaskParameter="AssignedFiles"  
                ItemName="OutAssignedFiles"/>  
        </AssignTargetPath>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Tasks (Aufgaben)](../msbuild/msbuild-tasks.md)   
 [Aufgabenreferenz](../msbuild/msbuild-task-reference.md)
