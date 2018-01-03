---
title: GenerateTrustInfo-Aufgabe | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateTrustInfo task
- GenerateTrustInfo task [MSBuild]
ms.assetid: 3ca60816-4bb0-4fef-ae43-ca0bfb63def3
caps.latest.revision: "4"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 614ace0800393b6c584da4cf4d85edfa7ea11b33
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="generatetrustinfo-task"></a>GenerateTrustInfo-Aufgabe
Generiert die Anwendungsvertrauensstellung aus dem Basismanifest und aus den `TargetZone`- und `ExcludedPermissions`-Parametern  
  
## <a name="parameters"></a>Parameter  
 In der folgenden Tabelle werden die Parameter der `GenerateTrustInfo` -Aufgabe beschrieben.  
  
|Parameter|description|  
|---------------|-----------------|  
|`ApplicationDependencies`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter<br /><br /> Gibt die abhängigen Assemblys an|  
|`BaseManifest`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem> -Parameter.<br /><br /> Gibt das Basismanifest an, über das die Anwendungsvertrauensstellung generiert wird|  
|`ExcludedPermissions`|Optionaler `String` -Parameter.<br /><br /> Gibt einen oder mehrere durch Semikolons getrennte Berechtigungsidentitätswerte an, die aus dem Standardberechtigungssatz der Zone ausgeschlossen werden sollen|  
|`TargetZone`|Optionaler `String` -Parameter.<br /><br /> Gibt einen Standardberechtigungssatz für eine Zone an, der von der Computerrichtlinie abgerufen wird.|  
|`TrustInfoFile`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>-Ausgabeparameter<br /><br /> Gibt die Datei an, die die Sicherheitsinformationen für die Anwendungsvertrauensstellung enthält|  
  
## <a name="remarks"></a>Hinweise  
 Zusätzlich zu den in der Tabelle aufgeführten Parametern erbt dieser Task Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Tasks (Aufgaben)](../msbuild/msbuild-tasks.md)   
 [Aufgabenreferenz](../msbuild/msbuild-task-reference.md)