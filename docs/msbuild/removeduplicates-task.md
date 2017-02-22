---
title: "RemoveDuplicates Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#RemoveDuplicates"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, RemoveDuplicates task"
  - "RemoveDuplicates task [MSBuild]"
ms.assetid: 481cbab6-73ff-488c-aba5-2c09f9eb1e04
caps.latest.revision: 9
caps.handback.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# RemoveDuplicates Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Entfernt doppelte Elemente aus der angegebenen Elementauflistung.  
  
## Parameter  
 In der folgenden Tabelle werden die Parameter der `RemoveDuplicates`\-Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|------------------|  
|`Filtered`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Ausgabeparameter.<br /><br /> Enthält eine Elementauflistung, aus der alle doppelten Elemente entfernt wurden.|  
|`Inputs`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Parameter.<br /><br /> Die Elementauflistung, aus der doppelte Elemente entfernt werden sollen.|  
  
## Hinweise  
 Bei dieser Aufgabe wird beim Ermitteln von Duplikaten die Groß\-\/Kleinschreibung nicht beachtet, und die Metadaten der Elemente werden nicht verglichen.  
  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>\-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>\-Klasse erbt.  Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Beispiel  
 Im folgenden Beispiel wird die `RemoveDuplicates`\-Aufgabe verwendet, um doppelte Elemente aus der `MyItems`\-Elementauflistung zu entfernen.  Nach Abschluss der Aufgabe enthält die `FilteredItems`\-Elementauflistung ein Element.  
  
```  
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
  
## Siehe auch  
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [MSBuild Concepts](../msbuild/msbuild-concepts.md)   
 [Tasks](../msbuild/msbuild-tasks.md)