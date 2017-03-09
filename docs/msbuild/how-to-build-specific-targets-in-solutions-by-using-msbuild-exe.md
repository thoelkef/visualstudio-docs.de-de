---
title: "Gewusst wie: Erstellen von bestimmten Zielen in Projektmappen mit MSBuild.exe | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Erstellen von spezifischen Zielen in einer Projektmappe MSBuild"
  - "MSBuild.exe, Erstellen von spezifischen Zielen in einer Projektmappe"
  - "MSBuild, msbuild.exe"
ms.assetid: f46feb9b-4c16-4fec-b6e1-36a959692ba3
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Gewusst wie: Erstellen von bestimmten Zielen in Projektmappen mit MSBuild.exe
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können MSBuild.exe verwenden, um bestimmte Ziele von bestimmten Projekten in einer Projektmappe zu erstellen.  
  
### <a name="to-build-a-specific-target-of-a-specific-project-in-a-solution"></a>Um ein bestimmtes Ziel eines bestimmten Projekts in einer Projektmappe zu erstellen.  
  
1.  Geben Sie an der Befehlszeile `MSBuild.exe <SolutionName>.sln`, wobei `<SolutionName>` entspricht dem Dateinamen der Projektmappe, die das Ziel enthält, die Sie ausführen möchten.  
  
2.  Geben Sie das Ziel nach der **/t** -Schalter im Format *Projektname*:*TargetName*.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel führt die `Rebuild` Ziel der `NotInSlnFolder` und führt dann die `Clean` Ziel der `InSolutionFolder` befindet sich im Projekt die `NewFolder` Projektmappenordner.  
  
```  
msbuild SlnFolders.sln /t:NotInSlnfolder:Rebuild;NewFolder\InSolutionFolder:Clean  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Befehlszeilenreferenz](../msbuild/msbuild-command-line-reference.md)   
 [MSBuild-Referenz](../msbuild/msbuild-reference.md)   
 [ MSBuild](../msbuild/msbuild1.md)  
 [MSBuild-Konzepte](../msbuild/msbuild-concepts.md)