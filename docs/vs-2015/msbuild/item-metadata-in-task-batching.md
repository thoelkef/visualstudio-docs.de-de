---
title: Elementmetadaten bei der Batchverarbeitung von Aufgaben | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, batching
- task batching [MSBuild]
- MSBuild, task batching
ms.assetid: 31e480f8-fe4d-4633-8c54-8ec498e2306d
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 15a6eeea6ebf75513419cc763b2e29a6b6264391
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436795"
---
# <a name="item-metadata-in-task-batching"></a>Elementmetadaten bei der Batchverarbeitung von Aufgaben
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] kann Elementlisten anhand von Elementmetadatenelementen in verschiedene Kategorien oder Batches unterteilen und eine Aufgabe einmal mit jedem Batch ausführen. Es ist schwierig zu erkennen, welche Elemente mit welchem Batch übergeben werden. In diesem Artikel werden die folgenden häufig auftretenden Szenarios thematisiert, bei denen die Batchverarbeitung ein Bestandteil ist.  
  
- Unterteilen einer Elementliste in Batches  
  
- Unterteilen mehrerer Elementlisten in Batches  
  
- Batchverarbeitung einzelner Elemente  
  
- Filtern von Elementlisten  
  
  Weitere Informationen zur Batchverarbeitung mit [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] finden Sie unter [Batching (Batchverarbeitung)](../msbuild/msbuild-batching.md).  
  
## <a name="dividing-an-item-list-into-batches"></a>Unterteilen einer Elementliste in Batches  
 Mithilfe der Batchverarbeitung können Sie anhand von Elementmetadatenelementen eine Elementliste in verschiedene Batches unterteilen und diese Batches anschließend einzeln an eine Aufgabe übergeben. Dieser Vorgang ist nützlich für die Erstellung von Satellitenassemblys.  
  
 Im untenstehenden Beispiel wird dargestellt, wie Sie eine Elementliste anhand von Elementmetadatenelementen in Batches unterteilen können. Die Elementliste `ExampColl` wird anhand des Elementmetadatenelements `Number` in drei Batches unterteilt. Dadurch, dass `%(ExampColl.Number)` im `Text`-Attribut vorhanden ist, wird [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] benachrichtigt, dass eine Batchverarbeitung ausgeführt werden sollte. Die Elementliste `ExampColl` ist anhand des Elementmetadatenelements `Number` in drei Batches unterteilt, und jeder Batch wird einzeln an eine Aufgabe übergeben.  
  
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
  
 Der [Message Task](../msbuild/message-task.md)-Task zeigt die folgenden Informationen an:  
  
 `Number: 1 -- Items in ExampColl: Item1;Item4`  
  
 `Number: 2 -- Items in ExampColl: Item2;Item5`  
  
 `Number: 3 -- Items in ExampColl: Item3;Item6`  
  
## <a name="dividing-several-item-lists-into-batches"></a>Unterteilen mehrerer Elementlisten in Batches  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] kann mehrere Elementlisten anhand desselben Elementmetadatenelements in Batches unterteilen. Dadurch können verschiedene Elementlisten einfacher in Batches unterteilt werden, um mehrere Assemblys zu erstellen. Beispielsweise kann eine Elementliste mit CS-Dateien, die in Anwendungsbatches und einen Assemblybatch unterteilt sind, sowie eine Elementliste mit Ressourcendateien vorhanden sein, die in ein Anwendungsbatch und ein Assemblybatch unterteilt ist. In diesem Fall können Sie die Batchverarbeitung nutzen, um diese Elementlisten an eine Aufgabe zu übergeben und sowohl die Anwendung als auch die Assembly zu erstellen.  
  
