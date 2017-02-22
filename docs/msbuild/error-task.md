---
title: "Error Task | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#Error"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Error task [MSBuild]"
  - "MSBuild, Error task"
ms.assetid: e96a90ee-a8ae-4e5b-8ef2-b5cf5fedd8b2
caps.latest.revision: 20
caps.handback.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Error Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Hält einen Build an und protokolliert einen Fehler anhand einer ausgewerteten Bedingungsanweisung.  
  
## Parameter  
 In der folgenden Tabelle werden die Parameter der `Error`\-Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|------------------|  
|`Code`|Optionaler `String`\-Parameter.<br /><br /> Der dem Fehler zuzuordnende Fehlercode.|  
|`File`|Optionaler `String`\-Parameter.<br /><br /> Der Name der Datei, die den Fehler enthält.  Wenn keine Datei angegeben ist, wird die Datei mit der Error\-Aufgabe verwendet.|  
|`HelpKeyword`|Optionaler `String`\-Parameter.<br /><br /> Das dem Fehler zuzuordnende Hilfeschlüsselwort.|  
|`Text`|Optionaler `String`\-Parameter.<br /><br /> Der Fehlertext, den [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] protokolliert, wenn der `Condition`\-Parameter `true` ergibt.|  
  
## Hinweise  
 Mithilfe der `Error`\-Aufgabe können [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]\-Projekte Fehlertext an Protokollierungen ausgeben und die Buildausführung anhalten.  
  
 Wenn der `Condition`\-Parameter `true` ergibt, wird die Buildausführung angehalten und ein Fehler protokolliert.  Wenn kein `Condition`\-Parameter vorhanden ist, wird der Fehler protokolliert und die Buildausführung angehalten.  Weitere Informationen zur Protokollierung finden Sie unter [Erhalten von Buildprotokollen](../msbuild/obtaining-build-logs-with-msbuild.md).  
  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>\-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>\-Klasse erbt.  Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Beispiel  
 Im folgenden Codebeispiel wird überprüft, ob alle erforderlichen Eigenschaften festgelegt sind.  Wenn sie nicht festgelegt sind, löst das Projekt ein Fehlerereignis aus und protokolliert den Wert des `Text`\-Parameters der `Error`\-Aufgabe.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="ValidateCommandLine">  
        <Error  
            Text=" The 0 property must be set on the command line."  
            Condition="'$(0)' == ''" />  
        <Error  
            Text="The FREEBUILD property must be set on the command line."  
            Condition="'$(FREEBUILD)' == ''" />  
    </Target>  
    ...  
</Project>  
```  
  
## Siehe auch  
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [Erhalten von Buildprotokollen](../msbuild/obtaining-build-logs-with-msbuild.md)