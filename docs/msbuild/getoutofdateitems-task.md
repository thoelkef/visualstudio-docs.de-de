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
- MSBuild (Visual C++), GetOutOfDateItems task
- GetOutOfDateItems task (MSBuild (Visual C++))
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: e3393dd7e81fa98c49dd09a32457171286f88f18
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977489"
---
# <a name="getoutofdateitems-task"></a>GetOutOfDateItems-Aufgabe

Hilfsaufgabe zum Lesen alter Nachverfolgungsprotokolle, Schreiben neuer Nachverfolgungsprotokolle und Zurückgeben von Elementen, die nicht auf dem neuesten Stand sind.

## <a name="parameters"></a>Parameter

In der folgenden Tabelle werden die Parameter der **GetOutOfDateItems-Aufgabe** beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|**CheckForInterdependencies**|Optionaler **bool**-Parameter|
|**CommandMetadataName**|Optionaler **string**-Parameter|
|**DependenciesMetadataName**|Optionaler **string**-Parameter|
|**HasInterdependencies**|Optionaler **bool**-Ausgabeparameter|
|**OutOfDateSources**|Optionaler **ITaskItem[]**-Ausgabeparameter.|
|**OutputsMetadataName**|Erforderlicher **String**-Parameter.|
|**Sources**|Optionaler **ITaskItem[]**-Parameter.|
|**TLogDirectory**|Erforderlicher **String**-Parameter.|
|**TLogNamePrefix**|Erforderlicher **String**-Parameter.|

## <a name="see-also"></a>Siehe auch

[Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)