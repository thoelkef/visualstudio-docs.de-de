---
title: CPPClean-Aufgabe | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vc.task.cppclean
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), CPPClean task
- CPPClean task (MSBuild (C++))
ms.assetid: b62a482e-8fb5-4999-b50b-6605a078e291
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 331a96c7cd67b933e521e3fe5f2d7a909ffa5d03
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634343"
---
# <a name="cppclean-task"></a>CPPClean-Aufgabe

Löscht die temporären Dateien, die MSBuild erstellt, wenn ein C++-Projekt erstellt wird. Das Löschen von Builddateien wird *Bereinigen* genannt.

## <a name="parameters"></a>Parameter

 In der folgenden Tabelle werden die Parameter der **CPPClean**-Aufgabe beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|**DeletedFiles**|Optionaler `ITaskItem[]`-Ausgabeparameter.<br /><br /> Definiert ein Array von MSBuild-Ausgabedateielementen, die von Aufgaben verbraucht und ausgegeben werden können|
|**DoDelete**|Optionaler **Boolean**-Parameter.<br /><br /> Wenn der Wert `true` ist, werden temporäre Builddateien bereinigt.|
|**FilePatternsToDeleteOnClean**|Erforderlicher `String`-Parameter.<br /><br /> Gibt eine durch ein Semikolon getrennte Liste von Dateierweiterungen von zu bereinigenden Dateien an|
|**FilesExcludedFromClean**|Optionaler `String`-Parameter.<br /><br /> Gibt eine durch ein Semikolon getrennte Liste von Dateien an, die nicht bereinigt werden sollen|
|**FoldersToClean**|Erforderlicher `String`-Parameter.<br /><br /> Gibt eine durch ein Semikolon getrennte Liste von Verzeichnissen an, die bereinigt werden sollen. Sie können einen vollständigen oder einen relativen Pfad angeben, und der relative Pfad kann ein Platzhaltersymbol (*) enthalten.|

## <a name="see-also"></a>Weitere Informationen

- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
