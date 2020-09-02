---
title: GetWinFXPath-Aufgabe | Microsoft-Dokumentation
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
- getting the directory of the current .NET Framework runtime [WPF MSBuild]
- GetWinFXPath task [WPF MSBuild], parameters
- GetWinFXPath task [WPF MSBuild]
- obtaining the path to the current .NET Framework runtime [WPF MSBuild]
ms.assetid: b1dfb467-f3d3-47f3-83ef-af7b0e33a772
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: da32f0bfce9edf652e19df6b68bc51ed92624d80
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65699021"
---
# <a name="getwinfxpath-task"></a>GetWinFXPath-Aufgabe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der <xref:Microsoft.Build.Tasks.Windows.GetWinFXPath>-Task gibt das Verzeichnis der aktuellen [!INCLUDE[TLA#tla_winfx](../includes/tlasharptla-winfx-md.md)]-Runtime zurück.  
  
## <a name="task-parameters"></a>Aufgabenparameter  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|`WinFXPath`|Optionaler **String**-Ausgabeparameter.<br /><br /> Gibt den tatsächlichen Pfad zur [!INCLUDE[TLA2#tla_winfx](../includes/tla2sharptla-winfx-md.md)]-Runtime an.|  
|`WinFXNativePath`|Erforderlicher **String**-Parameter.<br /><br /> Gibt den Pfad zur nativen [!INCLUDE[TLA2#tla_titlewinfx](../includes/tla2sharptla-titlewinfx-md.md)]-Runtime an.|  
|`WinFXWowPath`|Erforderlicher **String**-Parameter.<br /><br /> Gibt den Pfad zu den [!INCLUDE[TLA#tla_winfx](../includes/tlasharptla-winfx-md.md)]-Assemblys im 32-Bit-**Windows on Windows**-Modul auf 64-Bit-Systemen an.|  
  
## <a name="remarks"></a>Hinweise  
 Wenn der <xref:Microsoft.Build.Tasks.Windows.GetWinFXPath>-Task auf einem 64-Bit-Prozessor ausgeführt wird, wird der **WinFXPath**-Parametersatz auf den Pfad festgelegt, der im **WinFXWowPath**-Parameter gespeichert ist. Andernfalls wird der **WinFXPath**-Parameter auf den Pfad festgelegt, der im **WinFXNativePath**-Parameter gespeichert ist.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt, wie Sie die **GetWinFXPath**-Aufgabe verwenden, um den nativen Pfad zur [!INCLUDE[TLA2#tla_titlewinfx](../includes/tla2sharptla-titlewinfx-md.md)]-Runtime zu ermitteln.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [WPF-MSBuild-Referenz](../msbuild/wpf-msbuild-reference.md)   
 [Aufgaben Referenz](../msbuild/wpf-msbuild-task-reference.md)   
 [MSBuild-Referenz](../msbuild/msbuild-reference.md)   
 [Aufgaben Referenz](../msbuild/msbuild-task-reference.md)   
 [Entwickeln einer WPF-Anwendung (WPF)](https://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)
