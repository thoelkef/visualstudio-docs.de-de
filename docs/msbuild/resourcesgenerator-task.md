---
title: "ResourcesGenerator Task | Microsoft Docs"
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
  - "embedding resources into a .resources file [WPF MSBuild]"
  - "ResourcesGenerator task [WPF MSBuild]"
  - "ResourcesGenerator task [WPF MSBuild], parameters"
ms.assetid: e782bbac-9ee6-472b-8171-3ee008c77b4e
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# ResourcesGenerator Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Mithilfe der <xref:Microsoft.Build.Tasks.Windows.ResourcesGenerator>\-Aufgabe wird mindestens eine Ressource \(JPG, ICO, BMP, [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] im Binärformat und andere Erweiterungstypen\) in eine RESOURCES\-Datei eingebettet.  
  
## Aufgabenparameter  
  
|Parameter|Beschreibung|  
|---------------|------------------|  
|`OutputPath`|Erforderlicher **String**\-Parameter.<br /><br /> Gibt den Pfad des Ausgabeverzeichnisses an.  Wenn es sich nicht um einen absoluten Pfad handelt, wird der Pfad als relativ zum Stammverzeichnis des Projekts behandelt.|  
|`OutputResourcesFile`|Erforderlicher **ITaskItem\[\]**\-Ausgabeparameter.<br /><br /> Gibt den Pfad und den Namen der generierten RESOURCES\-Datei an.  Wenn es sich nicht um einen absoluten Pfad handelt, wird die RESOURCES\-Datei relativ zum Stammverzeichnis des Projekts generiert.|  
|`ResourcesFiles`|Erforderlicher **ITaskItem\[\]**\-Parameter.<br /><br /> Gibt mindestens eine Ressource an, die in die generierte RESOURCES\-Datei eingebettet werden soll.|  
  
## Beispiel  
 Im folgenden Beispiel wird eine RESOURCES\-Datei mit einer einzelnen BMP\-Ressource generiert.  Die BMP\-Ressource wird in einem Verzeichnis generiert, das relativ zum Stammverzeichnis des Projekts ist.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.ResourcesGenerator"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="ResourcesGeneratorTask">  
    <ResourcesGenerator  
      ResourceFiles="Resource1.bmp"  
      OutputPath="myresources"  
      OutputResourcesFile="myresources\my.resources" />  
  </Target>  
</Project>  
```  
  
## Siehe auch  
 [WPF MSBuild Reference](../msbuild/wpf-msbuild-reference.md)   
 [Task Reference](../msbuild/wpf-msbuild-task-reference.md)   
 [MSBuild Reference](../msbuild/msbuild-reference.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [Erstellen einer WPF\-Anwendung \(WPF\)](../Topic/Building%20a%20WPF%20Application%20\(WPF\).md)