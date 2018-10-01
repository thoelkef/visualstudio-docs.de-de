---
title: 'Vorgehensweise: Erstellen von bestimmten Zielen in Projektmappen mit MSBuild.exe | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSBuild, building specific targets in a solution
- msbuild.exe, building specific targets in a solution
- MSBuild, msbuild.exe
ms.assetid: f46feb9b-4c16-4fec-b6e1-36a959692ba3
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0bdc5d824d802916c38ef0267dae0de85e8814e8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47509265"
---
# <a name="how-to-build-specific-targets-in-solutions-by-using-msbuildexe"></a>Gewusst wie: Erstellen von bestimmten Zielen in Projektmappen mit MSBuild.exe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Vorgehensweise: Erstellen von bestimmten Zielen in Projektmappen von MSBuild.exe mithilfe](https://docs.microsoft.com/visualstudio/msbuild/how-to-build-specific-targets-in-solutions-by-using-msbuild-exe).  
  
  
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
 [MSBuild](msbuild.md)  
 [MSBuild-Grundlagen](../msbuild/msbuild-concepts.md)


