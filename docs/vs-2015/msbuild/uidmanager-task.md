---
title: UidManager-Aufgabe| Microsoft-Dokumentation
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
- UidManager task [WPF MSBuild]
- UidManager task [WPF MSBuild], parameters
- managing UIDs when localizing XAML elements [WPF MSBuild]
- localizing XAML elements [WPF MSBuild], managing UIDs
- checking UIDs when localizing XAML elements [WPF MSBuild]
ms.assetid: 4fc7b5a5-11b0-46ca-9656-8c2a0b08d1fe
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5fd8175911def7fb1b63dc63d967c404d649e9e4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703694"
---
# <a name="uidmanager-task"></a>UidManager-Aufgabe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der <xref:Microsoft.Build.Tasks.Windows.UidManager>-Task überprüft, aktualisiert oder entfernt eindeutige Bezeichner (UIDs), um alle [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)]-Elemente zu lokalisieren, die in den [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)]-Quelldateien enthalten sind.  
  
## <a name="task-parameters"></a>Aufgabenparameter  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|`IntermediateDirectory`|Optionaler **String**-Parameter.<br /><br /> Gibt das Verzeichnis an, das zur Sicherung der Quell-[!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)]-Dateien verwendet wird, die vom **MarkupFiles**-Parameter angegeben werden.|  
|`MarkupFiles`|Erforderlicher **ITaskItem[]** -Parameter.<br /><br /> Gibt die Quell-[!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)]-Dateien an, die für UID-Überprüfung, -Aktualisierung oder -Entfernung einbezogen werden.|  
|`Task`|Erforderlicher **String**-Parameter.<br /><br /> Gibt die UID-Verwaltungsaufgabe an, die Sie ausführen möchten. Gültige Optionen sind **Check**, **Update** oder **Remove**.|  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird mit dem <xref:Microsoft.Build.Tasks.Windows.UidManager>-Task überprüft, ob die angegebenen [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)]-Quelldateien [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)]-Elemente enthalten, die über geeignete UIDs verfügen.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [WPF-MSBuild-Referenz](../msbuild/wpf-msbuild-reference.md)   
 [Aufgaben Referenz](../msbuild/wpf-msbuild-task-reference.md)   
 [MSBuild-Referenz](../msbuild/msbuild-reference.md)   
 [Aufgaben Referenz](../msbuild/msbuild-task-reference.md)   
 [Entwickeln einer WPF-Anwendung (WPF)](https://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)   
 [Gewusst wie: Lokalisieren einer Anwendung](https://msdn.microsoft.com/library/5001227e-9326-48a4-9dcd-ba1b89ee6653)
