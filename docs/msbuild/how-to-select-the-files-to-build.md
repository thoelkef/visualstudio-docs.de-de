---
title: "How to: Select the Files to Build | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, wildcards"
  - "MSBuild, including files"
  - "Include attribute [MSBuild]"
ms.assetid: f5ff182f-7b3a-46fb-9335-37df54cfb8eb
caps.latest.revision: 14
caps.handback.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# How to: Select the Files to Build
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wenn Sie ein Projekt erstellen, das mehrere Dateien enthält, können Sie jede Datei separat in der Projektdatei aufführen. Alternativ können Sie Platzhalter verwenden, um alle Dateien aus einem Verzeichnis oder einer verschachtelten Gruppe von Verzeichnissen einzuschließen.  
  
## Festlegen von Eingaben  
 Elemente stellen die Eingaben für einen Build dar.  Weitere Informationen zu Elementen finden Sie unter [Items](../msbuild/msbuild-items.md).  
  
 Damit Dateien für einen Build eingeschlossen werden, müssen sie in einer Elementliste in der [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]\-Projektdatei enthalten sein.  Mehrere Dateien werden in Elementlisten aufgenommen, indem Sie die Dateien entweder einzeln einschließen oder Platzhalter verwenden, um mehrere Dateien in einem Schritt einzuschließen.  
  
#### So deklarieren Sie Elemente in Einzelschritten  
  
-   Verwenden Sie mit dem folgenden Beispiel vergleichbare `Include`\-Attribute:  
  
     `<CSFile Include="form1.cs"/>`  
  
     – oder –  
  
     `<VBFile Include="form1.vb"/>`  
  
    > [!NOTE]
    >  Wenn Elemente in einer Elementauflistung nicht im selben Verzeichnis wie die Projektdatei befinden, müssen Sie den vollständigen oder relativen Pfad des Elements angeben.  Beispiel: `Include="..\..\form2.cs"`.  
  
#### So deklarieren Sie mehrere Elemente  
  
-   Verwenden Sie mit dem folgenden Beispiel vergleichbare `Include`\-Attribute:  
  
     `<CSFile Include="form1.cs;form2.cs"/>`  
  
     – oder –  
  
     `<VBFile Include="form1.vb;form2.vb"/>`  
  
## Angeben von Eingaben über Platzhalter  
 Sie können auch Platzhalter verwenden, um alle Dateien rekursiv oder nur bestimmte Dateien aus Unterverzeichnissen als Eingaben für einen Build einzuschließen.  Weitere Informationen zu Platzhaltern finden Sie unter [Items](../msbuild/msbuild-items.md).  
  
 Die folgenden Beispiele basieren auf einem Projekt, das Grafikdateien in den folgenden Verzeichnissen und Unterverzeichnissen enthält. Die Projektdatei befindet sich im Verzeichnis Project:  
  
 Project\\Images\\BestJpgs  
  
 Project\\Images\\ImgJpgs  
  
 Project\\Images\\ImgJpgs\\Img1  
  
#### So schließen Sie alle JPG\-Dateien aus dem Verzeichnis Images und seinen Unterverzeichnissen ein  
  
-   Verwenden Sie das folgende `Include`\-Attribut:  
  
     `Include="Images\**\*.jpg"`  
  
#### So schließen Sie alle JPG\-Dateien ein, die mit "img" beginnen  
  
-   Verwenden Sie das folgende `Include`\-Attribut:  
  
     `Include="Images\**\img*.jpg"`  
  
#### So schließen Sie alle Dateien aus Verzeichnissen ein, deren Namen auf "jpgs" enden  
  
-   Verwenden Sie eines der folgenden `Include`\-Attribute:  
  
     `Include="Images\**\*jpgs\*.*"`  
  
     – oder –  
  
     `Include="Images\**\*jpgs\*"`  
  
## Übergeben von Elementen an eine Aufgabe  
 In einer Projektdatei können Sie die @\(\)\-Notation in Aufgaben verwenden, um eine vollständige Elementliste als Eingabe für einen Build anzugeben.  Diese Notation kann unabhängig davon verwendet werden, ob Sie alle Dateien separat aufführen oder Platzhalter einsetzen.  
  
#### So verwenden Sie alle Visual C\#\- oder Visual Basic\-Dateien als Eingaben  
  
-   Verwenden Sie mit dem folgenden Beispiel vergleichbare `Include`\-Attribute:  
  
     `<CSC Sources="@(CSFile)">...</CSC>`  
  
     – oder –  
  
     `<VBC Sources="@(VBFile)">...</VBC>`  
  
> [!NOTE]
>  Um Eingaben für einen Build anzugeben, müssen Sie Platzhalter mit Elementen verwenden. Das `Sources`\-Attribut in [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]\-Aufgaben, wie [Csc](../msbuild/csc-task.md) oder [Vbc](../msbuild/vbc-task.md), kann zu diesem Zweck nicht verwendet werden.  Das folgende Beispiel ist in einer Projektdatei nicht gültig:  
>   
>  `<CSC Sources="*.cs">...</CSC>`  
  
## Beispiel  
 Im folgenden Codebeispiel wird ein Projekt dargestellt, bei dem alle Eingabedateien getrennt eingeschlossen werden.  
  
```  
<Project DefaultTargets="Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
    <PropertyGroup>  
        <Builtdir>built</Builtdir>  
    </PropertyGroup>  
  
    <ItemGroup>  
        <CSFile Include="Form1.cs"/>  
        <CSFile Include="AssemblyInfo.cs"/>  
  
        <Reference Include="System.dll"/>  
        <Reference Include="System.Data.dll"/>  
        <Reference Include="System.Drawing.dll"/>  
        <Reference Include="System.Windows.Forms.dll"/>  
        <Reference Include="System.XML.dll"/>  
    </ItemGroup>  
  
    <Target Name="PreBuild">  
        <Exec Command="if not exist $(builtdir) md $(builtdir)"/>  
    </Target>  
  
    <Target Name="Compile" DependsOnTargets="PreBuild">  
        <Csc Sources="@(CSFile)"  
            References="@(Reference)"  
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).exe"  
            TargetType="exe" />  
    </Target>  
</Project>  
```  
  
## Beispiel  
 Im folgenden Codebeispiel wird ein Platzhalter verwendet, um alle CS\-Dateien einzuschließen.  
  
```  
<Project DefaultTargets="Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <PropertyGroup>  
        <builtdir>built</builtdir>  
    </PropertyGroup>  
  
    <ItemGroup>  
        <CSFile Include="*.cs"/>  
  
        <Reference Include="System.dll"/>  
        <Reference Include="System.Data.dll"/>  
        <Reference Include="System.Drawing.dll"/>  
        <Reference Include="System.Windows.Forms.dll"/>  
        <Reference Include="System.XML.dll"/>  
    </ItemGroup>  
  
    <Target Name="PreBuild">  
        <Exec Command="if not exist $(builtdir) md $(builtdir)"/>  
    </Target>  
  
    <Target Name="Compile" DependsOnTargets="PreBuild">  
        <Csc Sources="@(CSFile)"  
            References="@(Reference)"  
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).exe"  
            TargetType="exe" />  
    </Target>  
</Project>  
```  
  
## Siehe auch  
 [How to: Exclude Files from the Build](../msbuild/how-to-exclude-files-from-the-build.md)   
 [Items](../msbuild/msbuild-items.md)