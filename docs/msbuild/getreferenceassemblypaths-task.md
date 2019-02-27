---
title: GetReferenceAssemblyPaths-Task | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 178ef49c-5dee-405b-a14b-a37f41dc0609
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e752e345de9211a2b6c8d8fe076be863a04c70ca
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56610265"
---
# <a name="getreferenceassemblypaths-task"></a>GetReferenceAssemblyPaths-Aufgabe
Gibt den Verweisassemblypfad der verschiedenen Frameworks zurück

## <a name="parameters"></a>Parameter
 In der folgenden Tabelle werden die Parameter der `GetReferenceAssemblyPaths` -Aufgabe beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|`ReferenceAssemblyPaths`|Optionaler `String[]`-Ausgabeparameter.<br /><br /> Gibt den Pfad auf Grundlage des `TargetFrameworkMoniker`-Parameters zurück. Wenn `TargetFrameworkMoniker` gleich NULL oder leer ist, ist der Pfad `String.Empty`.|
|`FullFrameworkReferenceAssemblyPaths`|Optionaler `String[]`-Ausgabeparameter.<br /><br /> Gibt den Pfad auf Grundlage des `TargetFrameworkMoniker`-Parameters zurück, ohne den Profilteil des Linkpfads zu berücksichtigen. Wenn `TargetFrameworkMoniker` gleich NULL oder leer ist, ist der Pfad `String.Empty`.|
|`TargetFrameworkMoniker`|Optionaler `String` -Parameter.<br /><br /> Gibt den Ziel-Frameworklinkpfad an, der mit den Verweisassemblypfaden verknüpft ist|
|`RootPath`|Optionaler `String` -Parameter.<br /><br /> Gibt den Stammpfad an, der zum Generieren des Verweisassemblypfads verwendet werden soll.|
|`BypassFrameworkInstallChecks`|Optionaler <xref:System.Boolean> -Parameter.<br /><br /> Wenn `true`, werden die grundlegenden Prüfungen, die von `GetReferenceAssemblyPaths` ausgeführt werden, standardmäßig umgangen, um sicherzustellen, dass bestimmte Runtimeframeworks installiert sind, abhängig vom Zielframework.|
|`TargetFrameworkMonikerDisplayName`|Optionaler `String`-Ausgabeparameter.<br /><br /> Gibt den Ziel-Frameworklinkpfad an|

## <a name="remarks"></a>Anmerkungen
 Zusätzlich zu den in der Tabelle aufgeführten Parametern erbt dieser Task Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension-Basisklasse](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Siehe auch
- [Aufgaben](../msbuild/msbuild-tasks.md)
- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)