---
title: 'Vorgehensweise: Auswählen von Dateien für den Buildvorgang | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, wildcards
- MSBuild, including files
- Include attribute [MSBuild]
ms.assetid: f5ff182f-7b3a-46fb-9335-37df54cfb8eb
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 276d3306d908fa8af4e58f38c965b73c1fff9284
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2019
ms.locfileid: "59659813"
---
# <a name="how-to-select-the-files-to-build"></a>Vorgehensweise: Auswählen von Dateien für den Buildvorgang
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie ein Projekt erstellen, das mehrere Dateien enthält, können Sie jede Datei einzeln in der Projektdatei auflisten. Alternativ können Sie Platzhalter nutzen, um alle Dateien in ein Verzeichnis oder in einen geschachtelten Satz von Verzeichnissen einzufügen.  
  
## <a name="specifying-inputs"></a>Angeben von Eingaben  
 Elemente stellen die Eingaben für einen Build dar. Weitere Informationen zu Elementen finden Sie unter [Items (Elemente)](../msbuild/msbuild-items.md).  
  
 Damit Dateien für einen Build eingeschlossen werden können, müssen sie in einer Elementliste in der Projektdatei [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] aufgeführt sein. Es können mehrere Dateien einer Elementliste hinzugefügt werden, indem die Dateien entweder einzeln oder mithilfe von Platzhaltern eingefügt werden, mit denen viele Dateien gleichzeitig eingefügt werden können.  
  
#### <a name="to-declare-items-individually"></a>So deklarieren Sie Elemente einzeln  
  
-   Verwenden Sie die `Include`-Attribute, ähnlich wie folgt:  
  
     `<CSFile Include="form1.cs"/>`  
  
     – oder –  
  
     `<VBFile Include="form1.vb"/>`  
  
    > [!NOTE]
    >  Wenn sich Elemente in einer Elementauflistung nicht im gleichen Verzeichnis wie die Projektdatei befinden, müssen Sie den vollständigen oder relativen Pfad des Elements angeben. Beispiel: `Include="..\..\form2.cs"`.  
  
#### <a name="to-declare-multiple-items"></a>So deklarieren Sie mehrere Elemente  
  
-   Verwenden Sie die `Include`-Attribute, ähnlich wie folgt:  
  
     `<CSFile Include="form1.cs;form2.cs"/>`  
  
     – oder –  
  
     `<VBFile Include="form1.vb;form2.vb"/>`  
  
## <a name="specifying-inputs-with-wildcards"></a>Angeben von Eingaben mit Platzhaltern  
 Sie können auch Platzhalter verwenden, um rekursiv alle Dateien oder nur bestimmte Dateien aus Unterverzeichnissen als Eingaben für einen Build einzufügen. Weitere Informationen zu Elementen finden Sie unter [Items (Elemente)](../msbuild/msbuild-items.md).  
  
 Die folgenden Beispiele basieren auf einem Projekt, das Grafikdateien in den folgenden Verzeichnissen und Unterverzeichnissen enthält, wobei sich die Projektdatei im Verzeichnis „Project“ befindet.  
  
 Project\Images\BestJpgs  
  
 Project\Images\ImgJpgs  
  
 Project\Images\ImgJpgs\Img1  
  
#### <a name="to-include-all-jpg-files-in-the-images-directory-and-subdirectories"></a>So schließen Sie alle JPG-Dateien im Verzeichnis „Images“ bzw. in Unterverzeichnissen ein  
  
-   Verwenden Sie das folgende `Include`-Attribut:  
  
     `Include="Images\**\*.jpg"`  
  
#### <a name="to-include-all-jpg-files-starting-with-img"></a>So schließen Sie alle JPG-Dateien ein, die mit „img“ beginnen  
  
-   Verwenden Sie das folgende `Include`-Attribut:  
  
     `Include="Images\**\img*.jpg"`  
  
#### <a name="to-include-all-files-in-directories-with-names-ending-in-jpgs"></a>So schließen Sie alle Dateien in Verzeichnissen ein, die mit „jpgs“ enden  
  
-   Ändern Sie eines der folgenden `Include`-Attribute:  
  
     `Include="Images\**\*jpgs\*.*"`  
  
     – oder –  
  
     `Include="Images\**\*jpgs\*"`  
  
## <a name="passing-items-to-a-task"></a>Übergeben von Elementen an eine Aufgabe  
 Sie können in einer Projektdatei die Notation „@()“ in Aufgaben verwenden, um eine gesamte Elementliste als Eingabe für einen Build anzugeben. Sie können diese Notation verwenden, egal ob Sie alle Dateien einzeln auflisten oder Platzhalter verwenden.  
  
#### <a name="to-use-all-visual-c-or-visual-basic-files-as-inputs"></a>So verwenden Sie alle Visual C#- oder Visual Basic-Dateien als Eingabe  
  
-   Verwenden Sie die `Include`-Attribute ähnlich wie folgt:  
  
     `<CSC Sources="@(CSFile)">...</CSC>`  
  
     – oder –  
  
     `<VBC Sources="@(VBFile)">...</VBC>`  
  
> [!NOTE]
>  Sie müssen Platzhalter mit Elementen verwenden, um die Eingaben für einen Build anzugeben. Sie können keine Eingaben mithilfe des `Sources`-Attributs in [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]-Aufgaben verwenden, wie z.B. [Ccs](../msbuild/csc-task.md) oder [Vbc](../msbuild/vbc-task.md). Das folgende Beispiel ist in einer Projektdatei nicht gültig:  
>   
>  `<CSC Sources="*.cs">...</CSC>`  
  
## <a name="example"></a>Beispiel  
 Das folgende Codebeispiel zeigt ein Projekt, das alle Eingabedateien separat einschließt.  
  
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
  
## <a name="example"></a>Beispiel  
 Das folgende Codebeispiel verwendet einen Platzhalter, um alle CS-Dateien einzuschließen.  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Ausschließen von Dateien vom Buildvorgang](../msbuild/how-to-exclude-files-from-the-build.md)   
 [Elemente](../msbuild/msbuild-items.md)
