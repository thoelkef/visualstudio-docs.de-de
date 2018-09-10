---
title: GetFrameworkSdkPath-Aufgabe | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GetFrameworkSdkPath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- GetFrameworkSdkPath task [MSBuild]
- MSBuild, GetFrameworkSdkPath task
ms.assetid: 2ef82b98-02b6-40cf-a9b5-f0e882fb5064
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a3ce43a9b2acae5589e4b746ce4bf2b2a47b0111
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/10/2018
ms.locfileid: "37946832"
---
# <a name="getframeworksdkpath-task"></a>GetFrameworkSdkPath-Aufgabe
Ruft den Pfad zu [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] ab  
  
## <a name="task-parameters"></a>Aufgabenparameter  
 In der folgenden Tabelle werden die Parameter der `GetFrameworkSdkPath` -Aufgabe beschrieben.  
  
|Parameter|Beschreibung |  
|---------------|-----------------|  
|`FrameworkSdkVersion20Path`|Optionaler schreibgeschützter `String`-Parameter<br /><br /> Gibt den Pfad zum .NET SDK-Version 2.0 zurück, falls vorhanden Andernfalls wird `String.Empty` zurückgegeben.|  
|`FrameworkSdkVersion35Path`|Optionaler schreibgeschützter `String`-Parameter<br /><br /> Gibt den Pfad zum .NET SDK-Version 3.5 zurück, falls vorhanden Andernfalls wird `String.Empty` zurückgegeben.|  
|`FrameworkSdkVersion40Path`|Optionaler schreibgeschützter `String`-Parameter<br /><br /> Gibt den Pfad zum .NET SDK-Version 4.0 zurück, falls vorhanden Andernfalls wird `String.Empty` zurückgegeben.|  
|`Path`|Optionaler `String`-Ausgabeparameter.<br /><br /> Enthält den Pfad zum neuesten .NET SDK, wenn eine Version vorhanden ist. Andernfalls wird `String.Empty` zurückgegeben.|  
  
## <a name="remarks"></a>Hinweise  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension-Basisklasse](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird mit der Aufgabe `GetFrameworkSdkPath` der Pfad zu [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] in der `SdkPath`-Eigenschaft gespeichert.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="GetPath">  
        <GetFrameworkSdkPath>  
            <Output  
                TaskParameter="Path"  
                PropertyName="SdkPath" />  
        </GetFrameworkSdkPath>  
        <Message Text="$(SdkPath)"/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Tasks (Aufgaben)](../msbuild/msbuild-tasks.md)   
 [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)