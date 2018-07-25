---
title: WriteLinesToFile-Aufgabe | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#WriteLinesToFile
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- WriteLinesToFile task [MSBuild]
- MSBuild, WriteLinesToFile task
ms.assetid: 9c8862ac-8da5-4437-9430-ecc30421f1c9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 062270864c3fecb6556ef9b48d00177966a41859
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2018
ms.locfileid: "39233021"
---
# <a name="writelinestofile-task"></a>WriteLinesToFile-Aufgabe
Schreibt die Pfade der angegebenen Elemente in die angegebene Textdatei.  
  
## <a name="task-parameters"></a>Aufgabenparameter  
 In der folgenden Tabelle werden die Parameter der `WriteLinestoFile` -Aufgabe beschrieben.  
  
|Parameter|Beschreibung |  
|---------------|-----------------|  
|`File`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem> -Parameter.<br /><br /> Gibt die Datei an, in die Elemente geschrieben werden sollen|  
|`Lines`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter<br /><br /> Gibt die Elemente an, die in die Datei geschrieben werden sollen|  
|`Overwrite`|Optionaler `Boolean` -Parameter.<br /><br /> Wenn `true`, überschreibt die Aufgabe den vorhandenen Inhalt in der Datei|  
|`Encoding`|Optionaler `String` -Parameter.<br /><br /> Wählt die Zeichencodierung aus, z.B. „Unicode“  Siehe auch <xref:System.Text.Encoding>.|  
  
## <a name="remarks"></a>Hinweise  
 Wenn `Overwrite` `true` ist, wird eine neue Datei erstellt. Anschließend werden die Inhalte in die Datei geschrieben und diese wird geschlossen. Ist die Zieldatei bereits vorhanden, wird sie überschrieben. Wenn `Overwrite` `false` ist, wird der Inhalt an die Datei angefügt und die Zieldatei erstellt, wenn sie nicht bereits vorhanden ist.  
  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension-Basisklasse](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel verwendet die Aufgabe `WriteLinesToFile`, um Pfade der Elemente in der `MyItems`-Elementauflistung in die von der `MyTextFile`-Elementauflistung angegebene Datei zu schreiben.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyTextFile Include="Items.txt"/>  
        <MyItems Include="*.cs"/>  
    </ItemGroup>  
  
    <Target Name="WriteToFile">  
        <WriteLinesToFile  
            File="@(MyTextFile)"  
            Lines="@(MyItems)"  
            Overwrite="true"  
            Encoding="Unicode"/>  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Tasks (Aufgaben)](../msbuild/msbuild-tasks.md)   
 [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)