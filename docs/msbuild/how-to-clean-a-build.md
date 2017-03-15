---
title: "How to: Clean a Build | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Exec task [MSBuild]"
  - "MSBuild, cleaning a build"
  - "directories [.NET Framework], for output items"
  - "output, removing items"
ms.assetid: 999ba473-b0c4-45c7-930a-63ea7a510509
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# How to: Clean a Build
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wenn Sie einen Build bereinigen, werden alle Zwischen\- und Ausgabedateien gelöscht, sodass nur die Projekt\- und Komponentendateien übrig bleiben.  Anschließend können aus den Projekt\- und Komponentendateien neue Instanzen der Zwischen\- und Ausgabedateien erstellt werden.  Die mit [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] bereitgestellte Bibliothek allgemeiner Aufgaben umfasst eine [Exec](../msbuild/exec-task.md)\-Aufgabe, mit der Sie Systembefehle ausführen können.  Weitere Informationen zur Aufgabenbibliothek finden Sie unter [Task Reference](../msbuild/msbuild-task-reference.md).  
  
## Erstellen eines Verzeichnisses für Ausgabeelemente  
 Die während der Projektkompilierung erstellte EXE\-Datei wird standardmäßig im selben Verzeichnis wie die Projekt\- und Quelldateien abgelegt.  Ausgabeelemente werden jedoch normalerweise in einem separaten Verzeichnis erstellt.  
  
#### So erstellen Sie ein Verzeichnis für Ausgabeelemente  
  
1.  Verwenden Sie das `Property`\-Element, um den Speicherort und den Namen des Verzeichnisses zu definieren.  Erstellen Sie beispielsweise das Verzeichnis `BuiltApp` in dem Verzeichnis, das die Projekt\- und Quelldateien enthält:  
  
     `<builtdir>BuiltApp</builtdir>`  
  
2.  Falls das Verzeichnis nicht vorhanden ist, verwenden Sie die [MakeDir](../msbuild/makedir-task.md)\-Aufgabe, um es zu erstellen.  Beispiele:  
  
     `<MakeDir Directories = "$(builtdir)"`  
  
     `Condition = "!Exists('$(builtdir)')" />`  
  
## Entfernen der Ausgabeelemente  
 Bevor Sie neue Instanzen von Zwischen\- und Ausgabedateien erstellen, möchten Sie möglicherweise alle vorherigen Instanzen dieser Dateien löschen.  Verwenden Sie die [RemoveDir](../msbuild/removedir-task.md)\-Aufgabe, um ein Verzeichnis sowie alle darin enthaltenen Dateien und Verzeichnisse von einem Datenträger zu löschen.  
  
#### So entfernen Sie ein Verzeichnis und alle im Verzeichnis enthaltenen Dateien  
  
-   Verwenden Sie die `RemoveDir`\-Aufgabe, um das Verzeichnis zu entfernen.  Beispiele:  
  
     `<RemoveDir Directories="$(builtdir)" />`  
  
## Beispiel  
 Das folgende Codebeispielprojekt enthält das neue Ziel `Clean`, das die `RemoveDir`\-Aufgabe verwendet, um ein Verzeichnis mit allen enthaltenen Dateien und Verzeichnissen zu löschen.  Darüber hinaus wird vom Ziel `Compile` in diesem Beispiel ein separates Verzeichnis für die Ausgabeelemente erstellt, die beim Bereinigen des Builds gelöscht werden.  
  
 `Compile` ist als Standardziel definiert und wird deshalb automatisch verwendet, es sei denn, Sie geben ein bzw. mehrere andere Ziele an.  Mit dem Befehlszeilenschalter **\/target** können Sie ein anderes Ziel angeben.  Beispiele:  
  
 `msbuild <file name>.proj /target:Clean`  
  
 Der Schalter **\/target** kann in der Kurzform **\/t** sowie zum Festlegen mehrerer Ziele verwendet werden.  Um beispielsweise das Ziel `Clean` und dann das Ziel `Compile` zu verwenden, geben Sie Folgendes ein.  
  
 `msbuild <file name>.proj /t:Clean;Compile`  
  
```  
<Project DefaultTargets = "Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <PropertyGroup>  
        <!-- Set the application name as a property -->  
        <name>HelloWorldCS</name>  
  
        <!-- Set the output folder as a property -->  
        <builtdir>BuiltApp</builtdir>  
    </PropertyGroup>  
  
    <ItemGroup>  
        <!-- Specify the inputs by type and file name -->  
        <CSFile Include = "consolehwcs1.cs"/>  
    </ItemGroup>  
  
    <Target Name = "Compile">  
        <!-- Check whether an output folder exists and create  
        one if necessary -->  
        <MakeDir Directories = "$(builtdir)"   
            Condition = "!Exists('$(builtdir)')" />  
  
        <!-- Run the Visual C# compiler -->  
        <CSC Sources = "@(CSFile)"   
            OutputAssembly = "$(BuiltDir)\$(appname).exe">  
            <Output TaskParameter = "OutputAssembly"  
                ItemName = "EXEFile" />  
        </CSC>  
  
        <!-- Log the file name of the output file -->  
        <Message Text="The output file is @(EXEFile)"/>  
    </Target>  
  
    <Target Name = "Clean">  
        <RemoveDir Directories="$(builtdir)" />  
    </Target>  
</Project>  
```  
  
## Siehe auch  
 [Exec Task](../msbuild/exec-task.md)   
 [MakeDir Task](../msbuild/makedir-task.md)   
 [RemoveDir Task](../msbuild/removedir-task.md)   
 [Csc Task](../msbuild/csc-task.md)   
 [Targets](../msbuild/msbuild-targets.md)