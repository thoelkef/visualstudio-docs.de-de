---
title: XmlPeek-Aufgabe | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- XmlPeek task [MSBuild]
- MSBuild, XmlPeek task
ms.assetid: 19196031-a3bc-41b5-9c4a-f2572630e179
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 214320724d7bcda2c126d577deabda20a61c6104
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53865912"
---
# <a name="xmlpeek-task"></a>XmlPeek-Aufgabe
Gibt die Werte wie von der XPath-Abfrage angegeben aus einer XML-Datei zurück  
  
## <a name="parameters"></a>Parameter  
 In der folgenden Tabelle werden die Parameter der `XmlPeek` -Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|`Namespaces`|Optionaler `String` -Parameter.<br /><br /> Gibt die Namespaces für die Präfixe der XPath-Abfrage an|  
|`Query`|Optionaler `String` -Parameter.<br /><br /> Gibt die XPath-Abfrage an|  
|`Result`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Ausgabeparameter.<br /><br /> Enthält die Ergebnisse, die von dieser Aufgabe zurückgegeben werden|  
|`XmlContent`|Optionaler `String` -Parameter.<br /><br /> Gibt die XML-Eingabe als Zeichenfolge an|  
|`XmlInputPath`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem> -Parameter.<br /><br /> Gibt die XML-Eingabe als Dateipfad an|  
  
## <a name="remarks"></a>Hinweise  
 Zusätzlich zu den in der Tabelle aufgeführten Parametern erbt dieser Task Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension-Basisklasse](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Tasks (Aufgaben)](../msbuild/msbuild-tasks.md)   
 [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)