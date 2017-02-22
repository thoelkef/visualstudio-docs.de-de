---
title: "CreateProperty Task | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#CreateProperty"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "CreateProperty task [MSBuild]"
  - "MSBuild, CreateProperty task"
ms.assetid: fbc31a88-62d4-43d2-b739-68ef3fac38f5
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# CreateProperty Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Füllt Eigenschaften mit übergebenen Werten auf.  Auf diese Weise können Werte von einer Eigenschaft oder Zeichenfolge in eine andere kopiert werden.  
  
## Attribute  
 In der folgenden Tabelle werden die Parameter der `CreateProperty`\-Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|------------------|  
|`Value`|Optionaler `String`\-Ausgabeparameter.<br /><br /> Gibt den Wert an, der in die neue Eigenschaft kopiert werden soll.|  
|`ValueSetByTask`|Optionaler `String`\-Ausgabeparameter.<br /><br /> Enthält denselben Wert wie der `Value`\-Parameter.  Verwenden Sie diesen Parameter nur, wenn Sie vermeiden möchten, dass die Ausgabeeigenschaft von [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] festgelegt wird, falls das einschließende Ziel übersprungen wird, da die Ausgaben aktuell sind.|  
  
## Hinweise  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>\-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>\-Klasse erbt.  Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Beispiel  
 Im folgenden Beispiel wird die `CreateProperty`\-Aufgabe verwendet, um die `NewFile`\-Eigenschaft mit den kombinierten Werten der `SourceFilename`\-Eigenschaft und der `SourceFileExtension`\-Eigenschaft zu erstellen.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <PropertyGroup>  
        <SourceFilename>Module1</SourceFilename>  
        <SourceFileExtension>vb</SourceFileExtension>  
    </PropertyGroup>  
  
    <Target Name="CreateProperties">  
  
        <CreateProperty  
            Value="$(SourceFilename).$(SourceFileExtension)">  
            <Output  
                TaskParameter="Value"  
                PropertyName="NewFile" />  
        </CreateProperty>  
  
    </Target>  
  
</Project>  
```  
  
 Nach der Ausführung des Projekts lautet der Wert der `NewFile`\-Eigenschaft `Module1.vb`.  
  
## Siehe auch  
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [Tasks](../msbuild/msbuild-tasks.md)