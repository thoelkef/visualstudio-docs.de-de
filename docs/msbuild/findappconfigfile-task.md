---
title: FindAppConfigFile-Aufgabe | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- FindAppConfigFile task [MSBuild]
- MSBuild, FindAppConfigFile task
ms.assetid: e292de3e-7482-4426-83ce-d921061808bf
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c54f3c222588cd13711c832d12f7598f0cc5e223
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634174"
---
# <a name="findappconfigfile-task"></a>FindAppConfigFile-Aufgabe

Sucht nach der Datei *app.config* (falls vorhanden) in den angegebenen Listen.

## <a name="parameters"></a>Parameter

 In der folgenden Tabelle werden die Parameter der `FindAppConfigFile`-Aufgabe beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|`AppConfigFile`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Ausgabeparameter.<br /><br /> Gibt das erste übereinstimmende Element in der Liste an, sofern vorhanden|
|`PrimaryList`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter.<br /><br /> Gibt die primäre Liste an, die durchsucht werden soll|
|`SecondaryList`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter.<br /><br /> Gibt die sekundäre Liste an, die durchsucht werden soll|
|`TargetPath`|Erforderlicher `String`-Parameter.<br /><br /> Gibt den Wert an, der als Metadatenelement hinzugefügt werden soll|

## <a name="remarks"></a>Bemerkungen

 Zusätzlich zu den in der Tabelle aufgeführten Parametern erbt dieser Task Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension-Basisklasse](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Weitere Informationen

- [Tasks (Aufgaben)](../msbuild/msbuild-tasks.md)
- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
