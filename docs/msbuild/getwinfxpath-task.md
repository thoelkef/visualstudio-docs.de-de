---
title: "GetWinFXPath Task | Microsoft Docs"
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
  - "getting the directory of the current .NET Framework runtime [WPF MSBuild]"
  - "GetWinFXPath task [WPF MSBuild], parameters"
  - "GetWinFXPath task [WPF MSBuild]"
  - "obtaining the path to the current .NET Framework runtime [WPF MSBuild]"
ms.assetid: b1dfb467-f3d3-47f3-83ef-af7b0e33a772
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# GetWinFXPath Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Mithilfe der <xref:Microsoft.Build.Tasks.Windows.GetWinFXPath>\-Aufgabe wird das Verzeichnis der aktuellen [!INCLUDE[TLA#tla_winfx](../msbuild/includes/tlasharptla_winfx_md.md)]\-Laufzeit zurückgegeben.  
  
## Aufgabenparameter  
  
|Parameter|Beschreibung|  
|---------------|------------------|  
|`WinFXPath`|Optionaler **String**\-Ausgabeparameter.<br /><br /> Gibt den tatsächlichen Pfad zur [!INCLUDE[TLA2#tla_winfx](../msbuild/includes/tla2sharptla_winfx_md.md)]\-Laufzeit an.|  
|`WinFXNativePath`|Erforderlicher **String**\-Parameter.<br /><br /> Gibt den Pfad zur systemeigenen [!INCLUDE[TLA2#tla_titlewinfx](../msbuild/includes/tla2sharptla_titlewinfx_md.md)]\-Laufzeit an.|  
|`WinFXWowPath`|Erforderlicher **String**\-Parameter.<br /><br /> Gibt den Pfad zu den [!INCLUDE[TLA#tla_winfx](../msbuild/includes/tlasharptla_winfx_md.md)]\-Assemblys im **Windows on Windows**\-32\-Bit\-Modul auf 64\-Bit\-Systemen an.|  
  
## Hinweise  
 Wenn die <xref:Microsoft.Build.Tasks.Windows.GetWinFXPath>\-Aufgabe mit einem 64\-Bit\-Prozessor ausgeführt wird, wird der **WinFXPath**\-Parameter auf den im **WinFXWowPath**\-Parameter gespeicherten Pfad festgelegt. Andernfalls wird der **WinFXPath**\-Parameter auf den im **WinFXNativePath**\-Parameter gespeicherten Pfad festgelegt.  
  
## Beispiel  
 Im folgenden Beispiel wird veranschaulicht, wie mithilfe der **GetWinFXPath**\-Aufgabe der systemeigene Pfad zur [!INCLUDE[TLA2#tla_titlewinfx](../msbuild/includes/tla2sharptla_titlewinfx_md.md)]\-Laufzeit ermittelt wird.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.GetWinFXPath"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="GetWinFXPathTask">  
    <GetWinFXPath  
      WinFXNativePath="c:\WinFXNative"   
      WinFXWowPath="c:\WinFXWowNative" />  
  </Target>  
  <Import Project="$(MSBuildBinPath)\Microsoft.WinFX.targets" />  
</Project>  
```  
  
## Siehe auch  
 [WPF MSBuild Reference](../msbuild/wpf-msbuild-reference.md)   
 [Task Reference](../msbuild/wpf-msbuild-task-reference.md)   
 [MSBuild Reference](../msbuild/msbuild-reference.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [Erstellen einer WPF\-Anwendung \(WPF\)](../Topic/Building%20a%20WPF%20Application%20\(WPF\).md)