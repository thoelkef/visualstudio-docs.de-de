---
title: "RegisterAssembly Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#RegisterAssembly"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, RegisterAssembly task"
  - "RegisterAssembly task [MSBuild]"
ms.assetid: ba5f19ac-6764-4d28-9b79-a86de58f8987
caps.latest.revision: 16
caps.handback.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# RegisterAssembly Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Liest die Metadaten in der angegebenen Assembly und trägt die erforderlichen Einträge in die Registrierung ein, damit COM\-Clients [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]\-Klassen transparent erstellen können.  Das Verhalten dieser Aufgabe ist mit dem von [Regasm.exe \(Assembly Registration Tool\)](../Topic/Regasm.exe%20\(Assembly%20Registration%20Tool\).md) zu vergleichen, jedoch nicht identisch.  
  
## Parameter  
 In der folgenden Tabelle werden die Parameter der `RegisterAssembly`\-Aufgabe beschrieben.  
  
|Parameter|Description|  
|---------------|-----------------|  
|`Assemblies`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Parameter.<br /><br /> Gibt die in COM zu registrierenden Assemblys an.|  
|`AssemblyListFile`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>\-Parameter.<br /><br /> Enthält Informationen über den Zustand zwischen der `RegisterAssembly`\-Aufgabe und der [UnregisterAssembly](../msbuild/unregisterassembly-task.md)\-Aufgabe.  Dadurch wird verhindert, dass die `UnregisterAssembly`\-Aufgabe versucht, die Registrierung einer Assembly aufzuheben, die in der `RegisterAssembly`\-Aufgabe nicht registriert werden konnte.|  
|`CreateCodeBase`|Optionaler `Boolean`\-Parameter.<br /><br /> Wenn der Wert `true` lautet, wird in der Registrierung ein CodeBase\-Eintrag erstellt, der den Dateipfad einer nicht im globalen Assemblycache installierten Assembly angibt.  Die Option sollte nicht angegeben werden, wenn Sie die zu registrierende Assembly nachfolgend im globalen Assemblycache installieren.|  
|`TypeLibFiles`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Ausgabeparameter.<br /><br /> Gibt die Typbibliothek an, die aus der angegebenen Assembly generiert werden soll.  Die generierte Typbibliothek enthält Definitionen der innerhalb der Assembly definierten Typen, auf die zugegriffen werden kann.  Die Typbibliothek wird nur generiert, wenn eine der folgenden Voraussetzungen erfüllt ist:<br /><br /> -   Es ist keine Typbibliothek dieses Namens an diesem Speicherort vorhanden.<br />-   Es ist eine Typbibliothek vorhanden, die jedoch älter ist als die übergebene Assembly.<br /><br /> Wenn die Typbibliothek neuer ist als die übergebene Assembly, wird keine neue Typbibliothek erstellt, die Assembly wird jedoch trotzdem registriert.<br /><br /> Wenn dieser Parameter angegeben wird, muss er dieselbe Anzahl an Elementen aufweisen wie der `Assemblies`\-Parameter. Andernfalls schlägt die Aufgabe fehl.  Werden keine Eingaben angegeben, verwendet die Aufgabe standardmäßig den Namen der Assembly und ändert die Erweiterung des Elements in .tlb.|  
  
## Hinweise  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>\-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>\-Klasse erbt.  Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Beispiel  
 Im folgenden Beispiel wird die `RegisterAssembly`\-Aufgabe verwendet, um die von der `MyAssemblies`\-Elementauflistung angegebene Assembly zu registrieren.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyAssemblies Include="MyAssembly.dll" />  
    <ItemGroup>  
  
    <Target Name="RegisterAssemblies">  
        <RegisterAssembly  
            Assemblies="@(MyAssemblies)" >  
    </Target>  
  
</Project>  
```  
  
## Siehe auch  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)