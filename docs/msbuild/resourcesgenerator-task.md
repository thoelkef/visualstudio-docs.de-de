---
title: ResourcesGenerator-Aufgabe | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- embedding resources into a .resources file [WPF MSBuild]
- ResourcesGenerator task [WPF MSBuild]
- ResourcesGenerator task [WPF MSBuild], parameters
ms.assetid: e782bbac-9ee6-472b-8171-3ee008c77b4e
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 27ce9d8f507be900d76fe6a9c5a5fdc1876527bc
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="resourcesgenerator-task"></a>ResourcesGenerator-Aufgabe
Der <xref:Microsoft.Build.Tasks.Windows.ResourcesGenerator>-Task bettet mindestens eine Ressource (JPG, ICO, BMP, [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] im Binärformat und andere Erweiterungstypen) in eine RESOURCES-Datei ein.  
  
## <a name="task-parameters"></a>Aufgabenparameter  
  
|Parameter|description|  
|---------------|-----------------|  
|`OutputPath`|Erforderlicher **String**-Parameter.<br /><br /> Gibt den Pfad des Ausgabeverzeichnisses an. Wenn der Pfad kein absoluter Pfad ist, wird er als relativer Pfad zum Stammverzeichnis des Projekts behandelt.|  
|`OutputResourcesFile`|Erforderlicher **ITaskItem[]**-Ausgabeparameter.<br /><br /> Gibt Pfad und Namen der generierten RESOURCES-Datei an. Wenn der Pfad kein absoluter Pfad ist, wird die RESOURCES-Datei relativ zum Stammverzeichnis des Projekts generiert.|  
|`ResourcesFiles`|Erforderlicher **ITaskItem[]**-Parameter.<br /><br /> Gibt eine oder mehrere Ressourcen zum Einbetten in die generierte RESOURCES-Datei an.|  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird eine RESOURCES-Datei mit einer einzelnen BMP-Ressource generiert. Die BMP-Ressource wird in einem Verzeichnis generiert, das relativ zum Stammverzeichnis des Projekts ist.  
  
```xml  
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
  
## <a name="see-also"></a>Siehe auch  
 [WPF-MSBuild-Referenz](../msbuild/wpf-msbuild-reference.md)   
 [Task Reference](../msbuild/wpf-msbuild-task-reference.md)  (MSBuild-Aufgabenreferenz)  
 [MSBuild Reference](../msbuild/msbuild-reference.md)  (MSBuild-Referenz)  
 [Task Reference](../msbuild/msbuild-task-reference.md)  (MSBuild-Aufgabenreferenz)  
 [Erstellen einer WPF-Anwendung (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)