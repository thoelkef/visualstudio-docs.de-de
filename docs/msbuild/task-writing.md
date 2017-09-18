---
title: "Task Writing | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, writing tasks"
  - "tasks, creating for MSBuild"
  - "MSBuild, creating tasks"
ms.assetid: 3ebc5f87-8f00-46fc-82a1-228f35a6823b
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# Task Writing
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Aufgaben stellen den Code bereit, der während des Buildprozesses ausgeführt wird.  Aufgaben sind in Zielen enthalten.  Mit [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] wird eine Bibliothek häufig ausgeführter Aufgaben bereitgestellt. Darüber hinaus können Sie eigene Aufgaben erstellen.  Weitere Informationen zu der in [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] bereitgestellten Aufgabenbibliothek finden Sie unter [Task Reference](../msbuild/msbuild-task-reference.md).  
  
## Aufgaben  
 Beispiele für Aufgaben: [Copy](../msbuild/copy-task.md) zum Kopieren von mindestens einer Datei, [MakeDir](../msbuild/makedir-task.md) zum Erstellen eines Verzeichnisses und [Csc](../msbuild/csc-task.md), womit [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]\-Quellcodedateien kompiliert werden.  Jede Aufgabe wird als .NET\-Klasse implementiert, durch die die in der Assembly Microsoft.Build.Framework.dll definierte <xref:Microsoft.Build.Framework.ITask>\-Schnittstelle eingerichtet wird.  
  
 Es gibt zwei Vorgehensweisen für das Implementieren einer Aufgabe:  
  
-   Direktes Implementieren der <xref:Microsoft.Build.Framework.ITask>\-Schnittstelle  
  
-   Ableiten der Klasse von der <xref:Microsoft.Build.Utilities.Task>\-Hilfsklasse, die in der Assembly Microsoft.Build.Utilities.dll definiert ist.  Durch die Aufgabe wird ITask implementiert, und es werden Standardimplementierungen einiger ITask\-Member bereitgestellt.  Zusätzlich wird die Protokollierung vereinfacht.  
  
 In beiden Fällen müssen Sie der Klasse eine Methode mit dem Namen `Execute` hinzufügen. Diese Methode wird aufgerufen, wenn die Aufgabe ausgeführt wird.  Diese Methode enthält keine Parameter und gibt einen `Boolean`\-Wert zurück: `true` bei erfolgreicher und `false` bei nicht erfolgreicher Ausführung der Aufgabe.  Im folgenden Beispiel wird eine Aufgabe veranschaulicht, die keine Aktionen ausführt und `true` zurückgibt.  
  
```  
using System;  
using Microsoft.Build.Framework;  
using Microsoft.Build.Utilities;  
  
namespace MyTasks  
{  
    public class SimpleTask : Task  
    {  
        public override bool Execute()  
        {  
            return true;  
        }  
    }  
}  
```  
  
 Die folgende Projektdatei führt diese Aufgabe aus:  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="MyTarget">  
        <SimpleTask />  
    </Target>  
</Project>  
```  
  
 Wenn Aufgaben ausgeführt werden, können sie auch Eingaben von der Projektdatei empfangen, sofern Sie .NET\-Eigenschaften für die Aufgabenklasse erstellen.  [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] legt diese Eigenschaften unmittelbar vor dem Aufrufen der `Execute`\-Methode der Aufgabe fest.  Um eine Zeichenfolgeneigenschaft zu erstellen, verwenden Sie z. B. folgenden Aufgabencode:  
  
```  
using System;  
using Microsoft.Build.Framework;  
using Microsoft.Build.Utilities;  
  
namespace MyTasks  
{  
    public class SimpleTask : Task  
    {  
        public override bool Execute()  
        {  
            return true;  
         }  
  
        private string myProperty;  
        public string MyProperty  
        {  
            get { return myProperty; }  
            set { myProperty = value; }  
        }  
    }  
}  
```  
  
 Von der folgenden Projektdatei wird diese Aufgabe ausgeführt und `MyProperty` auf den angegebenen Wert festgelegt:  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <Target Name="MyTarget">  
      <SimpleTask MyProperty="Value for MyProperty" />  
   </Target>  
</Project>  
```  
  
## Registrieren von Aufgaben  
 Wenn ein Projekt für die Ausführung einer Aufgabe konfiguriert wird, muss [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] wissen, wo sich die Assembly mit der Aufgabenklasse befindet.  Aufgaben werden mit [UsingTask Element \(MSBuild\)](../msbuild/usingtask-element-msbuild.md) registriert.  
  
 Die [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]\-Datei Microsoft.Common.Tasks ist eine Projektdatei mit einer Liste von `UsingTask`\-Elementen, durch die alle mit [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] bereitgestellten Aufgaben registriert werden.  Diese Datei wird beim Erstellen der einzelnen Projekte automatisch eingeschlossen.  Wenn eine Aufgabe, die in Microsoft.Common.Tasks registriert ist, zusätzlich auch in der aktuellen Projektdatei registriert wird, hat die aktuelle Projektdatei Vorrang, d h., Sie können eine Standardaufgabe mit einer eigenen gleichnamigen Aufgabe überschreiben.  
  
> [!TIP]
>  Sie können eine Liste der mit [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] bereitgestellten Aufgaben aufrufen, indem Sie den Inhalt von Microsoft.Common.Tasks anzeigen.  
  
