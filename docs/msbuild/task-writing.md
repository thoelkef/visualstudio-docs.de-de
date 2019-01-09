---
title: Schreiben von Aufgaben | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, writing tasks
- tasks, creating for MSBuild
- MSBuild, creating tasks
ms.assetid: 3ebc5f87-8f00-46fc-82a1-228f35a6823b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 471e707b13992a0edf06eb8136d36f3f415b9d11
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53922150"
---
# <a name="task-writing"></a>Schreiben von Aufgaben
Aufgaben stellen den Code bereit, der während des Buildprozesses ausgeführt wird. Ziele enthalten Aufgaben. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] umfasst eine Bibliothek mit typischen Tasks. Sie können aber auch Ihre eigenen Tasks erstellen. Weitere Informationen zur Aufgabenbibliothek, die in [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] enthalten ist, finden Sie unter [MSBuild Task Reference](../msbuild/msbuild-task-reference.md).  
  
## <a name="tasks"></a>Aufgaben  
 Beispiele für Aufgaben sind u.a. [Kopieren](../msbuild/copy-task.md) (zum Kopieren mindestens einer Datei) [MakeDir](../msbuild/makedir-task.md) (zum Erstellen eines Verzeichnisses) und [Csc](../msbuild/csc-task.md) (zum Kompilieren einer [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]-Quellcodedatei). Jede Aufgabe wird als .NET-Klasse implementiert, die die <xref:Microsoft.Build.Framework.ITask>-Schnittstelle implementiert, die in der Assembly *Microsoft.Build.Framework.dll* definiert ist.  
  
 Es gibt zwei Ansätze zur Implementierung einer Aufgabe:  
  
-   Implementieren Sie die <xref:Microsoft.Build.Framework.ITask>-Schnittstelle direkt.  
  
-   Leiten Sie Ihre Klasse von der Hilfsklasse <xref:Microsoft.Build.Utilities.Task> ab, die in der Assembly *Microsoft.Build.Utilities.dll* definiert ist. „Task“ implementiert „ITask“ und stellt Standardimplementierungen einiger „ITask“-Elemente dar. Darüber hinaus wird die Protokollierung vereinfacht.  

In beiden Fällen müssen Sie Ihrer Klasse eine Methode mit dem Namen `Execute` hinzufügen. Dabei handelt es sich um die Methode, die aufgerufen wird, wenn eine Aufgabe ausgeführt wird. Sie nimmt keine Parameter und gibt einen `Boolean`-Wert zurück: `true`, wenn die Aufgabe erfolgreich ausgeführt wurde oder `false`, wenn sie fehlgeschlagen ist. Im folgenden Beispiel wird eine Aufgabe dargestellt, die keine Aktion ausführt, aber `true` zurückgibt.  
  
```csharp
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
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="MyTarget">  
        <SimpleTask />  
    </Target>  
</Project>  
```  
  
 Wenn Aufgaben ausgeführt werden, können sie gleichzeitig Eingaben von der Projektdatei enthalten, wenn Sie .NET-Eigenschaften in der Aufgabenklasse erstellen. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] legt diese Eigenschaften unmittelbar vor dem Aufrufen der `Execute`-Methode der Aufgabe fest. Verwenden Sie z.B. wie im Folgenden dargestellten Aufgabencode, um eine Zeichenfolgeneigenschaft zu erstellen:  
  
```csharp
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
  
 Die folgende Projektdatei führt diese Aufgabe aus und legt `MyProperty` auf den vorhandenen Wert fest:  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <Target Name="MyTarget">  
      <SimpleTask MyProperty="Value for MyProperty" />  
   </Target>  
</Project>  
```  
  
## <a name="register-tasks"></a>Protokollaufgaben  
 Wenn das Projekt eine Aufgabe ausführen möchte, muss [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] wissen, wo die Assembly mit der Aufgabenklasse zu finden ist. Aufgaben werden über das [UsingTask-Element (MSBuild)](../msbuild/usingtask-element-msbuild.md) registriert.  
  
 Die [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]-Datei *Microsoft.Common.Tasks* ist eine Projektdatei mit einer Liste von `UsingTask`-Elementen, die alle Aufgaben registrieren, die mit [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] bereitgestellt werden. Diese Datei wird automatisch beim Erstellen von Projekten mit eingeschlossen. Wenn eine Aufgabe, die in *Microsoft.Common.Tasks* registriert wird, ebenfalls in der aktuellen Projektdatei registriert wird, hat die aktuelle Projektdatei Vorrang. Das heißt, Sie können eine Standardaufgabe mit Ihrer eigenen Aufgabe, die denselben Namen hat, außer Kraft setzen.  
  
