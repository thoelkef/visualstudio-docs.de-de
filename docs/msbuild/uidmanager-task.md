---
title: "UidManager Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "UidManager task [WPF MSBuild]"
  - "UidManager task [WPF MSBuild], parameters"
  - "managing UIDs when localizing XAML elements [WPF MSBuild]"
  - "localizing XAML elements [WPF MSBuild], managing UIDs"
  - "checking UIDs when localizing XAML elements [WPF MSBuild]"
ms.assetid: 4fc7b5a5-11b0-46ca-9656-8c2a0b08d1fe
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# UidManager Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Mit der <xref:Microsoft.Build.Tasks.Windows.UidManager>\-Aufgabe werden eindeutige Bezeichner \(UIDs\) überprüft, aktualisiert oder entfernt, um alle [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)]\-Elemente in den [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]\-Quelldateien zu lokalisieren.  
  
## Aufgabenparameter  
  
|Parameter|Beschreibung|  
|---------------|------------------|  
|`IntermediateDirectory`|Optionaler **String**\-Parameter.<br /><br /> Gibt das Verzeichnis zur Sicherung der [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]\-Quelldateien an, die durch den **MarkupFiles**\-Parameter angegeben werden.|  
|`MarkupFiles`|Erforderlicher **ITaskItem\[\]**\-Parameter.<br /><br /> Gibt die [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]\-Quelldateien an, die für das Überprüfen, Aktualisieren oder Entfernen der UID berücksichtigt werden müssen.|  
|`Task`|Erforderlicher **String**\-Parameter.<br /><br /> Gibt die UID\-Verwaltungsaufgabe an, die Sie ausführen möchten.  Gültige Optionen sind **Check**, **Update** und **Remove**.|  
  
## Beispiel  
 Im folgenden Beispiel wird mithilfe der <xref:Microsoft.Build.Tasks.Windows.UidManager>\-Aufgabe überprüft, ob die angegebenen [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]\-Quelldateien [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]\-Elemente mit geeigneten UIDs enthalten.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.UidManager"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="UidManagerTask">  
    <UidManager  
      Task="Check"  
      MarkupFiles="Page1.xaml;Page2.xaml"  
      IntermediateDirectory="c:\UidManagerIntermediateDirectory" />  
  </Target>  
</Project>  
```  
  
## Siehe auch  
 [WPF MSBuild Reference](../msbuild/wpf-msbuild-reference.md)   
 [Task Reference](../msbuild/wpf-msbuild-task-reference.md)   
 [MSBuild Reference](../msbuild/msbuild-reference.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [Erstellen einer WPF\-Anwendung \(WPF\)](../Topic/Building%20a%20WPF%20Application%20\(WPF\).md)   
 [Gewusst wie: Lokalisieren einer Anwendung](../Topic/How%20to:%20Localize%20an%20Application.md)