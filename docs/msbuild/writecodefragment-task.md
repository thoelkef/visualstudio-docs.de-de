---
title: WriteCodeFragment-Aufgabe | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, WriteCodeFragment task
- WriteCodeFragment task [MSBuild]
ms.assetid: 1d2514b4-5bef-43bb-bebe-496da8ef063c
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 6d08d4499ba0fcdc044b7189abeb9de1716b7ba4
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="writecodefragment-task"></a>WriteCodeFragment-Aufgabe
Generiert eine temporäre Codedatei aus dem angegebenen generierten Codefragment. Die Datei wird nicht gelöscht.  
  
## <a name="parameters"></a>Parameter  
 In der folgenden Tabelle werden die Parameter der `WriteCodeFragment` -Aufgabe beschrieben.  
  
|Parameter|description|  
|---------------|-----------------|  
|`AssemblyAttributes`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter<br /><br /> Beschreibung der Attribute, die geschrieben werden sollen. Der Wert des Elements `Include` ist der vollständige Typname des Attributs, z.B. „System.AssemblyVersionAttribute“.<br /><br /> Jeder Metadatentyp stellt das Name/Wert-Paar eines Parameters dar, der dem Typ `String` entsprechen muss. Einige Attribute lassen nur positionelle Konstruktorargumente zu. Sie können solche Argumente allerdings in jedem Attribut verwenden. Um positionelle Konstruktorattribute festzulegen, verwenden Sie Metadatennamen, die „_Parameter1“, „_Parameter2“ usw. ähneln.<br /><br /> Ein Parameterindex kann nicht übersprungen werden.|  
|`Language`|Erforderlicher `String` -Parameter.<br /><br /> Gibt die Programmiersprache des zu generierenden Codes an.<br /><br /> `Language` kann jede Sprache sein, für die ein CodeDom-Anbieter verfügbar ist. Dies ist z.B. für „C#“ oder „VisualBasic“ der Fall. Die ausgegebene Datei verfügt dann über das standardmäßige Suffix für diese Sprache.|  
|`OutputDirectory`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem> -Parameter.<br /><br /> Gibt den Zielordner für den generierten Code an. In der Regel ist dies der Zwischenordner.|  
|`OutputFile`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>-Ausgabeparameter.<br /><br /> Gibt den Pfad der Datei an, die generiert wurde. Wenn dieser Parameter mithilfe eines Dateinamens festgelegt wird, wird dem Dateinamen der Zielordner vorangestellt. Wenn er mit einem Stamm festgelegt wird, wird der Zielordner ignoriert.<br /><br /> Wenn dieser Parameter nicht festgelegt wird, ist der Name der Ausgabedatei der Zielordner, eine willkürliche Datei und das standardmäßige Suffix für die angegebene Sprache.|  
  
## <a name="remarks"></a>Hinweise  
 Zusätzlich zu den in der Tabelle aufgeführten Parametern erbt dieser Task Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Tasks (Aufgaben)](../msbuild/msbuild-tasks.md)   
 [Aufgabenreferenz](../msbuild/msbuild-task-reference.md)