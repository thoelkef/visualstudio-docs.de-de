---
title: CPPClean-Aufgabe | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e29a80c9cc3f492a19de630e2a09e1f15ca9c45c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54791438"
---
# <a name="cppclean-task"></a>CPPClean-Aufgabe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]


Löscht die temporären Dateien, die MSBuild erstellt, wenn ein Visual C++-Projekt erstellt wird. Das Löschen von Builddateien wird *Bereinigen* genannt.  

## <a name="parameters"></a>Parameter  
 In der folgenden Tabelle werden die Parameter der **CPPClean**-Aufgabe beschrieben.  


|            Parameter            |                                                                                                Beschreibung                                                                                                 |
|---------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|        **DeletedFiles**         |                               Optionaler `ITaskItem[]`-Ausgabeparameter.<br /><br /> Definiert ein Array von MSBuild-Ausgabedateielementen, die von Aufgaben verbraucht und ausgegeben werden können                                |
|          **DoDelete**           |                                                            Optionaler **Boolean**-Parameter.<br /><br /> Wenn der Wert `true` ist, werden temporäre Builddateien bereinigt.                                                             |
| **FilePatternsToDeleteOnClean** |                                            Erforderlicher `String` -Parameter.<br /><br /> Gibt eine durch ein Semikolon getrennte Liste von Dateierweiterungen von zu bereinigenden Dateien an                                             |
|   **FilesExcludedFromClean**    |                                                    Optionaler `String` -Parameter.<br /><br /> Gibt eine durch ein Semikolon getrennte Liste von Dateien an, die nicht bereinigt werden sollen                                                    |
|       **FoldersToClean**        | Erforderlicher `String` -Parameter.<br /><br /> Gibt eine durch ein Semikolon getrennte Liste von Verzeichnissen an, die bereinigt werden sollen. Sie können einen vollständigen oder einen relativen Pfad angeben, und der relative Pfad kann ein Platzhaltersymbol (**\\**\*) enthalten. |

## <a name="remarks"></a>Anmerkungen  

## <a name="see-also"></a>Siehe auch  
 [Aufgabenreferenz](../msbuild/msbuild-task-reference.md)
