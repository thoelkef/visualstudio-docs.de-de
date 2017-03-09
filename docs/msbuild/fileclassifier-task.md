---
title: "FileClassifier Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "classifying a resource set to embed in an assembly [WPF MSBuild]"
  - "non-localizable resources [WPF MSBuild], classifying to embed in an assembly"
  - "FileClassifier task [WPF MSBuild]"
ms.assetid: 14e03310-fcc0-4bb2-a84d-cda12be66367
caps.latest.revision: 7
caps.handback.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# FileClassifier Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die <xref:Microsoft.Build.Tasks.Windows.FileClassifier>\-Aufgabe klassifiziert eine Gruppe von Quellressourcen als die Ressourcen, die in eine Assembly eingebettet werden sollen.  Wenn eine Ressource nicht lokalisierbar ist, wird sie in die Hauptassembly der Anwendung eingebettet. Andernfalls wird sie in eine Satellitenassembly eingebettet.  
  
## Aufgabenparameter  
  
|Parameter|Beschreibung|  
|---------------|------------------|  
|`CLREmbeddedResource`|Nicht verwendet.|  
|`CLRResourceFiles`|Nicht verwendet.|  
|`CLRSatelliteEmbeddedResource`|Nicht verwendet.|  
|`Culture`|Optionaler **String**\-Parameter.<br /><br /> Gibt die Kultur für den Build an.  Dieser Wert kann **null** sein, wenn der Build nicht lokalisierbar ist.  Bei **null** ist der Standardwert der Wert in Kleinbuchstaben, den **CultureInfo.InvariantCulture**  zurückgibt.|  
|`MainEmbeddedFiles`|Optionaler **ITaskItem\[\]**\-Ausgabeparameter.<br /><br /> Gibt die nicht lokalisierbaren Ressourcen an, die in die Hauptassembly eingebettet sind.|  
|`OutputType`|Erforderlicher **String**\-Parameter.<br /><br /> Gibt den Dateityp an, in den die angegebenen Quelldateien eingebettet werden sollen.  Die gültigen Werte sind **exe**, **winexe** und **library**.|  
|`SatelliteEmbeddedFiles`|Optionaler **ITaskItem\[\]**\-Ausgabeparameter.<br /><br /> Gibt die lokalisierbaren Dateien an, die in die Satellitenassembly für die durch den **Culture**\-Parameter angegebene Kultur eingebettet sind.|  
|`SourceFiles`|Erforderlicher **ITaskItem\[\]**\-Parameter.<br /><br /> Gibt die Liste der zu klassifizierenden Dateien an.|  
  
## Hinweise  
 Wenn der **Culture**\-Parameter nicht festgelegt ist, sind alle mit dem **SourceFiles**\-Parameter angegebenen Ressourcen nicht lokalisierbar. Andernfalls sind sie lokalisierbar, es sei denn, sie sind mit einem **Localizable**\-Attribut verknüpft, für das **false** festgelegt ist.  
  
## Beispiel  
 Im folgenden Beispiel wird eine einzelne Quelldatei als Ressource klassifiziert und dann in eine Satellitenassembly für die Kultur Französisch \(Kanada\) \(fr\-CA\) eingebettet.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask  
    TaskName="Microsoft.Build.Tasks.Windows.FileClassifier"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <ItemGroup>  
    <Resource Include="Resource1.bmp" />  
  </ItemGroup>  
  <Target Name="FileClassifierTask">  
    <FileClassifier  
      SourceFiles="Resource1.bmp"  
      Culture="fr-CA"  
      OutputType="exe" />  
  </Target>  
</Project>  
```  
  
## Siehe auch  
 [WPF MSBuild Reference](../msbuild/wpf-msbuild-reference.md)   
 [Task Reference](../msbuild/wpf-msbuild-task-reference.md)   
 [MSBuild Reference](../msbuild/msbuild-reference.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [Erstellen einer WPF\-Anwendung \(WPF\)](../Topic/Building%20a%20WPF%20Application%20\(WPF\).md)