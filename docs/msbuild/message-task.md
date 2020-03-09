---
title: Message-Aufgabe | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Message
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, Message task
- Message task [MSBuild]
ms.assetid: 2293309d-42b6-46dc-9684-8c146f66bc28
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2c570a5a783133f9422dc434d0ef460b9ca7510e
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633485"
---
# <a name="message-task"></a>Meldungsaufgabe

Protokolliert eine Meldung während eines Builds

## <a name="parameters"></a>Parameter

 In der folgenden Tabelle werden die Parameter der `Message` -Aufgabe beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|`Importance`|Optionaler `String`-Parameter.<br /><br /> Gibt die Wichtigkeit der Nachricht an. Dieser Parameter kann den Wert `high`, `normal` oder `low`haben. Der Standardwert ist `normal`.|
|`Text`|Optionaler `String`-Parameter.<br /><br /> Der zu protokollierende Fehlertext.|

## <a name="remarks"></a>Hinweise

 Die Aufgabe `Message` ermöglicht es MSBuild-Projekten, in verschiedenen Schritten des Buildprozesses Nachrichten an die Protokollierungen auszugeben.

 Wenn der `Condition`-Parameter `true` ergibt, wird der Wert des `Text`-Parameters protokolliert und der Build weiter ausgeführt. Wenn kein `Condition`-Parameter vorhanden ist, wird der Nachrichtentext protokolliert. Weitere Informationen zur Protokollierung finden Sie unter [Erhalten von Buildprotokollen](../msbuild/obtaining-build-logs-with-msbuild.md).

 Die Nachricht wird in der Regel an die MSBuild-Konsolenprotokollierung gesendet. Sie können diese Einstellung ändern, indem Sie den <xref:Microsoft.Build.Tasks.TaskExtension.Log%2A>-Parameter festlegen. Die Protokollierung interpretiert den `Importance` Parameter. Normalerweise wird eine Nachricht gesendet, die auf `high` gesetzt ist, wenn die Ausführlichkeit der Protokollierung auf <xref:Microsoft.Build.Framework.LoggerVerbosity>`Minimal` oder höher eingestellt ist. Es wird eine Nachricht gesendet, die auf `low` gesetzt ist, wenn die Ausführlichkeit der Protokollierung auf <xref:Microsoft.Build.Framework.LoggerVerbosity>`Detailed` eingestellt ist.

 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension-Basisklasse](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Beispiel

 Im folgenden Codebeispiel werden Nachrichten in allen registrierten Protokollierungen protokolliert.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="DisplayMessages">
        <Message Text="Project File Name = $(MSBuildProjectFile)" />
        <Message Text="Project Extension = $(MSBuildProjectExtension)" />
    </Target>
    ...
</Project>
```

## <a name="see-also"></a>Siehe auch

- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
- [Erhalten von Buildprotokollen](../msbuild/obtaining-build-logs-with-msbuild.md)
