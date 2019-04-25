---
title: FindInList-Aufgabe | Microsoft-Dokumentation
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7c2f6c5f14f6eff818a265e097f02e2bc76c7372
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62996671"
---
# <a name="findinlist-task"></a>FindInList-Aufgabe
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

## <a name="remarks"></a>Anmerkungen
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension-Basisklasse](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Siehe auch
- [Aufgaben](../msbuild/msbuild-tasks.md)
- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)