---
title: MSBuild-Antwortdateien | Microsoft-Dokumentation
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
- response files, MSBuild
- MSBuild, response files
- MSBuild, .rsp files
- .rsp files
ms.assetid: 9f53987b-20ee-470a-ab62-fce997bb5e15
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f685364bbcf69b8d4b91635cb42079f3f06e5311
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
ms.locfileid: "31571005"
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