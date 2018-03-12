---
title: 'Vorgehensweise: Verweisen auf den Namen oder Speicherort der Projektdatei | Microsoft-Dokumentation'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- locations, referencing
- locations
- MSBuildProjectName property
- MSBuild, referencing the project file
- names, referencing
- reserved properties
- project files, referencing
ms.assetid: c8fcc594-5d37-4e2e-b070-4d9c012043b5
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 7a688473b4657d905397d4798451b4860578ef0d
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="how-to-reference-the-name-or-location-of-the-project-file"></a>Gewusst wie: Verweisen auf den Namen oder Speicherort der Projektdatei
Sie können den Namen oder Speicherort des Projekts in der Projektdatei verwenden, selbst ohne eine eigene Eigenschaft erstellt zu haben. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] stellt reservierte Eigenschaften zur Verfügung, die auf die Projektdateinamen sowie andere Eigenschaften verweisen, die zum Projekt gehören. Weitere Informationen zu reservierten Eigenschaften finden Sie unter [Reservierte und bekannte Eigenschaften für MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md).  
  
## <a name="using-the-msbuildprojectname-property"></a>Verwenden der MSBuildProjectName-Eigenschaft  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] stellt einige reservierte Eigenschaften bereit, die Sie in den Projektdateien verwenden können, ohne diese jedes Mal zu definieren. Beispiel: Die reservierte Eigenschaft `MSBuildProjectName` stellt einen Verweis zum Projektdateinamen bereit.  
  
#### <a name="to-use-the-msbuildprojectname-property"></a>So verwenden Sie die MSBuildProjectName-Eigenschaft  
  
-   Verweisen Sie die Eigenschaft in der Projektdatei mit der $()-Notation genau so, wie Sie es mit anderen Eigenschaften machen würden. Zum Beispiel:  
  
    ```xml  
    <CSC Sources = "@(CSFile)"   
        OutputAssembly = "$(MSBuildProjectName).exe"/>  
    </CSC>  
    ```  
  
 Ein Vorteil der Verwendung einer reservierten Eigenschaft ist, dass alle Änderungen am Projektdateinamen automatisch integriert sind. Das nächste Mal, wenn Sie das Projekt erstellen, wird die Ausgabedatei den neuen Namen haben, ohne dass von Ihnen Handlungsbedarf besteht.  
  
> [!NOTE]
>  Reservierte Eigenschaften können nicht in der Projektdatei neu definiert werden.  
  
## <a name="example"></a>Beispiel  
 Die folgende Beispiel-Projektdatei verweist den Projektnamen als reservierte Eigenschaft, um den Namen für die Ausgabe anzugeben.  
  
```xml  
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
[MSBuild](../msbuild/msbuild.md)  
 [Reservierte und bekannte Eigenschaften für MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md)