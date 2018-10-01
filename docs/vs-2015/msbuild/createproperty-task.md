---
title: CreateProperty-Aufgabe | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#CreateProperty
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- CreateProperty task [MSBuild]
- MSBuild, CreateProperty task
ms.assetid: fbc31a88-62d4-43d2-b739-68ef3fac38f5
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 961f034f2bb508175d258259097f3be25e2a0b11
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47522895"
---
# <a name="createproperty-task"></a>CreateProperty-Aufgabe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [CreateProperty-Aufgabe](https://docs.microsoft.com/visualstudio/msbuild/createproperty-task).  
  
  
Füllt Eigenschaften mit den übergebenen Werten auf. Dadurch können Werte aus einer Eigenschaft oder Zeichenfolge in eine andere kopiert werden.  
  
## <a name="attributes"></a>Attribute  
 In der folgenden Tabelle werden die Parameter der `CreateProperty` -Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|`Value`|Optionaler `String`-Ausgabeparameter.<br /><br /> Gibt den Wert an, der in die neue Eigenschaft kopiert werden soll|  
|`ValueSetByTask`|Optionaler `String`-Ausgabeparameter.<br /><br /> Enthält denselben Wert wie der `Value`-Parameter. Verwenden Sie diesen Parameter nur, wenn die Ausgabeeigenschaft nicht von [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] festgelegt werden soll, wenn es das umschließende Ziel überspringt, weil die Ausgaben auf dem neuesten Stand sind.|  
  
## <a name="remarks"></a>Hinweise  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die `NewFile`-Eigenschaft mit der `CreateProperty`-Aufgabe und der Kombination der Werte der Eigenschaften `SourceFilename` und `SourceFileExtension` erstellt.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <PropertyGroup>  
        <SourceFilename>Module1</SourceFilename>  
        <SourceFileExtension>vb</SourceFileExtension>  
    </PropertyGroup>  
  
    <Target Name="CreateProperties">  
  
        <CreateProperty  
            Value="$(SourceFilename).$(SourceFileExtension)">  
            <Output  
                TaskParameter="Value"  
                PropertyName="NewFile" />  
        </CreateProperty>  
  
    </Target>  
  
</Project>  
```  
  
 Nach dem Ausführen des Projekts, ist der Wert der `NewFile`-Eigenschaft `Module1.vb`.  
  
## <a name="see-also"></a>Siehe auch  
 [Task Reference](../msbuild/msbuild-task-reference.md)  (MSBuild-Aufgabenreferenz)  
 [Tasks (Aufgaben)](../msbuild/msbuild-tasks.md)



