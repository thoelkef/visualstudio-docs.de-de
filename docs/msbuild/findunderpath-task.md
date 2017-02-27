---
title: "FindUnderPath Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#FindUnderPath"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, FindUnderPath task"
  - "FindUnderPath task [MSBuild]"
ms.assetid: 3c6d58b0-36e8-47aa-bfca-b73dd2045d91
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# FindUnderPath Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ermittelt, welche Elemente in der angegebenen Elementauflistung Pfade in dem angegebenen Ordner oder diesem untergeordnete Pfade aufweisen.  
  
## Parameter  
 In der folgenden Tabelle werden die Parameter der `FindUnderPath`\-Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|------------------|  
|`Files`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Parameter.<br /><br /> Gibt die Dateien an, deren Pfade mit dem vom `Path`\-Parameter angegebenen Pfad verglichen werden sollen.|  
|`InPath`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Ausgabeparameter.<br /><br /> Enthält die Elemente, die im angegebenen Pfad gefunden wurden.|  
|`OutOfPath`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Ausgabeparameter.<br /><br /> Enthält die Elemente, die im angegebenen Pfad nicht gefunden wurden.|  
|`Path`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>\-Parameter.<br /><br /> Gibt den Ordnerpfad an, auf den verwiesen werden soll.|  
|`UpdateToAbsolutePaths`|Optionaler `Boolean`\-Parameter.<br /><br /> Bei true werden die Pfade der Ausgabeelemente in absolute Pfade geändert.|  
  
## Hinweise  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>\-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>\-Klasse erbt.  Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Beispiel  
 Im folgenden Beispiel wird mithilfe der `FindUnderPath`\-Aufgabe ermittelt, ob die im `MyFiles`\-Element enthaltenen Dateien Pfade aufweisen, die dem von der `SearchPath`\-Eigenschaft angegebenen Pfad untergeordnet sind.  Nachdem Abschluss der Aufgabe enthält das `FilesNotFoundInPath`\-Element die Datei `File1.txt` und das `FilesFoundInPath`\-Element die Datei `File2.txt`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <MyFiles Include="C:\File1.txt" />  
        <MyFiles Include="C:\Projects\MyProject\File2.txt" />  
    </ItemGroup>  
  
    <PropertyGroup>  
        <SearchPath>C:\Projects\MyProject</SearchPath>  
    </PropertyGroup>  
  
    <Target Name="FindFiles">  
        <FindUnderPath  
            Files="@(MyFiles)"  
            Path="$(SearchPath)">  
            <Output  
                TaskParameter="InPath"  
                ItemName="FilesFoundInPath" />  
            <Output  
                TaskParameter="OutOfPath"  
                ItemName="FilesNotFoundInPath" />  
        </FindUnderPath>  
    </Target>  
  
</Project>  
```  
  
## Siehe auch  
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [Tasks](../msbuild/msbuild-tasks.md)   
 [MSBuild Concepts](../msbuild/msbuild-concepts.md)