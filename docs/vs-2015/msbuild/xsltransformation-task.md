---
title: XslTransformation-Aufgabe | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, XslTransformation task
- XslTransformation task [MSBuild]
ms.assetid: 6f3a7d81-3ae3-4703-9a06-870b32b69d80
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 892ecb7f97be3d89a0f6e8104b0b55647a6fe63e
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2019
ms.locfileid: "54793131"
---
# <a name="xsltransformation-task"></a>XslTransformation-Aufgabe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Transformiert eine XML-Eingabe mithilfe von XSLT oder kompiliertem XSLT-Code und gibt an ein Ausgabegerät oder eine Ausgabedatei aus  
  
## <a name="parameters"></a>Parameter  
 In der folgenden Tabelle werden die Parameter der `XslTransformation` -Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|`OutputPaths`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter.<br /><br /> Gibt die Ausgabedateien für die XML-Transformation an|  
|`Parameters`|Optionaler `String` -Parameter.<br /><br /> Gibt die Parameter für das XSLT-Eingabedokument an|  
|`XmlContent`|Optionaler `String` -Parameter.<br /><br /> Gibt die XML-Eingabe als Zeichenfolge an|  
|`XmlInputPaths`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter<br /><br /> Gibt die XML-Eingabedateien an|  
|`XslCompiledDllPath`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem> -Parameter.<br /><br /> Gibt den kompilierten XSLT-Code an|  
|`XslContent`|Optionaler `String` -Parameter.<br /><br /> Gibt die XSLT-Eingabe als Zeichenfolge an|  
|`XslInputPath`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem> -Parameter.<br /><br /> Gibt die XSLT-Eingabedatei an|  
  
## <a name="remarks"></a>Anmerkungen  
 Zusätzlich zu den in der Tabelle aufgeführten Parametern erbt dieser Task Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Tasks (Aufgaben)](../msbuild/msbuild-tasks.md)   
 [Aufgabenreferenz](../msbuild/msbuild-task-reference.md)
