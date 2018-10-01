---
title: AssignCulture-Aufgabe | Microsoft-Dokumentation
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
- http://schemas.microsoft.com/developer/msbuild/2003#AssignCulture
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, AssignCulture task
- AssignCulture task [MSBuild]
ms.assetid: 8f8314cc-82a6-4f16-a62d-b9f0d1d5e274
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8ee44937f48101454a00128405fb03ce4260de4a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47510900"
---
# <a name="assignculture-task"></a>AssignCulture-Aufgabe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [AssignCulture-Aufgabe](https://docs.microsoft.com/visualstudio/msbuild/assignculture-task).  
  
  
Diese Aufgabe akzeptiert eine Liste von Elementen, die eine gültige .NET-Kulturbezeichnerzeichenfolge als Teil des Dateinamens enthalten kann, und erzeugt Elemente, die Metadaten mit dem Namen `Culture` aufweisen, die die entsprechenden Kulturbezeichner enthalten. Der Dateiname „Form1.fr-fr.resx“ enthält beispielsweise den eingebetteten Kulturbezeichner „fr-fr“, damit diese Aufgabe ein Element erstellt, das den gleichen Dateinamen mit Metadaten aufweist, bei denen `Culture` gleich `fr-fr` ist. Die Aufgabe erstellt auch eine Liste von Dateinamen ohne Kultur.  
  
## <a name="task-parameters"></a>Aufgabenparameter  
 In der folgenden Tabelle werden die Parameter der `AssignCulture`-Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|`AssignedFiles`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Ausgabeparameter.<br /><br /> Enthält die Liste der Elemente, die innerhalb des `Files`-Parameters empfangen wurden, mit einem `Culture`-Metadateneintrag, der jedem Element hinzugefügt wurde.<br /><br /> Wenn das eingehende Element vom `Files`-Parameter bereits einen `Culture`-Metadateneintrag enthält, wird der ursprüngliche Metadateneintrag verwendet.<br /><br /> Die Aufgabe weist nur dann einen `Culture`-Metadateneintrag zu, wenn der Dateiname einen gültigen Kulturbezeichner enthält. Der Kulturbezeichner muss zwischen den letzten beiden Punkten im Dateinamen platziert werden.|  
|`AssignedFilesWithCulture`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Ausgabeparameter.<br /><br /> Enthält die Teilmenge der Elemente aus dem `AssignedFiles`-Parameter mit `Culture`-Metadateneintrag|  
|`AssignedFilesWithNoCulture`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Ausgabeparameter.<br /><br /> Enthält die Teilmenge der Elemente aus dem `AssignedFiles`-Parameter ohne `Culture`-Metadateneintrag|  
|`CultureNeutralAssignedFiles`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Ausgabeparameter.<br /><br /> Enthält dieselben Elemente, die im `AssignedFiles`-Parameter erzeugt werden. Der einzige Unterschied ist, dass die Kultur aus dem Dateinamen entfernt wurde.<br /><br /> Die Aufgabe entfernt nur die Kultur aus dem Dateinamen, wenn der Kulturbezeichner gültig ist.|  
|`Files`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter.<br /><br /> Gibt die Liste der Dateien mit eingebetteten Kulturnamen an, denen eine Kultur zugewiesen werden soll|  
  
## <a name="remarks"></a>Hinweise  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die `AssignCulture`-Aufgabe mit der `ResourceFiles`-Elementauflistung ausgeführt.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <ResourceFiles Include="MyResource1.fr.resx"/>  
        <ResourceFiles Include="MyResource2.XX.resx"/>  
    </ItemGroup>  
  
    <Target Name="Culture">  
        <AssignCulture  
            Files="@(ResourceFiles)"  
            <Output TaskParameter="AssignedFiles"  
                ItemName="OutAssignedFiles"/>  
            <Output TaskParameter="AssignedFilesWithCulture"  
                ItemName="OutAssignedFilesWithCulture"/>  
            <Output TaskParameter="AssignedFilesWithNoCulture"  
                ItemName="OutAssignedFilesWithNoCulture"/>  
            <Output TaskParameter="CultureNeutralAssignedFiles"  
                ItemName="OutCultureNeutralAssignedFiles"/>  
        </AssignCulture>  
    </Target>  
</Project>  
```  
  
 In der folgenden Tabelle wird der Wert der Ausgabeelemente nach der Ausführung der Aufgabe beschrieben. Elementmetadaten werden in Klammern nach dem Element angezeigt.  
  
|Elementauflistung|Inhalt|  
|---------------------|--------------|  
|`OutAssignedFiles`|`MyResource1.fr.resx (Culture="fr")`<br /><br /> `MyResource2.XX.resx` (keine zusätzlichen Metadaten)|  
|`OutAssignedFilesWithCulture`|`MyResource1.fr.resx (Culture="fr")`|  
|`OutAssignedFilesWithNoCulture`|`MyResource2.XX.resx` (keine zusätzlichen Metadaten)|  
|`OutCultureNeutralAssignedFiles`|`MyResource1.resx (Culture="fr")`<br /><br /> `MyResource2.XX.resx (`keine zusätzlichen Metadaten)|  
  
## <a name="see-also"></a>Siehe auch  
 [Tasks (Aufgaben)](../msbuild/msbuild-tasks.md)   
 [Aufgabenreferenz](../msbuild/msbuild-task-reference.md)



