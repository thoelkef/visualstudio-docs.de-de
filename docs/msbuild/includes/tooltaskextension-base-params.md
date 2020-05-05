---
author: ghogen
ms.author: ghogen
ms.topic: include
ms.date: 4/23/2020
ms.openlocfilehash: 40108f56ee9d64688fc665fdef0e0ab731bddfff
ms.sourcegitcommit: 596f92fcc84e6f4494178863a66aed85afe0bb08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2020
ms.locfileid: "82204489"
---
### <a name="tooltaskextension-parameters"></a>ToolTaskExtension-Parameter

Dieser Task erbt aus der <xref:Microsoft.Build.Tasks.ToolTaskExtension>-Klasse, die aus der <xref:Microsoft.Build.Utilities.ToolTask>-Klasse erbt, welche wiederum aus der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Diese Vererbungskette fügt verschiedene Parameter zu den Aufgaben hinzu, die aus ihnen abgeleitet werden.

In der folgenden Tabelle werden die Parameter der Basisklassen beschrieben:

| Parameter | Beschreibung |
| - | - |
| <xref:Microsoft.Build.Utilities.ToolTask.EchoOff%2A> | Optionaler `bool`-Parameter.<br /><br /> Bei der Festlegung auf `true` gibt diese Aufgabe **/Q** an die Befehlszeile *cmd.exe* so weiter, dass die Befehlszeile nicht zu „stdout“ kopiert wird. |
| <xref:Microsoft.Build.Utilities.ToolTask.EnvironmentVariables%2A> | Optionaler `String`-Arrayparameter.<br /><br /> Ein Array von Paaren von Umgebungsvariablen; durch Gleichheitszeichen getrennt. Diese Variablen werden an die erstellte ausführbare Datei zusätzlich zum regulären Umgebungsblock oder zum ausgewählten Überschreiben hinzugefügt. |
| <xref:Microsoft.Build.Utilities.ToolTask.ExitCode%2A> | Optionaler schreibgeschützter `Int32`-Ausgabeparameter.<br /><br /> Gibt den durch den ausgeführten Befehl bereitgestellten Exitcode an. Wenn bei der Aufgabe Fehler protokolliert wurden, der Prozess jedoch über einen Exitcode von „0“ (Erfolg) verfügt hat, wird dies auf „-1“ festgelegt. |
| <xref:Microsoft.Build.Utilities.ToolTask.LogStandardErrorAsError%2A> | Optionaler `bool`-Parameter.<br /><br /> Wenn `true` gegeben ist, werden alle im Standardfehlerstream empfangenen Meldungen als Fehler protokolliert. |
| <xref:Microsoft.Build.Utilities.ToolTask.LogStandardErrorAsError%2A> | Optionaler `bool`-Parameter.<br /><br /> Wenn `true` gegeben ist, werden alle im Standardfehlerstream empfangenen Meldungen als Fehler protokolliert. |
| <xref:Microsoft.Build.Utilities.ToolTask.StandardErrorImportance%2A> | Optionaler `String`-Parameter.<br /><br /> Wichtigkeit, mit der Text aus dem Standardausgabestream protokolliert wird. |
| <xref:Microsoft.Build.Utilities.ToolTask.StandardOutputImportance%2A> | Optionaler `String`-Parameter.<br /><br /> Wichtigkeit, mit der Text aus dem Standardausgabestream protokolliert wird. |
| <xref:Microsoft.Build.Utilities.ToolTask.Timeout%2A> | Optionaler `Int32`-Parameter.<br /><br /> Gibt die Zeitdauer in Millisekunden an, nach der die ausführbare Datei der Aufgabe beendet wird. Der Standardwert ist `Int.MaxValue`. Dieser gibt an, dass es kein Zeitlimit gibt. Das Timeout in Millisekunden. |
| <xref:Microsoft.Build.Utilities.ToolTask.ToolExe%2A> | Optionaler `string`-Parameter.<br /><br /> Projekte implementieren dies möglicherweise zum Überschreiben eines ToolName. Aufgaben überschreiben dies möglicherweise zum Beibehalten des ToolName. |
| <xref:Microsoft.Build.Utilities.ToolTask.ToolPath%2A> | Optionaler `string`-Parameter.<br /><br /> Gibt den Speicherort an, von wo aus die Aufgabe die zugrunde liegende ausführbare Datei lädt. Wenn dieser Parameter nicht angegeben ist, verwendet die Aufgabe den SDK-Installationspfad der Version des Frameworks, die von MSBuild ausgeführt wird. |
| <xref:Microsoft.Build.Utilities.ToolTask.UseCommandProcessor%2A> | Optionaler `bool`-Parameter.<br /><br /> Wenn die Festlegung auf `true` gegeben ist, erstellt diese Aufgabe eine Batchdatei für die Befehlszeile und führt sie aus, indem der Befehl nicht direkt ausgeführt wird, sondern der Befehlsprozessor verwendet wird. |
| <xref:Microsoft.Build.Utilities.ToolTask.YieldDuringToolExecution%2A> | Optionaler `bool`-Parameter.<br /><br /> Bei der Festlegung auf `true` ergibt diese Aufgabe den Knoten, wenn dessen Aufgabe ausgeführt wird. |
