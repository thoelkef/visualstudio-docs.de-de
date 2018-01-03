---
title: UpdateManifest-Aufgabe | Microsoft-Dokumentation
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
- MSBuild, UpdateManifest task
- UpdateManifest task [MSBuild]
ms.assetid: 1291fd33-b89e-4e15-8fb1-69f9625cf2d2
caps.latest.revision: "4"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f01c36ff7e89bbd1919d54896ec70abdcadf5fcf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="updatemanifest-task"></a>UpdateManifest-Aufgabe
Aktualisiert die ausgewählten Eigenschaften in einem Manifest und führt das Signieren erneut aus.  
  
## <a name="parameters"></a>Parameter  
 In der folgenden Tabelle werden die Parameter der `UpdateManifest` -Aufgabe beschrieben.  
  
|Parameter|description|  
|---------------|-----------------|  
|`ApplicationManifest`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem> -Parameter.<br /><br /> Gibt das Anwendungsmanifest an|  
|`ApplicationPath`|Erforderlicher `String` -Parameter.<br /><br /> Gibt den Pfad für das Anwendungsmanifest an|  
|`InputManifest`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem> -Parameter.<br /><br /> Gibt das upzudatende Manifest an|  
|`OutputManifest`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>-Ausgabeparameter.<br /><br /> Gibt das Manifest an, das geupdatete Eigenschaften enthält|  
  
## <a name="remarks"></a>Hinweise  
 Zusätzlich zu den in der Tabelle aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Utilities.Task>-Klasse. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [Taskbasisklasse](../msbuild/task-base-class.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Tasks (Aufgaben)](../msbuild/msbuild-tasks.md)   
 [Aufgabenreferenz](../msbuild/msbuild-task-reference.md)