---
title: CreateVisualBasicManifestResourceName-Aufgabe | Microsoft-Dokumentation
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
- MSBuild, CreateVisualBasicManifestResourceName task
- CreateVisualBasicManifestResourceName task [MSBuild]
ms.assetid: 251c47b9-de32-414b-a138-bf45290af12e
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7a1588ce170ad9e833f7378a837e4e75853c19ba
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47515592"
---
# <a name="createvisualbasicmanifestresourcename-task"></a>CreateVisualBasicManifestResourceName-Aufgabe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [CreateVisualBasicManifestResourceName-Aufgabe](https://docs.microsoft.com/visualstudio/msbuild/createvisualbasicmanifestresourcename-task).  
  
  
Erstellt einen Manifestnamen im [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]-Stil aus einem angegebenen RESX-Dateinamen oder aus einer anderen Ressource  
  
## <a name="parameters"></a>Parameter  
 In der folgenden Tabelle werden die Parameter der Aufgabe [CreateVisualBasicManifestResourceName](../msbuild/createvisualbasicmanifestresourcename-task.md) beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|`ManifestResourceNames`|Schreibgeschützter <xref:Microsoft.Build.Framework.ITaskItem>-`[]`-Ausgabeparameter<br /><br /> Die resultierenden Manifestnamen|  
|`ResourceFiles`|Erforderlicher `String` -Parameter.<br /><br /> Der Name der Ressourcendatei, von der der [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]-Manifestname erstellt werden soll.|  
|`RootNamespace`|Optionaler `String` -Parameter.<br /><br /> Der Stammnamespace der Ressourcendatei, der normalerweise aus der Projektdatei übernommen wird. Kann `null` sein.|  
|`PrependCultureAsDirectory`|Optionaler `Boolean` -Parameter.<br /><br /> Wenn der Wert `true` ist, wird der Name der Kultur als Verzeichnisname unmittelbar vor dem Manifestressourcennamen hinzugefügt. Der Standardwert ist `true`sein.|  
|`ResourceFilesWithManifestResourceNames`|Optionaler schreibgeschützter `String`-Ausgabeparameter<br /><br /> Gibt den Namen der Ressourcendatei zurück, die jetzt den Manifestressourcennamen enthält|  
  
## <a name="remarks"></a>Hinweise  
 Die Aufgabe [CreateVisualBasicManifestResourceName](../msbuild/createvisualbasicmanifestresourcename-task.md) bestimmt den richtigen Manifestressourcennamen, der einer bestimmten RESX- oder einer anderen Ressourcendatei zugewiesen werden soll. Die Aufgabe stellt einen logischen Namen für eine Ressourcendatei bereit und fügt sie dann an einen Ausgabeparameter als Metadatenelement an.  
  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Tasks (Aufgaben)](../msbuild/msbuild-tasks.md)   
 [Aufgabenreferenz](../msbuild/msbuild-task-reference.md)



