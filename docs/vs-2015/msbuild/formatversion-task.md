---
title: FormatVersion-Aufgabe | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 96e692f6-b581-46ca-8cc9-441a1861e371
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ee6e163bd6587d93c970a56ac1c08383084ddc0c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149615"
---
# <a name="formatversion-task"></a>FormatVersion-Aufgabe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Fügt die Revisionsnummer an die Versionsnummer an.  
  
- Groß-/Kleinschreibung #1: Eingabe: Version = \<undefined> ;  Revision = \<don't care> ;   Ausgabe: OutputVersion = "1.0.0.0"  
  
- Fall 2: Input: Version="1.0.0.*" Revision="5" Output: OutputVersion="1.0.0.5"  
  
- Case #3: Input: Version = "1.0.0.0" Revision = \<don't care> ;  Ausgabe: OutputVersion = "1.0.0.0"  
  
## <a name="parameters"></a>Parameter  
 In der folgenden Tabelle werden die Parameter der `FormatVersion`-Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|`FormatType`|Optionaler `String`-Parameter.<br /><br /> Gibt den Formattyp an<br /><br /> – "Version" = Version<br />– "Path" = "." durch "_" ersetzen|  
|`OutputVersion`|Optionaler `String`-Ausgabeparameter.<br /><br /> Gibt die Ausgabeversion an, die die Revisionsnummer beinhaltet|  
|`Revision`|Optionaler `Int32`-Parameter.<br /><br /> Gibt die Revision an, die an die Version angefügt werden soll|  
|`Version`|Optionaler `String`-Parameter.<br /><br /> Gibt die zu formatierende Versionsnummernzeichenfolge an|  
  
## <a name="remarks"></a>Bemerkungen  
 Zusätzlich zu den in der Tabelle aufgeführten Parametern erbt dieser Task Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension-Basisklasse](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erfüllen](../msbuild/msbuild-tasks.md)   
 [Aufgaben Referenz](../msbuild/msbuild-task-reference.md)
