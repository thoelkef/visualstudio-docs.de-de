---
title: "How to: Build Incrementally | Microsoft Docs"
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
  - "MSBuild, incremental builds"
  - "incremental builds"
  - "MSBuild, building incrementally"
ms.assetid: 8d82d7d8-a2f1-4df6-9d2f-80b9e0cb3ac3
caps.latest.revision: 21
caps.handback.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# How to: Build Incrementally
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wenn Sie ein großes Projekt erstellen, ist es wichtig, dass zuvor erstellte Komponenten, die immer noch aktuell sind, nicht neu erstellt werden.  Wenn alle Ziele jedes Mal neu erstellt werden, können die einzelnen Buildvorgänge sehr lange dauern.  Um inkrementelle Builds zu ermöglichen \(d. h. Builds, in denen nur zuvor nicht bereits erstellte bzw. nicht mehr aktuelle Ziele neu erstellt werden\), kann [!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] \([!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]\) die Timestamps der Eingabedateien mit den Timestamps der Ausgabedateien vergleichen und feststellen, ob ein Ziel übersprungen, erstellt oder teilweise neu erstellt wird.  Es muss jedoch eine 1:1\-Zuordnung zwischen Ein\- und Ausgaben vorliegen.  Sie können Transformationen verwenden, um die Identifizierung dieser direkten Zuordnung für Ziele zu aktivieren.  Weitere Informationen zu Transformationen finden Sie unter [Transforms](../msbuild/msbuild-transforms.md).  
  
## Angeben von Eingaben und Ausgaben  
 Ein Ziel kann inkrementell erstellt werden, wenn die Ein\- und Ausgaben in der Projektdatei angegeben wurden.  
  
#### So geben Sie Ein\- und Ausgaben für ein Ziel an  
  
-   Verwenden Sie das `Inputs`\-Attribut und das `Outputs`\-Attribut des `Target`\-Elements.  Beispiel:  
  
    ```  
    <Target Name="Build"  
        Inputs="@(CSFile)"  
        Outputs="hello.exe">  
    ```  
  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] kann die Timestamps der Eingabedateien mit den Timestamps der Ausgabedateien vergleichen und feststellen, ob ein Ziel übersprungen, erstellt oder teilweise neu erstellt wird.  Wenn eine beliebige Datei in der `@(CSFile)`\-Elementliste aktueller als die Datei "hello.exe" ist, führt [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] das Ziel im folgenden Beispiel aus. Andernfalls wird es übersprungen:  
  
```  
<Target Name="Build"   
    Inputs="@(CSFile)"   
    Outputs="hello.exe">  
  
    <Csc  
        Sources="@(CSFile)"   
        OutputAssembly="hello.exe"/>  
</Target>  
```  
  
 Wenn Ein\- und Ausgaben in einem Ziel angegeben wurden, können die einzelnen Ausgaben entweder nur einer Eingabe zugeordnet werden, oder es ist keine direkte Zuordnung zwischen Aus\- und Eingaben möglich.  In der vorherigen [Csc Task](../msbuild/csc-task.md)\-Aufgabe kann die Ausgabe hello.exe beispielsweise keiner einzelnen Eingabe zugeordnet werden, da sie von allen Eingaben abhängig ist.  
  
> [!NOTE]
>  Ein Ziel, bei dem keine direkte Zuordnung zwischen Ein\- und Ausgaben stattfindet, wird immer häufiger erstellt als ein Ziel, bei dem die einzelnen Ausgaben nur einer Eingabe zugeordnet werden können. Dies resultiert daraus, dass [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] nicht feststellen kann, welche Ausgaben neu erstellt werden müssen, wenn sich einige der Eingaben geändert haben.  
  
 Aufgaben, in denen eine direkte Zuordnung zwischen den Aus\- und Eingaben festgestellt werden kann, beispielsweise die Aufgabe [LC Task](../msbuild/lc-task.md), eignen sich im Unterschied zu Aufgaben wie `Csc` und [Vbc](../msbuild/vbc-task.md), die eine Ausgabeassembly aus einer Reihe von Eingaben erstellen, besonders für inkrementelle Builds.  
  
