---
title: CreateVisualBasicManifestResourceName-Aufgabe | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d4c4c4e93f157ef88452a7108e595dc7cd9a9ccb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49849475"
---
# <a name="createvisualbasicmanifestresourcename-task"></a>CreateVisualBasicManifestResourceName-Aufgabe
Erstellt einen Manifestnamen im [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]-Stil aus einem angegebenen *RESX*-Dateinamen oder aus einer anderen Ressource.  

## <a name="parameters"></a>Parameter  
 In der folgenden Tabelle werden die Parameter der Aufgabe [CreateVisualBasicManifestResourceName](../msbuild/createvisualbasicmanifestresourcename-task.md) beschrieben.  


| Parameter | Beschreibung  |
| - | - |
| `ManifestResourceNames` | Schreibgeschützter <xref:Microsoft.Build.Framework.ITaskItem>-`[]`-Ausgabeparameter<br /><br /> Die resultierenden Manifestnamen |
| `ResourceFiles` | Erforderlicher `String` -Parameter.<br /><br /> Der Name der Ressourcendatei, von der der [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]-Manifestname erstellt werden soll. |
| `RootNamespace` | Optionaler `String` -Parameter.<br /><br /> Der Stammnamespace der Ressourcendatei, der normalerweise aus der Projektdatei übernommen wird. Kann `null` sein. |
| `PrependCultureAsDirectory` | Optionaler `Boolean` -Parameter.<br /><br /> Wenn der Wert `true` ist, wird der Name der Kultur als Verzeichnisname unmittelbar vor dem Manifestressourcennamen hinzugefügt. Der Standardwert ist `true`sein. |
| `ResourceFilesWithManifestResourceNames` | Optionaler schreibgeschützter `String`-Ausgabeparameter<br /><br /> Gibt den Namen der Ressourcendatei zurück, die jetzt den Manifestressourcennamen enthält |

## <a name="remarks"></a>Hinweise  
 Die Aufgabe [CreateVisualBasicManifestResourceName](../msbuild/createvisualbasicmanifestresourcename-task.md) bestimmt den richtigen Manifestressourcennamen, der einer bestimmten *RESX*- oder einer anderen Ressourcendatei zugewiesen werden soll. Die Aufgabe stellt einen logischen Namen für eine Ressourcendatei bereit und fügt sie dann an einen Ausgabeparameter als Metadatenelement an.  

 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension-Basisklasse](../msbuild/taskextension-base-class.md).  

## <a name="see-also"></a>Siehe auch  
 [Tasks (Aufgaben)](../msbuild/msbuild-tasks.md)   
 [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)