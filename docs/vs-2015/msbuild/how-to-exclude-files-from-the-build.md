---
title: 'Vorgehensweise: Ausschließen von Dateien vom Buildvorgang | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, wildcards
- MSBuild, excluding files
- wildcards, MSBuild
ms.assetid: 1be36e45-01da-451c-972d-f9fc0e7d663c
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: eb390e98b8650764dfc9f4237f150a5b903f1618
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54796723"
---
# <a name="how-to-exclude-files-from-the-build"></a>Gewusst wie: Ausschließen von Dateien vom Buildvorgang
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Sie können in einer Projektdatei Platzhalter verwenden, um alle Dateien in einem Verzeichnis oder einer geschachtelten Gruppe von Verzeichnissen als Eingaben für einen Buildvorgang einzuschließen. Möglicherweise gibt es jedoch eine Datei im Verzeichnis oder ein Verzeichnis in einer geschachtelten Gruppe von Verzeichnissen, die nicht als Eingabe für einen Buildvorgang eingeschlossen werden sollen. Sie können diese Datei oder dieses Verzeichnis explizit aus der Liste der Eingaben ausschließen. Vielleicht gibt es auch eine Datei in einem Projekt, das Sie nur unter bestimmten Umständen miteinbeziehen wollen. Sie können die Bedingungen explizit deklarieren, unter denen eine Datei in einem Buildvorgang enthalten ist.  
  
## <a name="excluding-a-file-or-directory-from-the-inputs-for-a-build"></a>Ausschließen einer Datei oder eines Verzeichnis aus den Eingaben für einen Buildvorgang  
 Elementlisten sind die Eingabedateien für einen Buildvorgang. Die Elemente, die Sie einschließen möchten, werden entweder einzeln oder als Gruppe mithilfe des Attributs `Include` deklariert. Beispiel:  
  
```  
<CSFile Include="Form1.cs"/>  
<CSFile Include ="File1.cs;File2.cs"/>  
<CSFile Include="*.cs"/>  
<JPGFile Include="Images\**\*.jpg"/>  
```  
  
 Wenn Sie Platzhalter verwendet haben, um alle Dateien in einem Verzeichnis oder einer geschachtelten Gruppe von Verzeichnissen als Eingaben für einen Buildvorgang einzuschließen, gibt es möglicherweise eine oder mehrere Dateien im Verzeichnis oder ein Verzeichnis in einer geschachtelten Gruppe von Verzeichnissen, die Sie nicht einschließen möchten. So verwenden Sie das Attribut `Exclude` zum Ausschließen eines Elements aus der Elementliste.  
  
#### <a name="to-include-all-cs-or-vb-files-except-form2"></a>So schließen Sie alle CS- oder VB-Dateien außer Form2 ein.  
  
-   Ändern Sie eines der folgenden Attribute `Include` und `Exclude`:  
  
    ```  
    <CSFile Include="*.cs" Exclude="Form2.cs"/>  
    ```  
  
     - ODER  
  
    ```  
    <VBFile Include="*.vb" Exclude="Form2.vb"/>  
    ```  
  
#### <a name="to-include-all-cs-or-vb-files-except-form2-and-form3"></a>So schließen Sie alle CS- oder VB-Dateien außer Form2 und Form3 ein.  
  
-   Ändern Sie eines der folgenden Attribute `Include` und `Exclude`:  
  
    ```  
    <CSFile Include="*.cs" Exclude="Form2.cs;Form3.cs"/>  
    ```  
  
     - ODER  
  
    ```  
    <VBFile Include="*.vb" Exclude="Form2.vb;Form3.vb"/>  
    ```  
  
#### <a name="to-include-all-jpg-files-in-subdirectories-of-the-images-directory-except-those-in-the-version2-directory"></a>So schließen Sie alle JPG-Dateien in Unterverzeichnisse des Imageverzeichnisses ein, außer den Dateien im Version2-Verzeichnis.  
  
-   Verwenden Sie die folgenden Attribute `Include` und `Exclude`:  
  
    ```  
    <JPGFile  
        Include="Images\**\*.jpg"  
        Exclude = "Images\**\Version2\*.jpg"/>  
    ```  
  
    > [!NOTE]
    >  Sie müssen den Pfad für beide Attribute angeben. Wenn Sie einen absoluten Pfad zum Angeben von Dateispeicherorten im Attribut `Include` verwenden, müssen Sie auch einen absoluten Pfad im Attribut `Exclude` verwenden. Verwenden Sie einen relativen Pfad im Attribut `Include`, müssen Sie auch einen relativen Pfad im Attribut `Exclude` verwenden.  
  
## <a name="using-conditions-to-exclude-a-file-or-directory-from-the-inputs-for-a-build"></a>Verwenden von Bedingungen zum Ausschließen einer Datei oder eines Verzeichnis aus den Eingaben für einen Buildvorgang  
 Wenn es Elemente gibt, die Sie einschließen möchten, z.B. in einem Debugebuild, aber nicht in einem Releasebuild, können Sie das Element `Condition` verwenden, um die Bedingungen anzugeben, unter denen Sie das Element einschließen möchten.  
  
#### <a name="to-include-the-file-formulavb-only-in-release-builds"></a>So schließen Sie die Formula.vb-Datei nur in Releasebuilds ein  
  
-   Verwenden Sie Attribut `Condition`, das ähnlich des Folgenden ist:  
  
    ```  
    <Compile  
        Include="Formula.vb"  
        Condition=" '$(Configuration)' == 'Release' " />  
    ```  
  
## <a name="example"></a>Beispiel  
 Das folgende Codebeispiel erstellt ein Projekt mit allen CS-Dateien im Verzeichnis, außer Form2.cs.  
  
```  
<Project DefaultTargets="Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <PropertyGroup>  
        <builtdir>built</builtdir>  
    </PropertyGroup>  
  
    <ItemGroup>  
        <CSFile Include="*.cs Exclude="Form2.cs"/>  
  
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
 [Elemente](../msbuild/msbuild-items.md)   
 [MSBuild](msbuild.md) [Vorgehensweise: Auswählen von Dateien für den Buildvorgang](../msbuild/how-to-select-the-files-to-build.md)
