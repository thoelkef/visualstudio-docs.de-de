---
title: "WriteLinesToFile Task | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#WriteLinesToFile"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "WriteLinesToFile task [MSBuild]"
  - "MSBuild, WriteLinesToFile task"
ms.assetid: 9c8862ac-8da5-4437-9430-ecc30421f1c9
caps.latest.revision: 9
caps.handback.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# WriteLinesToFile Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Schreibt die Pfade der angegebenen Elemente in die angegebene Textdatei.  
  
## Aufgabenparameter  
 In der folgenden Tabelle werden die Parameter der `WriteLinestoFile`\-Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|------------------|  
|`File`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>\-Parameter.<br /><br /> Gibt die Datei an, in die die Elemente geschrieben werden sollen.|  
|`Lines`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Parameter.<br /><br /> Gibt die Elemente an, die in die Datei geschrieben werden sollen.|  
|`Overwrite`|Optionaler `Boolean`\-Parameter.<br /><br /> Wenn der Wert `true` lautet, überschreibt die Aufgabe den Inhalt der Datei, falls vorhanden.|  
|`Encoding`|Optionaler `String`\-Parameter.<br /><br /> Wählt die Zeichencodierung aus, z. B. "Unicode".  Siehe auch <xref:System.Text.Encoding>.|  
  
## Hinweise  
 Wenn `Overwrite` den Wert `true` hat, wird eine neue Datei erstellt, der Inhalt in die Datei geschrieben und die Datei anschließend geschlossen.  Ist die Zieldatei bereits vorhanden, wird sie überschrieben.  Wenn `Overwrite` `false` ist, wird der Inhalt an die Datei angefügt, dabei die Ziel\-Datei erstellt, wenn Sie nicht bereits vorhanden ist.  
  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>\-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>\-Klasse erbt.  Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Beispiel  
 Im folgenden Beispiel werden mithilfe der `WriteLinesToFile`\-Aufgabe die Pfade der Elemente in der `MyItems`\-Elementauflistung in die Datei geschrieben, die durch die `MyTextFile`\-Elementauflistung angegeben ist.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyTextFile Include="Items.txt"/>  
        <MyItems Include="*.cs"/>  
    </ItemGroup>  
  
    <Target Name="WriteToFile">  
        <WriteLinesToFile  
            File="@(MyTextFile)"  
            Lines="@(MyItems)"  
            Overwrite="true"  
            Encoding="Unicode"/>  
    </Target>  
  
</Project>  
```  
  
## Siehe auch  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)