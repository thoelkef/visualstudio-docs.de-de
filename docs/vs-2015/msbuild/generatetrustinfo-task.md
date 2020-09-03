---
title: GenerateTrustInfo-Aufgabe | Microsoft-Dokumentation
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
- MSBuild, GenerateTrustInfo task
- GenerateTrustInfo task [MSBuild]
ms.assetid: 3ca60816-4bb0-4fef-ae43-ca0bfb63def3
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ccbe11cefa730264e523390a0844086d6fb03ec1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149576"
---
# <a name="generatetrustinfo-task"></a>GenerateTrustInfo-Aufgabe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Generiert die Anwendungsvertrauensstellung aus dem Basismanifest und aus den `TargetZone`- und `ExcludedPermissions`-Parametern  
  
## <a name="parameters"></a>Parameter  
 In der folgenden Tabelle werden die Parameter der `GenerateTrustInfo`-Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|`ApplicationDependencies`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter<br /><br /> Gibt die abhängigen Assemblys an|  
|`BaseManifest`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>-Parameter.<br /><br /> Gibt das Basismanifest an, über das die Anwendungsvertrauensstellung generiert wird|  
|`ExcludedPermissions`|Optionaler `String`-Parameter.<br /><br /> Gibt einen oder mehrere durch Semikolons getrennte Berechtigungsidentitätswerte an, die aus dem Standardberechtigungssatz der Zone ausgeschlossen werden sollen|  
|`TargetZone`|Optionaler `String`-Parameter.<br /><br /> Gibt einen Standardberechtigungssatz für eine Zone an, der von der Computerrichtlinie abgerufen wird.|  
|`TrustInfoFile`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>-Ausgabeparameter<br /><br /> Gibt die Datei an, die die Sicherheitsinformationen für die Anwendungsvertrauensstellung enthält|  
  
## <a name="remarks"></a>Bemerkungen  
 Zusätzlich zu den in der Tabelle aufgeführten Parametern erbt dieser Task Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension-Basisklasse](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erfüllen](../msbuild/msbuild-tasks.md)   
 [Aufgaben Referenz](../msbuild/msbuild-task-reference.md)
