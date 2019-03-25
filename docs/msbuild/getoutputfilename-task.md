---
title: GetOutputFileName-Aufgabe | Microsoft-Dokumentation
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.getoutputfilename
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), GetOutputFileName task
- GetOutputFileName task (MSBuild (Visual C++))
author: mikeblome
ms.author: Michael.Blome
ms.workload:
- multiple
ms.openlocfilehash: ee44e891c8c5f6a95971cade0536b2a5ec5b4688
ms.sourcegitcommit: 4ffb7be5384ad566ce46538032bf8561754c61a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/15/2019
ms.locfileid: "58070427"
---
# <a name="getoutputfilename-task"></a>GetOutputFileName-Aufgabe

Hilfsaufgabe zum Abrufen von Ausgabedateinamen für CL und andere Tools, die nur die Angabe des Ausgabeverzeichnisses oder des vollständigen Dateinamens zulassen.

## <a name="parameters"></a>Parameter

In der folgenden Tabelle werden die Parameter der **GetOutputFileName**-Aufgabe beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|**OutputExtension**|Erforderlicher **String**-Parameter.|
|**OutputFile**|Optionaler **string**-Ausgabeparameter|
|**OutputPath**|Optionaler **string**-Parameter|
|**SourceFile**|Erforderlicher **String**-Parameter.|

## <a name="see-also"></a>Siehe auch

[Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)