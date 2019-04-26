---
title: ResolveNativeReference-Task | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ResolveNativeReference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, ResolveNativeReference task
- ResolveNativeReference task [MSBuild]
ms.assetid: 56acd101-de77-4eec-92c6-f5c6d2187579
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0f18549fece2db8a4a758dee17f6b4b1283d97e4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62996611"
---
# <a name="resolvenativereference-task"></a>ResolveNativeReference-Aufgabe
Löst native Verweise auf. Implementiert die <xref:Microsoft.Build.Tasks.ResolveNativeReference>-Klasse. Diese Klasse unterstützt die .NET Framework-Infrastruktur, die nicht für eine direkte Verwendung im Code vorgesehen ist.

## <a name="task-parameters"></a>Aufgabenparameter
 In der folgenden Tabelle werden die Parameter der `ResolveNativeReference` -Aufgabe beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|`AdditionalSearchPaths`|Erforderlicher <xref:System.String?displayProperty=fullName>`[]`-Parameter.<br /><br /> Ruft die Suchpfade zum Auflösen von Assemblyidentitäten systemeigener Verweise ab oder legt sie fest.|
|`ContainedComComponents`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Ausgabeparameter.<br /><br /> Ruft die COM-Komponenten der systemeigenen Assembly ab oder legt sie fest.|
|`ContainedLooseEtcFiles`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Ausgabeparameter.<br /><br /> Ruft die im systemeigenen Manifest aufgelisteten losen *ETC*-Dateien ab oder legt sie fest.|
|`ContainedLooseTlbFiles`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Ausgabeparameter.<br /><br /> Ruft die ungebundenen *TLB*-Dateien der systemeigenen Assembly ab oder legt sie fest.|
|`ContainedPrerequisiteAssemblies`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Ausgabeparameter.<br /><br /> Ruft die Assemblys ab oder legt diese fest, die vorliegen müssen, bevor das Manifest verwendet werden kann.|
|`ContainedTypeLibraries`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Ausgabeparameter.<br /><br /> Ruft die Typbibliotheken der systemeigenen Assembly ab oder legt sie fest.|
|`ContainingReferenceFiles`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Ausgabeparameter.<br /><br /> Ruft die Verweisdateien ab oder legt sie fest.|
|`NativeReferences`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter.<br /><br /> Ruft die systemeigenen Win32-Assemblyverweise ab oder legt diese fest.|

## <a name="remarks"></a>Anmerkungen
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension-Basisklasse](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Siehe auch
- [Aufgaben](../msbuild/msbuild-tasks.md)
- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)