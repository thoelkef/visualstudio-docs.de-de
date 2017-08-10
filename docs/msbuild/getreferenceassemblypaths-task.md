---
title: GetReferenceAssemblyPaths-Task | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 178ef49c-5dee-405b-a14b-a37f41dc0609
caps.latest.revision: 4
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 11a9cee75f912c5fb31cf4a031644abe9c63d744
ms.openlocfilehash: 6009ccb21696e207facfe6c172d4c131f13f8bc0
ms.contentlocale: de-de
ms.lasthandoff: 06/03/2017

---
# <a name="getreferenceassemblypaths-task"></a>GetReferenceAssemblyPaths-Aufgabe
Gibt den Verweisassemblypfad der verschiedenen Frameworks zurück  
  
## <a name="parameters"></a>Parameter  
 In der folgenden Tabelle werden die Parameter der `GetReferenceAssemblyPaths`-Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|`ReferenceAssemblyPaths`|Optionaler `String[]`-Ausgabeparameter.<br /><br /> Gibt den Pfad auf Grundlage des `TargetFrameworkMoniker`-Parameters zurück. Wenn `TargetFrameworkMoniker` gleich NULL oder leer ist, ist der Pfad `String.Empty`.|  
|`FullFrameworkReferenceAssemblyPaths`|Optionaler `String[]`-Ausgabeparameter.<br /><br /> Gibt den Pfad auf Grundlage des `TargetFrameworkMoniker`-Parameters zurück, ohne den Profilteil des Linkpfads zu berücksichtigen. Wenn `TargetFrameworkMoniker` gleich NULL oder leer ist, ist der Pfad `String.Empty`.|  
|`TargetFrameworkMoniker`|Optionaler `String` -Parameter.<br /><br /> Gibt den Ziel-Frameworklinkpfad an, der mit den Verweisassemblypfaden verknüpft ist|  
|`RootPath`|Optionaler `String` -Parameter.<br /><br /> Gibt den Stammpfad an, der zum Generieren des Verweisassemblypfads verwendet werden soll.|  
|`BypassFrameworkInstallChecks`|Optionaler <xref:System.Boolean> -Parameter.<br /><br /> Wenn `true`, werden die grundlegenden Prüfungen, die von `GetReferenceAssemblyPaths` ausgeführt werden, standardmäßig umgangen, um sicherzustellen, dass bestimmte Runtimeframeworks installiert sind, abhängig vom Zielframework.|  
|`TargetFrameworkMonikerDisplayName`|Optionaler `String`-Ausgabeparameter.<br /><br /> Gibt den Ziel-Frameworklinkpfad an|  
  
## <a name="remarks"></a>Hinweise  
 Zusätzlich zu den in der Tabelle aufgeführten Parametern erbt dieser Task Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Tasks (Aufgaben)](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md) (MSBuild-Aufgabenreferenz)
