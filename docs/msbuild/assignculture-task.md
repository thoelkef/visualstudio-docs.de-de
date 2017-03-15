---
title: "AssignCulture Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#AssignCulture"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, AssignCulture task"
  - "AssignCulture task [MSBuild]"
ms.assetid: 8f8314cc-82a6-4f16-a62d-b9f0d1d5e274
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# AssignCulture Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diese Aufgabe akzeptiert eine Liste von Elementen, die möglicherweise im Dateinamen eine gültige Zeichenfolge für den .NET\-Kulturbezeichner enthalten, und erzeugt Elemente, die Metadaten mit dem Namen `Culture` aufweisen, in denen der entsprechende Kulturbezeichner enthalten ist.  In den Dateinamen Form1.fr\-fr.resx beispielsweise ist der Kulturbezeichner "fr\-fr" eingebettet. Daher erzeugt diese Aufgabe ein Element, das denselben Dateinamen sowie die Metadaten `Culture` mit der Angabe `fr-fr` aufweist.  Zudem erzeugt die Aufgabe eine Liste mit Dateinamen, aus denen der Kulturbezeichner entfernt wurde.  
  
## Aufgabenparameter  
 In der folgenden Tabelle werden die Parameter der `AssignCulture`\-Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|------------------|  
|`AssignedFiles`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Ausgabeparameter.<br /><br /> Enthält die im `Files`\-Parameter empfangene Liste von Elementen, denen jeweils ein `Culture`\-Metadateneintrag hinzugefügt wurde.<br /><br /> Wenn das eingehende Element aus dem `Files`\-Parameter bereits einen `Culture`\-Metadateneintrag enthält, wird dieser ursprüngliche Metadateneintrag verwendet.<br /><br /> Die Aufgabe weist nur dann einen `Culture`\-Metadateneintrag zu, wenn der Dateiname einen gültigen Kulturbezeichner enthält.  Der Kulturbezeichner muss sich zwischen den letzten beiden Punkten im Dateinamen befinden.|  
|`AssignedFilesWithCulture`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Ausgabeparameter.<br /><br /> Enthält die Teilmenge der Elemente aus dem `AssignedFiles`\-Parameter, die einen `Culture`\-Metadateneintrag aufweisen.|  
|`AssignedFilesWithNoCulture`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Ausgabeparameter.<br /><br /> Enthält die Teilmenge der Elemente aus dem `AssignedFiles`\-Parameter, die keinen `Culture`\-Metadateneintrag aufweisen.|  
|`CultureNeutralAssignedFiles`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Ausgabeparameter.<br /><br /> Enthält dieselbe Liste von Elementen, die auch im `AssignedFiles`\-Parameter erzeugt wird, allerdings wird hier der Kulturbezeichner aus dem Dateinamen entfernt.<br /><br /> Die Aufgabe entfernt den Kulturbezeichner nur dann aus dem Dateinamen, wenn es sich um einen gültigen Kulturbezeichner handelt.|  
|`Files`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Parameter.<br /><br /> Gibt die Liste der Dateien mit eingebetteten Kulturnamen an, denen eine Kultur zugewiesen werden soll.|  
  
## Hinweise  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>\-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>\-Klasse erbt.  Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Beispiel  
 Im folgenden Beispiel wird die `AssignCulture`\-Aufgabe für die `ResourceFiles`\-Elementauflistung ausgeführt.  
  
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
  
 In der folgenden Tabelle wird der Wert der Ausgabeelemente nach der Ausführung der Aufgabe beschrieben.  Elementmetadaten werden in Klammern nach dem Element angezeigt.  
  
|Elementauflistung|Inhalt|  
|-----------------------|------------|  
|`OutAssignedFiles`|`MyResource1.fr.resx (Culture="fr")`<br /><br /> `MyResource2.XX.resx` \(keine zusätzlichen Metadaten\)|  
|`OutAssignedFilesWithCulture`|`MyResource1.fr.resx (Culture="fr")`|  
|`OutAssignedFilesWithNoCulture`|`MyResource2.XX.resx` \(keine zusätzlichen Metadaten\)|  
|`OutCultureNeutralAssignedFiles`|`MyResource1.resx (Culture="fr")`<br /><br /> `MyResource2.XX.resx (`keine zusätzlichen Metadaten\)|  
  
## Siehe auch  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)