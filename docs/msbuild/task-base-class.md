---
title: Task-Basisklasse | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 6c3f6238-b9f0-4325-b8b0-de61090bd0a2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f1859694a85b25effe56afef17f65bd831a65882
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54959407"
---
# <a name="task-base-class"></a>Aufgabenbasisklasse
Viele Aufgaben erben letztlich von der <xref:Microsoft.Build.Utilities.Task>-Klasse. Diese Klasse fügt den Aufgaben, die ihr abgeleitet werden, mehrere Parameter hinzu. Diese Parameter werden in diesem Dokument aufgeführt.  
  
## <a name="parameters"></a>Parameter  
 In der folgenden Tabelle werden die Parameter dieser Basisklasse beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine%2A>|Optionaler <xref:Microsoft.Build.Framework.IBuildEngine> -Parameter.<br /><br /> Gibt die für die Aufgaben verfügbare Build-Engine-Schnittstelle an. Die Build-Engine legt diesen Parameter automatisch fest, damit Aufgaben zurückgerufen werden können.|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine2%2A>|Optionaler <xref:Microsoft.Build.Framework.IBuildEngine2> -Parameter.<br /><br /> Gibt die für die Aufgaben verfügbare Build-Engine-Schnittstelle an. Die Build-Engine legt diesen Parameter automatisch fest, damit Aufgaben zurückgerufen werden können.<br /><br /> Hierbei handelt es sich um eine benutzerfreundliche Eigenschaft. Daher müssen die von dieser Klasse erbenden Aufgabenautoren den Wert nicht von `IBuildEngine` zu `IBuildEngine2` umwandeln.|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine3%2A>|Optionaler <xref:Microsoft.Build.Framework.IBuildEngine3> -Parameter.<br /><br /> Gibt die durch den Host bereitgestellte Build-Engine-Schnittstelle an.|  
|<xref:Microsoft.Build.Utilities.Task.HostObject%2A>|Optionaler <xref:Microsoft.Build.Framework.ITaskHost> -Parameter.<br /><br /> Gibt die Hostobjektinstanz (kann null sein) an. Die Build-Engine legt diese Eigenschaft fest, wenn die Host-IDE ein Hostobjekt mit dieser bestimmten Aufgabe verknüpft hat.|  
|<xref:Microsoft.Build.Utilities.Task.Log%2A>|Optionaler schreibgeschützter <xref:Microsoft.Build.Utilities.TaskLoggingHelper>-Parameter.<br /><br /> Das Hilfsobjekt für die Protokollierung|  
  
## <a name="see-also"></a>Siehe auch  
 [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)   
 [Aufgaben](../msbuild/msbuild-tasks.md)