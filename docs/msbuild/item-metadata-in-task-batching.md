---
title: "Item Metadata in Task Batching | Microsoft Docs"
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
  - "task batching [MSBuild]"
  - "MSBuild, task batching"
ms.assetid: 31e480f8-fe4d-4633-8c54-8ec498e2306d
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Item Metadata in Task Batching
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Mit [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] können Sie Elementlisten auf der Grundlage von Elementmetadaten in verschiedene Kategorien, so genannte Batches, unterteilen und eine Aufgabe mit jedem Batch ausführen.  Teilweise ist es schwer zu erkennen, welche Elemente mit welchem Batch übergeben werden.  In diesem Thema werden die folgenden allgemeinen Szenarien behandelt, bei denen Batchverarbeitung eine Rolle spielt.  
  
-   Unterteilen einer Elementliste in Batches  
  
-   Unterteilen von mehreren Elementlisten in Batches  
  
-   Batchverarbeitung von jeweils einem Element  
  
-   Filtern von Elementlisten  
  
 Weitere Informationen zur Batchverarbeitung mit [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] finden Sie unter [Batching](../msbuild/msbuild-batching.md).  
  
## Unterteilen einer Elementliste in Batches  
 Bei der Batchverarbeitung kann eine Elementliste auf der Grundlage von Elementmetadaten in verschiedene Batches unterteilt und jeder Batch separat an eine Aufgabe übergeben werden.  Dies ist hilfreich für die Erstellung von Satellitenassemblys.  
  
 Das folgende Beispiel zeigt, wie eine Elementliste auf der Grundlage von Elementmetadaten in Batches unterteilt wird.  Die `ExampColl`\-Elementliste wird auf der Grundlage der `Number`\-Elementmetadaten in drei Batches unterteilt.  Durch das Vorhandensein von `%(ExampColl.Number)` im `Text`\-Attribut wird [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] mitgeteilt, dass die Batchverarbeitung ausgeführt werden soll.  Die `ExampColl`\-Elementliste wird auf der Grundlage der `Number`\-Metadaten in drei Batches unterteilt, von denen jeder separat an die Aufgabe übergeben wird.  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <ExampColl Include="Item1">  
            <Number>1</Number>  
        </ExampColl>  
        <ExampColl Include="Item2">  
            <Number>2</Number>  
        </ExampColl>  
        <ExampColl Include="Item3">  
            <Number>3</Number>  
        </ExampColl>  
        <ExampColl Include="Item4">  
            <Number>1</Number>  
        </ExampColl>  
        <ExampColl Include="Item5">  
            <Number>2</Number>  
        </ExampColl>  
        <ExampColl Include="Item6">  
            <Number>3</Number>  
        </ExampColl>  
    </ItemGroup>  
  
    <Target Name="ShowMessage">  
        <Message  
            Text = "Number: %(ExampColl.Number) -- Items in ExampColl: @(ExampColl)"/>  
    </Target>  
  
</Project>  
```  
  
 Die [Message Task](../msbuild/message-task.md)\-Aufgabe zeigt die folgenden Informationen an:  
  
 `Number: 1 -- Items in ExampColl: Item1;Item4`  
  
 `Number: 2 -- Items in ExampColl: Item2;Item5`  
  
 `Number: 3 -- Items in ExampColl: Item3;Item6`  
  
## Unterteilen von mehreren Elementlisten in Batches  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] kann mehrere Elementlisten in Batches unterteilen, die auf denselben Metadaten basieren.  Dies erleichtert die Unterteilung verschiedener Elementlisten in Batches, um mehrere Assemblys zu erstellen.  Beispielsweise könnten Sie über eine Elementliste von CS\-Dateien sowie über eine Elementliste von Ressourcendateien verfügen, die jeweils in einen Anwendungsbatch und einen Assemblybatch unterteilt sind.  Sie könnten die Batchverarbeitung dann verwenden, um diese Elementlisten an eine Aufgabe zu übergeben und sowohl die Anwendung als auch die Assembly zu erstellen.  
  
> [!NOTE]
>  Wenn eine Elementliste, die an eine Aufgabe übergeben wird, keine Elemente mit den referenzierten Metadaten enthält, wird jedes einzelne Element in dieser Elementliste an jeden Batch übergeben.  
  
 Das folgende Beispiel zeigt, wie mehrere Elementlisten auf Grundlage von Elementmetadaten in Batches unterteilt werden.  Die `ExampColl`\- und die `ExampColl2`\-Elementlisten werden auf der Grundlage der `Number`\-Elementmetadaten in drei Batches unterteilt.  Durch das Vorhandensein von `%(Number)` im `Text`\-Attribut wird [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] mitgeteilt, dass die Batchverarbeitung ausgeführt werden soll.  Die `ExampColl`\- und die `ExampColl2`\-Elementlisten werden auf der Grundlage der `Number`\-Metadaten in drei Batches unterteilt, von denen jeder separat an die Aufgabe übergeben wird.  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
  
        <ExampColl Include="Item1">  
            <Number>1</Number>  
        </ExampColl>  
        <ExampColl Include="Item2">  
            <Number>2</Number>  
        </ExampColl>  
        <ExampColl Include="Item3">  
            <Number>3</Number>  
        </ExampColl>  
  
        <ExampColl2 Include="Item4">  
            <Number>1</Number>  
        </ExampColl2>  
        <ExampColl2 Include="Item5">  
            <Number>2</Number>  
        </ExampColl2>  
        <ExampColl2 Include="Item6">  
            <Number>3</Number>  
        </ExampColl2>  
  
    </ItemGroup>  
  
    <Target Name="ShowMessage">  
        <Message  
            Text = "Number: %(Number) -- Items in ExampColl: @(ExampColl) ExampColl2: @(ExampColl2)"/>  
    </Target>  
  
</Project>  
```  
  
 Die [Message Task](../msbuild/message-task.md)\-Aufgabe zeigt die folgenden Informationen an:  
  
 `Number: 1 -- Items in ExampColl: Item1 ExampColl2: Item4`  
  
 `Number: 2 -- Items in ExampColl: Item2 ExampColl2: Item5`  
  
 `Number: 3 -- Items in ExampColl: Item3 ExampColl2: Item6`  
  
