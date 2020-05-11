---
title: GetOutOfDateItems-Aufgabe | Microsoft-Dokumentation
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.getoutofdateitems
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), GetOutOfDateItems task
- GetOutOfDateItems task (MSBuild (C++))
author: corob-msft
ms.author: corob
ms.workload:
- multiple
ms.openlocfilehash: bfa60ff0f7e4060f5725fe54bd5950d858b86a22
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "77272394"
---
# <a name="getoutofdateitems-task"></a>GetOutOfDateItems-Aufgabe

Hilfsaufgabe zum Lesen alter Nachverfolgungsprotokolle, Schreiben neuer Nachverfolgungsprotokolle und Zurückgeben von Elementen, die nicht auf dem neuesten Stand sind.

## <a name="parameters"></a>Parameter

In der folgenden Tabelle werden die Parameter der **GetOutOfDateItems-Aufgabe** beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|**CheckForInterdependencies**|Optionaler **bool**-Parameter.|
|**CommandMetadataName**|Optionaler **string**-Parameter|
|**DependenciesMetadataName**|Optionaler **string**-Parameter|
|**HasInterdependencies**|Optionaler **bool**-Ausgabeparameter|
|**OutOfDateSources**|Optionaler **ITaskItem[]** -Ausgabeparameter.|
|**OutputsMetadataName**|Erforderlicher **String**-Parameter.|
|**Sources**|Optionaler **ITaskItem[]** -Parameter.|
|**TLogDirectory**|Erforderlicher **String**-Parameter.|
|**TLogNamePrefix**|Erforderlicher **String**-Parameter.|

## <a name="see-also"></a>Weitere Informationen

[Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)