---
title: MSBuild-Antwortdateien | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology: msbuild
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- response files, MSBuild
- MSBuild, response files
- MSBuild, .rsp files
- .rsp files
ms.assetid: 9f53987b-20ee-470a-ab62-fce997bb5e15
caps.latest.revision: 3
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 40a9f7b6e1456c511e70937ac6a1cff23dad30d0
ms.sourcegitcommit: a80e7ef2f0a0f6d906a44f4d696aeb208bc1ad70
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2018
---
# <a name="msbuild-response-files"></a>MSBuild-Antwortdateien
Anwortdateien (.rsp) sind Textdateien, die Schalter für „MSBuild.exe“-Befehlszeilen enthalten. Die Schalter können sich entweder in unterschiedlichen Zeilen oder in nur einer Zeile befinden. Den Befehlszeilen wird ein **#**-Symbol vorangestellt. Der **@**-Schalter wird verwendet, um eine andere Antwortdatei an „MSBuild.exe“ zu übergeben.  
  
## <a name="msbuildrsp"></a>MSBuild.rsp
Die automatische Antwortdatei ist eine besondere RSP-Datei, die „MSBuild.exe“ automatisch beim Erstellen eines Projekts verwendet. Diese Datei (MSBuild.rsp) muss sich in demselben Verzeichnis befinden, wie „MSBuild.exe“, um gefunden werden zu können. Sie können diese Datei ändern, um die Standardschalter für die Befehlszeile auf „MSBuild.exe“ festzulegen. Wenn Sie z.B. bei jeder Projekterstellung dieselbe Protokollierung verwenden, können Sie „MSBuild.rsp“ den Schalter **/logger** hinzufügen, damit „MSBuild.exe“ die Protokollierung bei jeder Projekterstellung verwendet.  

## <a name="directorybuildrsp"></a>Directory.Build.rsp
In Version 15.6 und höher durchsucht MSBuild übergeordnete Verzeichnisse des Projekts nach einer Datei namens `Directory.Build.rsp`.  Dies kann in einem Quellcoderepository nützlich sein, um Standardargumente während Befehlszeilenbuilds anzugeben.  Dies kann ebenfalls verwendet werden, um die Befehlszeilenargumente der gehosteten Builds anzugeben.

## <a name="see-also"></a>Siehe auch  
 [MSBuild Reference](../msbuild/msbuild-reference.md)  (MSBuild-Referenz)  
 [MSBuild-Befehlszeilenreferenz](../msbuild/msbuild-command-line-reference.md)