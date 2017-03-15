---
title: "Warning Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#Warning"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Warning task [MSBuild]"
  - "MSBuild, Warning task"
ms.assetid: 96ba5507-8b43-4f54-a1d7-9b15644dd56c
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# Warning Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Protokolliert eine Warnung während eines Buildvorgangs auf der Grundlage einer ausgewerteten Bedingungsanweisung.  
  
## Parameter  
 In der folgenden Tabelle werden die Parameter der `Warning`\-Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|------------------|  
|`Code`|Optionaler `String`\-Parameter.<br /><br /> Der der Warnung zuzuordnende Warncode.|  
|`File`|Optionaler `String`\-Parameter.<br /><br /> Gibt die relevante Datei an, falls vorhanden.  Wenn keine Datei angegeben ist, wird die Datei mit der Warning\-Aufgabe verwendet.|  
|`HelpKeyword`|Optionaler `String`\-Parameter.<br /><br /> Das der Warnung zuzuordnende Hilfeschlüsselwort.|  
|`Text`|Optionaler `String`\-Parameter.<br /><br /> Der Warnungstext, den [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] protokolliert, wenn der `Condition`\-Parameter `true` ergibt.|  
  
## Hinweise  
 Mithilfe der `Warning`\-Aufgabe können [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]\-Projekte vor der Ausführung des nächsten Buildschritts überprüfen, ob eine erforderliche Konfiguration oder Eigenschaft vorhanden ist.  
  
 Wenn der `Condition`\-Parameter der `Warning`\-Aufgabe `true` ergibt, wird der Wert des `Text`\-Parameters protokolliert und der Buildvorgang fortgesetzt.  Wenn kein `Condition`\-Parameter vorhanden ist, wird der Warnungstext protokolliert.  Weitere Informationen zur Protokollierung finden Sie unter [Erhalten von Buildprotokollen](../msbuild/obtaining-build-logs-with-msbuild.md).  
  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>\-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>\-Klasse erbt.  Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Beispiel  
 Im folgenden Codebeispiel wird nach Eigenschaften gesucht, die über die Befehlszeile festgelegt wurden.  Wenn keine Eigenschaften festgelegt wurden, löst das Projekt ein Warnereignis aus und protokolliert den Wert des `Text`\-Parameters der `Warning`\-Aufgabe.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="ValidateCommandLine">  
        <Warning  
            Text=" The 0 property was not set on the command line."  
            Condition="'$(0)' == ''" />  
        <Warning  
            Text=" The FREEBUILD property was not set on the command line."  
            Condition="'$(FREEBUILD)' == ''" />  
    </Target>  
    ...  
</Project>  
```  
  
## Siehe auch  
 [Erhalten von Buildprotokollen](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [Project File Schema Reference](../msbuild/msbuild-project-file-schema-reference.md)