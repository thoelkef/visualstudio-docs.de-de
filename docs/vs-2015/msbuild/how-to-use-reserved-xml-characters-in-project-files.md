---
title: 'Vorgehensweise: Verwenden reservierter XML-Zeichen in Projektdateien | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, using reserved XML characters
- MSBuild, reserved XML characters
ms.assetid: 1ae37275-96bf-4e6e-897b-6b048e5bbe93
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 709643cf082e8018153459845bba55fa133d1332
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2019
ms.locfileid: "59656253"
---
# <a name="how-to-use-reserved-xml-characters-in-project-files"></a>Gewusst wie: Verwenden reservierter XML-Zeichen in Projektdateien
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie Projektdateien erstellen, müssen Sie reservierte XML-Zeichen verwenden, z.B. in Eigenschaftswerten oder Aufgabenparameterwerten. Einige reservierte Zeichen müssen jedoch durch eine benannte Entität ersetzt werden, sodass die Projektdatei analysiert werden kann.  
  
## <a name="using-reserved-characters"></a>Reservierte Zeichen verwenden  
 Die folgende Tabelle beschreibt die reservierten XML-Zeichen, die durch die entsprechende benannte Entität ersetzt werden müssen, damit die Projektdatei analysiert werden kann.  
  
|Reserviertes Zeichen|Benannte Entität|  
|------------------------|------------------|  
|\<|&lt;|  
|>|&gt;|  
|&|&amp;|  
|"|&quot;|  
|'|&apos;|  
  
#### <a name="to-use-double-quotes-in-a-project-file"></a>Doppelte Anführungszeichen in einer Projektdatei verwenden  
  
-   Ersetzen Sie die doppelten Anführungszeichen durch die entsprechende benannte Entität &quot;. Um beispielsweise doppelte Anführungszeichen um die `EXEFile`-Elementliste zu setzen, geben Sie Folgendes ein:  
  
    ```  
    <Message Text="The output file is "@(EXEFile)"."/>  
    ```  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel werden doppelte Anführungszeichen zum Markieren des Dateinamens in der Meldung benutzt, die von der Projektdatei ausgegeben wird.  
  
```  
<Project DefaultTargets="Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
    <!-- Set the application name as a property -->  
    <PropertyGroup>  
        <appname>"HelloWorldCS"</appname>  
    </PropertyGroup>  
    <!-- Specify the inputs -->  
    <ItemGroup>  
        <CSFile Include = "consolehwcs1.cs" />  
    </ItemGroup>  
    <Target Name = "Compile">  
        <!-- Run the Visual C# compilation using input  
        files of type CSFile -->  
        <Csc Sources = "@(CSFile)">  
            <!-- Set the OutputAssembly attribute of the CSC task  
            to the name of the executable file that is created -->  
            <Output  
                TaskParameter = "OutputAssembly"  
                ItemName = "EXEFile"/>  
        </Csc>  
        <!-- Log the file name of the output file -->  
        <Message Text="The output file is "@(EXEFile)"."/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MSBuild-Referenz](../msbuild/msbuild-reference.md) [MSBuild](msbuild.md)
