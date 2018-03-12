---
title: CPPClean-Aufgabe | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 37f976d54e3a18d3bc854b46678f79ecec41659f
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="cppclean-task"></a>CPPClean-Aufgabe
Löscht die temporären Dateien, die MSBuild erstellt, wenn ein Visual C++-Projekt erstellt wird. Das Löschen von Builddateien wird *Bereinigen* genannt.  
  
## <a name="parameters"></a>Parameter  
 In der folgenden Tabelle werden die Parameter der **CPPClean**-Aufgabe beschrieben.  
  
|Parameter|description|  
|---------------|-----------------|  
|**DeletedFiles**|Optionaler `ITaskItem[]`-Ausgabeparameter.<br /><br /> Definiert ein Array von MSBuild-Ausgabedateielementen, die von Aufgaben verbraucht und ausgegeben werden können|  
|**DoDelete**|Optionaler **Boolean**-Parameter.<br /><br /> Wenn der Wert `true` ist, werden temporäre Builddateien bereinigt.|  
|**FilePatternsToDeleteOnClean**|Erforderlicher `String` -Parameter.<br /><br /> Gibt eine durch ein Semikolon getrennte Liste von Dateierweiterungen von zu bereinigenden Dateien an|  
|**FilesExcludedFromClean**|Optionaler `String` -Parameter.<br /><br /> Gibt eine durch ein Semikolon getrennte Liste von Dateien an, die nicht bereinigt werden sollen|  
|**FoldersToClean**|Erforderlicher `String` -Parameter.<br /><br /> Gibt eine durch ein Semikolon getrennte Liste von Verzeichnissen an, die bereinigt werden sollen. Sie können einen vollständigen oder einen relativen Pfad angeben, und der relative Pfad kann ein Platzhaltersymbol (**\***) enthalten.|  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [Aufgabenreferenz](../msbuild/msbuild-task-reference.md)