> [!TIP]
>  Es wird Ihnen eine Liste mit Aufgaben angezeigt, die mit [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] bereitgestellt werden, wenn Sie die Inhalte der *Microsoft.Common.Tasks* abrufen.  
  
## <a name="raise-events-from-a-task"></a>Auslösen von Ereignissen aus einer Aufgabe  
 Wenn Ihre Aufgabe aus der <xref:Microsoft.Build.Utilities.Task>-Hilfsklasse abgeleitet wird, können Sie eine der folgenden Hilfsmethoden für die <xref:Microsoft.Build.Utilities.Task>-Klasse verwenden, damit ein Ereignis ausgelöst wird, das von allen registrierten Protokollierungen abgefangen und angezeigt wird:  
  
```csharp
public override bool Execute()  
{  
    Log.LogError("messageResource1", "1", "2", "3");  
    Log.LogWarning("messageResource2");  
    Log.LogMessage(MessageImportance.High, "messageResource3");  
    ...  
}  
```  
  
 Wenn Ihre Aufgabe <xref:Microsoft.Build.Framework.ITask> direkt implementiert, können Sie solche Ereignisse immer noch auslösen, allerdings nur noch über die IBuildEngine-Schnittstelle. Im folgenden Beispiel wird eine Aufgabe gezeigt, die „ITask“ implementiert und ein benutzerdefiniertes Ereignis auslöst:  
  
```csharp
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
  
## <a name="require-task-parameters-to-be-set"></a>Erfordern, dass Aufgabenparameter festgelegt werden  
 Sie können Aufgabeneigenschaften als „Erforderlich“ markieren, damit jede Projektdatei, die die Aufgabe ausführt, Werte für diese Eigenschaften oder die fehlgeschlagenen Builds festlegt. Wenden Sie das erforderliche `[Required]`-Attribut in der .NET-Eigenschaft in Ihrer Aufgabe wie folgt an:  
  
```csharp
private string requiredProperty;  
  
[Required]  
public string RequiredProperty  
{  
    get { return requiredProperty; }  
    set { requiredProperty = value; }  
}  
```  
  
 Das `[Required]`-Attribut wird von <xref:Microsoft.Build.Framework.RequiredAttribute> im <xref:Microsoft.Build.Framework>-Namespace definiert.  
  
## <a name="example"></a>Beispiel  
  
### <a name="description"></a>Beschreibung  
 Die folgende [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]-Klasse veranschaulicht eine aus der <xref:Microsoft.Build.Utilities.Task>-Hilfsklasse abgeleitete Aufgabe. Dieser Task gibt den Wert `true` zurück, der darauf hindeutet, dass der Task erfolgreich ausgeführt wird.  
  
### <a name="code"></a>Code  
  
```csharp
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
  
## <a name="example"></a>Beispiel  
  
### <a name="description"></a>Beschreibung  
 Die folgende [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]-Klasse veranschaulicht eine Aufgabe, die die <xref:Microsoft.Build.Framework.ITask>-Schnittstelle implementiert. Dieser Task gibt den Wert `true` zurück, der darauf hindeutet, dass der Task erfolgreich ausgeführt wird.  
  
### <a name="code"></a>Code  
  
```csharp
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
  
## <a name="example"></a>Beispiel  
  
### <a name="description"></a>Beschreibung  
 Diese [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]-Klasse veranschaulicht eine aus der <xref:Microsoft.Build.Utilities.Task>-Hilfsklasse abgeleitete Aufgabe. Sie verfügt über eine erforderliche Zeichenfolgeneigenschaft und löst ein Ereignis aus, das von allen registrierten Protokollierungen angezeigt wird.  
  
### <a name="code"></a>Code  
 [!code-csharp[msbuild_SimpleTask3#1](../msbuild/codesnippet/CSharp/task-writing_1.cs)]  
  
## <a name="example"></a>Beispiel  
  
### <a name="description"></a>Beschreibung  
 Im folgenden Beispiel wird eine Projektdatei dargestellt, die die vorherigen Beispielaufgabe „SimpleTask3“ aufruft.  
  
### <a name="code"></a>Code  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <UsingTask TaskName="SimpleTask3.SimpleTask3"   
        AssemblyFile="SimpleTask3\bin\debug\simpletask3.dll"/>  
  
    <Target Name="MyTarget">  
        <SimpleTask3 MyProperty="Hello!"/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)   
