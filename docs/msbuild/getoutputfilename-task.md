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
author: ghogen
ms.author: ghogen
ms.workload:
- multiple
ms.openlocfilehash: d66a7be3751e74ff75787ef194f90da1dcd1d3ce
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593290"
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
