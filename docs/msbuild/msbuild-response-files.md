---
title: MSBuild-Antwortdateien | Microsoft-Dokumentation
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9e83ed29e2caf180cdd8950b73f65f62794a8783
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63004846"
---
# <a name="msbuild-response-files"></a>MSBuild-Antwortdateien
Anwortdateien (*RSP*-Dateien) sind Textdateien, die Schalter für die *MSBuild.exe*-Befehlszeile enthalten. Die Schalter können sich entweder in unterschiedlichen Zeilen oder in nur einer Zeile befinden. Den Befehlszeilen wird ein **#**-Symbol vorangestellt. Der **@**-Schalter wird verwendet, um eine andere Antwortdatei an *MSBuild.exe* zu übergeben.

## <a name="msbuildrsp"></a>MSBuild.rsp
Die automatische Antwortdatei ist eine besondere *RSP*-Datei, die *MSBuild.exe* automatisch beim Erstellen eines Projekts verwendet. Diese Datei (*MSBuild.rsp*) muss sich in demselben Verzeichnis befinden, in dem sich *MSBuild.exe* befindet, um gefunden werden zu können. Sie können diese Datei bearbeiten, um die Standardschalter für die Befehlszeile auf *MSBuild.exe* festzulegen. Wenn Sie z.B. bei jeder Projekterstellung dieselbe Protokollierung verwenden, können Sie *MSBuild.rsp* den Schalter **-logger** hinzufügen, damit *MSBuild.exe* die Protokollierung bei jeder Projekterstellung verwendet.

## <a name="directorybuildrsp"></a>Directory.Build.rsp
In Version 15.6 und höher durchsucht MSBuild übergeordnete Verzeichnisse des Projekts nach einer Datei namens *Directory.Build.rsp*.  Dies kann in einem Quellcoderepository nützlich sein, um Standardargumente während Befehlszeilenbuilds anzugeben.  Dies kann ebenfalls verwendet werden, um die Befehlszeilenargumente der gehosteten Builds anzugeben.

## <a name="see-also"></a>Siehe auch
- [MSBuild-Referenz](../msbuild/msbuild-reference.md)
- [Befehlszeilenreferenz](../msbuild/msbuild-command-line-reference.md)