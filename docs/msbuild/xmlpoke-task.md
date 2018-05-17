---
title: XmlPoke-Aufgabe | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- XmlPoke task [MSBuild]
- MSBuild, XmlPoke task
ms.assetid: 6ba1953c-be3b-4df8-8561-e133408f8270
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3295a5aee03badc52b980183e88f484e0d4bcc3a
ms.sourcegitcommit: 56018fb1f52f17bf35ae2ce71c50c763486e6173
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="xmlpoke-task"></a>XmlPoke-Aufgabe

Legt die Werte einer XML-Datei wie von der XPath-Abfrage angegeben fest

## <a name="parameters"></a>Parameter

 In der folgenden Tabelle werden die Parameter der `XmlPoke` -Aufgabe beschrieben.
  
|Parameter|description|
|---------------|-----------------|
|`Namespaces`|Optionaler `String` -Parameter.<br /><br /> Gibt die Namespaces für die Präfixe von XPath-Abfragen an|
|`Query`|Optionaler `String` -Parameter.<br /><br /> Gibt die XPath-Abfrage an|
|`Value`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem> -Parameter.<br /><br /> Gibt den Wert an, der in den angegebenen Pfad eingefügt werden soll.|
|`XmlInputPath`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem> -Parameter.<br /><br /> Gibt die XML-Eingabe als Dateipfad an|

## <a name="remarks"></a>Hinweise

 Zusätzlich zu den in der Tabelle aufgeführten Parametern erbt dieser Task Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Siehe auch

 [Tasks (Aufgaben)](../msbuild/msbuild-tasks.md)   
 [Aufgabenreferenz](../msbuild/msbuild-task-reference.md)