---
title: "Item Metadata in Target Batching | Microsoft Docs"
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
  - "batching [MSBuild]"
  - "MSBuild, target batching"
  - "target batching [MSBuild]"
ms.assetid: f3cc4186-6a4c-4161-bbe5-1ec638b4925b
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Item Metadata in Target Batching
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] ist in der Lage, Abhängigkeitsanalysen für die Eingaben und Ausgaben eines Buildziels auszuführen.  Wenn feststeht, dass die Eingaben oder die Ausgaben des Ziels aktuell sind, wird das Ziel übersprungen, und der Build wird fortgesetzt.  `Target`\-Elemente geben die Elemente, die während der Abhängigkeitsanalyse überprüft werden sollen, mit dem `Inputs`\-Attribut und dem `Outputs`\-Attribut an.  
  
 Wenn ein Ziel eine Aufgabe enthält, die Elemente im Batchmodus als Eingaben oder Ausgaben verwendet, sollte das `Target`\-Element des Ziels die Batchverarbeitung in seinem `Inputs`\-Attribut oder `Outputs`\-Attribut verwenden, damit Batches mit Elementen, die bereits auf dem neuesten Stand sind, von [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] übersprungen werden können.  
  
## Batchverarbeitung von Zielen  
 Das folgende Beispiel enthält eine Elementliste mit dem Namen `Res`, die auf der Grundlage der `Culture`\-Elementmetadaten in zwei Batches unterteilt ist.  Jeder dieser Batches wird an die `AL`\-Aufgabe übergeben, die eine Ausgabeassembly für jeden Batch erstellt.  Wenn das `Outputs`\-Attribut des `Target`\-Elements im Batchmodus verarbeitet wird, kann [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] vor dem Ausführen des Ziels für jeden einzelnen Batch feststellen, ob er aktuell ist.  Wenn keine Batchverarbeitung für Ziele verwendet wird, würde die Aufgabe bei jedem Ausführen des Ziels beide Elementbatches ausführen.  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <Res Include="Strings.fr.resources">  
            <Culture>fr</Culture>  
        </Res>  
        <Res Include="Strings.jp.resources">  
            <Culture>jp</Culture>  
        </Res>  
        <Res Include="Menus.fr.resources">  
            <Culture>fr</Culture>  
        </Res>  
        <Res Include="Dialogs.fr.resources">  
            <Culture>fr</Culture>  
        </Res>  
        <Res Include="Dialogs.jp.resources">  
            <Culture>jp</Culture>  
        </Res>  
        <Res Include="Menus.jp.resources">  
            <Culture>jp</Culture>  
        </Res>  
    </ItemGroup>  
  
    <Target Name="Build"  
        Inputs="@(Res)"  
        Outputs="%(Culture)\MyApp.resources.dll">  
  
        <AL Resources="@(Res)"  
            TargetType="library"  
            OutputAssembly="%(Culture)\MyApp.resources.dll"  
  
    </Target>  
  
</Project>  
```  
  
## Siehe auch  
 [How to: Build Incrementally](../msbuild/how-to-build-incrementally.md)   
 [Batching](../msbuild/msbuild-batching.md)   
 [Target\-Element \(MSBuild\)](../msbuild/target-element-msbuild.md)   
 [Item Metadata in Task Batching](../msbuild/item-metadata-in-task-batching.md)