---
title: "MergeLocalizationDirectives Task | Microsoft Docs"
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
  - "localizing XAML [WPF MSBuild], moving comments and attributes to a separate file"
  - "MergeLocalizationDirectives task [WPF MSBuild], parameters"
  - "MergeLocalizationDirectives task [WPF MSBuild]"
  - "moving localization comments and attributes to a separate file [WPF MSBuild]"
ms.assetid: 9095b4f1-88da-4194-914b-ee1456826830
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# MergeLocalizationDirectives Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Mit der <xref:Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives>\-Aufgabe werden die Lokalisierungsattribute und die Kommentare aus mindestens einer [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]\-Datei im Binärformat in einer Datei für die gesamte Assembly zusammengeführt.  
  
## Aufgabenparameter  
  
|Parameter|Beschreibung|  
|---------------|------------------|  
|`GeneratedLocalizationFiles`|Erforderlicher **ITaskItem\[\]**\-Parameter.<br /><br /> Gibt die Liste der Dateien mit Lokalisierungsdirektiven für einzelne Dateien im [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]\-Binärformat an.|  
|`OutputFile`|Erforderlicher **String**\-Ausgabeparameter.<br /><br /> Gibt den Ausgabepfad der kompilierten Lokalisierungsdirektivenassembly an.|  
  
## Hinweise  
 Sie können dem [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)]\-Inhalt Lokalisierungsattribute und Kommentare hinzufügen.  Mit der [!INCLUDE[TLA#tla_wpf](../msbuild/includes/tlasharptla_wpf_md.md)]\-Lokalisierungsunterstützung können Sie Lokalisierungsattribute und Kommentare entfernen und in eine LOC\-Datei einfügen, die getrennt von der generierten Assembly gespeichert wird.  Hierzu können Sie das **LocalizationPropertyStorage**\-Attribut verwenden.  Weitere Informationen zu Lokalisierungsattributen und Kommentaren sowie zu **LocalizationPropertyStorage** finden Sie unter [Lokalisierungsattribute und \-kommentare](../Topic/Localization%20Attributes%20and%20Comments.md).  
  
## Beispiel  
 Im folgenden Beispiel werden die Lokalisierungsattribute und mehrere [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]\-Dateien im Binärformat in einer LOC\-Datei zusammengeführt.  
  
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
  
## Siehe auch  
 [WPF MSBuild Reference](../msbuild/wpf-msbuild-reference.md)   
 [Task Reference](../msbuild/wpf-msbuild-task-reference.md)   
 [MSBuild Reference](../msbuild/msbuild-reference.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [Erstellen einer WPF\-Anwendung \(WPF\)](../Topic/Building%20a%20WPF%20Application%20\(WPF\).md)