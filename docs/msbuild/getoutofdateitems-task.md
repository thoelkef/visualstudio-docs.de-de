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
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: d3dc343c595606faf5bd31d7f087f7ba8d95f69e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747318"
---
# <a name="getoutofdateitems-task"></a>GetOutOfDateItems-Aufgabe

Hilfsaufgabe zum Lesen alter Nachverfolgungsprotokolle, Schreiben neuer Nachverfolgungsprotokolle und Zurückgeben von Elementen, die nicht auf dem neuesten Stand sind.

## <a name="parameters"></a>Parameter

In der folgenden Tabelle werden die Parameter der **GetOutOfDateItems-Aufgabe** beschrieben.

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|**CheckForInterdependencies**|Optionaler **bool**-Parameter|
|**CommandMetadataName**|Optionaler **string**-Parameter|
|**DependenciesMetadataName**|Optionaler **string**-Parameter|
|**HasInterdependencies**|Optionaler **bool**-Ausgabeparameter|
|**OutOfDateSources**|Optionaler **ITaskItem[]** -Ausgabeparameter.|
|**OutputsMetadataName**|Erforderlicher **String**-Parameter.|
|**Sources**|Optionaler **ITaskItem[]** -Parameter.|
|**TLogDirectory**|Erforderlicher **String**-Parameter.|
|**TLogNamePrefix**|Erforderlicher **String**-Parameter.|

## <a name="see-also"></a>Siehe auch

[Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)