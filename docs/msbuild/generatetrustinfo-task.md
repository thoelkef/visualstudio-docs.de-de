---
title: GenerateTrustInfo-Aufgabe | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateTrustInfo task
- GenerateTrustInfo task [MSBuild]
ms.assetid: 3ca60816-4bb0-4fef-ae43-ca0bfb63def3
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5b9c32681af56595f8b00feab4979a3ec45f1588
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/25/2020
ms.locfileid: "77578693"
---
# <a name="generatetrustinfo-task"></a>GenerateTrustInfo-Aufgabe
Generiert die Anwendungsvertrauensstellung aus dem Basismanifest und aus den `TargetZone`- und `ExcludedPermissions`-Parametern

## <a name="parameters"></a>Parameter
 In der folgenden Tabelle werden die Parameter der `GenerateTrustInfo` -Aufgabe beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|`ApplicationDependencies`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter<br /><br /> Gibt die abhängigen Assemblys an|
|`BaseManifest`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>-Parameter.<br /><br /> Gibt das Basismanifest an, über das die Anwendungsvertrauensstellung generiert wird|
|`ExcludedPermissions`|Optionaler `String`-Parameter.<br /><br /> Gibt einen oder mehrere durch Semikolons getrennte Berechtigungsidentitätswerte an, die aus dem Standardberechtigungssatz der Zone ausgeschlossen werden sollen|
|`TargetZone`|Optionaler `String`-Parameter.<br /><br /> Gibt einen Standardberechtigungssatz für eine Zone an, der von der Computerrichtlinie abgerufen wird.|
|`TrustInfoFile`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>-Ausgabeparameter<br /><br /> Gibt die Datei an, die die Sicherheitsinformationen für die Anwendungsvertrauensstellung enthält|

## <a name="remarks"></a>Hinweise
 Zusätzlich zu den in der Tabelle aufgeführten Parametern erbt dieser Task Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension-Basisklasse](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Siehe auch
- [Aufgaben](../msbuild/msbuild-tasks.md)
- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)