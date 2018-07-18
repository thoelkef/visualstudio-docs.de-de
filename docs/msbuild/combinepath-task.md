---
title: CombinePath-Aufgabe | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, CombinePath task
- CombinePath task [MSBuild]
ms.assetid: c20edbf4-3d4f-4f66-b1d5-753a0d858ed8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9efb3a997eb0e6aa0d731f4fbf5d9d8ce0e9e978
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
ms.locfileid: "31567069"
---
# <a name="combinepath-task"></a>CombinePath-Aufgabe
Kombiniert die angegebenen Pfade zu einem einzigen Pfad.  
  
## <a name="task-parameters"></a>Aufgabenparameter  
 In der folgenden Tabelle werden die Parameter der [CombinePath-Aufgabe](../msbuild/combinepath-task.md) beschrieben.  
  
|Parameter|description|  
|---------------|-----------------|  
|`BasePath`|Erforderlicher `String` -Parameter.<br /><br /> Der Basispfad, der mit den anderen Pfaden kombiniert werden soll. Der Pfad kann relativ, absolut oder nicht angegeben sein.|  
|`Paths`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter.<br /><br /> Eine Liste einzelner Pfade, die mit BasePath zu einem kombinierten Pfad kombiniert werden können. Pfade können relativ oder absolut sein.|  
|`CombinedPaths`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Ausgabeparameter.<br /><br /> Der kombinierte Pfad, der durch diese Aufgabe erstellt wurde|  
  
## <a name="remarks"></a>Hinweise  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Tasks (Aufgaben)](../msbuild/msbuild-tasks.md)   
 [Aufgabenreferenz](../msbuild/msbuild-task-reference.md)