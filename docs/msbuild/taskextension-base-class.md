---
title: TaskExtension-Basisklasse | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, tool task base class
- tool task base class [MSBuild]
ms.assetid: 08bb8059-b7e2-4565-89ba-d9034d4f0e16
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5f21bc2eacdc6886410e03ea80fad451c32abfc3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54949401"
---
# <a name="taskextension-base-class"></a>TaskExtension-Basisklasse
Viele Aufgaben erben von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Diese Vererbungskette fügt verschiedene Parameter zu den Aufgaben hinzu, die aus ihnen abgeleitet werden. Diese Parameter werden in diesem Dokument aufgeführt.  
  
## <a name="parameters"></a>Parameter  
 In der folgenden Tabelle werden die Parameter der Basisklassen beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine%2A>|Optionaler <xref:Microsoft.Build.Framework.IBuildEngine> -Parameter.<br /><br /> Gibt die für die Aufgaben verfügbare Build-Engine-Schnittstelle an. Die Build-Engine legt diesen Parameter automatisch fest, damit Aufgaben zurückgerufen werden können.|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine2%2A>|Optionaler <xref:Microsoft.Build.Framework.IBuildEngine2> -Parameter.<br /><br /> Gibt die für die Aufgaben verfügbare Build-Engine-Schnittstelle an. Die Build-Engine legt diesen Parameter automatisch fest, damit Aufgaben zurückgerufen werden können.<br /><br /> Hierbei handelt es sich um eine benutzerfreundliche Eigenschaft. Daher müssen die von dieser Klasse erbenden Aufgabenautoren den Wert nicht von `IBuildEngine` zu `IBuildEngine2` umwandeln.|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine3%2A>|Optionaler <xref:Microsoft.Build.Framework.IBuildEngine3> -Parameter.<br /><br /> Gibt die durch den Host bereitgestellte Build-Engine-Schnittstelle an.|  
|<xref:Microsoft.Build.Utilities.Task.HostObject%2A>|Optionaler <xref:Microsoft.Build.Framework.ITaskHost> -Parameter.<br /><br /> Gibt die Hostobjektinstanz (kann null sein) an. Die Build-Engine legt diese Eigenschaft fest, wenn die Host-IDE ein Hostobjekt mit dieser bestimmten Aufgabe verknüpft hat.|  
|<xref:Microsoft.Build.Tasks.TaskExtension.Log%2A>|Optionaler schreibgeschützter <xref:Microsoft.Build.Utilities.TaskLoggingHelper>-Parameter.<br /><br /> Ruft ein `TaskLoggingHelperExtension`-Objekt ab, das Aufgabenprotokollierungsmethoden enthält|  
  
## <a name="see-also"></a>Siehe auch  
 [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)   
 [Aufgaben](../msbuild/msbuild-tasks.md)