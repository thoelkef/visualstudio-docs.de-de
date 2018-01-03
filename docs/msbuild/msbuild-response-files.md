---
title: MSBuild-Antwortdateien | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
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
caps.latest.revision: "3"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d2d204535d24fc1ef000c897f45bdb51710dfee9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="msbuild-response-files"></a>MSBuild-Antwortdateien
Anwortdateien (.rsp) sind Textdateien, die Schalter für „MSBuild.exe“-Befehlszeilen enthalten. Die Schalter können sich entweder in unterschiedlichen Zeilen oder in nur einer Zeile befinden. Den Befehlszeilen wird ein **#**-Symbol vorangestellt. Der **@**-Schalter wird verwendet, um eine andere Antwortdatei an „MSBuild.exe“ zu übergeben.  
  
 Die automatische Antwortdatei ist eine besondere RSP-Datei, die „MSBuild.exe“ automatisch beim Erstellen eines Projekts verwendet. Diese Datei (MSBuild.rsp) muss sich in demselben Verzeichnis befinden, wie „MSBuild.exe“, um gefunden werden zu können. Sie können diese Datei ändern, um die Standardschalter für die Befehlszeile auf „MSBuild.exe“ festzulegen. Wenn Sie z.B. bei jeder Projekterstellung dieselbe Protokollierung verwenden, können Sie „MSBuild.rsp“ den Schalter **/logger** hinzufügen, damit „MSBuild.exe“ die Protokollierung bei jeder Projekterstellung verwendet.  
  
## <a name="see-also"></a>Siehe auch  
 [MSBuild Reference](../msbuild/msbuild-reference.md)  (MSBuild-Referenz)  
 [Command-Line Reference](../msbuild/msbuild-command-line-reference.md) (MSBuild-Befehlszeilenreferenz)