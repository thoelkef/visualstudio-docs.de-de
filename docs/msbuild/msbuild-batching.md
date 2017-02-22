---
title: "MSBuild Batching | Microsoft Docs"
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
  - "MSBuild, batching"
ms.assetid: d35c085b-27b8-49d7-b6f8-8f2f3a0eec38
caps.latest.revision: 9
caps.handback.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# MSBuild Batching
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Mit [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] können Sie Elementlisten auf der Grundlage von Elementmetadaten in verschiedene Kategorien, so genannte Batches, unterteilen und eine Aufgabe einmal mit jedem Batch ausführen.  
  
## Batchverarbeitung von Aufgaben  
 Durch die Batchverarbeitung von Aufgaben lassen sich Projektdateien einfacher gestalten. So können Elementlisten in verschiedene Batches unterteilt und die einzelnen Batches separat an eine Aufgabe übergeben werden.  Für eine Projektdatei muss die Aufgabe mit den zugehörigen Attributen also nur einmal deklariert werden, obwohl sie mehrere Male ausgeführt werden kann.  
  
 Sie können in [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] angeben, dass eine Aufgabe im Batchmodus verarbeitet werden soll. Dazu verwenden Sie die %\(*ItemMetaDataName*\)\-Notation in einem der Aufgabenattribute.  Im folgenden Beispiel wird die `Example`\-Elementlisten auf der Grundlage der `Color`\-Elementmetadaten in Batches unterteilt, die einzeln an die `MyTask`\-Aufgabe übergeben werden.  
  
> [!NOTE]
>  Falls in den Aufgabenattributen kein weiteres Mal auf die Elementlisten verwiesen wird oder der Metadatenname mehrdeutig ist, können Sie die %\(*ItemCollection.ItemMetaDataName*\)\-Notation verwenden, um den für die Batchverarbeitung zu verwendenden Elementmetadaten\-Wert vollständig zu qualifizieren.  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <Example Include="Item1">  
            <Color>Blue</Color>  
        </Example>  
        <Example Include="Item2">  
            <Color>Red</Color>  
        </Example>  
    </ItemGroup>  
  
    <Target Name="RunMyTask">  
        <MyTask  
            Sources = "@(Example)"  
            Output = "%(Color)\MyFile.txt"/>  
    </Target>  
  
</Project>  
```  
  
 Spezifischere Beispiele für die Batchverarbeitung finden Sie unter [Item Metadata in Task Batching](../msbuild/item-metadata-in-task-batching.md).  
  
## Batchverarbeitung von Zielen  
 Vor dem Ausführen des Ziels überprüft [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], ob die Eingaben und Ausgaben eines Ziels aktuell sind.  Wenn sowohl Eingaben als auch Ausgaben aktuell sind, wird das Ziel übersprungen.  Wenn eine Aufgabe innerhalb eines Ziels im Batchmodus verarbeitet wird, muss [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] ermitteln, ob die Eingaben und Ausgaben der einzelnen Elementbatches aktuell sind.  Andernfalls wird das Ziel jedes Mal ausgeführt, sobald es erreicht wird.  
  
 Im folgenden Beispiel wird ein `Target`\-Element veranschaulicht, das ein `Outputs`\-Attribut mit der Notation %\(*ItemMetaDataName*\) enthält.  [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] unterteilt die `Example`\-Elementlisten basierend auf den `Color`\-Elementmetadaten in Batches und analysiert die Timestamps der Ausgabedateien für jeden Batch.  Wenn die Ausgaben eines Batches nicht aktuell sind, wird das Ziel ausgeführt.  Andernfalls wird das Ziel übersprungen.  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <Example Include="Item1">  
            <Color>Blue</Color>  
        </Example>  
        <Example Include="Item2">  
            <Color>Red</Color>  
        </Example>  
    </ItemGroup>  
  
    <Target Name="RunMyTask"  
        Inputs="@(Example)"  
        Outputs="%(Color)\MyFile.txt">  
        <MyTask  
            Sources = "@(Example)"  
            Output = "%(Color)\MyFile.txt"/>  
    </Target>  
  
</Project>  
```  
  
 Ein anderes Beispiel für die Batchverarbeitung von Zielen finden Sie unter [Item Metadata in Target Batching](../msbuild/item-metadata-in-target-batching.md).  
  
## Eigenschaftenfunktionen mit Metadaten  
 Die Batchverarbeitung kann von Eigenschaftenfunktionen gesteuert werden, die Metadaten enthalten.  Beispiel:  
  
 `$([System.IO.Path]::Combine($(RootPath),%(Compile.Identity)))`  
  
 In diesem Beispiel wird <xref:System.IO.Path.Combine%2A> verwendet, um einen Stammordnerpfad mit einem Compile\-Elementpfad zu kombinieren.  
  
 Eigenschaftenfunktionen werden möglicherweise nicht in Metadatenwerten angezeigt.  Beispiel:  
  
 `%(Compile.FullPath.Substring(0,3))`  
  
 ist nicht zulässig.  
  
 Weitere Informationen über Eigenschaftenfunktionen finden Sie unter [Property Functions](../msbuild/property-functions.md).  
  
## Siehe auch  
 [ItemMetadata Element \(MSBuild\)](../msbuild/itemmetadata-element-msbuild.md)   
 [MSBuild Concepts](../msbuild/msbuild-concepts.md)   
 [MSBuild Reference](../msbuild/msbuild-reference.md)   
 [Advanced Concepts](../msbuild/msbuild-advanced-concepts.md)