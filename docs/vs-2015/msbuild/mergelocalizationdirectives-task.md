---
title: MergeLocalizationDirectives-Aufgabe | Microsoft-Dokumentation
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
- localizing XAML [WPF MSBuild], moving comments and attributes to a separate file
- MergeLocalizationDirectives task [WPF MSBuild], parameters
- MergeLocalizationDirectives task [WPF MSBuild]
- moving localization comments and attributes to a separate file [WPF MSBuild]
ms.assetid: 9095b4f1-88da-4194-914b-ee1456826830
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2d6c2aa6cea687119e69b565da5468e8fa723641
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703422"
---
# <a name="mergelocalizationdirectives-task"></a>MergeLocalizationDirectives-Aufgabe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der <xref:Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives>-Task führt die Lokalisierungsattribute und -kommentare aus einer oder mehreren [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)]-Binärformatdateien für die gesamte Assembly in einer einzelnen Datei zusammen.  
  
## <a name="task-parameters"></a>Aufgabenparameter  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|`GeneratedLocalizationFiles`|Erforderlicher **ITaskItem[]** -Parameter.<br /><br /> Gibt die Liste der Dateien mit Lokalisierungsrichtlinien für einzelne Dateien im [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)]-Binärformat an.|  
|`OutputFile`|Erforderlicher **String**-Ausgabeparameter.<br /><br /> Gibt den Ausgabepfad der kompilierten Lokalisierungsrichtlinien-Assembly an.|  
  
## <a name="remarks"></a>Hinweise  
 Sie können dem [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)]-Inhalt Lokalisierungsattribute und -kommentare hinzufügen. Mit [!INCLUDE[TLA#tla_wpf](../includes/tlasharptla-wpf-md.md)]-Lokalisierungsunterstützung können Sie Lokalisierungsattribute und -kommentare entfernen und in einer von der generierten Assembly separaten LOC-Datei ablegen. Verwenden Sie hierzu das **LocalizationPropertyStorage**-Attribut. Weitere Informationen über Lokalisierungs Attribute und-Kommentare und **LocalizationPropertyStorage**finden Sie unter [Lokalisierungs Attribute und-Kommentare](https://msdn.microsoft.com/library/ead2d9ac-b709-4ec1-a924-39927a29d02f).  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel werden die Lokalisierungskommentare mehrerer [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)]-Binärformatdateien in einer einzelnen LOC-Datei zusammengeführt.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="MergeLocalizationDirectivesTask">  
    <MergeLocalizationDirectives   
      GeneratedLocalizationFiles="obj\debug\page1.loc;obj\debug\page2.loc;obj\debug\page3.loc"  
      OutputFile="obj\debug\WPFMSBuildSample.loc" />  
  </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [WPF-MSBuild-Referenz](../msbuild/wpf-msbuild-reference.md)   
 [Aufgaben Referenz](../msbuild/wpf-msbuild-task-reference.md)   
 [MSBuild-Referenz](../msbuild/msbuild-reference.md)   
 [Aufgaben Referenz](../msbuild/msbuild-task-reference.md)   
 [Entwickeln einer WPF-Anwendung (WPF)](https://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)
