---
title: GetWinFXPath-Aufgabe | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- getting the directory of the current .NET Framework runtime [WPF MSBuild]
- GetWinFXPath task [WPF MSBuild], parameters
- GetWinFXPath task [WPF MSBuild]
- obtaining the path to the current .NET Framework runtime [WPF MSBuild]
ms.assetid: b1dfb467-f3d3-47f3-83ef-af7b0e33a772
caps.latest.revision: 5
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 79460291e91f0659df0a4241e17616e55187a0e2
ms.openlocfilehash: 45d07bf0834aa1488e8c2e3b22ee460eb629539e
ms.lasthandoff: 02/22/2017

---
# <a name="getwinfxpath-task"></a>GetWinFXPath-Aufgabe
Die <xref:Microsoft.Build.Tasks.Windows.GetWinFXPath>-Aufgabe gibt das Verzeichnis der aktuellen [!INCLUDE[TLA#tla_winfx](../msbuild/includes/tlasharptla_winfx_md.md)]-Runtime zurück.  
  
## <a name="task-parameters"></a>Aufgabenparameter  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|`WinFXPath`|Optionaler **String**-Ausgabeparameter.<br /><br /> Gibt den tatsächlichen Pfad zur [!INCLUDE[TLA2#tla_winfx](../msbuild/includes/tla2sharptla_winfx_md.md)]-Runtime an.|  
|`WinFXNativePath`|Erforderlicher **String**-Parameter.<br /><br /> Gibt den Pfad zur nativen [!INCLUDE[TLA2#tla_titlewinfx](../msbuild/includes/tla2sharptla_titlewinfx_md.md)]-Runtime an.|  
|`WinFXWowPath`|Erforderlicher **String**-Parameter.<br /><br /> Gibt den Pfad zu den [!INCLUDE[TLA#tla_winfx](../msbuild/includes/tlasharptla_winfx_md.md)]-Assemblys im 32-Bit-**Windows on Windows**-Modul auf 64-Bit-Systemen an.|  
  
## <a name="remarks"></a>Hinweise  
 Wenn die <xref:Microsoft.Build.Tasks.Windows.GetWinFXPath>-Aufgabe auf einem 64-Bit-Prozessor ausgeführt wird, wird der **WinFXPath**-Parametersatz auf den Pfad festgelegt, der im **WinFXWowPath**-Parameter gespeichert ist; andernfalls wird der **WinFXPath**-Parameter auf den Pfad festgelegt, der im **WinFXNativePath**-Parameter gespeichert ist.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt, wie Sie die **GetWinFXPath**-Aufgabe verwenden, um den nativen Pfad zur [!INCLUDE[TLA2#tla_titlewinfx](../msbuild/includes/tla2sharptla_titlewinfx_md.md)]-Runtime zu ermitteln.  
  
```xml  
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
  
## <a name="see-also"></a>Siehe auch  
 [WPF-MSBuild-Referenz](../msbuild/wpf-msbuild-reference.md)   
 [Task Reference](../msbuild/wpf-msbuild-task-reference.md)  (MSBuild-Aufgabenreferenz)  
 [MSBuild Reference](../msbuild/msbuild-reference.md)  (MSBuild-Referenz)  
 [Task Reference](../msbuild/msbuild-task-reference.md)  (MSBuild-Aufgabenreferenz)  
 [Erstellen einer WPF-Anwendung (WPF)](http://msdn.microsoft.com/Library/a58696fd-bdad-4b55-9759-136dfdf8b91c)
