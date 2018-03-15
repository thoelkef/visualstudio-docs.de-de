---
title: RemoveDuplicates-Aufgabe | Microsoft-Dokumentation
ms.custom: 
ms.date: 03/01/2018
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#RemoveDuplicates
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, RemoveDuplicates task
- RemoveDuplicates task [MSBuild]
ms.assetid: 481cbab6-73ff-488c-aba5-2c09f9eb1e04
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: ce3271b84d4d6bbb4f7905294d0c9fad678c1b8f
ms.sourcegitcommit: 39c525ec200c6c4ea94815567b3fad7ab14fb7b3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2018
---
# <a name="removeduplicates-task"></a>RemoveDuplicates-Aufgabe
Entfernt doppelte Elemente aus der angegebenen Elementauflistung  
  
## <a name="parameters"></a>Parameter  
 In der folgenden Tabelle werden die Parameter der `RemoveDuplicates` -Aufgabe beschrieben.  
  
|Parameter|description|  
|---------------|-----------------|  
|`Filtered`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Ausgabeparameter.<br /><br /> Enthält eine Elementauflistung, aus der alle doppelten Elemente entfernt wurden Die Eingabereihenfolge der Elemente wird beibehalten, wobei die erste Instanz jedes doppelten Elements beibehalten wird.|  
|`Inputs`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter<br /><br /> Die Elementauflistung, aus der doppelte Elemente entfernt werden sollen|  
  
## <a name="remarks"></a>Hinweise  
 Bei dieser Aufgabe wird die Groß- und Kleinschreibung beachtet, und Elementmetadaten werden beim Ermitteln von Duplikaten nicht verglichen.  
  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel werden mithilfe der `RemoveDuplicates`-Aufgabe doppelte Elemente aus der `MyItems` -Elementauflistung entfernt. Wenn die Aufgabe abgeschlossen ist, enthält die `FilteredItems`-Elementauflistung ein Element.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyItems Include="MyFile.cs"/>  
        <MyItems Include="MyFile.cs">  
            <Culture>fr</Culture>  
        </MyItems>  
        <MyItems Include="myfile.cs"/>  
    </ItemGroup>  
  
    <Target Name="RemoveDuplicateItems">  
        <RemoveDuplicates  
            Inputs="@(MyItems)">  
            <Output  
                TaskParameter="Filtered"  
                ItemName="FilteredItems"/>  
        </RemoveDuplicates>  
    </Target>  
</Project>  
```  

 Das folgende Beispiel zeigt, dass die `RemoveDuplicates`-Aufgabe ihre Eingabereihenfolge beibehält. Wenn die Aufgabe abgeschlossen ist, enthält die `FilteredItems`-Elementauflistung die Elemente „MyFile2.cs“, „MyFile1.cs“ und „MyFile3.cs“ in dieser Reihenfolge.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyItems Include="MyFile2.cs"/>  
        <MyItems Include="MyFile1.cs" />  
        <MyItems Include="MyFile3.cs" />  
        <MyItems Include="myfile1.cs"/>  
    </ItemGroup>  
  
    <Target Name="RemoveDuplicateItems">  
        <RemoveDuplicates  
            Inputs="@(MyItems)">  
            <Output  
                TaskParameter="Filtered"  
                ItemName="FilteredItems"/>  
        </RemoveDuplicates>  
    </Target>  
</Project>  
```  

## <a name="see-also"></a>Siehe auch  
 [Task Reference](../msbuild/msbuild-task-reference.md)  (MSBuild-Aufgabenreferenz)  
 [MSBuild Concepts](../msbuild/msbuild-concepts.md)  (MSBuild-Grundlagen)  
 [Aufgaben](../msbuild/msbuild-tasks.md)
