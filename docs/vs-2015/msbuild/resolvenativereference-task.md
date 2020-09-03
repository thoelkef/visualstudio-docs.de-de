---
title: ResolveNativeReference-Task | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 137ab6c54176c7c95c13c4b3e4defb3924937bc7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205638"
---
# <a name="resolvenativereference-task"></a>ResolveNativeReference-Aufgabe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Löst native Verweise auf. Implementiert die <xref:Microsoft.Build.Tasks.ResolveNativeReference>-Klasse. Diese Klasse unterstützt die .NET Framework-Infrastruktur, die nicht für eine direkte Verwendung im Code vorgesehen ist.  
  
## <a name="task-parameters"></a>Aufgabenparameter  
 In der folgenden Tabelle werden die Parameter der `ResolveNativeReference`-Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|`AdditionalSearchPaths`|Erforderlich [Zeichenfolge] (<!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  -->)`[]`-Parameter.<br /><br /> Ruft die Suchpfade zum Auflösen von Assemblyidentitäten systemeigener Verweise ab oder legt sie fest.|  
|`ContainedComComponents`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Ausgabeparameter.<br /><br /> Ruft die COM-Komponenten der systemeigenen Assembly ab oder legt sie fest.|  
|`ContainedLooseEtcFiles`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Ausgabeparameter.<br /><br /> Ruft die im systemeigenen Manifest aufgelisteten losen ETC-Dateien ab oder legt sie fest.|  
|`ContainedLooseTlbFiles`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Ausgabeparameter.<br /><br /> Ruft die ungebundenen TLB-Dateien der systemeigenen Assembly ab oder legt sie fest.|  
|`ContainedPrerequisiteAssemblies`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Ausgabeparameter.<br /><br /> Ruft die Assemblys ab oder legt diese fest, die vorliegen müssen, bevor das Manifest verwendet werden kann.|  
|`ContainedTypeLibraries`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Ausgabeparameter.<br /><br /> Ruft die Typbibliotheken der systemeigenen Assembly ab oder legt sie fest.|  
|`ContainingReferenceFiles`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Ausgabeparameter.<br /><br /> Ruft die Verweisdateien ab oder legt sie fest.|  
|`NativeReferences`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter.<br /><br /> Ruft die systemeigenen Win32-Assemblyverweise ab oder legt diese fest.|  
  
## <a name="remarks"></a>Hinweise  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension-Basisklasse](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erfüllen](../msbuild/msbuild-tasks.md)   
 [Aufgaben Referenz](../msbuild/msbuild-task-reference.md)