> [!NOTE]
> Wenn eine Elementliste, die an eine Aufgabe übergeben wird, keine Elemente mit dem Metadatenelement enthält, auf das verwiesen wird, werden sämtliche Elemente in dieser Elementliste an jeden Batch übergeben.  
  
 Im untenstehenden Beispiel wird dargestellt, wie Sie mehrere Elementlisten anhand von Elementmetadatenelementen in Batches unterteilen können. Die Elementlisten `ExampColl` und `ExampColl2` werden jeweils anhand des Elementmetadatenelements `Number` in drei Batches unterteilt. Dadurch, dass `%(Number)` im `Text`-Attribut vorhanden ist, wird [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] benachrichtigt, dass eine Batchverarbeitung ausgeführt werden sollte. Die Elementlisten `ExampColl` und `ExampColl2` werden jeweils anhand des Elementmetadatenelements `Number` in drei Batches unterteilt, und jeder Batch wird einzeln an eine Aufgabe übergeben.  
  
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
  
 Der [Message Task](../msbuild/message-task.md)-Task zeigt die folgenden Informationen an:  
  
 `Number: 1 -- Items in ExampColl: Item1 ExampColl2: Item4`  
  
 `Number: 2 -- Items in ExampColl: Item2 ExampColl2: Item5`  
  
 `Number: 3 -- Items in ExampColl: Item3 ExampColl2: Item6`  
  
## <a name="batching-one-item-at-a-time"></a>Batchverarbeitung einzelner Elemente nacheinander  
 Die Batchverarbeitung kann auch für bekannte Elementmetadaten durchgeführt werden, die jedem Element bei der Erstellung zugeordnet werden. Dadurch wird garantiert, dass jedes Element in einer Auflistung auch über Metadaten verfügt, die bei der Batchverarbeitung verwendet werden können. Jedes Element hat seinen eigenen `Identity`-Metadatenwert, der nützlich für die Unterteilung der in Elementlisten enthaltenen Elemente in separate Batches ist. Eine vollständige Liste bekannter Elementmetadaten finden Sie unter [Well-known Item Metadata (Bekannte Elementmetadaten)](../msbuild/msbuild-well-known-item-metadata.md).  
  
 Im untenstehenden Beispiel wird dargestellt, wie Sie die Elemente in einer Elementliste einzeln nacheinander in Batches unterteilen können. Da jedes Element seinen eigenen `Identity`-Metadatenwert hat, wird die Elementliste `ExampColl` in sechs Batches unterteilt, wobei jedes Batch jeweils ein Element der Elementliste enthält. Dadurch, dass `%(Identity)` im `Text`-Attribut vorhanden ist, wird [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] benachrichtigt, dass eine Batchverarbeitung ausgeführt werden sollte.  
  
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
  
 Der [Message Task](../msbuild/message-task.md)-Task zeigt die folgenden Informationen an:  
  
```  
Identity: "Item1" -- Items in ExampColl: Item1  
Identity: "Item2" -- Items in ExampColl: Item2  
Identity: "Item3" -- Items in ExampColl: Item3  
Identity: "Item4" -- Items in ExampColl: Item4  
Identity: "Item5" -- Items in ExampColl: Item5  
Identity: "Item6" -- Items in ExampColl: Item6  
```  
  
## <a name="filtering-item-lists"></a>Filtern von Elementlisten  
 Die Batchverarbeitung kann auch dafür genutzt werden, bestimmte Elemente einer Elementliste herauszufiltern, bevor sie an eine Aufgabe übergeben wird. Wenn Sie z.B. nach dem bekannten `Extension`-Elementmetadatenwert filtern, können Sie eine Aufgabe nur für Dateien ausführen, die eine spezifische Erweiterung enthalten.  
  
 Im untenstehenden Beispiel wird dargestellt, wie Sie zunächst eine Elementliste anhand eines Elementmetadatenelements in Batches unterteilen und anschließend diese Batches bei der Übergabe an eine Aufgabe filtern. Die Elementliste `ExampColl` wird anhand des Elementmetadatenelements `Number` in drei Batches unterteilt. Das `Condition`-Attribut einer Aufgabe gibt an, dass nur Batches mit einem `Number`-Elementmetadatenwert von `2` an die Aufgabe übergeben werden sollen.  
  
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
  
 Der [Message Task](../msbuild/message-task.md)-Task zeigt die folgenden Informationen an:  
  
```  
Items in ExampColl: Item2;Item5  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Well-known Item Metadata (Bekannte Elementmetadaten)](../msbuild/msbuild-well-known-item-metadata.md)   
 [Item-Element (MSBuild)](../msbuild/item-element-msbuild.md)   
 [ItemMetadata-Element (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)   
 [Batching (Batchverarbeitung)](../msbuild/msbuild-batching.md)   
 [MSBuild Concepts](../msbuild/msbuild-concepts.md)  (MSBuild-Grundlagen)  
 [MSBuild-Referenz](../msbuild/msbuild-reference.md)
