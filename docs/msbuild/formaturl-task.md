---
title: FormatUrl-Aufgabe | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, FormatUrl task
- FormatUrl task [MSBuild]
ms.assetid: 81114b67-520f-43b5-8891-224f68a78516
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5fcd4ed0c60d615f0c213e1af5099c5e94a9b485
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634122"
---
# <a name="formaturl-task"></a>FormatUrl-Aufgabe

Konvertiert eine URL in ein gültiges URL-Format

## <a name="parameters"></a>Parameter

 In der folgenden Tabelle werden die Parameter der `FormatUrl` -Aufgabe beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|`InputUrl`|Optionaler `String`-Parameter.<br /><br /> Gibt die zu formatierende URL an|
|`OutputUrl`|Optionaler `String`-Ausgabeparameter.<br /><br /> Gibt die formatierte URL an|

## <a name="remarks"></a>Hinweise

 Zusätzlich zu den in der Tabelle aufgeführten Parametern erbt dieser Task Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension-Basisklasse](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Siehe auch

- [Aufgaben](../msbuild/msbuild-tasks.md)
- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)