---
title: Move-Task| Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, Move task
- Move task [MSBuild]
ms.assetid: d1405347-1309-4f18-b565-905408093d59
caps.latest.revision: 4
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: c00adbbabf0d3b82acb17f4a269dfc693246bc69
ms.openlocfilehash: deee8db477425c628e214ad1332884f5a5693ea4
ms.contentlocale: de-de
ms.lasthandoff: 08/01/2017

---
# <a name="move-task"></a>Move-Task
Verschiebt Dateien in einen neuen Speicherort.  
  
## <a name="parameters"></a>Parameter  
 In der folgenden Tabelle werden die Parameter des `Move`-Tasks beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|`DestinationFiles`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Ausgabeparameter.<br /><br /> Gibt die Liste der Dateien an, in die die Quelldateien verschoben werden sollen. Diese Liste sollte eine Eins-zu-Eins-Zuordnung zu der Liste sein, die im `SourceFiles`-Parameter angegeben ist. Das heißt, die erste in `SourceFiles` angegebene Datei wird in den ersten in `DestinationFiles` angegebenen Speicherort verschoben usw.|  
|`DestinationFolder`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem> -Parameter.<br /><br /> Gibt das Verzeichnis an, in das die Dateien verschoben werden sollen.|  
|`MovedFiles`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Ausgabeparameter.<br /><br /> Enthält die Elemente, die erfolgreich verschoben wurden.|  
|`OverwriteReadOnlyFiles`|Optionaler `Boolean` -Parameter.<br /><br /> Wenn `true`, werden Dateien überschrieben, auch wenn diese als schreibgeschützt gekennzeichnet sind.|  
|`SourceFiles`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter.<br /><br /> Gibt die zu verschiebenden Dateien an.|  
  
## <a name="remarks"></a>Hinweise  
 Es muss entweder der `DestinationFolder`-Parameter oder der `DestinationFiles`-Parameter angegeben werden, jedoch nicht beide. Wenn beide angegeben werden, schlägt der Task fehl, und ein Fehler wird protokolliert.  

 Der `Move`-Task erstellt Ordner, die für die gewünschten Zieldateien benötigt werden.

 Zusätzlich zu den in der Tabelle aufgeführten Parametern erbt dieser Task Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Tasks (Aufgaben)](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md) (MSBuild-Aufgabenreferenz)

