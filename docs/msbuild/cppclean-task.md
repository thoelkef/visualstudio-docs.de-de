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
- MSBuild (Visual C++), CPPClean task
- CPPClean task (MSBuild (Visual C++))
ms.assetid: b62a482e-8fb5-4999-b50b-6605a078e291
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 674d3408de10cee51179c125d69bcaf8a457908d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62939117"
---
# <a name="cppclean-task"></a>CPPClean-Aufgabe
Löscht die temporären Dateien, die MSBuild erstellt, wenn ein Visual C++-Projekt erstellt wird. Das Löschen von Builddateien wird *Bereinigen* genannt.

## <a name="parameters"></a>Parameter
 In der folgenden Tabelle werden die Parameter der **CPPClean**-Aufgabe beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|**DeletedFiles**|Optionaler `ITaskItem[]`-Ausgabeparameter.<br /><br /> Definiert ein Array von MSBuild-Ausgabedateielementen, die von Aufgaben verbraucht und ausgegeben werden können|
|**DoDelete**|Optionaler **Boolean**-Parameter.<br /><br /> Wenn der Wert `true` ist, werden temporäre Builddateien bereinigt.|
|**FilePatternsToDeleteOnClean**|Erforderlicher `String` -Parameter.<br /><br /> Gibt eine durch ein Semikolon getrennte Liste von Dateierweiterungen von zu bereinigenden Dateien an|
|**FilesExcludedFromClean**|Optionaler `String` -Parameter.<br /><br /> Gibt eine durch ein Semikolon getrennte Liste von Dateien an, die nicht bereinigt werden sollen|
|**FoldersToClean**|Erforderlicher `String` -Parameter.<br /><br /> Gibt eine durch ein Semikolon getrennte Liste von Verzeichnissen an, die bereinigt werden sollen. Sie können einen vollständigen oder einen relativen Pfad angeben, und der relative Pfad kann ein Platzhaltersymbol (*) enthalten.|

## <a name="see-also"></a>Siehe auch
- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)