## Beispiel  
 Im folgenden Beispiel wird ein Projekt verwendet, das Hilfedateien für ein hypothetisches Hilfesystem erstellt.  Das Projekt konvertiert TXT\-Quelldateien in CONTENT\-Zwischendateien, die anschließend mit XML\-Metadatendateien kombiniert werden, um schließlich die vom Hilfesystem verwendete HELP\-Datei zu erstellen.  Das Projekt verwendet die folgenden hypothetischen Aufgaben:  
  
-   `GenerateContentFiles`: Konvertiert TXT\-Dateien in CONTENT\-Dateien.  
  
-   `BuildHelp`: Kombiniert CONTENT\-Dateien und XML\-Metadatendateien, um die HELP\-Datei zu erstellen.  
  
 Das Projekt verwendet Transformationen, um eine 1:1\-Zuordnung zwischen Ein\- und Ausgaben in der `GenerateContentFiles`\-Aufgabe zu erstellen.  Weitere Informationen finden Sie unter [Transforms](../msbuild/msbuild-transforms.md).  Außerdem wurde für das `Output`\-Element festgelegt, dass die Ausgaben aus der `GenerateContentFiles`\-Aufgabe automatisch als Eingaben für die `BuildHelp`\-Aufgabe verwendet werden.  
  
 Diese Projektdatei enthält sowohl das `Convert`\-Ziel als auch das `Build`\-Ziel.  Die `GenerateContentFiles`\-Aufgabe und die `BuildHelp`\-Aufgabe werden dem `Convert`\-Ziel bzw. dem `Build`\-Ziel hinzugefügt, sodass jedes Ziel inkrementell erstellt werden kann.  Durch Verwendung des `Output`\-Elements werden die Ausgaben der `GenerateContentFiles`\-Aufgabe in die `ContentFile`\-Elementliste aufgenommen, wo sie als Eingaben für die `BuildHelp`\-Aufgabe verwendet werden können.  Wenn Sie das `Output`\-Element auf diese Weise verwenden, werden die Ausgaben aus einer Aufgabe automatisch als Eingaben für eine andere Aufgabe bereitgestellt, sodass Sie die einzelnen Elemente oder Elementlisten nicht in jeder Aufgabe manuell aufführen müssen.  
  
> [!NOTE]
>  Obwohl das `GenerateContentFiles`\-Ziel inkrementell erstellt werden kann, sind alle Ausgaben dieses Ziels immer als Eingaben für das `BuildHelp`\-Ziel erforderlich.  [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] stellt alle Ausgaben eines Ziels automatisch als Eingaben für ein anderes Ziel bereit, wenn Sie das `Output`\-Element verwenden.  
  
```  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <ItemGroup>  
        <TXTFile Include="*.txt"/>  
        <XMLFile Include="\metadata\*.xml"/>  
    </ItemGroup>  
  
    <Target Name = "Convert"  
        Inputs="@(TXTFile)"  
        Outputs="@(TXTFile->'%(Filename).content')">  
  
        <GenerateContentFiles  
            Sources = "@(TXTFile)">  
            <Output TaskParameter = "OutputContentFiles"  
                ItemName = "ContentFiles"/>  
        </GenerateContentFiles>  
    </Target>  
  
    <Target Name = "Build" DependsOnTargets = "Convert"  
        Inputs="@(ContentFiles);@(XMLFiles)"  
        Outputs="$(MSBuildProjectName).help">  
  
        <BuildHelp  
            ContentFiles = "@(ContentFiles)"  
            MetadataFiles = "@(XMLFile)"  
            OutputFileName = "$(MSBuildProjectName).help"/>  
    </Target>  
</Project>  
```  
  
## Siehe auch  
 [Targets](../msbuild/msbuild-targets.md)   
 [Target\-Element \(MSBuild\)](../msbuild/target-element-msbuild.md)   
 [Transforms](../msbuild/msbuild-transforms.md)   
 [Csc Task](../msbuild/csc-task.md)   
 [Vbc Task](../msbuild/vbc-task.md)