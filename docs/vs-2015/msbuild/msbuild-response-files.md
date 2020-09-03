---
title: MSBuild-Antwortdateien | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a1ce11edac37368b9c4993a87a8c2b3e734b7862
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189377"
---
# <a name="msbuild-response-files"></a>MSBuild-Antwortdateien
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Anwortdateien (.rsp) sind Textdateien, die Schalter für „MSBuild.exe“-Befehlszeilen enthalten. Die Schalter können sich entweder in unterschiedlichen Zeilen oder in nur einer Zeile befinden. Den Befehlszeilen wird ein **#** -Symbol vorangestellt. Der **@** Schalter wird verwendet, um eine andere Antwortdatei an MSBuild.exe zu übergeben.  
  
 Die automatische Antwortdatei ist eine besondere RSP-Datei, die „MSBuild.exe“ automatisch beim Erstellen eines Projekts verwendet. Diese Datei (MSBuild.rsp) muss sich in demselben Verzeichnis befinden, wie „MSBuild.exe“, um gefunden werden zu können. Sie können diese Datei ändern, um die Standardschalter für die Befehlszeile auf „MSBuild.exe“ festzulegen. Wenn Sie z. b. dieselbe Protokollierung jedes Mal verwenden, wenn Sie ein Projekt erstellen, können Sie "MSBuild. rsp" den **/Logger** -Schalter hinzufügen. MSBuild.exe wird die Protokollierung bei jedem Erstellen eines Projekts verwenden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [MSBuild-Referenz](../msbuild/msbuild-reference.md)   
 [Befehlszeilen Referenz](../msbuild/msbuild-command-line-reference.md)
