---
title: MSBuild-Antwortdateien | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 7520a9f51f0d9420039728a75e84d4ed16583738
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="msbuild-response-files"></a>MSBuild-Antwortdateien
Anwortdateien (.rsp) sind Textdateien, die Schalter für „MSBuild.exe“-Befehlszeilen enthalten. Die Schalter können sich entweder in unterschiedlichen Zeilen oder in nur einer Zeile befinden. Den Befehlszeilen wird ein **#**-Symbol vorangestellt. Der **@**-Schalter wird verwendet, um eine andere Antwortdatei an „MSBuild.exe“ zu übergeben.  
  
 Die automatische Antwortdatei ist eine besondere RSP-Datei, die „MSBuild.exe“ automatisch beim Erstellen eines Projekts verwendet. Diese Datei (MSBuild.rsp) muss sich in demselben Verzeichnis befinden, wie „MSBuild.exe“, um gefunden werden zu können. Sie können diese Datei ändern, um die Standardschalter für die Befehlszeile auf „MSBuild.exe“ festzulegen. Wenn Sie z.B. bei jeder Projekterstellung dieselbe Protokollierung verwenden, können Sie „MSBuild.rsp“ den Schalter **/logger** hinzufügen, damit „MSBuild.exe“ die Protokollierung bei jeder Projekterstellung verwendet.  
  
## <a name="see-also"></a>Siehe auch  
 [MSBuild Reference](../msbuild/msbuild-reference.md)  (MSBuild-Referenz)  
 [MSBuild-Befehlszeilenreferenz](../msbuild/msbuild-command-line-reference.md)