## Batchverarbeitung jeweils eines Elements  
 Die Batchverarbeitung kann auch auf der Basis von bekannten Elementmetadaten ausgeführt werden, die jedem Element bei der Erstellung zugewiesen werden.  Dadurch wird gewährleistet, dass jedes Element in einer Auflistung einige Metadaten aufweist, die für die Batchverarbeitung verwendet werden.  Der `Identity`\-Metadatenwert ist für jedes Element eindeutig, und er ist hilfreich, um jedes Element in einer Elementliste einem separaten Batch zuzuordnen.  Eine vollständige Liste bekannter Elementmetadaten finden Sie unter [Well\-known Item Metadata](../msbuild/msbuild-well-known-item-metadata.md).  
  
 Im folgenden Beispiel wird veranschaulicht, wie die einzelnen Elemente in einer Elementliste jeweils separat als Batch verarbeitet werden.  Da der `Identity`\-Metadatenwert der einzelnen Elemente eindeutig ist, wird die `ExampColl` \-Elementliste in sechs Batches unterteilt, von denen jeder ein Element der Elementliste enthält.  Durch das Vorhandensein von `%(Identity)` im `Text`\-Attribut wird [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] mitgeteilt, dass die Batchverarbeitung ausgeführt werden soll.  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
  
        <ExampColl Include="Item1"/>  
        <ExampColl Include="Item2"/>  
        <ExampColl Include="Item3"/>  
        <ExampColl Include="Item4"/>  
        <ExampColl Include="Item5"/>  
        <ExampColl Include="Item6"/>  
  
    </ItemGroup>  
  
    <Target Name="ShowMessage">  
        <Message  
            Text = "Identity: "%(Identity)" -- Items in ExampColl: @(ExampColl)"/>  
    </Target>  
  
</Project>  
```  
  
 Die [Message Task](../msbuild/message-task.md)\-Aufgabe zeigt die folgenden Informationen an:  
  
```  
Identity: "Item1" -- Items in ExampColl: Item1  
Identity: "Item2" -- Items in ExampColl: Item2  
Identity: "Item3" -- Items in ExampColl: Item3  
Identity: "Item4" -- Items in ExampColl: Item4  
Identity: "Item5" -- Items in ExampColl: Item5  
Identity: "Item6" -- Items in ExampColl: Item6  
```  
  
## Filtern von Elementlisten  
 Bevor Elemente an eine Aufgabe übergeben werden, können mithilfe der Batchverarbeitung bestimmte Elemente aus einer Elementliste herausgefiltert werden.  Durch das Filtern nach dem bekannten `Extension`\-Elementmetadaten\-Wert haben Sie beispielsweise die Möglichkeit, eine Aufgabe nur für Dateien mit einer bestimmten Erweiterung auszuführen.  
  
 Im folgenden Beispiel wird veranschaulicht, wie Sie eine Elementliste auf der Grundlage von Elementmetadaten in Batches unterteilen und diese Batches anschließend bei der Übergabe an eine Aufgabe filtern.  Die `ExampColl`\-Elementliste wird auf der Grundlage der `Number`\-Elementmetadaten in drei Batches unterteilt.  Durch das `Condition`\-Attribut der Aufgabe wird festgelegt, dass nur Batches mit dem `Number`\-Elementmetadaten\-Wert `2` an die Aufgabe übergeben werden.  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
  
        <ExampColl Include="Item1">  
            <Number>1</Number>  
        </ExampColl>  
        <ExampColl Include="Item2">  
            <Number>2</Number>  
        </ExampColl>  
        <ExampColl Include="Item3">  
            <Number>3</Number>  
        </ExampColl>  
        <ExampColl Include="Item4">  
            <Number>1</Number>  
        </ExampColl>  
        <ExampColl Include="Item5">  
            <Number>2</Number>  
        </ExampColl>  
        <ExampColl Include="Item6">  
            <Number>3</Number>  
        </ExampColl>  
  
    </ItemGroup>  
  
    <Target Name="Exec">  
        <Message  
            Text = "Items in ExampColl: @(ExampColl)"  
            Condition="'%(Number)'=='2'"/>  
    </Target>  
  
</Project>  
```  
  
 Die [Message Task](../msbuild/message-task.md)\-Aufgabe zeigt die folgenden Informationen an:  
  
```  
Items in ExampColl: Item2;Item5  
```  
  
## Siehe auch  
 [Well\-known Item Metadata](../msbuild/msbuild-well-known-item-metadata.md)   
 [Item Element \(MSBuild\)](../msbuild/item-element-msbuild.md)   
 [ItemMetadata Element \(MSBuild\)](../msbuild/itemmetadata-element-msbuild.md)   
 [Batching](../msbuild/msbuild-batching.md)   
 [MSBuild Concepts](../msbuild/msbuild-concepts.md)   
 [MSBuild Reference](../msbuild/msbuild-reference.md)