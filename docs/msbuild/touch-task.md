---
title: "Touch Task | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#Touch"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, Touch task"
  - "Touch task [MSBuild]"
ms.assetid: 8a978645-1393-4904-ae69-42afabd8c109
caps.latest.revision: 17
caps.handback.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Touch Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Legt die Zugriffs\- und die Änderungszeiten für Dateien fest.  
  
## Parameter  
 In der folgenden Tabelle werden die Parameter der `Touch`\-Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|------------------|  
|`AlwaysCreate`|Optionaler `Boolean`\-Parameter.<br /><br /> Wenn der Wert `true` lautet, werden Dateien, die noch nicht vorhanden sind, erstellt.|  
|`Files`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Parameter.<br /><br /> Gibt die Auflistung der zu ändernden Dateien an.|  
|`ForceTouch`|Optionaler `Boolean`\-Parameter.<br /><br /> Wenn der Wert `true` lautet, wird die Änderung der Dateien erzwungen, auch wenn die Dateien schreibgeschützt sind.|  
|`Time`|Optionaler `String`\-Parameter.<br /><br /> Gibt eine andere als die aktuelle Zeit an.  Die Angabe muss in einem für die <xref:System.DateTime.Parse%2A>\-Methode zulässigen Format vorliegen.|  
|`TouchedFiles`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Ausgabeparameter.<br /><br /> Enthält die Auflistung der Elemente, die erfolgreich aktualisiert wurden.|  
  
## Hinweise  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>\-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>\-Klasse erbt.  Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Beispiel  
 Im folgenden Beispiel wird die `Touch`\-Aufgabe verwendet, um die Zugriffs\- und Änderungszeiten der in der `Files`\-Elementauflistung angegebenen Dateien zu ändern. Die Liste der Dateien, die erfolgreich aktualisiert wurden, wird in der `FilesTouched`\-Elementauflistung gespeichert.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
<ItemGroup>  
    <Files Include="File1.cs;File2.cs;File3.cs" />  
</ItemGroup>  
  
    <Target Name="TouchFiles">  
        <Touch  
            Files="@(Files)">  
            <Output  
                TaskParameter="TouchedFiles"  
                ItemName="FilesTouched"/>  
    </Touch>  
</Target>  
</Project>  
```  
  
## Siehe auch  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)