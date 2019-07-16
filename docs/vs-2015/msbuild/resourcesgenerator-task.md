---
title: ResourcesGenerator-Aufgabe | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
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
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fa8b438727160bb5a752643f7ef9791ca5e09245
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65682138"
---
# <a name="resourcesgenerator-task"></a>ResourcesGenerator-Aufgabe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der <xref:Microsoft.Build.Tasks.Windows.ResourcesGenerator>-Task bettet mindestens eine Ressource (JPG, ICO, BMP, [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] im Binärformat und andere Erweiterungstypen) in eine RESOURCES-Datei ein.  
  
## <a name="task-parameters"></a>Aufgabenparameter  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|`OutputPath`|Erforderlicher **String**-Parameter.<br /><br /> Gibt den Pfad des Ausgabeverzeichnisses an. Wenn der Pfad kein absoluter Pfad ist, wird er als relativer Pfad zum Stammverzeichnis des Projekts behandelt.|  
|`OutputResourcesFile`|Erforderlicher **ITaskItem[]**-Ausgabeparameter.<br /><br /> Gibt Pfad und Namen der generierten RESOURCES-Datei an. Wenn der Pfad kein absoluter Pfad ist, wird die RESOURCES-Datei relativ zum Stammverzeichnis des Projekts generiert.|  
|`ResourcesFiles`|Erforderlicher **ITaskItem[]**-Parameter.<br /><br /> Gibt eine oder mehrere Ressourcen zum Einbetten in die generierte RESOURCES-Datei an.|  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird eine RESOURCES-Datei mit einer einzelnen BMP-Ressource generiert. Die BMP-Ressource wird in einem Verzeichnis generiert, das relativ zum Stammverzeichnis des Projekts ist.  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [WPF-MSBuild-Referenz](../msbuild/wpf-msbuild-reference.md)   
 [Task Reference](../msbuild/wpf-msbuild-task-reference.md)  (MSBuild-Aufgabenreferenz)  
 [MSBuild Reference](../msbuild/msbuild-reference.md)  (MSBuild-Referenz)  
 [Task Reference](../msbuild/msbuild-task-reference.md)  (MSBuild-Aufgabenreferenz)  
 [Erstellen einer WPF-Anwendung (WPF)](https://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)
