---
title: XslTransformation-Aufgabe | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, XslTransformation task
- XslTransformation task [MSBuild]
ms.assetid: 6f3a7d81-3ae3-4703-9a06-870b32b69d80
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 84bc83f60d133dcaf22c9fa690357fa2624adabd
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/26/2020
ms.locfileid: "77630794"
---
# <a name="xsltransformation-task"></a>XslTransformation-Aufgabe

Transformiert eine XML-Eingabe mithilfe von XSLT oder kompiliertem XSLT-Code und gibt an ein Ausgabegerät oder eine Ausgabedatei aus

## <a name="parameters"></a>Parameter

 In der folgenden Tabelle werden die Parameter der `XslTransformation` -Aufgabe beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|`OutputPaths`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter.<br /><br /> Gibt die Ausgabedateien für die XML-Transformation an|
|`Parameters`|Optionaler `String`-Parameter.<br /><br /> Gibt die Parameter für das XSLT-Eingabedokument an|
|`XmlContent`|Optionaler `String`-Parameter.<br /><br /> Gibt die XML-Eingabe als Zeichenfolge an|
|`XmlInputPaths`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter<br /><br /> Gibt die XML-Eingabedateien an|
|`XslCompiledDllPath`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>-Parameter.<br /><br /> Gibt den kompilierten XSLT-Code an|
|`XslContent`|Optionaler `String`-Parameter.<br /><br /> Gibt die XSLT-Eingabe als Zeichenfolge an|
|`XslInputPath`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>-Parameter.<br /><br /> Gibt die XSLT-Eingabedatei an|

## <a name="remarks"></a>Hinweise

 Zusätzlich zu den in der Tabelle aufgeführten Parametern erbt dieser Task Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension-Basisklasse](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Siehe auch

- [Aufgaben](../msbuild/msbuild-tasks.md)
- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
