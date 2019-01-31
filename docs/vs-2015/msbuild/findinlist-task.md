---
title: FindInList-Aufgabe | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- FindInList task [MSBuild]
- MSBuild, FindInList task
ms.assetid: d49b9f84-52a2-4242-9269-b741a7a7e9f7
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f5011d1b9e83b379be8eb4b23ec6a7aac649ef9a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54774556"
---
# <a name="findinlist-task"></a>FindInList-Aufgabe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Sucht in einer angegebenen Liste ein Element, das über die entsprechende Elementspezifikation verfügt  
  
## <a name="parameters"></a>Parameter  
 In der folgenden Tabelle werden die Parameter der [FindInList-Aufgabe](../msbuild/findinlist-task.md) beschrieben.  
  
|Parameter|Beschreibung|  
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
