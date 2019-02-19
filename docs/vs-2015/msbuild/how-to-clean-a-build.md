---
title: 'Vorgehensweise: Bereinigen eines Builds | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- Exec task [MSBuild]
- MSBuild, cleaning a build
- directories [.NET Framework], for output items
- output, removing items
ms.assetid: 999ba473-b0c4-45c7-930a-63ea7a510509
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: aa90a0d10b06559b3f4f46fd8dc0c5da4cef981e
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2019
ms.locfileid: "54780746"
---
# <a name="how-to-clean-a-build"></a>Gewusst wie: Bereinigen eines Builds
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Wenn Sie einen Build bereinigen, werden alle Zwischen- und Ausgabedateien gelöscht, wodurch nur die Projekt- und Komponentendateien verbleiben. Aus den Projekt- und Komponentendateien können neue Instanzen der Zwischen- und Ausgabedateien erstellt werden. Die Bibliothek mit allgemeinen Aufgaben, die mit [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] bereitgestellt wird, enthält eine [Exec](../msbuild/exec-task.md)-Aufgabe, die Sie für das Ausführen von Systembefehlen verwenden können. Weitere Informationen zur Aufgabenbibliothek finden Sie unter [Task Reference (Aufgabenverweis)](../msbuild/msbuild-task-reference.md).  
  
## <a name="creating-a-directory-for-output-items"></a>Erstellen eines Verzeichnisses für Ausgabeelemente  
 Standardmäßig wird die erstellte EXE-Datei beim Kompilieren eines Projekts im selben Verzeichnis wie das Projekt und die Quelldateien platziert. Die Ausgabeelemente werden jedoch üblicherweise in einem separaten Verzeichnis erstellt.  
  
#### <a name="to-create-a-directory-for-output-items"></a>Erstellen eines Verzeichnisses für Ausgabeelemente  
  
1.  Verwenden Sie das `Property`-Element, um den Speicherort und den Namen des Verzeichnisses zu definieren. Erstellen Sie beispielsweise ein Verzeichnis namens `BuiltApp` in dem Verzeichnis, das das Projekt und die Quelldateien enthält:  
  
     `<builtdir>BuiltApp</builtdir>`  
  
2.  Verwenden Sie die [MakeDir](../msbuild/makedir-task.md)-Aufgabe, um das Verzeichnis zu erstellen, wenn dieses noch nicht vorhanden ist. Beispiel:  
  
     `<MakeDir Directories = "$(builtdir)"`  
  
     `Condition = "!Exists('$(builtdir)')" />`  
  
## <a name="removing-the-output-items"></a>Entfernen der Ausgabeelemente  
 Bevor Sie neue Instanzen der Zwischen- und Ausgabedateien erstellen, sollten Sie alle vorherigen Instanzen der Zwischen- und Ausgabedateien löschen. Verwenden Sie die [RemoveDir](../msbuild/removedir-task.md)-Aufgabe, um ein Verzeichnis und alle enthaltenen Dateien und Verzeichnisse vom Datenträger zu löschen.  
  
#### <a name="to-remove-a-directory-and-all-files-contained-in-the-directory"></a>Entfernen eines Verzeichnisses und aller enthaltenen Dateien  
  
-   Verwenden Sie die `RemoveDir`-Aufgabe, um das Verzeichnis zu entfernen. Beispiel:  
  
     `<RemoveDir Directories="$(builtdir)" />`  
  
## <a name="example"></a>Beispiel  
 Das folgende Codebeispielprojekt enthält ein neues Ziel, `Clean`, das die `RemoveDir`-Aufgabe verwendet, um ein Verzeichnis und alle enthaltenen Dateien und Verzeichnisse zu löschen. In diesem Beispiel erstellt `Compile` ebenfalls ein separates Verzeichnis für die Ausgabeelemente, die gelöscht werden, wenn der Build bereinigt wird.  
  
 `Compile` wird als Standardziel definiert und wird darum automatisch verwendet, wenn Sie kein anderes Ziel bzw. keine anderen Ziele angeben. Verwenden Sie den Befehlszeilenschalter **/target**, um ein anderes Ziel anzugeben. Beispiel:  
  
 `msbuild <file name>.proj /target:Clean`  
  
 Der Schalter **/target** kann auf **/t** verkürzt werden und mehrere Ziele angeben. Geben Sie beispielsweise Folgendes ein, um das Ziel `Clean` und dann das Ziel `Compile` zu verwenden:  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [Exec Task (Exec-Aufgabe)](../msbuild/exec-task.md)   
 [MakeDir Task (MakeDir-Aufgabe)](../msbuild/makedir-task.md)   
 [RemoveDir Task (RemoveDir-Aufgabe)](../msbuild/removedir-task.md)   
 [Csc-Aufgabe](../msbuild/csc-task.md)   
 [Ziele](../msbuild/msbuild-targets.md)
