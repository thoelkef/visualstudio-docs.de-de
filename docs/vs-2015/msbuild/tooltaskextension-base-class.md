---
title: ToolTaskExtension-Basisklasse | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
f1_keywords:
- MSBuild.ToolTask.ToolCommandFailed
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 258ae433-f68a-49f1-b276-da20e3472e68
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 41ac1db7348ff993671623214b59113d6210b83e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193331"
---
# <a name="tooltaskextension-base-class"></a>ToolTaskExtension-Basisklasse
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Viele Aufgaben erben aus der <xref:Microsoft.Build.Tasks.ToolTaskExtension>-Klasse, die aus der <xref:Microsoft.Build.Utilities.ToolTask>-Klasse erbt, welche wiederum aus der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Diese Vererbungskette fügt verschiedene Parameter zu den Aufgaben hinzu, die aus ihnen abgeleitet werden. Diese Parameter werden in diesem Dokument aufgeführt.  
  
## <a name="parameters"></a>Parameter  
 In der folgenden Tabelle werden die Parameter der Basisklassen beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine%2A>|Optionaler <xref:Microsoft.Build.Framework.IBuildEngine>-Parameter.<br /><br /> Gibt die für die Aufgaben verfügbare Build-Engine-Schnittstelle an. Die Build-Engine legt diesen Parameter automatisch fest, damit Aufgaben zurückgerufen werden können.|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine2%2A>|Optionaler <xref:Microsoft.Build.Framework.IBuildEngine2>-Parameter.<br /><br /> Gibt die für die Aufgaben verfügbare Build-Engine-Schnittstelle an. Die Build-Engine legt diesen Parameter automatisch fest, damit Aufgaben zurückgerufen werden können.<br /><br /> Hierbei handelt es sich um eine benutzerfreundliche Eigenschaft. Daher müssen die von dieser Klasse erbenden Aufgabenautoren den Wert nicht von `IBuildEngine` zu `IBuildEngine2` umwandeln.|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine3%2A>|Optionaler <xref:Microsoft.Build.Framework.IBuildEngine3>-Parameter.<br /><br /> Gibt die durch den Host bereitgestellte Build-Engine-Schnittstelle an.|  
|<xref:Microsoft.Build.Utilities.ToolTask.EchoOff%2A>|Optionaler `bool`-Parameter.<br /><br /> Bei der Festlegung auf `true` gibt diese Aufgabe **/Q** an die Befehlszeile cmd.exe so weiter, dass die Befehlszeile nicht zu „stdout“ kopiert wird.|  
|<xref:Microsoft.Build.Utilities.ToolTask.EnvironmentVariables%2A>|Optionaler `String`-Arrayparameter.<br /><br /> Ein Array von Paaren von Umgebungsvariablen; durch Gleichheitszeichen getrennt. Diese Variablen werden an die erstellte ausführbare Datei zusätzlich zum regulären Umgebungsblock oder zum ausgewählten Überschreiben hinzugefügt.|  
|<xref:Microsoft.Build.Utilities.ToolTask.ExitCode%2A>|Optionaler schreibgeschützter `Int32`-Ausgabeparameter.<br /><br /> Gibt den durch den ausgeführten Befehl bereitgestellten Exitcode an. Wenn bei der Aufgabe Fehler protokolliert wurden, der Prozess jedoch über einen Exitcode von „0“ (Erfolg) verfügt hat, wird dies auf „-1“ festgelegt.|  
|<xref:Microsoft.Build.Utilities.Task.HostObject%2A>|Optionaler <xref:Microsoft.Build.Framework.ITaskHost>-Parameter.<br /><br /> Gibt die Hostobjektinstanz (kann null sein) an. Die Build-Engine legt diese Eigenschaft fest, wenn die Host-IDE ein Hostobjekt mit dieser bestimmten Aufgabe verknüpft hat.|  
|<xref:Microsoft.Build.Tasks.ToolTaskExtension.Log%2A>|Optionaler schreibgeschützter <xref:Microsoft.Build.Utilities.TaskLoggingHelper>-Parameter.<br /><br /> Ruft eine Instanz einer <xref:Microsoft.Build.Tasks.TaskLoggingHelperExtension>-Klasse ab, die Aufgabenprotokollierungsmethoden enthält.|  
|<xref:Microsoft.Build.Utilities.ToolTask.LogStandardErrorAsError%2A>|Optionaler `bool`-Parameter.<br /><br /> Wenn `true` gegeben ist, werden alle im Standardfehlerstream empfangenen Meldungen als Fehler protokolliert.|  
|<xref:Microsoft.Build.Utilities.ToolTask.StandardErrorImportance%2A>|Optionaler `String`-Parameter.<br /><br /> Wichtigkeit, mit der Text aus dem Standardausgabestream protokolliert wird.|  
|<xref:Microsoft.Build.Utilities.ToolTask.StandardOutputImportance%2A>|Optionaler `String`-Parameter.<br /><br /> Wichtigkeit, mit der Text aus dem Standardausgabestream protokolliert wird.|  
|<xref:Microsoft.Build.Utilities.ToolTask.Timeout%2A>|Virtueller optionaler `Int32`-Parameter.<br /><br /> Gibt die Zeitdauer in Millisekunden an, nach der die ausführbare Datei der Aufgabe beendet wird. Der Standardwert ist `Int.MaxValue`. Dieser gibt an, dass es kein Zeitlimit gibt. Das Zeitlimit wird in Millisekunden angegeben.|  
|<xref:Microsoft.Build.Utilities.ToolTask.ToolExe%2A>|Virtueller optionaler `string`-Parameter.<br /><br /> Projekte implementieren dies möglicherweise zum Überschreiben eines ToolName. Aufgaben überschreiben dies möglicherweise zum Beibehalten des ToolName.|  
|<xref:Microsoft.Build.Utilities.ToolTask.ToolPath%2A>|Optionaler `string`-Parameter.<br /><br /> Gibt den Speicherort an, von wo aus die Aufgabe die zugrunde liegende ausführbare Datei lädt. Wenn dieser Parameter nicht angegeben ist, verwendet die Aufgabe den SDK-Installationspfad, der der Version des Frameworks entspricht, das [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] ausführt.|  
|<xref:Microsoft.Build.Utilities.ToolTask.UseCommandProcessor%2A>|Optionaler `bool`-Parameter.<br /><br /> Wenn die Festlegung auf `true` gegeben ist, erstellt diese Aufgabe eine Batchdatei für die Befehlszeile und führt sie aus, indem der Befehl nicht direkt ausgeführt wird, sondern der Befehlsprozessor verwendet wird.|  
|<xref:Microsoft.Build.Utilities.ToolTask.YieldDuringToolExecution%2A>|Optionaler `bool`-Parameter.<br /><br /> Bei der Festlegung auf `true` ergibt diese Aufgabe den Knoten, wenn dessen Aufgabe ausgeführt wird.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Aufgaben Referenz](../msbuild/msbuild-task-reference.md)   
 [Aufgaben](../msbuild/msbuild-tasks.md)
