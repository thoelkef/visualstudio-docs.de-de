---
title: "CallTarget Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "CallTarget task [MSBuild]"
  - "MSBuild, CallTarget task"
ms.assetid: bb1fe2c4-4383-436f-8326-c24cc4a46150
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# CallTarget Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ruft die angegebenen Ziele in der Projektdatei auf.  
  
## Aufgabenparameter  
 In der folgenden Tabelle werden die Parameter der `CallTarget`\-Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|------------------|  
|`RunEachTargetSeparately`|Optionaler `Boolean`\-Ausgabeparameter.<br /><br /> Wenn er `true` ist, wird das [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]\-Modul einmal pro Ziel aufgerufen.  Wenn er `false` ist, wird das [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]\-Modul ein Mal aufgerufen, um alle Ziele zu erstellen.  Der Standardwert ist `false`.|  
|`TargetOutputs`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Ausgabeparameter.<br /><br /> Enthält die Ausgaben von allen erstellten Zielen.|  
|`Targets`|Optionaler `String[]`\-Parameter.<br /><br /> Gibt die zu erstellenden Ziele an.|  
|`UseResultsCache`|Optionaler `Boolean`\-Parameter.<br /><br /> Bei `true` wird das zwischengespeicherte Ergebnis zurückgegeben, falls vorhanden.<br /><br /> **Hinweis** Wenn eine MSBuild\-Aufgabe ausgeführt wird, wird deren Ausgabe in einem Bereich \(ProjectFileName, GlobalProperties\)\[TargetNames\] als Liste von Build\-Elemente zwischengespeichert.|  
  
## Hinweise  
 Wenn ein in `Targets` angegebenes Ziel fehlschlägt und `RunEachTargetSeparately` `true` ist, setzt die Aufgabe die Erstellung der restlichen Ziele fort.  
  
 Wenn Sie die Standardziele erstellen möchten, verwenden Sie die [MSBuild\-Aufgabe](../msbuild/msbuild-task.md), und legen Sie den `Projects`\-Parameter auf `$(MSBuildProjectFile)` fest.  
  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>\-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>\-Klasse erbt.  Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Beispiel  
 Im folgenden Beispiel wird `TargetA` aus `CallOtherTargets` aufgerufen.  
  
```  
<Project DefaultTargets="CallOtherTargets"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <Target Name="CallOtherTargets">  
        <CallTarget Targets="TargetA"/>  
    </Target>  
  
    <Target Name="TargetA">  
        <Message Text="Building TargetA..." />  
    </Target>  
  
</Project>  
```  
  
## Siehe auch  
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [Targets](../msbuild/msbuild-targets.md)