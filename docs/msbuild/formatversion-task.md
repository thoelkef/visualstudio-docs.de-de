---
title: FormatVersion-Aufgabe | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 96e692f6-b581-46ca-8cc9-441a1861e371
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0b36c4eb63c503132aaf434c64249e4a5fdd3872
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595253"
---
# <a name="formatversion-task"></a>FormatVersion-Aufgabe
Fügt die Revisionsnummer an die Versionsnummer an.

- Fall 1: Eingabe: Version=\<undefined>;  Revision=\<don't care>;   Output: OutputVersion="1.0.0.0"

- Fall 2: Eingabe: Version="1.0.0.*"  Revision="5"  Output: OutputVersion="1.0.0.5"

- Fall 3: Eingabe: Version="1.0.0.0"  Revision=\<don't care>;  Output: OutputVersion="1.0.0.0"

## <a name="parameters"></a>Parameter
 In der folgenden Tabelle werden die Parameter der `FormatVersion` -Aufgabe beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|`FormatType`|Optionaler `String`-Parameter.<br /><br /> Gibt den Formattyp an<br /><br /> – "Version" = Version<br />– "Path" = "." durch "_" ersetzen|
|`OutputVersion`|Optionaler `String`-Ausgabeparameter.<br /><br /> Gibt die Ausgabeversion an, die die Revisionsnummer beinhaltet|
|`Revision`|Optionaler `Int32`-Parameter.<br /><br /> Gibt die Revision an, die an die Version angefügt werden soll|
|`Version`|Optionaler `String`-Parameter.<br /><br /> Gibt die zu formatierende Versionsnummernzeichenfolge an|

## <a name="remarks"></a>Hinweise
 Zusätzlich zu den in der Tabelle aufgeführten Parametern erbt dieser Task Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension-Basisklasse](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Siehe auch
- [Aufgaben](../msbuild/msbuild-tasks.md)
- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
