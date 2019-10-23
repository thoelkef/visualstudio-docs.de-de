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
- MSBuild (C++), GetOutputFileName task
- GetOutputFileName task (MSBuild (C++))
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: 9733aae5e53948cdf07d62f62cd7ca5f930d08a3
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747298"
---
# <a name="getoutputfilename-task"></a>GetOutputFileName-Aufgabe

Hilfsaufgabe zum Abrufen von Ausgabedateinamen für CL und andere Tools, die nur die Angabe des Ausgabeverzeichnisses oder des vollständigen Dateinamens zulassen.

## <a name="parameters"></a>Parameter

In der folgenden Tabelle werden die Parameter der **GetOutputFileName**-Aufgabe beschrieben.

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|**OutputExtension**|Erforderlicher **String**-Parameter.|
|**OutputFile**|Optionaler **string**-Ausgabeparameter|
|**OutputPath**|Optionaler **string**-Parameter|
|**SourceFile**|Erforderlicher **String**-Parameter.|

## <a name="see-also"></a>Siehe auch

[Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)