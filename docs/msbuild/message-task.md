---
title: "Message Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#Message"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, Message task"
  - "Message task [MSBuild]"
ms.assetid: 2293309d-42b6-46dc-9684-8c146f66bc28
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# Message Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Protokolliert eine Meldung während eines Builds.  
  
## Parameter  
 In der folgenden Tabelle werden die Parameter der `Message`\-Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|------------------|  
|`Importance`|Optionaler `String`\-Parameter.<br /><br /> Gibt die Wichtigkeit der Meldung an.  Dieser Parameter kann den Wert `high`, `normal` oder `low` aufweisen.  Der Standardwert ist `normal`.|  
|`Text`|Optionaler `String`\-Parameter.<br /><br /> Der zu protokollierende Fehlertext.|  
  
## Hinweise  
 Die `Message`\-Aufgabe ermöglicht es [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]\-Projekten, bei verschiedenen Schritten im Buildprozess Meldungen an Protokollierungen auszugeben.  
  
 Wenn der `Condition`\-Parameter `true` ergibt, wird der Wert des `Text`\-Parameters protokolliert und der Buildprozess fortgesetzt.  Wenn kein `Condition`\-Parameter vorhanden ist, wird der Meldungstext protokolliert.  Weitere Informationen zur Protokollierung finden Sie unter [Erhalten von Buildprotokollen](../msbuild/obtaining-build-logs-with-msbuild.md).  
  
 Standardmäßig wird die Nachricht an die MSBuild\-Konsolenprotokollierung gesendet.  Dies kann geändert werden, indem der Parameter <xref:Microsoft.Build.Tasks.TaskExtension.Log%2A> festgelegt wird.  Die Protokollierung interpretiert den Parameter `Importance`.  
  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>\-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>\-Klasse erbt.  Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Beispiel  
 Im folgenden Codebeispiel werden Meldungen an alle registrierten Protokollierungen protokolliert.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="DisplayMessages">  
        <Message Text="Project File Name = $(MSBuildProjectFile)" />  
        <Message Text="Project Extension = $(MSBuildProjectExtension)" />  
    </Target>  
    ...  
</Project>  
```  
  
## Siehe auch  
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [Erhalten von Buildprotokollen](../msbuild/obtaining-build-logs-with-msbuild.md)