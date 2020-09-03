---
title: FindAppConfigFile-Aufgabe | Microsoft-Dokumentation
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
- FindAppConfigFile task [MSBuild]
- MSBuild, FindAppConfigFile task
ms.assetid: e292de3e-7482-4426-83ce-d921061808bf
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fb9e1f3fbdc1a6f4d7c4e2c589f620f331a904ed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179606"
---
# <a name="findappconfigfile-task"></a>FindAppConfigFile-Aufgabe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sucht nach der Datei „app.config“ (falls vorhanden) in den angegebenen Listen  
  
## <a name="parameters"></a>Parameter  
 In der folgenden Tabelle werden die Parameter der `FindAppConfigFile`-Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|`AppConfigFile`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Ausgabeparameter.<br /><br /> Gibt das erste übereinstimmende Element in der Liste an, sofern vorhanden|  
|`PrimaryList`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter.<br /><br /> Gibt die primäre Liste an, die durchsucht werden soll|  
|`SecondaryList`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter.<br /><br /> Gibt die sekundäre Liste an, die durchsucht werden soll|  
|`TargetPath`|Erforderlicher `String`-Parameter.<br /><br /> Gibt den Wert an, der als Metadatenelement hinzugefügt werden soll|  
  
## <a name="remarks"></a>Bemerkungen  
 Zusätzlich zu den in der Tabelle aufgeführten Parametern erbt dieser Task Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension-Basisklasse](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erfüllen](../msbuild/msbuild-tasks.md)   
 [Aufgaben Referenz](../msbuild/msbuild-task-reference.md)
