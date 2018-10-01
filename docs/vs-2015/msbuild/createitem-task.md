---
title: CreateItem-Aufgabe | Microsoft-Dokumentation
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
- http://schemas.microsoft.com/developer/msbuild/2003#CreateItem
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- CreateItem task [MSBuild]
- MSBuild, CreateItem task
ms.assetid: c4311f38-979e-4324-b524-9e8c1cbdc41a
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dae25b1a187c446e1076d709e3dc8f7a7d6a82a1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47512534"
---
# <a name="createitem-task"></a>CreateItem-Aufgabe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [CreateItem-Aufgabe](https://docs.microsoft.com/visualstudio/msbuild/createitem-task).  
  
  
Füllt Elementauflistungen mit den Eingabeelementen aus. Dadurch können Elemente aus einer Liste in eine andere kopiert werden.  
  
> [!NOTE]
>  Diese Aufgabe ist veraltet. Seit .NET Framework 3.5 können Elementgruppen innerhalb von [Ziel](../msbuild/target-element-msbuild.md)-Elementen platziert werden. Weitere Informationen finden Sie unter [Elemente](../msbuild/msbuild-items.md).  
  
## <a name="attributes"></a>Attribute  
 In der folgenden Tabelle werden die Parameter der `CreateItem` -Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|`AdditionalMetadata`|Optionaler `String`-Arrayparameter.<br /><br /> Gibt zusätzliche Metadaten an, die an die Ausgabeelemente angefügt werden sollen.  Geben Sie den Metadatennamen und -wert für das Element mit der folgenden Syntax an:<br /><br /> *MetadatenName* `=` *MetadatenWert*<br /><br /> Mehrere Metadaten-Name/Wert-Paare sollten mit einem Semikolon getrennt werden. Wenn entweder der Name oder der Wert ein Semikolon oder andere Sonderzeichen enthält, müssen sie mit einem Escapezeichen versehen werden. Weitere Informationen finden Sie unter [Vorgehensweise: Escapesonderzeichen in MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md).|  
|`Exclude`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Ausgabeparameter.<br /><br /> Gibt die Elemente an, die aus der Ausgabeelementauflistung ausgeschlossen werden sollen. Dieser Parameter kann Platzhalter enthalten. Weitere Informationen finden Sie unter [Elemente](../msbuild/msbuild-items.md) und [Vorgehensweise: Ausschließen von Dateien vom Buildvorgang](../msbuild/how-to-exclude-files-from-the-build.md).|  
|`Include`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>-`[]`-Parameter<br /><br /> Gibt die Elemente an, die in die Ausgabeelementauflistung einbezogen werden sollen. Dieser Parameter kann Platzhalter enthalten.|  
|`PreserveExistingMetadata`|Optionaler `Boolean` -Parameter.<br /><br /> Bei `True` gelten nur die zusätzlichen Metadaten, wenn sie nicht bereits vorhanden sind.|  
  
## <a name="remarks"></a>Hinweise  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel wird eine neue Elementauflistung namens `MySourceItemsWithMetadata` aus der Elementauflistung `MySourceItems` erstellt. Die `CreateItem`-Aufgabe füllt die neuen Elementauflistungen mit den Elementen im `MySourceItems`-Element auf. Anschließend fügt es jedem Element in der neuen Sammlung einen zusätzlichen Metadateneintrag namens `MyMetadata` mit dem Wert `Hello` hinzu.  
  
 Nachdem die Aufgabe ausgeführt wurde, enthält die `MySourceItemsWithMetadata`-Elementauflistung die Elemente `file1.resx` und `file2.resx`, und beide verfügen über Metadateneinträge für `MyMetadata`. Die `MySourceItems`-Elementauflistung bleibt unverändert.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MySourceItems Include="file1.resx;file2.resx" />  
    </ItemGroup>  
  
    <Target Name="NewItems">  
        <CreateItem  
            Include="@(MySourceItems)"  
            AdditionalMetadata="MyMetadata=Hello">  
           <Output  
               TaskParameter="Include"  
               ItemName="MySourceItemsWithMetadata"/>  
        </CreateItem>  
  
    </Target>  
  
</Project>  
```  
  
 In der folgenden Tabelle wird der Wert des Ausgabeelements nach der Ausführung der Aufgabe beschrieben. Elementmetadaten werden in Klammern nach dem Element angezeigt.  
  
|Elementauflistung|Inhalt|  
|---------------------|--------------|  
|`MySourceItemsWithMetadata`|`file1.resx` (`MyMetadata="Hello"`)<br /><br /> `file2.resx` (`MyMetadata="Hello"`)|  
  
## <a name="see-also"></a>Siehe auch  
 [Task Reference](../msbuild/msbuild-task-reference.md)  (MSBuild-Aufgabenreferenz)  
 [Tasks (Aufgaben)](../msbuild/msbuild-tasks.md)



