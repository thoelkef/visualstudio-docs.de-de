---
title: 'Vorgehensweise: Konfigurieren von Zielen und Aufgaben | Microsoft-Dokumentation'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 92814100-392a-471d-96fd-e26f637d6cc2
caps.latest.revision: 5
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 79460291e91f0659df0a4241e17616e55187a0e2
ms.openlocfilehash: ac979e7287046164db37848778f648656f7230a6
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-configure-targets-and-tasks"></a>Gewusst wie: Konfigurieren von Zielen und Aufgaben
Ausgewählte MSBuild-Aufgaben können unabhängig von der Umgebung des Entwicklungscomputers zur Ausführung in der Umgebung, für die sie bestimmt sind, eingestellt werden. Wenn Sie z.B. einen 64-Bit-Computer zum Erstellen einer Anwendung verwenden, die in einer 32-Bit-Architektur ausgeführt werden soll, werden ausgewählte Vorgänge in einem 32-Bit-Prozess ausgeführt.  
  
> [!NOTE]
>  Wenn eine Buildaufgabe in einer .NET-Sprache wie z.B. Visual C# oder Visual Basic geschrieben ist und keine nativen Ressourcen oder Tools verwendet, wird sie in jedem Zielkontext ohne Anpassung ausgeführt.  
  
## <a name="usingtask-attributes-and-task-parameters"></a>UsingTask-Attribute und Aufgabenparameter  
 Die folgenden `UsingTask`-Attribute wirken sich auf alle Vorgänge einer Aufgabe in einem bestimmten Buildprozess aus:  
  
-   Das `Runtime`-Attribut, sofern vorhanden, legt die Version der Common Language Runtime (CLR) fest, und kann einen der folgenden Werte annehmen: `CLR2`, `CLR4`, `CurrentRuntime` oder `*` (beliebige Runtime).  
  
-   Das `Architecture`-Attribut, sofern vorhanden, legt Plattform und Bitanzahl fest und kann einen der folgenden Werte annehmen: `x86`, `x64`, `CurrentArchitecture` oder `*` (beliebige Architektur).  
  
-   Das `TaskFactory`-Attribut, sofern vorhanden, legt die Aufgabenfactory fest, die die Aufgabeninstanz erstellt und ausführt, und nimmt nur den Wert `TaskHostFactory` an. Weitere Informationen finden Sie im Abschnitt „Aufgabenfactorys“ weiter unten in diesem Dokument.  
  
```xml  
<UsingTask TaskName="SimpleTask"   
   Runtime="CLR2"  
   Architecture="x86"  
   AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v3.5.dll" />  
```  
  
 Sie können auch mit den Parametern `MSBuildRuntime` und `MSBuildArchitecture` den Zielkontext einer einzelnen Aufgabe festlegen.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <Target Name="MyTarget">  
      <SimpleTask MSBuildRuntime="CLR2" MSBuildArchitecture= "x86"/>  
   </Target>  
</Project>  
```  
  
 Bevor MSBuild eine Aufgabe ausführt, wird nach einer übereinstimmenden `UsingTask` mit gleichem Zielkontext gesucht.  In der `UsingTask`, jedoch nicht in der entsprechenden Aufgabe angegebene Parameter werden als übereinstimmend betrachtet.  In der Aufgabe, jedoch nicht in der entsprechenden `UsingTask` angegebene Parameter werden auch als übereinstimmend betrachtet. Wenn Parameterwerte weder in der `UsingTask` noch in der Aufgabe angegeben sind, sind die Werte standardmäßig `*` (beliebiger Parameter).  
  
> [!WARNING]
>  Wenn mehr als eine `UsingTask` vorhanden ist und alle übereinstimmende `TaskName`-, `Runtime`- und `Architecture`-Attribute haben, ersetzt die zuletzt ausgewertete die anderen.  
  
 Wenn Parameter für die Aufgabe festgelegt sind, versucht MSBuild, eine `UsingTask` zu finden, die mit diesen Parametern übereinstimmt oder zumindest nicht in Konflikt mit ihnen steht.  Mehr als eine `UsingTask` können den Zielkontext der gleichen Aufgabe angeben.  Beispielsweise könnte eine Aufgabe mit verschiedenen ausführbaren Dateien für unterschiedliche Zielumgebungen dieser ähneln:  
  
```xml  
<UsingTask TaskName="MyTool"   
   Runtime="CLR2"  
   Architecture="x86"  
   AssemblyFile="$(MyToolsPath)\MyTool.v2.0.dll" />  
  
<UsingTask TaskName="MyTool"   
   Runtime="CLR4"  
   Architecture="x86"  
   AssemblyFile="$(MyToolsPath)\MyTool.4.0.dll" />  
  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <Target Name="MyTarget">  
      <MyTool MSBuildRuntime="CLR2" MSBuildArchitecture= "x86"/>  
   </Target>  
</Project>  
  
```  
  
## <a name="task-factories"></a>Aufgabenfactorys  
 Bevor eine Aufgabe ausgeführt wird, überprüft MSBuild, ob sie zur Ausführung im aktuellen Softwarekontext bestimmt ist.  Wenn die Aufgabe hierfür bestimmt ist, übergibt MSBuild sie an die AssemblyTaskFactory, die sie im aktuellen Prozess ausführt; andernfalls übergibt MSBuild die Aufgabe an die TaskHostFactory, die die Aufgabe in einem Prozess ausführt, der dem Zielkontext entspricht. Auch wenn aktueller Kontext und Zielkontext übereinstimmen, können Sie durch Festlegen von `TaskFactory` auf `TaskHostFactory` erzwingen, dass eine Aufgabe prozessextern ausgeführt wird (zur Isolation, zur Sicherheit oder aus anderen Gründen).  
  
```xml  
<UsingTask TaskName="MisbehavingTask"   
   TaskFactory="TaskHostFactory"  
   AssemblyFile="$(MSBuildToolsPath)\MyTasks.dll">  
</UsingTask>  
```  
  
## <a name="phantom-task-parameters"></a>Phantomaufgabenparameter  
 Wie alle anderen Aufgabenparameter können `MSBuildRuntime` und `MSBuildArchitecture` über die Buildeigenschaften festgelegt werden .  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <PropertyGroup>  
      <FrameworkVersion>3.0</FrameworkVersion>  
   </PropertyGroup>  
   <Target Name="MyTarget">  
      <SimpleTask MSBuildRuntime="$(FrameworkVerion)" MSBuildArchitecture= "x86"/>  
   </Target>  
</Project>  
```xml  
  
 Unlike other task parameters, `MSBuildRuntime` and `MSBuildArchitecture` are not apparent to the task itself.  To write a task that is aware of the context in which it runs, you must either test the context by calling the .NET Framework, or use build properties to pass the context information through other task parameters.  
  
> [!NOTE]
>  `UsingTask` attributes can be set from toolset and environment properties.  
  
 The `MSBuildRuntime` and `MSBuildArchitecture` parameters provide the most flexible way to set the target context, but also the most limited in scope.  On the one hand, because they are set on the task instance itself and are not evaluated until the task is about to run, they can derive their value from the full scope of properties available at both evaluation-time and build-time.  On the other hand, these parameters only apply to a particular instance of a task in a particular target.  
  
> [!NOTE]
>  Task parameters are evaluated in the context of the parent node, not in the context of the task host.Environment variables that are runtime- or architecture- dependent (such as the Program files location) will evaluate to the value that matches the parent node.  However, if the same environment variable is read directly by the task, it will correctly be evaluated in the context of the task host.  
  
## See Also  
 [Configuring Targets and Tasks](../msbuild/configuring-targets-and-tasks.md)
