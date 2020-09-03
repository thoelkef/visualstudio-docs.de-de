---
title: CreateCSharpManifestResourceName-Aufgabe | Microsoft-Dokumentation
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
- MSBuild, CreateCSharpManifestResourceName task
- CreateCSharpManifestResourceName task [MSBuild]
ms.assetid: 2ace88c1-d757-40a7-8158-c1d3f5ff0511
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9308f94e865bfe54384719d8f57f3ad1819c79fb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184044"
---
# <a name="createcsharpmanifestresourcename-task"></a>CreateCSharpManifestResourceName-Aufgabe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Erstellt einen Manifestnamen im [!INCLUDE[csprcs](../includes/csprcs-md.md)]-Stil aus einem angegebenen RESX-Dateinamen oder aus einer anderen Ressource  
  
## <a name="parameters"></a>Parameter  
 In der folgenden Tabelle werden die Parameter der [Aufgabe "| atecsharpmanifestresourcename](../msbuild/createcsharpmanifestresourcename-task.md)" beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|`ManifestResourceNames`|Schreibgeschützter <xref:Microsoft.Build.Framework.ITaskItem> `[]`-Ausgabeparameter<br /><br /> Die resultierenden Manifestnamen|  
|`ResourceFiles`|Erforderlicher `String` -Parameter.<br /><br /> Der Name der Ressourcendatei, von der der [!INCLUDE[csprcs](../includes/csprcs-md.md)]-Manifestname erstellt werden soll.|  
|`RootNamespace`|Optionaler `String`-Parameter.<br /><br /> Der Stammnamespace der Ressourcendatei, der normalerweise aus der Projektdatei übernommen wird. Kann `null` sein.|  
|`PrependCultureAsDirectory`|Optionaler `Boolean`-Parameter.<br /><br /> Wenn der Wert `true` ist, wird der Name der Kultur als Verzeichnisname unmittelbar vor dem Manifestressourcennamen hinzugefügt. Der Standardwert ist `true`sein.|  
|`ResourceFilesWithManifestResourceNames`|Optionaler schreibgeschützter `String`-Ausgabeparameter<br /><br /> Gibt den Namen der Ressourcendatei zurück, die jetzt den Manifestressourcennamen enthält|  
  
## <a name="remarks"></a>Hinweise  
 Mit der Aufgabe "" von "" "" "" "" "" "" "" "" "," "," "wird der entsprechende [Manifestressourcenname](../msbuild/createvisualbasicmanifestresourcename-task.md) für eine bestimmte RESX-oder Die Aufgabe stellt einen logischen Namen für eine Ressourcendatei bereit und fügt sie dann an einen Ausgabeparameter als Metadatenelement an.  
  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension-Basisklasse](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erfüllen](../msbuild/msbuild-tasks.md)   
 [Aufgaben Referenz](../msbuild/msbuild-task-reference.md)
