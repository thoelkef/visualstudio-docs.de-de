---
title: UsingTask-Element (MSBuild) | Microsoft-Dokumentation
ms.custom: 
ms.date: 03/13/2017
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#UsingTask
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- UsingTask element [MSBuild]
- <UsingTask> element [MSBuild]
ms.assetid: 20247902-9446-4a1f-8253-5c7a17e4fe43
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 79d87029365d5e527f886dc3c86ff260a0cbb612
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="usingtask-element-msbuild"></a>UsingTask-Element (MSBuild)
Ordnet den in einem [Task](../msbuild/task-element-msbuild.md)-Element referenzierten Task der Assembly zu, die die Taskimplementierung enthält.  

 \<Project>  
 \<UsingTask>  

## <a name="syntax"></a>Syntax  

```  
<UsingTask TaskName="TaskName"  
    AssemblyName = "AssemblyName"   
    TaskFactory = "ClassName"  
    Condition="'String A'=='String B'" />  
```  

## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  

### <a name="attributes"></a>Attribute  

|Attribut|Beschreibung|  
|---------------|-----------------|  
|`AssemblyName`|Entweder ist das Attribut `AssemblyName` oder das Attribut `AssemblyFile` erforderlich.<br /><br /> Der Namen zu ladenden Assembly. Das Attribut `AssemblyName` akzeptiert Assemblys mit sicheren Namen, auch wenn sichere Namen nicht erforderlich sind. Die Verwendung dieses Attributs entspricht dem Laden einer Assembly mit der <xref:System.Reflection.Assembly.Load%2A>-Methode in .NET.<br /><br /> Sie können dieses Attribut nicht verwenden, wenn das `AssemblyFile`-Attribut verwendet wird.|  
|`AssemblyFile`|Entweder ist das Attribut `AssemblyName` oder das Attribut `AssemblyFile` erforderlich.<br /><br /> Der Dateipfad der Assemblydatei. Dieses Attribut akzeptiert vollständige oder relative Pfade. Relative Pfade sind relativ zum Verzeichnis der Projektdatei oder Zieldatei, in dem das `UsingTask`-Element deklariert ist. Die Verwendung dieses Attributs entspricht dem Laden einer Assembly mit der <xref:System.Reflection.Assembly.LoadFrom%2A>-Methode in .NET.<br /><br /> Sie können dieses Attribut nicht verwenden, wenn das `AssemblyName`-Attribut verwendet wird.|  
|`TaskFactory`|Optionales Attribut.<br /><br /> Gibt die Klasse in der Assembly an, die für das Generieren von Instanzen des angegebenen `Task`-Namens verantwortlich ist.  Der Benutzer kann auch `TaskBody` als ein untergeordnetes Element angeben, welches durch die Aufgabenfactory empfangen und zum Generieren der Aufgabe verwendet wird. Der Inhalt von `TaskBody` ist für die Aufgabenfactory spezifisch.|  
|`TaskName`|Erforderliches Attribut.<br /><br /> Der Name der aus einer Assembly zu referenzierenden Aufgabe. Wenn Mehrdeutigkeiten möglich sind, sollte dieses Attribut immer vollständige Namespaces angeben. Wenn Mehrdeutigkeiten vorliegen, wählt MSBuild eine willkürliche Übereinstimmung auf, die zu unerwarteten Ergebnissen führen kann.|  
|`Condition`|Optionales Attribut.<br /><br /> Die auszuwertende Bedingung. Weitere Informationen finden Sie unter [Conditions](../msbuild/msbuild-conditions.md) (MSBuild-Bedingungen).|  

### <a name="child-elements"></a>Untergeordnete Elemente  

|Element|description|  
|-------------|-----------------|  
|[ParameterGroup](../msbuild/parametergroup-element.md)|Der Satz an Parametern, die in der Aufgabe angezeigt werden, welche durch die angegebene `TaskFactory` generiert wurde.|  
|[Aufgabe](../msbuild/task-element-msbuild.md)|Die `TaskFactory` weitergegebenen Daten zum Generieren einer Instanz der Aufgabe.|  

### <a name="parent-elements"></a>Übergeordnete Elemente  

|Element|description|  
|-------------|-----------------|  
|[Projekt](../msbuild/project-element-msbuild.md)|Erforderliches Stammelement einer [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] -Projektdatei.|  

## <a name="remarks"></a>Hinweise  
 Umgebungsvariablen, Befehlszeileneigenschaften und Eigenschaften auf Projektebene können im gesamten `UsingTask`-Element referenziert werden, wenn es in der Projektdatei angezeigt wird, und zwar entweder explizit oder mithilfe einer importierten Projektdatei. Weitere Informationen finden Sie unter [Tasks](../msbuild/msbuild-tasks.md) (MSBuild-Aufgaben).  

> [!NOTE]
>  Eigenschaften auf Projektebene haben keine Bedeutung, wenn das `UsingTask`-Element aus einer der TASKS-Dateien stammt, die global im MSBuild-Modul registriert sind. Eigenschaften auf Projektebene sind nicht global in MSBuild.  

 In MSBuild 4.0 kann das Laden mithilfe von Aufgaben aus .overridetask-Dateien erfolgen.  

## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Verwendung des Elements `UsingTask` mit dem Attribut `AssemblyName` gezeigt.  

```xml  
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">  
       <ParameterGroup>  
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>  
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>  
              ...  
</ParameterGroup>  
       <TaskBody>  
      ... Task factory-specific data ...  
       </TaskBody>  
</UsingTask>  
```  

## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Verwendung des Elements `UsingTask` mit dem Attribut `AssemblyFile` gezeigt.  

```xml  
<UsingTask TaskName="Email"  
              AssemblyFile="c:\myTasks\myTask.dll" />  
```  

## <a name="see-also"></a>Siehe auch  
 [Tasks (Aufgaben)](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)  (MSBuild-Aufgabenreferenz)  
 [Referenz zum MSBuild-Projektdateischema](../msbuild/msbuild-project-file-schema-reference.md)
