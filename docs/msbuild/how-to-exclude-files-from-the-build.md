---
title: "Gewusst wie: Ausschlie&#223;en von Dateien vom Buildvorgang | Microsoft Docs"
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
  - "MSBuild Platzhalter"
  - "MSBuild und Ausschließen von Dateien"
  - "Platzhalter MSBuild"
ms.assetid: 1be36e45-01da-451c-972d-f9fc0e7d663c
caps.latest.revision: 16
caps.handback.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Gewusst wie: Ausschlie&#223;en von Dateien vom Buildvorgang
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In einer Projektdatei können Sie Platzhalter verwenden, um alle Dateien in einem Verzeichnis oder einer geschachtelten Gruppe von Verzeichnissen als Eingaben für einen Build einzuschließen. Möglicherweise gibt es jedoch eine Datei im Verzeichnis oder ein Verzeichnis in einer geschachtelten Gruppe von Verzeichnissen, die nicht als Eingabe für einen Build eingeschlossen werden sollen. Sie können diese Datei oder dieses Verzeichnis explizit aus der Liste der Eingaben ausschließen. Gibt es möglicherweise eine Datei in ein Projekt, das nur unter bestimmten Umständen enthalten sein sollen. Sie können die Bedingung explizit deklarieren, unter denen eine Datei in einem Build enthalten ist.  
  
## <a name="excluding-a-file-or-directory-from-the-inputs-for-a-build"></a>Ausschließen einer Datei oder das Verzeichnis aus den Eingaben für einen Build  
 Element sind Listen die Eingabedateien für einen Build. Die Elemente, die Sie einschließen möchten werden deklariert, entweder einzeln oder als Gruppe mithilfe der `Include` Attribut. Zum Beispiel:  
  
```  
<CSFile Include="Form1.cs"/>  
<CSFile Include ="File1.cs;File2.cs"/>  
<CSFile Include="*.cs"/>  
<JPGFile Include="Images\**\*.jpg"/>  
```  
  
 Wenn Sie Platzhalter verwendet haben, um alle Dateien in einem Verzeichnis oder einer geschachtelten Gruppe von Verzeichnissen als Eingaben für einen Build einzuschließen, gibt es möglicherweise eine oder mehrere Dateien im Verzeichnis oder ein Verzeichnis in der eine geschachtelte Gruppe von Verzeichnissen, die Sie nicht einschließen möchten. Verwenden Sie zum Ausschließen eines Elements aus der Liste der `Exclude` Attribut.  
  
#### <a name="to-include-all-cs-or-vb-files-except-form2"></a>Alle cs- oder VB-Dateien außer Form2 einschließen  
  
-   Verwenden Sie eine der folgenden `Include` und `Exclude` Attribute:  
  
    ```  
    <CSFile Include="*.cs" Exclude="Form2.cs"/>  
    ```  
  
     - ODER  
  
    ```  
    <VBFile Include="*.vb" Exclude="Form2.vb"/>  
    ```  
  
#### <a name="to-include-all-cs-or-vb-files-except-form2-and-form3"></a>Alle cs- oder VB-Dateien außer Form2 und Form3 einfügen  
  
-   Verwenden Sie eine der folgenden `Include` und `Exclude` Attribute:  
  
    ```  
    <CSFile Include="*.cs" Exclude="Form2.cs;Form3.cs"/>  
    ```  
  
     - ODER  
  
    ```  
    <VBFile Include="*.vb" Exclude="Form2.vb;Form3.vb"/>  
    ```  
  
#### <a name="to-include-all-jpg-files-in-subdirectories-of-the-images-directory-except-those-in-the-version2-directory"></a>Alle JPG-Dateien in den Unterverzeichnissen des Verzeichnisses Images außer denen im Verzeichnis Version2 einschließen  
  
-   Verwenden Sie die folgenden `Include` und `Exclude` Attribute:  
  
    ```  
    <JPGFile  
        Include="Images\**\*.jpg"  
        Exclude = "Images\**\Version2\*.jpg"/>  
    ```  
  
    > [!NOTE]
    >  Sie müssen den Pfad für beide Attribute angeben. Wenn Sie einen absoluten Pfad Dateispeicherorte im Angeben der `Include` -Attribut, müssen Sie auch einen absoluten Pfad verwenden die `Exclude` Attribut, wenn Sie einen relativen Pfad im Verwenden der `Include` -Attribut, müssen Sie auch einen relativen Pfad im Verwenden der `Exclude` Attribut.  
  
## <a name="using-conditions-to-exclude-a-file-or-directory-from-the-inputs-for-a-build"></a>Mithilfe einer Datei oder das Verzeichnis der Eingaben für einen Build ausschließen  
 Wenn es Elemente, die Sie einschließen möchten, z. B. in einem Debugbuild jedoch keinen Releasebuild, können die `Condition` -Attribut zum Angeben der Bedingungen, unter denen das Element enthalten.  
  
#### <a name="to-include-the-file-formulavb-only-in-release-builds"></a>Die Datei Formula.vb nur in Releasebuilds einbeziehen  
  
-   Verwenden einer `Condition` Attribut ähnlich dem folgenden:  
  
    ```  
    <Compile  
        Include="Formula.vb"  
        Condition=" '$(Configuration)' == 'Release' " />  
    ```  
  
## <a name="example"></a>Beispiel  
 Das folgende Codebeispiel erstellt ein Projekt mit allen cs-Dateien im Verzeichnis mit Ausnahme der Form2.cs.  
  
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
 [MSBuild](../msbuild/msbuild1.md)
 [Gewusst wie: Auswählen von Dateien für den Buildvorgang](../msbuild/how-to-select-the-files-to-build.md)