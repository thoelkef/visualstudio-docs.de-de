---
title: "UsingTask Element (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#UsingTask"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "UsingTask element [MSBuild]"
  - "<UsingTask> element [MSBuild]"
ms.assetid: 20247902-9446-4a1f-8253-5c7a17e4fe43
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# UsingTask Element (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ordnet die in einem [Task](../msbuild/task-element-msbuild.md)\-Element referenzierte Aufgabe der Assembly zu, die die Aufgabenimplementierung enthält.  
  
## Syntax  
  
```  
<UsingTask TaskName="TaskName"  
    AssemblyName = "AssemblyName"   
    TaskFactory = "ClassName"  
    Condition="'String A'=='String B'" />  
```  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### Attribute  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`AssemblyName`|Entweder ist das Attribut `AssemblyName` oder das Attribut `AssemblyFile` erforderlich.<br /><br /> Der Namen zu ladenden Assembly.  Das Attribut `AssemblyName` akzeptiert Assemblys mit sicheren Namen, auch wenn sichere Namen nicht erforderlich sind.  Die Verwendung dieses Attributs entspricht dem Laden einer Assembly mit der <xref:System.Reflection.Assembly.Load%2A>\-Methode in .NET.<br /><br /> Sie können dieses Attribut nicht verwenden, wenn das `AssemblyFile`\-Attribut verwendet wird.|  
|`AssemblyFile`|Entweder ist das Attribut `AssemblyName` oder das Attribut `AssemblyFile` erforderlich.<br /><br /> Der Dateipfad der Assemblydatei.  Dieses Attribut akzeptiert vollständige oder relative Pfade.  Relative Pfade sind relativ zum Verzeichnis der Projektdatei oder Zieldatei, in dem das `UsingTask`\-Element deklariert ist.  Die Verwendung dieses Attributs entspricht dem Laden einer Assembly mit der <xref:System.Reflection.Assembly.LoadFrom%2A>\-Methode in .NET.<br /><br /> Sie können dieses Attribut nicht verwenden, wenn das `AssemblyName`\-Attribut verwendet wird.|  
|`TaskFactory`|Optionales Attribut.<br /><br /> Gibt die Klasse in der Assembly an, die für das Generieren von Instanzen des angegebenen `Task`\-Namens verantwortlich ist.  Der Benutzer kann auch `TaskBody` als ein untergeordnetes Element angeben, welches durch die Aufgabenfactory empfangen und zum Generieren der Aufgabe verwendet wird.  Der Inhalt von `TaskBody` ist für die Aufgabenfactory spezifisch.|  
|`TaskName`|Erforderliches Attribut.<br /><br /> Der Name der aus einer Assembly zu referenzierenden Aufgabe.  Wenn Mehrdeutigkeiten möglich sind, sollte dieses Attribut immer vollständige Namespaces angeben.  Wenn Mehrdeutigkeiten vorliegen, wählt MSBuild eine willkürliche Übereinstimmung auf, die zu unerwarteten Ergebnissen führen kann.|  
|`Condition`|Optionales Attribut.<br /><br /> Die auszuwertende Bedingung.  Weitere Informationen finden Sie unter [Conditions](../msbuild/msbuild-conditions.md).|  
  
### Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[ParameterGroup](../msbuild/parametergroup-element.md)|Der Satz an Parametern, die in der Aufgabe angezeigt werden, welche durch die angegebene `TaskFactory` generiert wurde.|  
|[Aufgabe](../msbuild/task-element-msbuild.md)|Die `TaskFactory` weitergegebenen Daten zum Generieren einer Instanz der Aufgabe.|  
  
### Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[Project](../msbuild/project-element-msbuild.md)|Erforderliches Stammelement einer [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]\-Projektdatei.|  
  
## Hinweise  
 Umgebungsvariablen, Befehlszeileneigenschaften und Eigenschaften auf Projektebene können im gesamten `UsingTask`\-Element referenziert werden, wenn es in der Projektdatei angezeigt wird, und zwar entweder explizit oder mithilfe einer importierten Projektdatei.  Weitere Informationen finden Sie unter [Tasks](../msbuild/msbuild-tasks.md).  
  
> [!NOTE]
>  Eigenschaften auf Projektebene haben keine Bedeutung, wenn das `UsingTask`\-Element aus einer der TASKS\-Dateien stammt, die global im MSBuild\-Modul registriert sind.  Eigenschaften auf Projektebene sind nicht global in MSBuild.  
  
 In MSBuild 4.0 kann das Laden mithilfe von Aufgaben aus .overridetask\-Dateien erfolgen.  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung des Elements `UsingTask` mit dem Attribut `AssemblyName` gezeigt.  
  
```  
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
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung des Elements `UsingTask` mit dem Attribut `AssemblyFile` gezeigt.  
  
```  
<UsingTask TaskName="Email"  
              AssemblyFile="c:\myTasks\myTask.dll" />  
```  
  
## Siehe auch  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [Project File Schema Reference](../msbuild/msbuild-project-file-schema-reference.md)