---
title: CreateVisualBasicManifestResourceName-Aufgabe | Microsoft-Dokumentation
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
- MSBuild, CreateVisualBasicManifestResourceName task
- CreateVisualBasicManifestResourceName task [MSBuild]
ms.assetid: 251c47b9-de32-414b-a138-bf45290af12e
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d923c83c513ff33b971e1b5ca77109d6ff057db7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184061"
---
# <a name="createvisualbasicmanifestresourcename-task"></a>CreateVisualBasicManifestResourceName-Aufgabe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Erstellt einen Manifestnamen im [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]-Stil aus einem angegebenen RESX-Dateinamen oder aus einer anderen Ressource  
  
## <a name="parameters"></a>Parameter  
 In der folgenden Tabelle werden die Parameter der Aufgabe "" von " [kreatevisualbasicmanifestresourcename](../msbuild/createvisualbasicmanifestresourcename-task.md)" beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|`ManifestResourceNames`|Schreibgeschützter <xref:Microsoft.Build.Framework.ITaskItem> `[]`-Ausgabeparameter<br /><br /> Die resultierenden Manifestnamen|  
|`ResourceFiles`|Erforderlicher `String` -Parameter.<br /><br /> Der Name der Ressourcendatei, von der der [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]-Manifestname erstellt werden soll.|  
|`RootNamespace`|Optionaler `String`-Parameter.<br /><br /> Der Stammnamespace der Ressourcendatei, der normalerweise aus der Projektdatei übernommen wird. Kann `null` sein.|  
|`PrependCultureAsDirectory`|Optionaler `Boolean`-Parameter.<br /><br /> Wenn der Wert `true` ist, wird der Name der Kultur als Verzeichnisname unmittelbar vor dem Manifestressourcennamen hinzugefügt. Der Standardwert ist `true`sein.|  
|`ResourceFilesWithManifestResourceNames`|Optionaler schreibgeschützter `String`-Ausgabeparameter<br /><br /> Gibt den Namen der Ressourcendatei zurück, die jetzt den Manifestressourcennamen enthält|  
  
## <a name="remarks"></a>Hinweise  
 Mit der Aufgabe "" von "" "" "" "" "" "" "" "" "," "," "wird der entsprechende [Manifestressourcenname](../msbuild/createvisualbasicmanifestresourcename-task.md) für eine bestimmte RESX-oder Die Aufgabe stellt einen logischen Namen für eine Ressourcendatei bereit und fügt sie dann an einen Ausgabeparameter als Metadatenelement an.  
  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension-Basisklasse](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erfüllen](../msbuild/msbuild-tasks.md)   
 [Aufgaben Referenz](../msbuild/msbuild-task-reference.md)
