---
title: CallTarget-Aufgabe | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- CallTarget task [MSBuild]
- MSBuild, CallTarget task
ms.assetid: bb1fe2c4-4383-436f-8326-c24cc4a46150
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d12fde1654c4645a6b543e44f8c48f273f32349b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47521787"
---
# <a name="calltarget-task"></a>CallTarget-Aufgabe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [CallTarget-Aufgabe](https://docs.microsoft.com/visualstudio/msbuild/calltarget-task).  
  
  
Ruft die angegebenen Ziele in der Projektdatei ab.  
  
## <a name="task-parameters"></a>Aufgabenparameter  
 In der folgenden Tabelle werden die Parameter der `CallTarget`-Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|`RunEachTargetSeparately`|Optionaler `Boolean`-Ausgabeparameter.<br /><br /> Wenn `true`, wird die [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]-Engine einmal pro Ziel aufgerufen. Wenn `false`, wird die [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]-Engine einmal aufgerufen, um alle Ziele zu erstellen. Der Standardwert ist `false`.|  
|`TargetOutputs`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Ausgabeparameter.<br /><br /> Enthält die Ausgaben aller erstellten Ziele.|  
|`Targets`|Optionaler `String[]` -Parameter.<br /><br /> Gibt das Ziel oder die Ziele an, die erstellt werden sollen.|  
|`UseResultsCache`|Optionaler `Boolean` -Parameter.<br /><br /> Wenn `true`, wird das zwischengespeicherte Ergebnis zurückgegeben, sofern es vorhanden ist.<br /><br /> **Hinweis** Wenn eine MSBuild-Aufgabe ausgeführt wird, wird deren Ausgabe in einem Gültigkeitsbereich als eine Liste von Buildelementen zwischengespeichert (ProjectFileName, GlobalProperties)[TargetNames].|  
  
## <a name="remarks"></a>Hinweise  
 Wenn ein in `Targets` angegebenes Ziel fehlschlägt und `RunEachTargetSeparately` `true` ist, fährt die Aufgabe mit dem Erstellen der verbleibenden Ziele fort.  
  
 Wenn Sie die Standardziele erstellen möchten, verwenden Sie die [MSBuild-Aufgabe](../msbuild/msbuild-task.md), und legen Sie den `Projects`-Parameter auf `$(MSBuildProjectFile)` fest.  
  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Beispiel  
 Über das folgende Beispiel wird `TargetA` in `CallOtherTargets` aufgerufen.  
  
```  
<Project DefaultTargets="CallOtherTargets"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <Target Name="CallOtherTargets">  
        <CallTarget Targets="TargetA"/>  
    </Target>  
  
    <Target Name="TargetA">  
        <Message Text="Building TargetA..." />  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Task Reference](../msbuild/msbuild-task-reference.md)  (MSBuild-Aufgabenreferenz)  
 [Ziele](../msbuild/msbuild-targets.md)



