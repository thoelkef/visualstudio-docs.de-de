---
title: Move-Task| Microsoft-Dokumentation
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
- MSBuild, Move task
- Move task [MSBuild]
ms.assetid: d1405347-1309-4f18-b565-905408093d59
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ab75ccebd618946454c3386f564e3f6199409935
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68191574"
---
# <a name="move-task"></a>Move-Task
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Verschiebt Dateien in einen neuen Speicherort.  
  
## <a name="parameters"></a>Parameter  
 In der folgenden Tabelle werden die Parameter des `Move`-Tasks beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|`DestinationFiles`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Ausgabeparameter.<br /><br /> Gibt die Liste der Dateien an, in die die Quelldateien verschoben werden sollen. Diese Liste sollte eine Eins-zu-Eins-Zuordnung zu der Liste sein, die im `SourceFiles`-Parameter angegeben ist. Das heißt, die erste in `SourceFiles` angegebene Datei wird in den ersten in `DestinationFiles` angegebenen Speicherort verschoben usw.|  
|`DestinationFolder`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>-Parameter.<br /><br /> Gibt das Verzeichnis an, in das die Dateien verschoben werden sollen.|  
|`MovedFiles`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Ausgabeparameter.<br /><br /> Enthält die Elemente, die erfolgreich verschoben wurden.|  
|`OverwriteReadOnlyFiles`|Optionaler `Boolean`-Parameter.<br /><br /> Wenn `true`, werden Dateien überschrieben, auch wenn diese als schreibgeschützt gekennzeichnet sind.|  
|`SourceFiles`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter.<br /><br /> Gibt die zu verschiebenden Dateien an.|  
  
## <a name="remarks"></a>Bemerkungen  
 Es muss entweder der `DestinationFolder`-Parameter oder der `DestinationFiles`-Parameter angegeben werden, jedoch nicht beide. Wenn beide angegeben werden, schlägt die Aufgabe fehl, und ein Fehler wird protokolliert.  
  
 Zusätzlich zu den in der Tabelle aufgeführten Parametern erbt dieser Task Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension-Basisklasse](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erfüllen](../msbuild/msbuild-tasks.md)   
 [Aufgaben Referenz](../msbuild/msbuild-task-reference.md)
