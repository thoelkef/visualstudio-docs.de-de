---
title: 'Vorgehensweise: Erstellen von bestimmten Zielen in Projektmappen mit MSBuild.exe | Microsoft-Dokumentation'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, building specific targets in a solution
- msbuild.exe, building specific targets in a solution
- MSBuild, msbuild.exe
ms.assetid: f46feb9b-4c16-4fec-b6e1-36a959692ba3
caps.latest.revision: "10"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: 3d683a5f8e8dd78e399fc0fadbc4cccf614013a3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-build-specific-targets-in-solutions-by-using-msbuildexe"></a>Gewusst wie: Erstellen von bestimmten Zielen in Projektmappen mit MSBuild.exe
Sie können MSBuild.exe verwenden, um bestimmte Ziele von bestimmten Projekten in einer Projektmappe zu erstellen.  
  
### <a name="to-build-a-specific-target-of-a-specific-project-in-a-solution"></a>So erstellen Sie ein bestimmtes Ziel von einem bestimmten Projekt in einer Projektmappe.  
  
1.  Geben Sie in der Befehlszeile `MSBuild.exe <SolutionName>.sln` ein, bei der `<SolutionName>` dem Dateinamen der Projektmappe entspricht, die das Ziel enthält, das Sie ausführen möchten.  
  
2.  Geben Sie das Ziel nach dem **/t**-Schalter im Format *ProjektName*:*ZielName* an.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel führt das Ziel `Rebuild` des Projekts `NotInSlnFolder` aus und führt anschließend das Ziel `Clean` des Projekts `InSolutionFolder` aus, das im Projektmappenordner `NewFolder` ist .  
  
```  
msbuild SlnFolders.sln /t:NotInSlnfolder:Rebuild;NewFolder\InSolutionFolder:Clean  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Befehlszeilenreferenz](../msbuild/msbuild-command-line-reference.md)   
 [MSBuild-Referenz](../msbuild/msbuild-reference.md)   
 [MSBuild](../msbuild/msbuild.md)  
 [MSBuild-Grundlagen](../msbuild/msbuild-concepts.md)