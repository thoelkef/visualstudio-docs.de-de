---
title: GenerateTrustInfo-Aufgabe | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
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
- MSBuild, GenerateTrustInfo task
- GenerateTrustInfo task [MSBuild]
ms.assetid: 3ca60816-4bb0-4fef-ae43-ca0bfb63def3
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a20a50e74f702c1c015f29abde81b2e24a5551b5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49208694"
---
# <a name="generatetrustinfo-task"></a>GenerateTrustInfo-Aufgabe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Generiert die Anwendungsvertrauensstellung aus dem Basismanifest und aus den `TargetZone`- und `ExcludedPermissions`-Parametern  
  
## <a name="parameters"></a>Parameter  
 In der folgenden Tabelle werden die Parameter der `GenerateTrustInfo` -Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
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



