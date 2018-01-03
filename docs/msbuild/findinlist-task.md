---
title: FindInList-Aufgabe | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- FindInList task [MSBuild]
- MSBuild, FindInList task
ms.assetid: d49b9f84-52a2-4242-9269-b741a7a7e9f7
caps.latest.revision: "7"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8f64a5949dbb4440ccb940cdd5e0315c4f23d58b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="findinlist-task"></a>FindInList-Aufgabe
Sucht in einer angegebenen Liste ein Element, das über die entsprechende Elementspezifikation verfügt  
  
## <a name="parameters"></a>Parameter  
 In der folgenden Tabelle werden die Parameter der [FindInList-Aufgabe](../msbuild/findinlist-task.md) beschrieben.  
  
|Parameter|description|  
|---------------|-----------------|  
|`CaseSensitive`|Optionaler `Boolean` -Parameter.<br /><br /> Wenn der Wert `true` ist, wird die Groß- und Kleinschreibung bei der Suche berücksichtigt. Andernfalls ist die Groß- und Kleinschreibung unerheblich. Der Standardwert ist `true`sein.|  
|`FindLastMatch`|Optionaler `Boolean` -Parameter.<br /><br /> Wenn `true`, wird die letzte Übereinstimmung zurückgegeben. Ansonsten wird die erste Übereinstimmung zurückgegeben. Der Standardwert ist `false`sein.|  
|`ItemFound`|Optionaler schreibgeschützter <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Parameter.<br /><br /> Das erste übereinstimmende Element in der Liste, sofern vorhanden|  
|`ItemSpecToFind`|Erforderlicher `String` -Parameter.<br /><br /> Die zu suchende Elementspezifikation|  
|`List`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter.<br /><br /> Die Liste, in der nach der Elementspezifikation gesucht werden soll|  
|`MatchFileNameOnly`|Optionaler `Boolean` -Parameter.<br /><br /> Wenn `true`, wird nur gegen den Dateinamenteil der Elementspezifikation abgeglichen. Andernfalls wird die gesamte Elementspezifikation abgeglichen. Der Standardwert ist `true`sein.|  
  
## <a name="remarks"></a>Hinweise  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Tasks (Aufgaben)](../msbuild/msbuild-tasks.md)   
 [Aufgabenreferenz](../msbuild/msbuild-task-reference.md)