---
title: "Gewusst wie: Verweisen auf den Namen oder Speicherort der Projektdatei | Microsoft Docs"
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
  - "Speicherorte, verweisen auf"
  - "Speicherorte"
  - "MSBuildProjectName-Eigenschaft"
  - "Verweisen auf die Projektdatei MSBuild"
  - "Namen, verweisen auf"
  - "Reservierte Eigenschaften"
  - "Verweisen auf Projektdateien."
ms.assetid: c8fcc594-5d37-4e2e-b070-4d9c012043b5
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Gewusst wie: Verweisen auf den Namen oder Speicherort der Projektdatei
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können den Namen oder Speicherort des Projekts in der Projektdatei selbst ohne eine eigene Eigenschaft erstellen verwenden. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] Stellt reservierte Eigenschaften, die den Namen der Projektdatei und andere Eigenschaften in Bezug auf das Projekt bereit. Weitere Informationen zu reservierten Eigenschaften finden Sie unter [MSBuild reservierte und bekannte Eigenschaften](../msbuild/msbuild-reserved-and-well-known-properties.md).  
  
## <a name="using-the-msbuildprojectname-property"></a>Verwenden der MSBuildProjectName-Eigenschaft  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] stellt einige reservierten Eigenschaften, die Sie in den Projektdateien verwenden können, ohne dass sie jedes Mal zu definieren. Angenommen, die reservierte Eigenschaft `MSBuildProjectName` stellt einen Verweis auf den Namen der Projektdatei.  
  
#### <a name="to-use-the-msbuildprojectname-property"></a>Verwenden Sie die MSBuildProjectName-Eigenschaft  
  
-   Verweisen Sie die Eigenschaft in der Projektdatei mit der $-Notation (), wie Sie jede Eigenschaft. Zum Beispiel:  
  
    ```  
    <CSC Sources = "@(CSFile)"   
        OutputAssembly = "$(MSBuildProjectName).exe"/>  
    </CSC>  
    ```  
  
 Ein Vorteil der Verwendung einer reservierten Eigenschaft ist, dass alle Änderungen an den Namen der Projektdatei automatisch integriert sind. Beim nächsten des Projekts erstellen wird keine weitere Aktion erforderlich die Ausgabedatei den neuen Namen haben.  
  
> [!NOTE]
>  Reservierte Eigenschaften können nicht in der Projektdatei neu definiert werden.  
  
## <a name="example"></a>Beispiel  
 Die folgende Beispiel-Projektdatei verweist den Projektnamen als reservierte Eigenschaft den Namen für die Ausgabe angeben.  
  
```  
<Project xmlns="http://scheams.microsoft.com/developer/msbuild/2003"   
    DefaultTargets = "Compile">  
  
    <!-- Specify the inputs -->  
    <ItemGroup>  
        <CSFile Include = "consolehwcs1.cs"/>  
    </ItemGroup>  
    <Target Name = "Compile">  
        <!-- Run the Visual C# compilation using  
        input files of type CSFile -->  
        <CSC Sources = "@(CSFile)"  
            OutputAssembly = "$(MSBuildProjectName).exe" >  
            <!-- Set the OutputAssembly attribute of the CSC task  
            to the name of the project -->  
            <Output  
                TaskParameter = "OutputAssembly"  
                ItemName = "EXEFile" />  
        </CSC>  
        <!-- Log the file name of the output file -->  
        <Message Text="The output file is @(EXEFile)"/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Siehe auch  
[MSBuild](../msbuild/msbuild1.md)  
 [MSBuild reservierte und bekannte Eigenschaften](../msbuild/msbuild-reserved-and-well-known-properties.md)