## Auslösen von Ereignissen aus einer Aufgabe  
 Wenn die Aufgabe von der <xref:Microsoft.Build.Utilities.Task>\-Hilfsklasse abgeleitet ist, können Sie zum Auslösen von Ereignissen, die von beliebigen registrierten Protokollierungen erkannt und angezeigt werden, eine der folgenden Hilfsmethoden in der <xref:Microsoft.Build.Utilities.Task>\-Klasse verwenden:  
  
```  
public override bool Execute()  
{  
    Log.LogError("messageResource1", "1", "2", "3");  
    Log.LogWarning("messageResource2");  
    Log.LogMessage(MessageImportance.High, "messageResource3");  
    ...  
}  
```  
  
 Wenn <xref:Microsoft.Build.Framework.ITask> von der Aufgabe direkt implementiert wird, können Sie diese Ereignisse weiterhin auslösen, müssen dabei jedoch die IBuildEngine\-Schnittstelle verwenden.  Im folgenden Beispiel wird eine Aufgabe angezeigt, durch die ITask implementiert und ein benutzerdefiniertes Ereignis ausgelöst wird:  
  
```  
public class SimpleTask : ITask  
{  
    private IBuildEngine buildEngine;  
    public IBuildEngine BuildEngine  
    {  
        get{ return buildEngine; }  
        set{ buildEngine = value; }  
    }  
  
    public override bool Execute()  
    {  
        TaskEventArgs taskEvent =  
            new TaskEventArgs(BuildEventCategory.Custom,  
            BuildEventImportance.High, "Important Message",  
           "SimpleTask");  
        BuildEngine.LogBuildEvent(taskEvent);  
        return true;  
    }  
}  
```  
  
## Kennzeichnen von Aufgabenparametern als erforderlich  
 Sie können bestimmte Aufgabeneigenschaften als "erforderlich" kennzeichnen, sodass von jeder Projektdatei, die diese Aufgabe ausführt, Werte für diese Eigenschaften festgelegt werden müssen. Andernfalls ist der Buildvorgang nicht erfolgreich.  Übernehmen Sie das `[Required]`\-Attribut in der Aufgabe wie folgt für die .NET\-Eigenschaft:  
  
```  
private string requiredProperty;  
  
[Required]  
public string RequiredProperty  
{  
    get { return requiredProperty; }  
    set { requiredProperty = value; }  
}  
```  
  
 Das `[Required]`\-Attribut wird von <xref:Microsoft.Build.Framework.RequiredAttribute> im <xref:Microsoft.Build.Framework>\-Namespace definiert.  
  
## Beispiel  
  
### Beschreibung  
 Mit der folgenden [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]\-Klasse wird eine Aufgabe veranschaulicht, die von der <xref:Microsoft.Build.Utilities.Task>\-Hilfsklasse abgeleitet wird.  Diese Aufgabe gibt `true` zurück; sie wurde also erfolgreich ausgeführt.  
  
### Code  
  
```  
using System;  
using Microsoft.Build.Utilities;  
  
namespace SimpleTask1  
{  
    public class SimpleTask1: Task  
    {  
        public override bool Execute()  
        {  
            // This is where the task would presumably do its work.  
            return true;  
        }  
    }  
}  
```  
  
## Beispiel  
  
### Beschreibung  
 Mit der folgenden [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]\-Klasse wird eine Aufgabe veranschaulicht, die die <xref:Microsoft.Build.Framework.ITask>\-Schnittstelle implementiert.  Diese Aufgabe gibt `true` zurück; sie wurde also erfolgreich ausgeführt.  
  
### Code  
  
```  
using System;  
using Microsoft.Build.Framework;  
  
namespace SimpleTask2  
{  
    public class SimpleTask2: ITask  
    {  
        //When implementing the ITask interface, it is necessary to  
        //implement a BuildEngine property of type  
        //Microsoft.Build.Framework.IBuildEngine. This is done for  
        //you if you derive from the Task class.  
        private IBuildEngine buildEngine;  
        public IBuildEngine BuildEngine  
        {  
            get  
            {  
                return buildEngine;  
            }  
            set  
            {  
                buildEngine = value;  
            }  
         }  
  
        // When implementing the ITask interface, it is necessary to  
        // implement a HostObject property of type Object.  
        // This is done for you if you derive from the Task class.  
        private Object hostObject;  
        public Object HostObject  
        {  
            get  
            {  
                return hostObject;  
            }  
  
            set  
            {  
                hostObject = value;  
            }  
        }  
  
        public bool Execute()  
        {  
            // This is where the task would presumably do its work.  
            return true;  
        }  
    }  
}  
```  
  
## Beispiel  
  
### Beschreibung  
 Mit der [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]\-Klasse wird eine Aufgabe veranschaulicht, die von der <xref:Microsoft.Build.Utilities.Task>\-Hilfsklasse abgeleitet wird.  Sie verfügt über eine erforderliche Zeichenfolgeneigenschaft und löst ein Ereignis aus, das von allen registrierten Protokollierungen angezeigt wird.  
  
### Code  
 [!code-cs[msbuild_SimpleTask3#1](../msbuild/codesnippet/CSharp/task-writing_1.cs)]  
  
## Beispiel  
  
### Beschreibung  
 Im folgenden Beispiel wird eine Projektdatei veranschaulicht, durch die SimpleTask3, die Aufgabe aus dem vorherigen Beispiel, aufgerufen wird.  
  
### Code  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <UsingTask TaskName="SimpleTask3.SimpleTask3"   
        AssemblyFile="SimpleTask3\bin\debug\simpletask3.dll"/>  
  
    <Target Name="MyTarget">  
        <SimpleTask3 MyProperty="Hello!"/>  
    </Target>  
</Project>  
```  
  
## Siehe auch  
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)