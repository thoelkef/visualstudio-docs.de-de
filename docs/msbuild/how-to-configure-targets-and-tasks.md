---
title: "How to: Configure Targets and Tasks | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 92814100-392a-471d-96fd-e26f637d6cc2
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# How to: Configure Targets and Tasks
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Auswählen von MSBuild\-Aufgaben können so festgelegt werden, dass sie in der CLR\-Umgebung ausgeführt, unabhängig von der Umgebung für das jeweilige computers.  Wenn Sie z. B. einem 64\-Bit\-Computer verwenden, um eine Anwendung zu erstellen, die eine 32\-Bit\-Architektur abzielt, sind ausgewählte Aufgaben in einem 32\-Bit\-Prozess ausgeführt.  
  
> [!NOTE]
>  Wenn eine Erstellung aufgabe in einer .NET\-Sprache wie Visual C\# oder Visual Basic, und verwendet keine systemeigene Ressourcen oder Tools geschrieben wird, wird sie in jedem Zielkontext ohne Anpassung.  
  
## UsingTask\-Attribute und Aufgabenparameter  
 Die folgenden `UsingTask`\-Attribute wirken sich auf alle Vorgänge einer Aufgabe in einem bestimmten Buildvorgang:  
  
-   Das Attribut `Runtime`, sofern vorhanden, welche Version der Common Language Runtime \(CLR\) festgelegt und eines dieser Werte annehmen kann: `CLR2`, `CLR4`, `CurrentRuntime`oder `*` beliebig \(Common Language Runtime\).  
  
-   Das Attribut `Architecture`, sofern vorhanden, die Plattform und Bitanzahl festgelegt und eines dieser Werte annehmen kann: `x86`, `x64`, `CurrentArchitecture`oder `*` \(jede architektonische\).  
  
-   Das Attribut `TaskFactory`, sofern vorhanden, wird die Aufgabenfactory, die die Aufgabeninstanz erstellt und ausgeführt werden, fest und verwendet nur den Wert `TaskHostFactory`.  Weitere Informationen finden Sie im Abschnitt Aufgaben\-Factory weiter unten in diesem Dokument.  
  
```  
<UsingTask TaskName="SimpleTask"   
   Runtime="CLR2"  
   Architecture="x86"  
   AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v3.5.dll" />  
```  
  
 Sie können die `MSBuildRuntime` und `MSBuildArchitecture`\-Parameter auch verwenden, um den Zielkontext einer einzelnen Aufgabe festzulegen.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <Target Name="MyTarget">  
      <SimpleTask MSBuildRuntime="CLR2" MSBuildArchitecture= "x86"/>  
   </Target>  
</Project>  
```  
  
 Bevor MSBuild eine Aufgabe ausführt, sucht er nach übereinstimmenden `UsingTask`, die denselben Zielkontext verfügt.  Parameter, die in `UsingTask` aber nicht in der entsprechenden Aufgabe angegeben werden, werden als übereinstimmende betrachtet.  Parameter, die in der Aufgabe aber nicht an den entsprechenden `UsingTask` angegeben haben, werden auch als übereinstimmende betrachtet.  Wenn Parameterwerte entweder nicht in `UsingTask` oder in der Aufgabe angegeben werden, werden die Werte in `*` \(entweder Parameter\).  
  
> [!WARNING]
>  Wenn mehr als ein `UsingTask` vorhanden ist und alle übereinstimmende `TaskName`, `Runtime`und `Architecture`\-Attribute verfügen, ersetzt das zuletzt ausgewertet werden, die einen anderen.  
  
 Wenn Parameter in der Aufgabe festgelegt werden, `UsingTask` MSBuild versucht, die diese Parameter übereinstimmt, oder es handelt sich um mindestens nicht im Widerspruch zu ihnen.  Mehr als ein `UsingTask` kann den Zielkontext der gleichen Aufgabe angeben.  Zum Beispiel ähnelte möglicherweise eine Aufgabe, die andere ausführbare Dateien für unterschiedliche Zielumgebung hat dies:  
  
```  
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
  
## Aufgaben\-Factorys  
 Bevor Sie eine Aufgabe ausführt, MSBuild\-Überprüfungen, um zu überprüfen, ob sie zur Ausführung im aktuellen Software\-Kontext festgelegt ist.  Wenn die Aufgabe so festgelegt ist, führt MSBuild sie in den AssemblyTaskFactory, das sie im aktuellen Prozess ausgeführt wird. Andernfalls führt MSBuild das die Aufgabe TaskHostFactory, das die Aufgabe in einem Prozess ausgeführt wird, der den Zielkontext übereinstimmt.  Auch wenn der aktuelle Kontext und den Zielkontext entsprechen, können Sie eine Aufgabe erzwingen, dass prozessexterne \(für Isolierung, Sicherheits\- oder anderen Gründen\), indem Sie `TaskFactory` auf Ausführen `TaskHostFactory`festlegen.  
  
```  
<UsingTask TaskName="MisbehavingTask"   
   TaskFactory="TaskHostFactory"  
   AssemblyFile="$(MSBuildToolsPath)\MyTasks.dll">  
</UsingTask>  
```  
  
## Phantomaufgaben\-Parameter  
 Wie alle anderen Aufgabenparameter können `MSBuildRuntime` und `MSBuildArchitecture` von Buildeigenschaften festgelegt werden.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <PropertyGroup>  
      <FrameworkVersion>3.0</FrameworkVersion>  
   </PropertyGroup>  
   <Target Name="MyTarget">  
      <SimpleTask MSBuildRuntime="$(FrameworkVerion)" MSBuildArchitecture= "x86"/>  
   </Target>  
</Project>  
```  
  
 Im Gegensatz zu anderen Aufgabenparameter sind `MSBuildRuntime` und `MSBuildArchitecture` für die Aufgabe selbst nicht offensichtlich.  Um eine Aufgabe berücksichtigt die den Kontext zum Schreiben in den sie ausgeführt wird, müssen Sie entweder den Kontext indem Sie .NET Framework testen oder Buildeigenschaften verwenden, um die Kontextinformationen über andere Aufgabenparameter zu übergeben.  
  
> [!NOTE]
>  `UsingTask`\-Attribute können Toolset\- und Umgebungseigenschaften festgelegt werden.  
  
 Die `MSBuildRuntime``MSBuildArchitecture`\-Parameter angeben und die flexibelste Methode für den Zielkontext festzulegen, sondern auch das begrenzteste im Bereich.  Einerseits da sie für die Aufgabeninstanz selbst und nicht ausgewertet werden, bis die Aufgabe gerade ausgeführt werden, können sie ihren Wert aus dem vollständigen Bereich von Eigenschaften abgeleitet werden, die unter Auswertung gültige und unter Build gültige verfügbar sind.  Ebenso erfüllen diese Parameter nur für eine bestimmte Instanz einer Aufgabe in einem bestimmten Ziel auf.  
  
> [!NOTE]
>  Aufgabenparameter werden im Kontext des übergeordneten Knotens, nicht im Kontext des Tasks Language Runtime\-Hosts ausgewertet. Umgebungsvariablen, die die sind bzw. Architektur abhängiges Element \(z. B. den Speicherort der Programmdateien Werten\) den Wert aus, der den übergeordneten Knoten entspricht.  Wenn jedoch die gleiche Umgebungsvariable direkt von der Aufgabe gelesen wird, wird er im Bereich des Tasks korrekt gehostet ausgewertet.  
  
## Siehe auch  
 [Configuring Targets and Tasks](../msbuild/configuring-targets-and-tasks.md)