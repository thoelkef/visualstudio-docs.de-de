---
title: FindUnderPath-Aufgabe | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#FindUnderPath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, FindUnderPath task
- FindUnderPath task [MSBuild]
ms.assetid: 3c6d58b0-36e8-47aa-bfca-b73dd2045d91
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 92745b79b769ef82445523a6d5b66816077433ca
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2019
ms.locfileid: "54777049"
---
# <a name="findunderpath-task"></a>FindUnderPath-Aufgabe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Bestimmt, welche Elemente in der angegebenen Elementauflistung über Pfade im oder unter dem angegebenen Ordner verfügen  
  
## <a name="parameters"></a>Parameter  
 In der folgenden Tabelle werden die Parameter der `FindUnderPath` -Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|`Files`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter<br /><br /> Gibt die Dateien an, deren Pfade mit dem von der `Path`-Eigenschaft angegebenen Parameter verglichen werden sollen|  
|`InPath`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Ausgabeparameter.<br /><br /> Enthält die Elemente, die unter dem angegebenen Pfad gefunden wurden|  
|`OutOfPath`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Ausgabeparameter.<br /><br /> Enthält die Elemente, die unter dem angegebenen Pfad nicht gefunden wurden|  
|`Path`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem> -Parameter.<br /><br /> Gibt den Ordnerpfad an, der als Verweis verwendet werden soll|  
|`UpdateToAbsolutePaths`|Optionaler `Boolean` -Parameter.<br /><br /> Wenn TRUE, werden die Pfade der Ausgabeelemente als absolute Pfade aktualisiert.|  
  
## <a name="remarks"></a>Anmerkungen  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die `FindUnderPath`-Aufgabe verwendet um zu bestimmen, ob die im `MyFiles`-Element enthaltenen Dateien über Pfade verfügen, die unter dem Pfad existieren, der von der `SearchPath`-Eigenschaft angegeben wird. Nach Abschluss der Aufgabe enthält das Element `FilesNotFoundInPath` die Datei `File1.txt`. Das Element `FilesFoundInPath` enthält die Datei `File2.txt`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <MyFiles Include="C:\File1.txt" />  
        <MyFiles Include="C:\Projects\MyProject\File2.txt" />  
    </ItemGroup>  
  
    <PropertyGroup>  
        <SearchPath>C:\Projects\MyProject</SearchPath>  
    </PropertyGroup>  
  
    <Target Name="FindFiles">  
        <FindUnderPath  
            Files="@(MyFiles)"  
            Path="$(SearchPath)">  
            <Output  
                TaskParameter="InPath"  
                ItemName="FilesFoundInPath" />  
            <Output  
                TaskParameter="OutOfPath"  
                ItemName="FilesNotFoundInPath" />  
        </FindUnderPath>  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Task Reference](../msbuild/msbuild-task-reference.md)  (MSBuild-Aufgabenreferenz)  
 [Tasks (Aufgaben)](../msbuild/msbuild-tasks.md)   
 [MSBuild-Grundlagen](../msbuild/msbuild-concepts.md)
