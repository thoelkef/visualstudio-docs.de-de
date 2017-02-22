---
title: "CreateItem Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#CreateItem"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "CreateItem task [MSBuild]"
  - "MSBuild, CreateItem task"
ms.assetid: c4311f38-979e-4324-b524-9e8c1cbdc41a
caps.latest.revision: 15
caps.handback.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# CreateItem Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Füllt Elementauflistungen mit Eingabeelementen auf.  Auf diese Weise können Elemente aus einer Liste in eine andere kopiert werden.  
  
> [!NOTE]
>  Diese Aufgabe ist veraltet.  Ab .NET Framework 3.5 können Elementgruppen in [Zielelemente](../msbuild/target-element-msbuild.md) platziert werden.  Weitere Informationen finden Sie unter [Items](../msbuild/msbuild-items.md).  
  
## Attribute  
 In der folgenden Tabelle werden die Parameter der `CreateItem`\-Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|------------------|  
|`AdditionalMetadata`|Optionale `String`\-Arrayparameter.<br /><br /> Gibt zusätzliche Metadaten an, die an die Ausgabeelemente angefügt werden sollen.  Geben Sie den Metadatennamen und \-wert für das Element mit der folgenden Syntax an:<br /><br /> *Metadatenname* `=` *Metadatenwert*<br /><br /> Mehrere Metadatenname\/Wert\-Paare müssen durch Semikolons voneinander getrennt werden.  Semikolons oder andere Sonderzeichen in einem Namen oder Wert müssen mit Escapezeichen versehen werden.  Weitere Informationen finden Sie unter [How to: Escape Special Characters in MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md).|  
|`Exclude`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Ausgabeparameter.<br /><br /> Gibt die Elemente an, die aus der Ausgabeelementauflistung ausgeschlossen werden sollen.  Dieser Parameter kann Platzhalter enthalten.  Weitere Informationen finden Sie unter [Items](../msbuild/msbuild-items.md) und [How to: Exclude Files from the Build](../msbuild/how-to-exclude-files-from-the-build.md).|  
|`Include`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Parameter.<br /><br /> Gibt die Elemente an, die in die Ausgabeelementauflistung eingeschlossen werden sollen.  Dieser Parameter kann Platzhalter enthalten.|  
|`PreserveExistingMetadata`|Optionaler `Boolean`\-Parameter.<br /><br /> Bei `True` werden nur die zusätzliche Metadaten angewendet, wenn sie nicht bereits vorhanden sind.|  
  
## Hinweise  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>\-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>\-Klasse erbt.  Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Beispiel  
 Im folgenden Codebeispiel wird auf Grundlage der Elementauflistung `MySourceItems` eine neue Elementauflistung mit dem Namen `MySourceItemsWithMetadata` erstellt.  Die neue Elementsammlung wird von der `CreateItem`\-Aufgabe mit den neuen Elementen im `MySourceItems`\-Element ausgefüllt.  Anschließend wird jedem Element in der neuen Auflistung ein zusätzlicher Metadateneintrag mit dem Namen `MyMetadata` und dem Wert `Hello` hinzugefügt.  
  
 Nach der Ausführung der Aufgabe enthält die `MySourceItemsWithMetadata`\-Elementauflistung die Elemente `file1.resx` und `file2.resx`, die jeweils Metadateneinträge für `MyMetadata` enthalten.  Die `MySourceItems`\-Elementauflistung ist unverändert.  
  
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
  
 In der folgenden Tabelle wird der Wert des Ausgabeelements nach der Ausführung der Aufgabe beschrieben.  Elementmetadaten werden in Klammern nach dem Element angezeigt.  
  
|Elementauflistung|Inhalt|  
|-----------------------|------------|  
|`MySourceItemsWithMetadata`|`file1.resx` \(`MyMetadata="Hello"`\)<br /><br /> `file2.resx` \(`MyMetadata="Hello"`\)|  
  
## Siehe auch  
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [Tasks](../msbuild/msbuild-tasks.md)