---
title: FormatVersion-Aufgabe | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 96e692f6-b581-46ca-8cc9-441a1861e371
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 29f9cae12a66e2b442d6c42032d3f4bf65942127
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/10/2018
ms.locfileid: "37946247"
---
# <a name="formatversion-task"></a>FormatVersion-Aufgabe
Fügt die Revisionsnummer an die Versionsnummer an.  
  
-   Fall 1: Input: Version=\<undefined>; Revision=\<don't care>; Output: OutputVersion="1.0.0.0"  
  
-   Fall 2: Input: Version="1.0.0.*" Revision="5" Output: OutputVersion="1.0.0.5"  
  
-   Fall 3: Input: Version="1.0.0.0" Revision=\<don't care>; Output: OutputVersion="1.0.0.0"  
  
## <a name="parameters"></a>Parameter  
 In der folgenden Tabelle werden die Parameter der `FormatVersion` -Aufgabe beschrieben.  
  
|Parameter|Beschreibung |  
|---------------|-----------------|  
|`FormatType`|Optionaler `String` -Parameter.<br /><br /> Gibt den Formattyp an<br /><br /> – "Version" = Version<br />– "Path" = "." durch "_" ersetzen|  
|`OutputVersion`|Optionaler `String`-Ausgabeparameter.<br /><br /> Gibt die Ausgabeversion an, die die Revisionsnummer beinhaltet|  
|`Revision`|Optionaler `Int32` -Parameter.<br /><br /> Gibt die Revision an, die an die Version angefügt werden soll|  
|`Version`|Optionaler `String` -Parameter.<br /><br /> Gibt die zu formatierende Versionsnummernzeichenfolge an|  
  
## <a name="remarks"></a>Hinweise  
 Zusätzlich zu den in der Tabelle aufgeführten Parametern erbt dieser Task Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension-Basisklasse](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Tasks (Aufgaben)](../msbuild/msbuild-tasks.md)   
 [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)