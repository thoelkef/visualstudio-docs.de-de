---
title: CallTarget-Aufgabe | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- CallTarget task [MSBuild]
- MSBuild, CallTarget task
ms.assetid: bb1fe2c4-4383-436f-8326-c24cc4a46150
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 83240cfa9deec2585aaa23db4aa79fbfe6929b09
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="calltarget-task"></a>CallTarget-Aufgabe
Ruft die angegebenen Ziele in der Projektdatei ab.  
  
## <a name="task-parameters"></a>Aufgabenparameter  
 In der folgenden Tabelle werden die Parameter der `CallTarget`-Aufgabe beschrieben.  
  
|Parameter|description|  
|---------------|-----------------|  
|`RunEachTargetSeparately`|Optionaler `Boolean`-Eingabeparameter.<br /><br /> Wenn `true`, wird das [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]-Modul einmal pro Ziel aufgerufen. Wenn `false`, wird das [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]-Modul einmal aufgerufen, um alle Ziele zu erstellen. Der Standardwert ist `false`.|  
|`TargetOutputs`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Ausgabeparameter.<br /><br /> Enthält die Ausgaben aller erstellten Ziele.|  
|`Targets`|Optionaler `String[]` -Parameter.<br /><br /> Gibt das Ziel oder die Ziele an, die erstellt werden sollen.|  
|`UseResultsCache`|Optionaler `Boolean` -Parameter.<br /><br /> Wenn `true`, wird das zwischengespeicherte Ergebnis zurückgegeben, sofern es vorhanden ist.<br /><br /> **Hinweis** Wenn eine MSBuild-Aufgabe ausgeführt wird, wird deren Ausgabe in einem Gültigkeitsbereich als eine Liste von Buildelementen zwischengespeichert (ProjectFileName, GlobalProperties)[TargetNames].|  
  
## <a name="remarks"></a>Hinweise  
 Wenn ein in `Targets` angegebenes Ziel fehlschlägt und `RunEachTargetSeparately` `true` ist, fährt die Aufgabe mit dem Erstellen der verbleibenden Ziele fort.  
  
 Wenn Sie die Standardziele erstellen möchten, verwenden Sie die [MSBuild-Aufgabe](../msbuild/msbuild-task.md), und legen Sie den `Projects`-Parameter auf `$(MSBuildProjectFile)` fest.  
  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Beispiel  
 Über das folgende Beispiel wird `TargetA` in `CallOtherTargets` aufgerufen.  
  
```xml  
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
 [Targets](../msbuild/msbuild-targets.md) (MSBuild-Ziele)