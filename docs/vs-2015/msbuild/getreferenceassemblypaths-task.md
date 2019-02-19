---
title: GetReferenceAssemblyPaths-Task | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 178ef49c-5dee-405b-a14b-a37f41dc0609
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4563e1c28c17a173c211f979d2ca46503a6d19a7
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2019
ms.locfileid: "54805129"
---
# <a name="getreferenceassemblypaths-task"></a>GetReferenceAssemblyPaths-Aufgabe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Gibt den Verweisassemblypfad der verschiedenen Frameworks zurück  
  
## <a name="parameters"></a>Parameter  
 In der folgenden Tabelle werden die Parameter der `GetReferenceAssemblyPaths` -Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|`ReferenceAssemblyPaths`|Optionaler `String[]`-Ausgabeparameter.<br /><br /> Gibt den Pfad auf Grundlage des `TargetFrameworkMoniker`-Parameters zurück. Wenn `TargetFrameworkMoniker` gleich NULL oder leer ist, ist der Pfad `String.Empty`.|  
|`FullFrameworkReferenceAssemblyPaths`|Optionaler `String[]`-Ausgabeparameter.<br /><br /> Gibt den Pfad auf Grundlage des `TargetFrameworkMoniker`-Parameters zurück, ohne den Profilteil des Linkpfads zu berücksichtigen. Wenn `TargetFrameworkMoniker` gleich NULL oder leer ist, ist der Pfad `String.Empty`.|  
|`TargetFrameworkMoniker`|Optionaler `String` -Parameter.<br /><br /> Gibt den Ziel-Frameworklinkpfad an, der mit den Verweisassemblypfaden verknüpft ist|  
|`RootPath`|Optionaler `String` -Parameter.<br /><br /> Gibt den Stammpfad an, der zum Generieren des Verweisassemblypfads verwendet werden soll.|  
|`BypassFrameworkInstallChecks`|Optionaler [Boolean](<!-- TODO: review code entity reference <xref:assetId:///Boolean?qualifyHint=False&amp;autoUpgrade=True>  -->)-Parameter.<br /><br /> Wenn `true`, werden die grundlegenden Prüfungen, die von `GetReferenceAssemblyPaths` ausgeführt werden, standardmäßig umgangen, um sicherzustellen, dass bestimmte Runtimeframeworks installiert sind, abhängig vom Zielframework.|  
|`TargetFrameworkMonikerDisplayName`|Optionaler `String`-Ausgabeparameter.<br /><br /> Gibt den Ziel-Frameworklinkpfad an|  
  
## <a name="remarks"></a>Anmerkungen  
 Zusätzlich zu den in der Tabelle aufgeführten Parametern erbt dieser Task Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Tasks (Aufgaben)](../msbuild/msbuild-tasks.md)   
 [Aufgabenreferenz](../msbuild/msbuild-task-reference.md)
